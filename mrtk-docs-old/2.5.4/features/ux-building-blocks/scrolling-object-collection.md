---
title: ScrolingObjectCollection
description: Tipi di menu Panoramica MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, oggetto scrolling
ms.openlocfilehash: 06ad2d8ac19ac7784a9b83ea5c9801612fb24842d8e4c64433394eac416080fc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222773"
---
# <a name="scrolling-object-collection"></a>Scorrimento della raccolta di oggetti

![Scorrimento della raccolta di oggetti](../images/scrolling-collection/ScrollingCollection_Main.jpg)

La raccolta di oggetti di scorrimento di MRTK è un componente dell'esperienza utente che consente lo scorrimento del contenuto 3D in un'area visualizzabile contenuta. Lo scorrimento può essere attivato da un'interazione di input da vicino o da lontano e da una paginazione discreta. Supporta sia oggetti interattivi che non interattivi.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Introduzione alla raccolta di oggetti di scorrimento

### <a name="setting-up-the-scene"></a>Configurazione della scena

1. Creare una nuova scena unity.
1. Aggiungere MRTK alla scena passando alla pagina **Mixed Reality (Realtà mista) Toolkit** Add to Scene  >  **(Aggiungi alla scena) e Configure (Configura).**

### <a name="setting-up-the-scrolling-object"></a>Configurazione dell'oggetto di scorrimento

1. Creare un oggetto gioco vuoto nella scena e modificarne la posizione in (0, 0, 1).
1. Aggiungere un [componente della raccolta di oggetti scorrendo](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) all'oggetto gioco.

    Quando viene aggiunta la raccolta di oggetti scorrevoli, un collisore di box e un componente toccabile con interazione da vicino verranno collegati automaticamente all'oggetto gioco radice. [](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) Questi componenti consentono all'oggetto di scorrimento di restare in ascolto di eventi di input di interazione da vicino e da lontano, ad esempio un tocco o un clic del puntatore.  

    La raccolta di oggetti di scorrimento DI MRTK ha due elementi importanti che vengono creati come oggetti gioco figlio nella gerarchia di oggetti di scorrimento radice:
    * `Container` - Tutti gli oggetti contenuto di scorrimento devono essere elementi figlio dell'oggetto gioco del contenitore.
    * `Clipping bounds` - Se la maschera del contenuto scorrevole è abilitata, l'elemento dei limiti di ritaglio garantisce che sia visibile solo il contenuto scorrevole all'interno dei limiti. L'oggetto gioco dei limiti di ritaglio ha due componenti: un collisore di box disabilitato e un [rettangolo di ritaglio.](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)

