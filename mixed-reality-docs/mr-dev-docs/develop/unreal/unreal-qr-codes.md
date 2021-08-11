---
title: Codici a matrice in Unreal
description: Informazioni su come configurare, usare e tenere traccia dei codici a matrice nelle applicazioni di realtà mista Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 689ebe9b904b269c00078245b137bc21f2e56df2b441150c7c6b18c179ac51f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205125"
---
# <a name="qr-codes-in-unreal"></a>Codici a matrice in Unreal

HoloLens 2 può individuare i codici a matrice nello spazio globale usando la webcam, eseguendone il rendering come ologrammi nella posizione reale di ciascun codice. HoloLens 2 è in grado di eseguire il rendering degli ologrammi nella stessa posizione su più dispositivi per creare un'esperienza condivisa. Assicurati di seguire le procedure consigliate per l'aggiunta di codici a matrice alle tue applicazioni:

- Zone silenziose
- Illuminazione e sfondo
- Dimensione, distanza e posizione angolare

Presta particolare attenzione alle [considerazioni sull'ambiente](/hololens/hololens-environment-considerations) quando vengono inseriti codici a matrice nell'app. Per altre informazioni su questi argomenti e per istruzioni su come scaricare il pacchetto NuGet necessario, vedi il documento principale [Rilevamento di codici a matrice](../platform-capabilities-and-apis/qr-code-tracking.md).

> [!CAUTION]
> I codici a matrice sono l'unico tipo di immagini che possono essere rilevate da HoloLens automaticamente. Il modulo **UARTrackedImage** di Unreal non è supportato in HoloLens. Se è necessario rilevare immagini personalizzate, è possibile accedere alla [webcam](unreal-hololens-camera.md) del dispositivo ed elaborare le immagini usando una libreria di riconoscimento immagini di terze parti. 

## <a name="enabling-qr-detection"></a>Abilitazione del rilevamento di codici a matrice

Dato che HoloLens 2 deve usare la webcam per visualizzare i codici a matrice, è necessario abilitarla nelle impostazioni del progetto:
- Aprire **Edit > Project Settings** (Modifica > Impostazioni progetto), scorrere fino alla sezione **Platforms** (Piattaforme) e selezionare **HoloLens**.
    + Espandi la sezione **Capabilities** (Funzionalità) e seleziona **Webcam**.  
- Devi anche acconsentire esplicitamente al rilevamento dei codici a matrice [aggiungendo un asset ARSessionConfig](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Configurazione di un codice a matrice rilevato

I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata. Per procedere, è necessario:
1. Creare un attore di progetto e aggiungere un componente **ARTrackableNotify**:

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Selezionare **ARTrackableNotify** ed espandere la sezione **Events** (Eventi) nel pannello **Details** (Dettagli):

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

3. Fare clic su **+** accanto a **On Add Tracked Geometry** (All'aggiunta della geometria rilevata) per aggiungere il nodo in Event Graph (Grafico eventi).
    - L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Aggiungere il nodo a On Add Tracked Geometry (All'aggiunta della geometria rilevata)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Uso di un codice a matrice rilevato

Il grafico degli eventi nell'immagine seguente mostra l'evento **OnUpdateTrackedImage** usato per eseguire il rendering di un punto al centro di un codice a matrice e stamparne i dati.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Ecco cosa accade:
1. Prima di tutto, viene eseguito il cast dell'immagine rilevata in un codice **ARTrackedQRCode** per verificare che l'immagine aggiornata corrente sia un codice a matrice.  
2. I dati codificati vengono recuperati dalla variabile **QRCode**. È possibile ottenere la parte superiore sinistra del codice a matrice dalla posizione di **GetLocalToWorldTransform** e le dimensioni con **GetEstimateSize**.

È anche possibile [ottenere il sistema di coordinate per un codice a matrice](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) nel codice.

## <a name="finding-the-unique-id"></a>Ricerca dell'ID univoco

Ogni codice a matrice ha un ID GUID univoco. Per trovarlo:
- Trascina e rilascia il segnaposto **As ARTracked QRCode** e cerca **Get Unique ID** (Ottieni ID univoco).

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

Le operazioni sui codici a matrice sono piuttosto complesse, quindi ci sono diversi aspetti da approfondire. I collegamenti riportati di seguito consentono di accedere a informazioni più dettagliate a questo proposito.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Distribuzione nel dispositivo](unreal-deploying.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#3-advanced-features) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](../../design/spatial-mapping.md)
* [Ologrammi](../../discover/hologram.md)
* [Sistemi di coordinate](../../design/coordinate-systems.md)