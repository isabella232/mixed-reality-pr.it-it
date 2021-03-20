---
title: ScrolingObjectCollection
description: Tipi di menu Panoramica MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, oggetto scorrevole
ms.openlocfilehash: 86d0d79c2b9230beb84b8beda4ba488d857828a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683724"
---
# <a name="scrolling-object-collection"></a>Scorrimento della raccolta di oggetti

![Scorrimento della raccolta di oggetti](../images/scrolling-collection/ScrollingCollection_Main.jpg)

La raccolta di oggetti di scorrimento MRTK è un componente UX che consente lo scorrimento di contenuto 3D attraverso un'area visualizzabile contenuta. Il movimento di scorrimento può essere attivato da un'interazione di input quasi o lontano e da una paginazione discreta. Supporta sia oggetti interattivi che non interattivi.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Introduzione alla raccolta di oggetti di scorrimento

### <a name="setting-up-the-scene"></a>Impostazione della scena

1. Creare una nuova scena Unity.
1. Per aggiungere MRTK alla scena, passare al Toolkit di **realtà mista**  >  **Aggiungi a scena e configurare**.

### <a name="setting-up-the-scrolling-object"></a>Impostazione dell'oggetto di scorrimento

1. Creare un oggetto gioco vuoto nella scena e modificarne la posizione in (0, 0, 1).
1. Aggiungere un componente della [raccolta di oggetti di scorrimento](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) all'oggetto gioco.

    Quando viene aggiunta la raccolta di oggetti di scorrimento, un Collider di box e un componente [toccabile near Interaction](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) verranno collegati automaticamente all'oggetto del gioco radice. Questi componenti consentono all'oggetto Scroll di restare in ascolto di eventi di input di interazione near e lontani, ad esempio un tocco o un clic del puntatore.  

    La raccolta di oggetti di scorrimento MRTK include due elementi importanti che vengono creati come oggetti gioco figlio nella gerarchia degli oggetti di scorrimento radice:
    * `Container` -Tutti gli oggetti di contenuto di scorrimento devono essere elementi figlio dell'oggetto Game del contenitore.
    * `Clipping bounds` -Se lo scorrimento della maschera di contenuto è abilitato, l'elemento dei limiti di ritaglio garantisce che sia visibile solo il contenuto scorrevole all'interno dei relativi limiti. L'oggetto gioco dei limiti di ritaglio è costituito da due componenti: un Collider box disabilitato e un [riquadro di ridimensionamento](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Scorrimento degli elementi della raccolta di oggetti](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Aggiunta di contenuto all'oggetto di scorrimento

La raccolta di oggetti di scorrimento può essere combinata con una [raccolta di oggetti Grid](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) per il layout del contenuto in una griglia di elementi allineati con dimensioni e spaziatura uniformi.

1. Creare un oggetto gioco vuoto come figlio del contenitore di scorrimento.
1. Aggiungere un componente della raccolta di oggetti Grid all'oggetto Game.
1. Per lo scorrimento di una singola colonna verticale, nella scheda Inspector configurare la raccolta di oggetti Grid come segue:
    * **Num colonne**: 1
    * **Layout**: colonna quindi riga
    * **Ancoraggio**: in alto a sinistra
1. Modificare la **larghezza** e l' **altezza** della cella in base alle dimensioni degli oggetti contenuto.
1. Aggiungere gli oggetti contenuto come elementi figlio dell'oggetto Grid.
1. Premere **Aggiorna raccolta**.

