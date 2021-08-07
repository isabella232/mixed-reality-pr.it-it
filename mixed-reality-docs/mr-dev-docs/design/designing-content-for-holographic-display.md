---
title: Progettazione di contenuto per la visualizzazione olografica
description: Informazioni sulle linee guida di progettazione e sulle procedure consigliate per la visualizzazione olografica HoloLens dispositivi.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Progettazione dell'interfaccia utente, visualizzazione olografica, progettazione del contenuto, tema scuro, tema chiaro, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, progettazione, pixel
ms.openlocfilehash: 1fab172f6d737b25e95b10a6dded2a5ab805e0086de8d0fae40c5a6a4ef7d805
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212949"
---
# <a name="designing-content-for-holographic-display"></a>Progettazione di contenuto per la visualizzazione olografica

![Posizione sul lato Ulnar](images/UX_Hero_DarkTheme.jpg)

Quando si progettano contenuti per schermi olografici, è necessario prendere in considerazione diversi elementi per ottenere un'esperienza ottimale. Di seguito sono elencate alcune raccomandazioni. Per altre informazioni sulle caratteristiche degli schermi olografici, vedere la pagina [Color, light and materials (Colore,](color-light-and-materials.md) luce e materiali).

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Problemi con il colore chiaro su una superficie di grandi dimensioni 

In base alle HoloLens di ricerca e test, è stato rilevato che l'uso di colori chiari in un'area di grandi dimensioni dello schermo può causare diversi problemi: 

**Affaticamento oculare** 

Poiché la visualizzazione olografica è additiva, gli ologrammi con colori chiari usano più luce. Un colore chiaro e a tinta unita in un'area di grandi dimensioni dello schermo può causare facilmente affaticamento oculare per l'utente. 

**Occlusione manuale** 

Il colore chiaro rende difficile per l'utente visualizzare le mani quando interagisce direttamente con gli oggetti. Poiché l'utente non può vedere le mani, diventa difficile percepirne la profondità/distanza dalla superficie di destinazione. Il cursore del dito consente di compensare questo problema, ma può comunque risultare complesso su una superficie bianca. 

![Colore e occlusione della mano ](images/color_handocclusion.jpg)
 *Difficile vedere la mano sul backplate del contenuto* di colore chiaro

**Uniformità dei colori**

A causa delle caratteristiche degli schermi olografici, un'area di grandi dimensioni sullo schermo può diventare di tipo blotchy. L'uso di combinazioni di colori scuri consente di ridurre al minimo questo problema. 

## <a name="design-guidelines-for-color-choices"></a>Linee guida di progettazione per le scelte di colore

**Usare il colore scuro per lo sfondo dell'interfaccia utente**

Usando la combinazione colori scura, è possibile ridurre al minimo l'affaticamento oculare e migliorare l'attendibilità delle interazioni dirette con la mano. 

![Esempi di colore scuro usato per lo sfondo del contenuto ](images/color_dark_examples.jpg)
 *Esempi di colore scuro usato per lo sfondo del contenuto*

**Usare lo spessore del carattere semibold o bold**

HoloLens consente all'esperienza di visualizzare testo ad alta risoluzione. Tuttavia, è consigliabile evitare spessori del carattere leggeri o semi-leggeri, perché i tratti verticali possono instabilità nelle dimensioni ridotte del carattere. 

![Lo spessore del carattere in grassetto o semi grassetto (pannello superiore) migliora la leggibilità Del carattere grassetto o semi ](images/color_font_examples.jpg)
 *grassetto (pannello superiore)* migliora la leggibilità

**Usare il materiale HolographicBackplate di MRTK**

Il materiale HolographicBackplate viene applicato a diversi pannelli dell'interfaccia utente nella HoloLens shell. Una delle funzionalità è un effetto di iridescenza visibile agli utenti quando si spostano in base al pannello. Il colore del backplate si sposta in modo secondario in uno spettro predefinito, creando un effetto visivo coinvolgente e dinamico senza interferire con la leggibilità del contenuto. Questo lieve cambiamento di colore serve anche a compensare eventuali piccole irregolarità di colore. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Problemi con backplate dell'interfaccia utente trasparente o traslucido 