![Scorrimento degli elementi della raccolta di oggetti](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Aggiunta di contenuto all'oggetto di scorrimento

La raccolta di oggetti di [](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) scorrimento può essere combinata con una raccolta di oggetti griglia per il layout del contenuto in una griglia di elementi allineati con dimensioni e spaziatura uniformi.

1. Creare un oggetto gioco vuoto come figlio del contenitore di scorrimento.
1. Aggiungere un componente della raccolta di oggetti griglia all'oggetto gioco.
1. Per uno scorrimento verticale a colonna singola, nella scheda inspector (Controllo) configurare la raccolta di oggetti griglia come segue:
    * **Colonne Num**: 1
    * **Layout:** colonna e riga
    * **Ancoraggio:** in alto a sinistra
1. Modificare la larghezza e **l'altezza delle** celle in base alle dimensioni degli oggetti contenuto. 
1. Aggiungere gli oggetti contenuto come elementi figlio dell'oggetto griglia.
1. Premere **aggiorna raccolta**.

![Layout griglia](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Per il corretto funzionamento dell'effetto di ritaglio sull'area visualizzabile, qualsiasi materiale di oggetto contenuto scorrevole deve usare lo [shader standard MRTK.](../rendering/MRTK-standard-shader.md)

> [!NOTE]
> Se la maschera del contenuto di scorrimento è abilitata, la raccolta di oggetti scorrenti aggiungerà un componente dell'istanza materiale [a](../rendering/material-instance.md) tutti gli oggetti contenuto a cui è associato un renderer. Questo componente viene usato per gestire la durata dei materiali con istanze e migliorare le prestazioni della memoria.

### <a name="configuring-the-scrolling-viewable-area"></a>Configurazione dell'area scorrevole visualizzabile

1. Per lo scorrimento verticale in una singola colonna di oggetti, nella scheda inspector (Controllo) configurare la raccolta di oggetti scorrendo come segue:
    * **Celle per livello:** 1
    * Scegliere il numero di **livelli per pagina** in base al numero desiderato di righe visibili
1. Modificare la **larghezza, l'altezza** **e la** profondità delle celle **della** pagina in base alle dimensioni degli oggetti contenuto.

Si noti come gli oggetti di contenuto che si esergano all'esterno dell'area scorrevole visualizzabile siano ora disabilitati, mentre gli oggetti che intersecano il wireframe di scorrimento potrebbero essere parzialmente mascherati dalla primitiva di ritaglio.

![Area visualizzabile](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Test della raccolta di oggetti scorrenti nell'editor

1. Premere play e tenere premuta la barra spaziatrice per visualizzare una mano di simulazione di input.
1. Spostare la mano fino a quando il collisore di scorrimento o qualsiasi contenuto interattivo di scorrimento si trova nello stato attivo e attivare lo scorrimento facendo clic e trascinando verso l'alto e verso il basso con il mouse sinistro.

## <a name="controlling-the-scrolling-object-from-code"></a>Controllo dell'oggetto di scorrimento dal codice

La raccolta di oggetti di scorrimento di MRTK espone alcuni metodi pubblici che consentono di spostare il contenitore di scorrimento bloccando la posizione in base alla configurazione `pagination` delle proprietà.

Un esempio di come accedere all'interfaccia di paginazione della raccolta di oggetti a scorrimento è disponibile per l'uso nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` cartella . Lo script [di esempio di paginazione](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) scorrevole può essere collegato a qualsiasi raccolta di oggetti scorrevoli esistente nella scena. È quindi possibile fare riferimento allo script dai componenti della scena che espongono eventi Unity (ad esempio, [il pulsante MRTK).](button.md)

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }       
}
```

## <a name="scrolling-object-collection-properties"></a>Scorrimento delle proprietà della raccolta di oggetti

| Generale                      |                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Direzione di scorrimento             | Direzione di scorrimento del contenuto.|

| Paginazione                   |               Descrizione                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Celle per livello               | Numero di celle in una riga nella visualizzazione di scorrimento verso l'alto o numero di celle in una colonna nella visualizzazione di scorrimento da sinistra a destra.                                                                                                         |
| Livelli per pagina               | Numero di livelli visibili nell'area di scorrimento.                                                                                                                                                                         |
| Cella della pagina                    | Dimensioni della cella di paginazione.                  |

| Impostazioni avanzate            |                  Descrizione                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Modalità di modifica maschera               | Modalità di modifica per la definizione dei limiti di maschera della casella di ritaglio. Scegliere "Automatico" per usare automaticamente i valori di paginazione. Scegliere "Manuale" per abilitare la manipolazione diretta dell'oggetto riquadro di ritaglio.|
| Modalità di modifica collisore           | Modalità di modifica per la definizione dei limiti del collisore di interazione di scorrimento. Scegliere "Automatico" per usare automaticamente i valori di paginazione. Scegliere "Manuale" per abilitare la manipolazione diretta del collisore.|
| Può scorrere                   | Abilita/disabilita lo scorrimento con l'interazione da vicino/lontano.                  |
| Usare in fase di pre-rendering            | Attiva o disattiva se scrollingObjectCollection userà l'evento Camera OnPreRender per gestire la visibilità del contenuto.                  |
| Curva di paginazione             | Curva di animazione per la paginazione.                  |
| Lunghezza dell'animazione             | Quantità di tempo (in secondi) che PaginationCurve dovrà valutare.                  |
| Soglia di scorrimento delta mano  | La distanza, in metri, il puntatore corrente può scorrere lungo la direzione di scorrimento prima di attivare un trascinamento dello scorrimento.                  |
| Distanza tocco anteriore         | Distanza, in metri, per posizionare un piano xy locale usato per verificare se un'interazione tramite tocco è iniziata nella parte anteriore della visualizzazione di scorrimento.                  |
| Soglia di rilascio            | Importo del prelievo, in metri, dai limiti di scorrimento necessari per passare dal tocco attivato al rilascio.                  |

| Velocità |               Descrizione                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tipo di velocità       | Tipo desiderato di falloff di velocità per lo scorrimento.                                                                                        |
| Moltiplicatore di velocità     | Quantità di velocità (aggiuntiva) da applicare al controllo di scorrimento.                                                                                                                                                        |
| Smorzare la velocità     | Quantità di falloff applicata alla velocità. |
| Moltiplicatore di bounce     | Moltiplicatore per aggiungere più bounce all'overscroll di un elenco quando si usa il falloff per fotogramma o il falloff per elemento. |

| Opzione di debug |            Descrizione                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maschera abilitata       | Modalità di visibilità del contenuto di scorrimento. Il valore predefinito maschera tutti gli oggetti all'esterno dell'area visualizzabile a scorrimento.                                                                                        |
| Mostra piani di soglia     | Se true, l'editor eseguirà il rendering dei piani soglia di rilascio tocco intorno ai limiti di scorrimento.                                                                                                                                                        |
| Paginazione di debug     | Usare questa sezione per eseguire il debug della paginazione di scorrimento durante il runtime. |

| Eventi|    Descrizione                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Al clic del mouse       | Evento attivato quando il collisore dello sfondo di scorrimento o qualsiasi contenuto interattivo riceve un clic.                                                                                        |
| Al tocco avviato     | Evento attivato quando il collisore dello sfondo di scorrimento o uno qualsiasi dei contenuti interattivi riceve un tocco quasi di interazione.                                                                                                                                                        |
| Al tocco terminato     | Evento attivato quando un'interazione con tocco attiva viene terminata con il puntatore di interazione vicino che attraversa uno dei piani di soglia di rilascio. |
| Avvio in corso     | Evento attivato quando il contenitore di scorrimento inizia a spostarsi in base all'interazione, al fallofff della velocità o all'impaginazione. |
| Al momento della fine     | Evento attivato quando il contenitore di scorrimento smette di spostarsi in base all'interazione, al fallofff della velocità o all'impaginazione. |

## <a name="scrolling-example-scene"></a>Scena di esempio di scorrimento

**La scena di esempio ScrollingObjectCollection.unity** è costituita da 3 esempi scorrevoli, ognuno con una configurazione di falloff della velocità diversa. La scena di esempio contiene le pareti per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia. La scena di esempio è disponibile nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` cartella .

![Scena di esempio di raccolta di oggetti a scorrimento](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Prefab di esempio di scorrimento

Per praticità, sono disponibili due prefab per la raccolta di oggetti a scorrimento. I prefab di esempio sono disponibili nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` cartella .

![Prefab della raccolta di oggetti a scorrimento](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Vedi anche

* [Primitiva di ritaglio](../rendering/clipping-primitive.md)
* [Istanza material](../rendering/material-instance.md)
* [Standard Shader](../rendering/MRTK-standard-shader.md)
* [Raccolta di oggetti](object-collection.md)
