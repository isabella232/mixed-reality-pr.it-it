---
title: Tavola periodica degli elementi
description: Informazioni su come creare il piano di una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti con la tabella periodica dell'app di esempio Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, app di esempio, controlli, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: aab6789939823b8c6e200bb5456118002b848e3c2f166abe50d4788ac8e7430d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211886"
---
# <a name="periodic-table-of-the-elements"></a>Tavola periodica degli elementi
![Tabella Period dell'app Elements](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>Questo articolo illustra un esempio esplorativo creato in [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un luogo in cui condividiamo le informazioni e i suggerimenti per lo sviluppo di app di realtà mista. Gli articoli e il codice relativi alla progettazione si evolveranno man appena si effettuano nuove individuazioni.

>[!NOTE]
>Questa app di esempio è stata progettata HoloLens prima generazione. Vedere [la tabella periodica degli elementi 2.0 per](periodic-table-of-the-elements-2.md) HoloLens 2 versione.

[La tabella periodica degli elementi è](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) un'app di esempio open source di Microsoft Mixed Reality Design Labs. Informazioni su come creare una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta di oggetti](../../design/object-collection.md)**. Informazioni anche su come creare oggetti con interazione che rispondono a input standard da HoloLens. È possibile usare i componenti di questo progetto per creare un'esperienza di app di realtà mista personalizzata.


## <a name="demo-video"></a>Video demo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Registrato con HoloLens 2 usando Acquisizione realtà mista

## <a name="about-the-app"></a>Informazioni sull'app

La tabella periodica degli elementi visualizza gli elementi chimica e ognuna delle relative proprietà in uno spazio 3D. Incorpora le interazioni di base di HoloLens ad esempio lo sguardo fisso e il tocco. Gli utenti possono ottenere informazioni sugli elementi con modelli 3D animati. Possono comprendere visivamente la shell degli elettroni di un elemento e il relativo nucleo, costituito da protoni e neutroni.

## <a name="background"></a>Sfondo

Dopo aver provato HoloLens, ho provato a sperimentare con un'app di tabella periodica in realtà mista. Poiché ogni elemento ha molti punti dati visualizzati con testo, ho pensato che fosse un argomento molto importante per esplorare la composizione tipografica in uno spazio 3D. Offrire agli utenti la possibilità di visualizzare il modello di elettroni dell'elemento è stata un'altra parte interessante di questo progetto.

## <a name="design"></a>Progettazione

Per la visualizzazione predefinita della tabella periodica, ho pensato a caselle tridimensionali che conterrebbero il modello di elettrone di ogni elemento. La superficie di ogni scatola sarebbe traslucida in modo che l'utente possa avere un'idea approssimativa del volume dell'elemento. Con lo sguardo fisso e il tocco, l'utente può aprire una visualizzazione dettagliata di ogni elemento. Per rendere la transizione tra la visualizzazione tabella e la visualizzazione dettagli uniforme e naturale, è stata resa simile all'interazione fisica di un'apertura di un riquadro nella vita reale.

![Sketch di progettazione](images/640px-sketch20170406.jpg)<br>
*Progettare gli sketch*

Nella visualizzazione dettagli, si desidera visualizzare le informazioni di ogni elemento con testo ben sottoposto a rendering nello spazio 3D. Il modello di elettrone 3D animato viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.

![Interazione](images/640px-periodictable-interaction.jpg)

![Prototipi](images/640px-periodictable-prototypes.jpg)<br>
*Prototipi di interazione*

L'utente può modificare il tipo di superficie toccando in aria i pulsanti nella parte inferiore del tavolo, che possono passare da piano, cilindro, sfera e dispersione.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controlli e modelli comuni usati in questa app

### <a name="interactable-object-button"></a>Oggetto con interazione (pulsante)

[L'oggetto con](../../design/interactable-object.md) interazione è un oggetto che può rispondere agli input HoloLens base. Viene fornito come prefab/script, che è possibile applicare facilmente a qualsiasi oggetto. Ad esempio, puoi fare in modo che una tazzina per il caffè nella scena interagisca e risponda a input come sguardo fisso, tocco d'aria, navigazione e movimenti di manipolazione. [Scopri di più](../../design/interactable-object.md)

![Oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Raccolta di oggetti

[La raccolta](../../design/object-collection.md) di oggetti è un oggetto che consente di creare più oggetti in varie forme. Supporta piano, cilindro, sfera e dispersione. È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura. [Scopri di più](../../design/object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare script e prefab per la tabella periodica dell'app Elements in [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Storia di porting per HoloLens 2

Leggere la storia su come la tabella periodica dell'app Elements è stata aggiornata HoloLens 2 interazioni istintiva del cliente.

[Tavola periodica degli elementi 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche

* [Hub di esempi MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tavola periodica degli elementi 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)