---
title: Progettazione di contenuto per la visualizzazione olografica
description: Linee guida per la progettazione e procedure consigliate per la visualizzazione olografica
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Progettazione dell'interfaccia utente, schermo olografico, progettazione del contenuto, tema scuro, tema chiaro, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, progettazione, pixel
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702637"
---
# <a name="designing-content-for-holographic-display"></a>Progettazione di contenuto per la visualizzazione olografica

![Posizione della mano del lato ulnare](images/UX_Hero_DarkTheme.jpg)

Quando si progettano contenuti per le visualizzazioni olografiche, è necessario prendere in considerazione diversi elementi per ottenere un'esperienza ottimale. Di seguito sono elencate alcune delle raccomandazioni ed è possibile ottenere altre informazioni sulle caratteristiche delle visualizzazioni olografiche nella pagina [colore, luce e materiali](color-light-and-materials.md) .

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Problemi con colore luminoso su larga superficie 
In base alla ricerca e al test degli utenti su diversi tipi di esperienza HoloLens, abbiamo scoperto che l'uso di colori luminosi in un'area di grandi dimensioni della visualizzazione può causare diversi problemi: 

**Affaticamento degli occhi** 

Poiché la visualizzazione olografica è additiva, colore chiaro usa una maggiore luminosità per visualizzare gli ologrammi. Un colore chiaro e a tinta unita in un'area di grandi dimensioni dello schermo può causare la fatica degli occhi per l'utente. 

**Occlusione mano** 

Il colore luminoso rende difficile per l'utente vedere le proprie mani quando si interagisce direttamente con gli oggetti. Poiché l'utente non può visualizzare le loro mani, diventa difficile percepire la profondità o la distanza tra la mano/il dito e la superficie di destinazione. Il cursore del dito aiuta a compensare questo problema, ma può comunque essere difficile su una superficie bianca luminosa. 

![Occlusione di colore e mano ](images/color_handocclusion.jpg)
 *difficili da visualizzare la mano sul Backplate del contenuto colorato*

**Uniformità del colore**

A causa delle caratteristiche delle visualizzazioni olografiche, una grande area luminosa sullo schermo può diventare chiazzata. Con le combinazioni di colori scure è possibile ridurre il problema. 

## <a name="design-guidelines"></a>Linee guida di progettazione

**Usa colore scuro per lo sfondo dell'interfaccia utente**

Utilizzando la combinazione di colori scura, è possibile ridurre al minimo l'affaticamento degli occhi e migliorare la confidenza sulle interazioni con la mano diretta. 

![Esempi di interfaccia utente scura ](images/color_dark_examples.jpg)
 *esempi di colore scuro usati per lo sfondo del contenuto*

**USA SemiBold o spessore carattere grassetto**

HoloLens consente alla tua esperienza di mostrare un bel testo ad alta risoluzione. Tuttavia, si consiglia di evitare i pesi dei tipi di carattere sottili, ad esempio Light o Semilight, perché i tratti verticali possono ingrandire le dimensioni del tipo di carattere ridotto. 

![Esempi di interfaccia utente scura ](images/color_font_examples.jpg)
 *spessore del carattere grassetto o semi-grassetto (pannello superiore) migliora la leggibilità*

**Usa il materiale HolographicBackplate di MRTK**

Il materiale HolographicBackplate viene applicato a diversi pannelli dell'interfaccia utente nella shell di HoloLens. Una delle sue funzionalità è un effetto iridescenza che è visibile agli utenti mentre spostano la posizione in relazione al pannello. Il colore del backplate si sposta leggermente in uno spettro predefinito, creando un effetto visivo accattivante e dinamico senza interferire con la leggibilità del contenuto. Questo piccolo cambiamento di colore serve anche per compensare eventuali irregolarità dei colori minori. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Problemi con la contropiastra dell'interfaccia utente trasparente o traslucida 
![Esempi di interfaccia utente trasparente ](images/color_transparent_examples.jpg)
 *esempi di backplating dell'interfaccia utente trasparente*

**Complessità visiva e accessibilità**

Poiché gli oggetti olografici vengono combinati con l'ambiente fisico, la leggibilità del contenuto o dell'interfaccia utente nella finestra trasparente o traslucido potrebbe essere degradata. Inoltre, quando gli oggetti olografici trasparenti sono sovrapposti l'uno sull'altro, potrebbe rendere difficile per l'utente interagire a causa del livello di confusione.

**Prestazioni**

Per eseguire il rendering corretto degli oggetti trasparenti o traslucidi, è necessario ordinarli e combinarli con tutti gli oggetti presenti in background. L'ordinamento degli oggetti trasparenti presenta un modesto costo della CPU, mentre la fusione ha un notevole costo della GPU, perché non consente alla GPU di eseguire la rimozione della superficie nascosta tramite l'abbattimento z, ovvero test di profondità). Se non si consente la rimozione della superficie nascosta, aumenta il numero di operazioni che devono essere calcolate per il pixel finale sottoposto a rendering e in questo modo viene maggiore la pressione sui vincoli di velocità di riempimento.

**Problema di stabilità degli ologrammi con tecnologia Depth LSR**

Per migliorare la riproiezione olografica o la stabilità dell'ologramma, un'applicazione può inviare un buffer di profondità al sistema per ogni frame sottoposto a rendering. Quando si usa il buffer di profondità per la riproiezione, una regola è che per ogni pixel di colore di cui è stato eseguito il rendering è necessario scrivere un valore di profondità corrispondente nel buffer di profondità (e qualsiasi pixel con un valore di profondità deve avere anche un valore di colore). Se il materiale sussidiario sopra indicato non viene seguito, le aree dell'immagine di cui è stato eseguito il rendering che non dispongono di informazioni di profondità valide possono essere riproiettate in modo da produrre artefatti (spesso visibili come distorsioni di tipo Wave).


## <a name="design-guidelines"></a>Linee guida di progettazione
**Usa sfondo interfaccia utente opaco**

Per impostazione predefinita, gli oggetti trasparenti o traslucidi non scrivono la profondità per consentire la corretta combinazione. I modi per attenuare questo problema includono l'utilizzo di oggetti opachi, assicurando che gli oggetti traslucidi siano visualizzati vicino a oggetti opachi, ad esempio un pulsante traslucido davanti a un Backplate opaco, forzando gli oggetti traslucidi a scrivere profondità (non applicabile in tutti gli scenari) o eseguendo il rendering di oggetti proxy che contribuiscono solo a valori di profondità alla fine del frame.

Soluzioni in MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

Grazie a una contropiastra solida e opaca, possiamo proteggere la leggibilità e la confidenza dell'interazione.

**Ridurre al minimo il numero di pixel interessati**

Se il progetto deve usare oggetti trasparenti, provare a ridurre al minimo il numero di pixel interessati. Se, ad esempio, un oggetto è visibile solo in determinate condizioni (ad esempio un effetto di bagliore additivo), disabilitare l'oggetto quando è completamente invisibile, anziché impostare il colore additivo su nero. Per le semplici forme 2D create usando un quad con una maschera alfa, provare a creare una rappresentazione mesh della forma con uno shader opaco. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Esempi di interfaccia utente scura in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce molti esempi di blocchi di compilazione dell'interfaccia utente basati sulle combinazioni di colori oscuri.

* [Menu vicino](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [Finestra di dialogo](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [Menu a mano](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a>Vedere anche
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
