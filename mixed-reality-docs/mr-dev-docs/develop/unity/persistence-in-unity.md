---
title: Persistenza in Unity
description: La persistenza consente agli utenti di aggiungere singoli ologrammi ovunque si trovino e quindi di trovarli in un secondo momento rispetto a molti utilizzi dell'app.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistenza, Unity, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: d74f9c0a118c1886037c564073742ebedc7d0146
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010442"
---
# <a name="persistence-in-unity"></a>Persistenza in Unity

**Spazio dei nomi:** *UnityEngine. XR. WSA. Persistence*<br>
**Classe:** *WorldAnchorStore*

WorldAnchorStore è la chiave per la creazione di esperienze olografiche in cui gli ologrammi mantengono posizioni reali specifiche tra le istanze dell'applicazione. Gli utenti possono quindi aggiungere singoli ologrammi ovunque si trovino e trovarli più avanti nello stesso punto rispetto a molti utilizzi dell'app.

## <a name="how-to-persist-holograms-across-sessions"></a>Come salvare in modo permanente gli ologrammi tra le sessioni

Il WorldAnchorStore consentirà di rendere permanente il percorso di WorldAnchor tra le sessioni. Per rendere effettivamente permanente gli ologrammi tra le sessioni, è necessario tenere traccia separatamente dei GameObject che usano un particolare ancoraggio mondiale. Spesso è opportuno creare una radice GameObject con un ancoraggio globale e avere elementi figlio olografici ancorati con un offset della posizione locale.

Per caricare gli ologrammi dalle sessioni precedenti:
1. Ottenere il WorldAnchorStore
2. Caricare i dati dell'app correlati all'ancoraggio globale, che fornisce l'ID dell'ancoraggio globale
3. Caricare un ancoraggio globale dall'ID

Per salvare gli ologrammi per le sessioni future:
1. Ottenere il WorldAnchorStore
2. Salva un ancoraggio globale specificando un ID
3. Salva i dati dell'app correlati all'ancoraggio globale insieme a un ID

### <a name="getting-the-worldanchorstore"></a>Recupero di WorldAnchorStore

È consigliabile tenere un riferimento a WorldAnchorStore in modo da essere a conoscenza quando è pronto per eseguire un'operazione. Poiché si tratta di una chiamata asincrona, potenzialmente non appena viene avviata, si vuole chiamare:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded in questo caso è il gestore per il completamento del caricamento di WorldAnchorStore:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

È ora disponibile un riferimento a WorldAnchorStore, che verrà usato per salvare e caricare specifici ancoraggi internazionali.

### <a name="saving-a-worldanchor"></a>Salvataggio di un WorldAnchor

Per salvare, è sufficiente assegnare un nome a quello che si sta salvando e passarlo nel WorldAnchor ottenuto in precedenza quando si desidera salvare. Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (Store. Il salvataggio restituirà false. Eliminare il salvataggio precedente prima di salvare quello nuovo:

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

### <a name="loading-a-worldanchor"></a>Caricamento di un WorldAnchor

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

È inoltre possibile utilizzare Store. Eliminare () per rimuovere un ancoraggio precedentemente salvato e archiviato. Deselezionare () per rimuovere tutti i dati salvati in precedenza.

### <a name="enumerating-existing-anchors"></a>Enumerazione degli ancoraggi esistenti

Per individuare gli ancoraggi precedentemente archiviati, chiamare GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Mantenimento degli ologrammi per più dispositivi

È possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.  Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il contenuto di cui è stato eseguito il rendering rispetto a tale ancoraggio nella stessa posizione fisica.

Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.

Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Mapping spaziale](spatial-mapping-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Persistenza di ancoraggio spaziale](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