![Layout griglia](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Per il corretto funzionamento dell'effetto di ritaglio nell'area visualizzabile, qualsiasi materiale oggetto contenuto scorrevole deve usare lo [shader standard MRTK](../rendering/MRTKStandardShader.md) .

> [!NOTE]
> Se la maschera di contenuto scorrevole è abilitata, la raccolta di oggetti di scorrimento aggiungerà un componente dell' [istanza del materiale](../rendering/MaterialInstance.md) a tutti gli oggetti contenuto a cui è associato un renderer. Questo componente viene utilizzato per gestire la durata dei materiali di istanza e migliorare le prestazioni di memoria.

### <a name="configuring-the-scrolling-viewable-area"></a>Configurazione dell'area visualizzabile a scorrimento

1. Per lo scorrimento verticale di una singola colonna di oggetti, nella scheda Inspector configurare la raccolta di oggetti di scorrimento come segue:
    * **Celle per livello**: 1
    * Scegliere il numero di **livelli per pagina** in base al numero desiderato di righe visibili
1. Modificare la **larghezza**, l' **altezza** e la **profondità** della cella della pagina in base alle dimensioni degli oggetti contenuto.

Si noti che gli oggetti contenuto che si trovano al di fuori dell'area visualizzabile a scorrimento sono ora disabilitati, mentre gli oggetti che intersecano il wireframe di scorrimento potrebbero essere parzialmente mascherati dalla primitiva di ritaglio.

![Area visualizzabile](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Test della raccolta di oggetti di scorrimento nell'editor

1. Premere Riproduci e tenere premuto la barra spaziatrice per visualizzare una mano di simulazione di input.
1. Spostare la mano fino a quando lo scorrimento o il contenuto interattivo scorrevole non è attivo e attivare lo scorrimento facendo clic e trascinando verso l'alto e verso il basso con il mouse sinistro.

## <a name="controlling-the-scrolling-object-from-code"></a>Controllo dell'oggetto di scorrimento dal codice

La raccolta di oggetti di scorrimento MRTK espone alcuni metodi pubblici che consentono lo spostamento del contenitore di scorrimento bloccando la posizione in base alla `pagination` configurazione delle proprietà.

Un esempio di come accedere all'interfaccia di paginazione della raccolta di oggetti di scorrimento è disponibile per l'utilizzo nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` cartella. Lo script di esempio di [impaginazione scorrevole](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) può essere collegato a qualsiasi raccolta di oggetti di scorrimento esistente nella scena. È possibile fare riferimento allo script tramite i componenti della scena che espongono eventi Unity (ad esempio, il [pulsante MRTK](Button.md)).

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

| Generale                      |               Descrizione                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Direzione scorrimento             | Direzione di scorrimento del contenuto.|

| Paginazione                   |              Descrizione                                                                                                                                                                                       |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Celle per livello               | Numero di celle in una riga nella visualizzazione di scorrimento verso il basso o il numero di celle in una colonna nella visualizzazione di scorrimento a destra sinistra.                                                                                                         |
| Livelli per pagina               | Numero di livelli visibili nell'area di scorrimento.                                                                                                                                                                         |
| Cella della pagina                    | Dimensioni della cella di paginazione.                  |

| Impostazioni avanzate            |           Descrizione                                                                                                                                                                                          |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Modalità di modifica maschera               | Modificare le modalità per definire i limiti di maschera del riquadro di ridimensionamento. Scegliere "auto" per usare automaticamente i valori di impaginazione. Scegliere ' manuale ' per abilitare la manipolazione diretta dell'oggetto riquadro di ritaglio.|
| Modalità di modifica Collider           | Modalità di modifica per la definizione dei limiti del Collider di interazione di scorrimento. Scegliere "auto" per usare automaticamente i valori di impaginazione. Scegliere ' manuale ' per abilitare la manipolazione diretta del Collider.|
| Scorrimento                   | Abilita/Disabilita lo scorrimento con interazione near/lontano.                  |
| USA in pre-rendering            | Consente di specificare se scrollingObjectCollection utilizzerà l'evento OnPreRender della fotocamera per gestire la visibilità del contenuto.                  |
| Curva di impaginazione             | Curva di animazione per la paginazione.                  |
| Lunghezza animazione             | Intervallo di tempo (in secondi) necessario per la valutazione del PaginationCurve.                  |
| Soglia di scorrimento Delta della mano  | Distanza, in metri, che il puntatore corrente può spostarsi lungo la direzione di scorrimento prima di attivare un trascinamento di scorrimento.                  |
| Distanza dal tocco anteriore         | Distanza, in metri, per posizionare un piano XY locale usato per verificare se un'interazione tocco è stata avviata nella parte anteriore della visualizzazione a scorrimento.                  |
| Soglia versione            | Preleva l'importo, in metri, dai limiti di scorrimento necessari per la transizione dal tocco occupato al rilascio.                  |

| Velocità |       Descrizione                                                                                                                                                                             |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tipo di velocità       | Tipo desiderato di interruzione della velocità per lo scorrimento.                                                                                        |
| Moltiplicatore velocità     | Quantità di velocità (extra) da applicare allo scorrimento.                                                                                                                                                        |
| Smorzamento velocità     | Quantità di interruzione applicata alla velocità. |
| Moltiplicatore rimbalzo     | Moltiplicatore per aggiungere altro rimbalzo alla sovrascorrimento di un elenco quando si usa il decadimento per fotogramma o il decadimento per ogni elemento. |

| Opzione di debug |          Descrizione                                                                                                                                                                          |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maschera abilitata       | Modalità di visibilità del contenuto di scorrimento. Il valore predefinito maschera tutti gli oggetti all'esterno dell'area visualizzabile di scorrimento.                                                                                        |
| Mostra i piani di soglia     | Se true, l'editor eseguirà il rendering dei piani di soglia della versione tocco intorno ai limiti di scorrimento.                                                                                                                                                        |
| Pagina debug     | Usare questa sezione per eseguire il debug della paginazione di scorrimento durante il Runtime. |

| Eventi|     Descrizione                                                                                                                                                                               |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Al clic       | Evento attivato quando lo scorrimento dello sfondo dello scorrimento o di qualsiasi contenuto interattivo riceve un clic.                                                                                        |
| Al tocco avviato     | Evento attivato quando lo scorrimento dello sfondo dello scorrimento o di qualsiasi contenuto interattivo riceve un tocco di interazione near.                                                                                                                                                        |
| Al termine del tocco     | Evento attivato quando un'interazione con il tocco attivo viene terminata con il puntatore near Interaction che attraversa uno dei piani della soglia di rilascio. |
| Nel momento in cui è stato avviato     | Evento attivato quando il contenitore di scorrimento inizia lo spostamento mediante interazione, velocità fallofff o impaginazione. |
| Al termine del momento     | Evento attivato quando il contenitore di scorrimento smette di spostarsi per interazione, velocità fallofff o impaginazione. |

## <a name="scrolling-example-scene"></a>Sequenza di esempio di scorrimento

La scena di esempio **ScrollingObjectCollection. Unity** è costituita da 3 esempi scorrevoli, ognuno con una configurazione del decadimento della velocità differente. La scena di esempio contiene i muri per mostrare il comportamento di posizionamento della superficie disabilitato per impostazione predefinita nella gerarchia. La scena di esempio si trova nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` cartella.

![Scena di esempio della raccolta di oggetti scorrevoli](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Prefabbricati di esempio di scorrimento

Per praticità, sono disponibili due prefabbricati per la raccolta di oggetti di scorrimento. Le prefabbricazioni di esempio sono disponibili nella ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` cartella.

![Scorrimento delle prefabbricati della raccolta di oggetti](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Vedi anche

* [Primitiva di ritaglio](../rendering/ClippingPrimitive.md)
* [Istanza del materiale](../rendering/MaterialInstance.md)
* [Shader standard](../rendering/MRTKStandardShader.md)
* [Raccolta di oggetti](ObjectCollection.md)
