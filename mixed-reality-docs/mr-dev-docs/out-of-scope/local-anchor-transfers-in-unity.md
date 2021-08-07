---
title: Trasferimenti di ancoraggi locali in Unity
description: Informazioni su come trasferire ancoraggi tra più dispositivi HoloLens in un'applicazione unity di realtà mista.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transfer, local anchor transfer, anchor export, anchor import
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189128"
---
# <a name="local-anchor-transfers-in-unity"></a>Trasferimenti di ancoraggi locali in Unity

Nei casi in cui non è possibile usare Ancoraggi nello stato di <a href="/azure/spatial-anchors" target="_blank">Azure,</a>i trasferimenti di ancoraggio locali consentono HoloLens un dispositivo di esportare un ancoraggio da importare da un secondo HoloLens dispositivo.

>[!NOTE]
>I trasferimenti di ancoraggio locali offrono un richiamo dell'ancoraggio meno affidabile rispetto ad Ancoraggi nello spazio di <a href="/azure/spatial-anchors" target="_blank">Azure</a>e i dispositivi iOS e Android non sono supportati da questo approccio.

### <a name="setting-the-spatialperception-capability"></a>Impostazione della funzionalità SpatialPerception

Per consentire a un'app di trasferire ancoraggi spaziali, è necessario che sia abilitata la funzionalità *SpatialPerception.*

Come abilitare la *funzionalità SpatialPerception:*
1. Nell'editor unity aprire il riquadro **"Player Impostazioni"** (Modifica > Project Impostazioni > Lettore)
2. Fare clic sulla **scheda "Windows Store"**
3. Espandere **"Pubblicazione Impostazioni"** e controllare la **funzionalità "SpatialPerception"** nell'elenco **"Funzionalità"**

>[!NOTE]
>Se il progetto Unity è già stato esportato in una soluzione Visual Studio, è necessario esportare in una nuova cartella o impostare manualmente questa funzionalità [in AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Trasferimento dell'ancoraggio

**Spazio dei nomi:** *UnityEngine.XR.WSA.Sharing*<br>
**Tipo:** *WorldAnchorTransferBatch*

Per trasferire un [Oggetto WorldAnchor,](../develop/unity/coordinate-systems-in-unity.md)è necessario stabilire l'ancoraggio da trasferire. L'utente di un HoloLens analizza l'ambiente e sceglie manualmente o a livello di codice un punto nello spazio come ancoraggio per l'esperienza condivisa. I dati che rappresentano questo punto possono quindi essere serializzati e trasmessi agli altri dispositivi che condividono nell'esperienza. Ogni dispositivo de serializza quindi i dati di ancoraggio e tenta di individuare tale punto nello spazio. Per consentire il funzionamento del trasferimento di ancoraggi, ogni dispositivo deve avere analizzato un numero sufficiente di ambienti in modo che sia possibile identificare il punto rappresentato dall'ancoraggio.

### <a name="setup"></a>Eseguire la configurazione

Il codice di esempio in questa pagina include alcuni campi che dovranno essere inizializzati:
1. *GameObject rootGameObject* è un *GameObject* in Unity con un *componente WorldAnchor.* Un utente nell'esperienza condivisa inserirà *questo GameObject* ed esporterà i dati agli altri utenti.
2. *WorldAnchor gameRootAnchor* è *UnityEngine.XR.WSA.WorldAnchor* che si trova in *rootGameObject.*
3. *byte[] importedData* è una matrice di byte per l'ancoraggio serializzato che ogni client riceve in rete.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Esportazione

Per esportare, è sufficiente *un WorldAnchor* e sapere come verrà chiamato in modo che sia sensato per l'app ricevente. Un client nell'esperienza condivisa eseguirà questi passaggi per esportare l'ancoraggio condiviso:
1. Creare un *Oggetto WorldAnchorTransferBatch*
2. Aggiungere gli *elementi WorldAnchors* da trasferire
3. Avviare l'esportazione
4. Gestire *l'evento OnExportDataAvailable* quando i dati diventano disponibili
5. Gestire *l'evento OnExportComplete*

Viene creato un *oggetto WorldAnchorTransferBatch* per incapsulare ciò che verrà trasferito e quindi esportato in byte:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Quando i dati diventano disponibili, inviare i byte al client o al buffer quando i segmenti di dati sono disponibili e inviare tramite qualsiasi mezzo desiderato:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Al termine dell'esportazione, se i dati sono stati trasferiti e la serializzazione non è riuscita, indicare al client di rimuovere i dati. Se la serializzazione ha avuto esito positivo, indicare al client che tutti i dati sono stati trasferiti e che l'importazione può essere avviata:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importazione

Dopo aver ricevuto tutti i byte dal mittente, è possibile importare di nuovo i dati in *un Oggetto WorldAnchorTransferBatch* e bloccare l'oggetto di gioco radice nella stessa posizione fisica. Nota: l'importazione a volte avrà esito negativo temporaneo e deve essere ritentata:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Dopo essere stato bloccato tramite la chiamata *LockObject,* un *GameObject* avrà un *WorldAnchor* che lo manterà nella stessa posizione fisica del mondo, ma potrebbe essere in una posizione diversa nello spazio delle coordinate di Unity rispetto ad altri utenti.