---
title: La creazione della fuga di Kippy
description: Seguici mentre esploriamo la creazione dell'applicazione di realtà mista Kippy's Escape per HoloLens 2 in Unreal Engine.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, deploy to device, PC, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757114"
---
# <a name="the-making-of-kippys-escape"></a>La creazione di Kippy's Escape
![Immagine dell'hero escape di Kippy](images/KippysEscape_1920.jpg)

Kippy il robot si sveglia per trovare se stesso bloccato su un'isola. Sta a te mettere il tuo hat per risolvere i problemi per trovare un percorso per tornare alla sua naVe di razzi. Aggiungere il HoloLens 2 e [scaricare l'app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) dal Microsoft Store o clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) da GitHub e ottenere Kippy a casa al sicuro.  

> [!IMPORTANT]
> Assicurarsi di usare **Unreal Engine 4.25** o versione successiva se si sta creando Kippy's Escape dal repository GitHub.

Kippy's Escape è un'app HoloLens 2 open [source](/hololens/hololens2-hardware) compilata con Unreal Engine 4 e [Mixed Reality UX Tools per Unreal.](https://github.com/microsoft/MixedReality-UXTools-Unreal) Questo post illustra il processo, dai primi principi e progettazione visiva all'implementazione e all'ottimizzazione dell'esperienza. Altre informazioni sullo sviluppo di applicazioni di realtà mista con MRTK UX Tools sono disponibili nella panoramica sullo sviluppo [di Unreal.](unreal-development-overview.md)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Scaricare l'app Microsoft Store in HoloLens 2
Se si dispone di HoloLens 2, è possibile scaricare e installare direttamente l'app nel dispositivo.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>Primi principi 

Per creare l'escape di Kippy, l'obiettivo era creare un'esperienza che evidenziasse il supporto HoloLens 2 di [Unreal Engine,](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)le funzionalità del HoloLens 2 e l'Toolkit di realtà mista. Abbiamo voluto ispirare gli sviluppatori a immaginare cosa potevano creare con Unreal e HoloLens 2.  

Sono stati emersi tre principi guida per l'esperienza: che doveva essere divertente, interattivo e avere una bassa barriera all'ingresso. L'esperienza era sufficientemente intuitiva che anche un utente di realtà mista per la prima volta non avrebbe bisogno di un'esercitazione.  

## <a name="designing-the-game"></a>Progettazione del gioco 

Il HoloLens 2 ha accesso a funzionalità di progettazione che non si trovano in nessun'altra parte del gioco. Gli oggetti possono essere spinti o manipolati direttamente usando le mani o mirati con il tracciamento oculare. Queste funzionalità chiave sono alla base di alcuni dei momenti divertenti che abbiamo creato in Kippy's Escape.  

Usando le funzionalità HoloLens 2 come indicazioni per la progettazione del gioco, sono stati descritti alcuni scenari di ambiente di piccole dimensioni. Le isole hanno senso perché possono essere regolate in base alle diverse altezze dei giocatori e hanno fornito alcune idee di bridge divertenti. Il tema dell'erezione moderna incontra la tecnologia sci-fi, con l'idea che qualcuno abbia costruito macchinari sopra le macerie sfruttando una energia sconosciuta fornita da ogni isola. Alle isole è stato assegnato il proprio aspetto, un dettaglio che ha contribuito a creare interesse visivo. Un buon equilibrio tra modellazione e texturing mantenerebbe le chiamate di disegno basse per le prestazioni di rendering, quindi un aspetto stilizzato è stato progettato in base a questo aspetto. 

![Bozzetti di progettazione dei primi giochi ](images/kippys-escape/kippys-escape-img-01.png)
 *Alcuni bozzetti iniziali per l'aspetto dell'esperienza*

![Rendering della seconda isola ](images/kippys-escape/kippys-escape-img-02.png)
 *Rendering della seconda isola*

Per rimanere entro la pianificazione di produzione breve, è stato concordato che un carattere mobile potrebbe acquisire finalità ed emozioni senza cicli di animazione rigorosi. E così è nato Kippy! Emotes alcune espressioni diverse attraverso i suoi occhi e attraverso effetti sonori vocali minimali per aiutare a guidare il giocatore durante l'esperienza. 

![Kippy che mostra espressioni diverse tramite gli occhi](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy che mostra espressioni diverse tramite gli occhi*

![Se l'utente impiega troppo tempo per risolvere un rompicapo, Kippy offrirà all'utente un suggerimento](images/kippys-escape/kippys-escape-img-04.gif)

*Se l'utente impiega troppo tempo per risolvere un rompicapo, Kippy offrirà all'utente un suggerimento*

Oltre alla progettazione del carattere e dell'ambiente, abbiamo fatto uno sforzo comune per far si che il gioco si senta divertente. Il tracciamento oculare ha consentito di spegnere gli attributi del materiale e del suono, che hanno evidenziato le parti chiave del gioco. L'audio spaziale ha contribuito a far si che i livelli si senta a casa nell'ambiente del lettore. La possibilità di afferrare oggetti, premere i pulsanti e manipolare i dispositivi di scorrimento determina interazioni innovative tra i giocatori. Era importante assicurarsi che questi punti di connessione si sentisse naturale. 

![La fine del cavo del ponte si illumina quando la mano dell'utente si avvicina](images/kippys-escape/kippys-escape-img-05.gif)

*La fine del cavo del ponte si illumina quando la mano dell'utente si avvicina*

## <a name="building-the-game-mechanics"></a>Compilazione dei meccanismi di gioco 

Kippy's Escape si basa principalmente sui componenti degli strumenti dell'esperienza utente di realtà mista per rendere interattivo il gioco, ad esempio attori di interazione manuale, controlli limite, manipolatori, dispositivi di scorrimento e pulsanti.   

[L'attore di interazione manuale](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) consente sia la manipolazione diretta che la manipolazione di lontano degli ologrammi. All'inizio di Kippy's Escape, l'utente ha la possibilità di impostare la posizione del gioco. I travi a mano che si estendono dal palmo dell'utente semplificano la manipolazione di ologrammi di grandi dimensioni che si estendono lontano, come illustrato nella gif seguente.  

![Gif dell'attore dell'interazione con la mano](images/kippys-escape/kippys-escape-img-06.gif)

La scena segnaposto può essere trascinata e ruotata usando il componente di controllo dei limiti [di](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) UX Tools.  

Nella seconda isola, l'utente deve raccogliere le gemme e posizionarle negli slot corrispondenti. Alle gemme sono [associati manipolatori](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) che consentono all'utente di prelevarli e posizionarli. 

![Gif di esempio del manipolatore](images/kippys-escape/kippys-escape-img-07.gif)

Un [pulsante pressabile](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) è la chiave per far alzare le bombe per l'uso nella terza isola.  

![Gif di esempio del pulsante pressable](images/kippys-escape/kippys-escape-img-08.gif)

Un [componente dispositivo](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) di scorrimento viene visualizzato sulla quarta isola, attivando il bridge finale da alzare.  

![Gif di esempio del componente Slider](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Ottimizzazione per HoloLens 2 

Con qualsiasi esperienza creata per l'esecuzione in un dispositivo mobile, tenere sotto controllo le prestazioni è fondamentale. Unreal 4.25 include un aggiornamento importante per il supporto della multi-visualizzazione per dispositivi mobili, che riduce significativamente l'overhead di rendering e aumenta la frequenza dei fotogrammi. È consigliabile controllare le altre impostazioni [di](performance-recommendations-for-unreal.md) prestazioni consigliate per HoloLens 2 sviluppo con Unreal durante l'ottimizzazione.  

Gli oggetti fisici rimangono comunque costosi per le prestazioni, quindi sono state usate due soluzioni alternative intelligenti. Ad esempio, il terzo "ponte" richiede l'espianto di alcuni residui che bloccano la scala. Invece di avere una forza che influisce sulle rocce come oggetti fisici, la detonazione della bomba attiva uno scambio, scambiando le rocce statiche per un effetto di particella che esplode. 

![Esempio ottimizzato per HoloLens 2 gif](images/kippys-escape/kippys-escape-img-10.gif) 

È anche possibile ridurre le chiamate di disegno da oltre 400 a ~260 per: 
* Riduzione della complessità della mesh
* Combinazione di mesh
* Rimozione di alcuni elementi di illuminazione dinamica iniziali

Anche se probabilmente si sarebbe potuto fare di più, si è ritenuto che si trattasse di un buon equilibrio tra prestazioni e qualità visiva.  

## <a name="try-it-out"></a>Verifica 

Avviare il HoloLens 2 e [scaricare l'app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) dal Microsoft Store oppure clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) da GitHub e compilare l'app manualmente.  

## <a name="about-the-team"></a>Informazioni sul team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack attualmente lavora su esperienze di realtà mista per Microsoft, inclusi HoloLens 2 e AltspaceVR, ed è stato in precedenza designer nel team HoloLens platform.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Wu estivo</b><br><i>Producer</i><br>Summer lavora sulla piattaforma per sviluppatori di realtà mista e dirige gli sforzi correlati al motore Unreal del team.</td>
</tr>
</table>

Grazie speciale ai nostri amici di [Framestore per](https://www.framestore.com/) averci aiutati a dare vita a Kippy's Escape. Dallo sviluppo di personaggi, alla progettazione di asset, alla programmazione di giochi, la collaborazione su questo progetto è stata fondamentale.