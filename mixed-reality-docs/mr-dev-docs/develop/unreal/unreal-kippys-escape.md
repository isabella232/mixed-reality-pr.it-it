---
title: The Making of Kippy's Escape
description: Seguici mentre esploriamo la creazione dell'applicazione di realtà mista Escape di Kippy per HoloLens 2 in Unreal Engine.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione nel dispositivo, PC, documentazione, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: 96799de948cf9e1cbca89b7e781f3f830fbc005810680d1164d04acb757b1a09
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208224"
---
# <a name="the-making-of-kippys-escape"></a>Creazione della sequenza di escape di Kippy
![Immagine del hero escape di Kippy](images/KippysEscape_1920.jpg)

Kippy il robot si riattiva per trovare se stesso in un'isola. È l'utente a mettere il proprio hat nella risoluzione dei problemi per trovare un percorso per tornare alla sua astronave di razzi. A questo HoloLens 2 scaricare [l'app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) dal Microsoft Store o clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) da GitHub e fare in modo che Kippy sia al sicuro.  

> [!IMPORTANT]
> Assicurarsi di usare **Unreal Engine 4.25** o versione successiva se si sta compilando Kippy's Escape dal repository GitHub.

Kippy's Escape è un'app HoloLens 2 open [source](/hololens/hololens2-hardware) compilata con Unreal Engine 4 e [Mixed Reality UX Tools per Unreal.](https://github.com/microsoft/MixedReality-UXTools-Unreal) Questo post illustra il processo, dai primi principi e dalla progettazione visiva all'implementazione e all'ottimizzazione dell'esperienza. Per altre informazioni sullo sviluppo di applicazioni di realtà mista con MRTK UX Tools, vedere Panoramica [dello sviluppo di Unreal.](unreal-development-overview.md)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Scaricare l'app Microsoft Store in HoloLens 2
Se si dispone HoloLens 2 dispositivo, è possibile scaricare e installare direttamente l'app nel dispositivo.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>Primi principi 

Per creare l'escape di Kippy, l'obiettivo era quello di creare un'esperienza che evidenziasse il supporto di HoloLens 2 di [Unreal Engine,](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)le funzionalità del HoloLens 2 e il modello di realtà mista Toolkit. Abbiamo voluto ispirare gli sviluppatori a immaginare cosa potevano creare con Unreal e HoloLens 2.  

Abbiamo creato tre principi guida per l'esperienza: che doveva essere divertente, interattivo e avere una barriera di ingresso bassa. L'esperienza era sufficientemente intuitiva che anche un utente di realtà mista per la prima volta non avrebbe bisogno di un'esercitazione per completarla.  

## <a name="designing-the-game"></a>Progettazione del gioco 

Il HoloLens 2 ha accesso alle funzionalità di progettazione presenti in altri giochi. Gli oggetti possono essere spinti o manipolati direttamente usando le mani o mirati con il tracciamento oculare. Queste funzionalità chiave sono alla base di alcuni dei momenti di gioco creati in Kippy's Escape.  

Usando le funzionalità HoloLens 2 come indicazioni per la progettazione del gioco, sono stati descritti alcuni scenari di ambiente di piccole dimensioni. Le isole hanno senso perché possono essere regolate in base alle diverse altezze del giocatore e hanno fornito alcune idee di ponte interessanti. Abbiamo preso il tema dell'insoddisfiamento della tecnologia sci-fi, con l'idea che qualcuno abbia costruito macchinari su bare che sfruttano un'energia strano fornita da ogni isola. Alle isole è stato assegnato il proprio aspetto, un dettaglio che ha contribuito a creare interesse visivo. Un buon equilibrio tra modellazione e texturing mantenerebbe le chiamate di disegno basse per le prestazioni di rendering, quindi è stato progettato un aspetto stilizzato. 

![Primi bozze di progettazione del ](images/kippys-escape/kippys-escape-img-01.png)
 *gioco Alcuni bozzetti iniziali per l'aspetto dell'esperienza*

![Rendering della seconda isola ](images/kippys-escape/kippys-escape-img-02.png)
 *Rendering della seconda isola*

Per rimanere entro la breve pianificazione di produzione, è stato concordato che un carattere mobile può acquisire finalità ed emozioni senza cicli di animazione rigorosi. Kippy è quindi nato. Emotizza alcune espressioni diverse attraverso gli occhi e attraverso effetti sonori a forma di emoticon che aiutano a guidare il giocatore durante l'esperienza. 

![Kippy che mostra espressioni diverse tramite gli occhi](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy che mostra espressioni diverse tramite gli occhi*

![Se l'utente impiega troppo tempo per risolvere un problema, Kippy offrirà all'utente un suggerimento](images/kippys-escape/kippys-escape-img-04.gif)

*Se l'utente impiega troppo tempo per risolvere un problema, Kippy offrirà all'utente un suggerimento*

Oltre alla progettazione del carattere e dell'ambiente, abbiamo fatto uno sforzo comune per fare in modo che il gioco sia divertente. Il tracciamento oculare ha consentito di dare il via a materiali e attributi audio, che hanno evidenziato le parti chiave del gioco. L'audio spaziale ha contribuito a rendere i livelli come a casa nell'ambiente circostante del lettore. La possibilità di afferrare oggetti, premere pulsanti e manipolare i dispositivi di scorrimento è un'azione di gioco innovativo. È importante assicurarsi che questi punti di connessione siano naturali. 

![L'estremità del cavo del ponte si illumina quando la mano dell'utente si avvicina](images/kippys-escape/kippys-escape-img-05.gif)

*L'estremità del cavo del ponte si illumina quando la mano dell'utente si avvicina*

## <a name="building-the-game-mechanics"></a>Creazione dei meccanismi di gioco 

Kippy's Escape si basa principalmente sui componenti di Mixed Reality UX Tools per rendere interattivo il gioco, ad esempio attori di interazione manuale, controlli limite, manipolatori, dispositivi di scorrimento e pulsanti.   

[L'attore di interazione manuale](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) consente la manipolazione diretta e da lontano degli ologrammi. All'inizio di Kippy's Escape, l'utente ha la possibilità di impostare la posizione del gioco. I trasli di mano che si estendono dal palmo dell'utente semplificano la manipolazione di ologrammi di grandi dimensioni molto distorsi, come illustrato nella gif seguente.  

![Gif dell'attore di interazione manuale](images/kippys-escape/kippys-escape-img-06.gif)

La scena segnaposto può essere trascinata e ruotata usando il componente di controllo dei limiti [di](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) UX Tools.  

Nella seconda isola, l'utente deve prelevare le gemme e posizionarle negli slot corrispondenti. Alle gemme sono [collegati manipolatori](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) che consentono all'utente di prelevarli e posizionarli. 

![Gif di esempio del manipolatore](images/kippys-escape/kippys-escape-img-07.gif)

Un [pulsante a pressione](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) è il tasto per portare in alto i cani da usare nella terza isola.  

![Gif di esempio di pulsante a pressione](images/kippys-escape/kippys-escape-img-08.gif)

Un [componente](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) dispositivo di scorrimento viene visualizzato nella quarta isola, attivando l'innalzamento del ponte finale.  

![Gif di esempio del componente Slider](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Ottimizzazione per HoloLens 2 

Con qualsiasi esperienza creata per l'esecuzione in un dispositivo mobile, è fondamentale tenere sotto controllo le prestazioni. Unreal 4.25 include un aggiornamento importante del supporto per la visualizzazione multipla per dispositivi mobili, che riduce significativamente l'overhead di rendering e aumenta la frequenza dei fotogrammi. È consigliabile controllare le altre [impostazioni delle prestazioni](performance-recommendations-for-unreal.md) consigliate per HoloLens 2 sviluppo con Unreal durante l'ottimizzazione.  

Gli oggetti fisici rimangono comunque costosi per le prestazioni, quindi sono state usate due soluzioni alternative intelligenti. Ad esempio, il terzo "ponte" richiede l'affollamento di alcuni blocchi che bloccano la scale. Invece di avere una forza che influisce sulle particelle come oggetti fisici, la detonazione della collisione attiva uno scambio, scambiando la particella statica per un effetto particella che esplode. 

![Esempio ottimizzato per HoloLens 2 gif](images/kippys-escape/kippys-escape-img-10.gif) 

Le chiamate di disegno vengono anche tagliate da oltre 400 a ~260 per: 
* Riduzione della complessità della mesh
* Combinazione di mesh
* Rimozione di alcuni degli elementi di illuminazione dinamica iniziali

Anche se probabilmente si sarebbe potuto fare di più, abbiamo ritenuto che fosse un buon equilibrio tra prestazioni e qualità visiva.  

## <a name="try-it-out"></a>Verifica 

Avviare il HoloLens 2 e [scaricare l'app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) dal Microsoft Store oppure clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) dal GitHub e compilare l'app manualmente.  

## <a name="about-the-team"></a>Informazioni sul team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack attualmente lavora a esperienze di realtà mista per Microsoft, inclusi HoloLens 2 e AltspaceVR, ed è stato in precedenza designer del team HoloLens piattaforma.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Estate Wu</b><br><i>Producer</i><br>L'estate lavora sulla piattaforma per sviluppatori di realtà mista e guida le attività correlate a Unreal Engine del team.</td>
</tr>
</table>

Grazie speciale agli amici di [Framestore per](https://www.framestore.com/) averci aiutati a dare vita a Kippy's Escape. Dallo sviluppo di caratteri, alla progettazione di asset, alla programmazione di giochi, la loro collaborazione su questo progetto è stata fondamentale.