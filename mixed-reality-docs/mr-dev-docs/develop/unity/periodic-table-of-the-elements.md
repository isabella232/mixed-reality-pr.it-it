---
title: Tavola periodica degli elementi
description: La tabella periodica degli elementi è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs, in cui è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, controlli, MRTK, Toolkit per realtà mista, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, auricolare per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 4b85631fb044ee0b24c003f7808fd0455b87deec
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677680"
---
# <a name="periodic-table-of-the-elements"></a>Tavola periodica degli elementi

>[!NOTE]
>Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste. Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.

[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs. Con questo progetto è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta di oggetti](../../design/object-collection.md)**. Viene inoltre illustrato come creare oggetti interagibili che rispondono agli input standard da HoloLens. È possibile usare i componenti di questo progetto per creare un'esperienza di app per realtà mista.

![Tabella del periodo dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>Video dimostrativo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Registrato con HoloLens 2 con l'acquisizione di realtà mista

## <a name="about-the-app"></a>Informazioni sull'app

La tabella periodica degli elementi Visualizza gli elementi chimici e ognuna delle relative proprietà in uno spazio 3D. Incorpora le interazioni di base di HoloLens, ad esempio lo sguardo e il tocco aereo. Gli utenti possono ottenere informazioni sugli elementi con i modelli 3D animati. Possono comprendere visivamente la Shell degli elettroni di un elemento e il suo nucleo, composto da protoni e neutroni.

## <a name="background"></a>Sfondo

Dopo la prima volta che ho sperimentato HoloLens, un'app di tabella periodica era un'idea che ho voluto sperimentare in realtà mista. Poiché ogni elemento dispone di molti punti dati visualizzati con testo, ho pensato che sarebbe stato molto soggetto per l'esplorazione della composizione tipografica in uno spazio 3D. La possibilità di visualizzare il modello Electron dell'elemento era un'altra parte interessante di questo progetto.

## <a name="design"></a>Progettazione

Per la visualizzazione predefinita della tabella periodica, ho immaginato le caselle tridimensionali che contenevano il modello Electron di ogni elemento. La superficie di ogni casella sarà translucida, in modo che l'utente possa ottenere un'idea approssimativa del volume dell'elemento. Con lo sguardo e il tocco aereo, l'utente può aprire una visualizzazione dettagliata di ogni elemento. Per fare in modo che la transizione tra la visualizzazione tabella e la visualizzazione dei dettagli sia uniforme e naturale, è stata creata in modo analogo all'interazione fisica di una scatola aperta in vita reale.

![Schizzo di progettazione](images/640px-sketch20170406.jpg)<br>
*Schizzi di progettazione*

In visualizzazione dettagli, ho voluto visualizzare le informazioni di ogni elemento con un testo con rendering bello nello spazio 3D. Il modello di elettroni 3D animato viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.

![Interazione](images/640px-periodictable-interaction.jpg)

![Prototipi](images/640px-periodictable-prototypes.jpg)<br>
*Prototipi di interazione*

L'utente può modificare il tipo di superficie per aria toccando i pulsanti nella parte inferiore della tabella, che possono spostarsi tra il piano, il cilindro, la sfera e la dispersione.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controlli e modelli comuni usati in questa app

### <a name="interactable-object-button"></a>Oggetto interagibile (pulsante)

L' [oggetto interagibile](../../design/interactable-object.md) è un oggetto che può rispondere agli input HoloLens di base. Viene fornito come prefabbricato/script che è possibile applicare facilmente a qualsiasi oggetto. Ad esempio, è possibile rendere interattivo un caffè nella scena e rispondere a input come lo sguardo, il tocco aereo, i movimenti di spostamento e manipolazione. [Scopri di più](../../design/interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Raccolta di oggetti

La [raccolta](../../design/object-collection.md) di oggetti è un oggetto che consente di disporre più oggetti in varie forme. Supporta piani, cilindri, sfere e dispersione. È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura. [Scopri di più](../../design/object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare gli script e i prefabbricati per la tabella periodica dell'app elementi nel [progetto Mixed Reality Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Storia di porting per HoloLens 2

Leggere la storia relativa alla modalità di aggiornamento della tabella periodica dell'app elementi con le interazioni istintive di HoloLens 2.

[Tavola periodica degli elementi 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche

* [Hub di esempi MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tavola periodica degli elementi 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)