![Esempi di interfaccia utente ](images/color_transparent_examples.jpg)
 *trasparente Esempi di backplate dell'interfaccia utente trasparente*

**Complessità visiva e accessibilità**

Poiché gli oggetti olografici si integrano con l'ambiente fisico, il contenuto o la leggibilità dell'interfaccia utente nelle finestre trasparenti o traslucidi potrebbero essere ridotte. Inoltre, quando gli oggetti olografici trasparenti sono sovrapposti l'uno all'altro, potrebbe rendere difficile l'interazione dell'utente a causa della profondità confusa.

**Prestazioni**

Per il corretto rendering degli oggetti trasparenti o traslucidi, è necessario ordinare e unire gli oggetti esistenti sullo sfondo. L'ordinamento degli oggetti trasparenti ha un costo medio della CPU, la fusione ha un costo notevole per la GPU perché non consente alla GPU di eseguire la rimozione della superficie nascosta tramite z-culling (ad esempio test di profondità). Se non si consente la rimozione della superficie nascosta, aumenta il numero di operazioni necessarie per il pixel finale sottoposto a rendering. In questo modo si imposta una maggiore pressione fill rate vincoli.

**Problema di stabilità dell'ologramma con la tecnologia Depth LSR**

Per migliorare la proiezione olografica o la stabilità dell'ologramma, un'applicazione può inviare un buffer di profondità al sistema per ogni frame sottoposto a rendering. Quando si usa il buffer di profondità per la nuovaproiezione, è necessario scrivere un buffer di profondità per ogni pixel di cui è stato eseguito il rendering di colore a una profondità corrispondente. Anche i pixel con un valore di profondità devono avere un valore di colore. Se le indicazioni precedenti non vengono seguite, le aree dell'immagine di cui è stato eseguito il rendering che non dispongono di informazioni di profondità valide possono essere riposizionate in modo da produrre artefatti, spesso visibili come distorsioni simili a onde.


## <a name="design-guidelines-for-transparent-elements"></a>Linee guida di progettazione per gli elementi trasparenti

**Usare lo sfondo opaco dell'interfaccia utente**

Per impostazione predefinita, gli oggetti trasparenti o traslucidi non scrivono profondità per consentire la fusione corretta. I modi per attenuare questo problema includono l'uso di oggetti opachi, la garanzia che gli oggetti traslucidi vengano visualizzati vicino agli oggetti opachi (ad esempio un pulsante traslucido davanti a un backplate opaco), la forzatura degli oggetti traslucidi alla profondità di scrittura (non applicabile in tutti gli scenari) o il rendering di oggetti proxy, che contribuiscono solo ai valori di profondità alla fine del frame.

Soluzioni all'interno di MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/ologram-stabilization#depth-buffer-sharing-in-unity  

Usando un backplate solido e opaco, è possibile proteggere la leggibilità e l'attendibilità dell'interazione.

**Ridurre al minimo il numero di pixel interessati**

Se il progetto deve usare oggetti trasparenti, provare a ridurre al minimo il numero di pixel interessati. Ad esempio, se un oggetto è visibile solo in determinate condizioni (ad esempio un effetto di alone additivo), disabilitare l'oggetto quando è completamente invisibile (invece di impostare il colore additivo su nero). Per le forme 2D semplici create usando un quad con una maschera alfa, prendere in considerazione la creazione di una rappresentazione mesh della forma con uno shader opaco. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Esempi di interfaccia utente scura in MRTK (Mixed Reality Toolkit) per Unity

**[MRTK offre molti](https://github.com/Microsoft/MixedRealityToolkit-Unity)** esempi di blocchi predefiniti dell'interfaccia utente basati sulle combinazioni di colori scuri.

* [Menu vicino](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [Finestra di dialogo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [Menu mano](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>Vedi anche

* [Colore, luce e materiali](color-light-and-materials.md)
* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)