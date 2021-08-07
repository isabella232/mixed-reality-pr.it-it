---
title: Persistenza in Unity
description: La persistenza consente all'utente di aggiungere singoli ologrammi ovunque vogliano e quindi di trovarlo in un secondo momento su molti usi dell'app.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistenza, Unity, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208971"
---
# <a name="persistence-in-unity"></a>Persistenza in Unity

**Spazio dei nomi:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

WorldAnchorStore è la chiave per creare esperienze olografiche in cui gli ologrammi rimangono in posizioni reali specifiche tra istanze dell'applicazione. Gli utenti possono quindi aggiungere singoli ologrammi dove vogliono e trovarli in un secondo momento nello stesso punto per molti usi dell'app.

## <a name="how-to-persist-holograms-across-sessions"></a>Come rendere persistenti gli ologrammi tra le sessioni

WorldAnchorStore consente di rendere persistente la posizione di WorldAnchor tra le sessioni. Per rendere persistenti gli ologrammi tra le sessioni, è necessario tenere traccia separatamente degli oggetti GameObject che usano un ancoraggio mondo specifico. Spesso è opportuno creare una radice GameObject con un ancoraggio mondo e avere ologrammi figlio ancorati con un offset di posizione locale.

Per caricare ologrammi dalle sessioni precedenti:
1. Ottenere WorldAnchorStore
2. Caricare i dati dell'app relativi all'ancoraggio del mondo, che fornisce l'ID dell'ancoraggio del mondo
3. Caricare un ancoraggio mondo dal relativo ID

Per salvare gli ologrammi per le sessioni future:
1. Ottenere WorldAnchorStore
2. Salvare un ancoraggio mondo specificando un ID
3. Salvare i dati dell'app relativi all'ancoraggio mondiale insieme a un ID

### <a name="getting-the-worldanchorstore"></a>Recupero di WorldAnchorStore

È necessario mantenere un riferimento a WorldAnchorStore per sapere quando è pronto per eseguire un'operazione. Poiché si tratta di una chiamata asincrona, potenzialmente non appena si avvia, si vuole chiamare:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded in questo caso è il gestore per quando WorldAnchorStore ha completato il caricamento:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

È ora disponibile un riferimento a WorldAnchorStore, che verrà utilizzato per salvare e caricare ancoraggi del mondo specifici.

### <a name="saving-a-worldanchor"></a>Salvataggio di un oggetto WorldAnchor

Per salvare, è sufficiente assegnare un nome a ciò che si sta salvando e passarlo all'oggetto WorldAnchor ottenuto in precedenza quando si vuole salvare. Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (archivio. Save restituirà false. Eliminare il salvataggio precedente prima di salvare quello nuovo:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Caricamento di un oggetto WorldAnchor

E per caricare:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

È anche possibile usare l'archivio. Delete() per rimuovere un ancoraggio salvato e salvato in precedenza. Clear() per rimuovere tutti i dati salvati in precedenza.

### <a name="enumerating-existing-anchors"></a>Enumerazione di ancoraggi esistenti

Per individuare ancoraggi archiviati in precedenza, chiamare GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Salvataggio permanente di ologrammi per più dispositivi

È possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi</a> nello stato di Azure per creare un ancoraggio cloud durevole da un WorldAnchor locale, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.  Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il rendering del contenuto relativo a tale ancoraggio nella stessa posizione fisica.

Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity di</a>5 minuti.

Dopo aver eseguito l'esecuzione con Ancoraggi nello spazio di Azure, è possibile creare e individuare <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">ancoraggi in Unity.</a>

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint di sviluppo di Unity che è stato previsto, si stanno esplorando i blocchi predefiniti di base della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Mapping spaziale](spatial-mapping-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Persistenza dell'ancoraggio spaziale](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>