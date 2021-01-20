---
title: Creazione dell'escape di Kippy
description: Seguici durante l'esplorazione della creazione dell'applicazione di escape Mixed Reality Kippy per HoloLens 2 in Unreal Engine.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione su dispositivo, PC, documentazione, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: 7302e6c8d5de866b652ec4741fbef128eca616e0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580810"
---
# <a name="the-making-of-kippys-escape"></a>Creazione dell'escape di Kippy

Kippy il robot si riattiva per trovarsi in un'isola. L'utente deve mettere in pratica il cappello per risolvere i problemi per trovare un percorso di ritorno alla propria astronave. È possibile [scaricare l'app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) dal Microsoft Store o clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) da GitHub e ottenere Kippy Home Safe.  

> [!IMPORTANT]
> Assicurarsi di usare **Unreal Engine 4,25 o versione successiva** se si sta creando l'escape di Kippy dal repository GitHub.

L'escape di Kippy è un'app di esempio [HoloLens 2](/hololens/hololens2-hardware) Open Source compilata con Unreal Engine 4 e [gli strumenti UX per la realtà mista per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal). In questo post verrà illustrata la procedura da seguire per i primi principi e la progettazione visiva per l'implementazione e l'ottimizzazione dell'esperienza. È possibile trovare altre informazioni sullo sviluppo di applicazioni di realtà miste con gli strumenti UX MRTK nella [Panoramica dello sviluppo non reale](unreal-development-overview.md).

## <a name="first-principles"></a>Principi iniziali 

Nell'impostazione di per creare l'escape di Kippy, il nostro obiettivo era quello di creare un'esperienza che evidenziasse il [supporto di HoloLens 2 di Unreal Engine](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), le funzionalità di HoloLens 2 e il Toolkit di realtà mista. Volevamo ispirare gli sviluppatori a immaginare cosa potessero creare con Unreal e HoloLens 2.  

Sono stati rilevati tre principi guida per l'esperienza: che era necessario per essere divertenti, interattivi e avere un basso ostacolo all'ingresso. Volevamo che l'esperienza fosse abbastanza intuitiva che anche un utente di realtà mista per la prima volta non necessiti di un'esercitazione.  

## <a name="designing-the-game"></a>Progettazione del gioco 

HoloLens 2 ha accesso alle funzionalità di progettazione che non sono state trovate in nessun altro momento nei giochi. Gli oggetti possono essere direttamente spostati o modificati usando le mani o mirati al rilevamento a occhio. Queste funzionalità principali sono alla base di alcuni dei momenti di divertimento compilati nell'escape di Kippy.  

Usando le funzionalità di HoloLens 2 univoche come linee guida per la progettazione di giochi, abbiamo definito alcuni scenari di ambiente di piccole dimensioni. Le isole hanno avuto senso perché possono essere modificate per diverse altezze dei giocatori e forniscono alcune interessanti idee sul Bridge. Siamo atterrati sul tema della civiltà antica che soddisfa la fantascienza, con l'idea che qualcuno ha creato macchinari su rovine che sfruttano una strana energia fornita da ogni isola. Le isole venivano ognuna con un aspetto specifico, un dettaglio che consentiva di creare un interesse visivo. Un giusto equilibrio tra la modellazione e la creazione di texturing consente di tenere le chiamate di traccia basse per le prestazioni di rendering, quindi un aspetto stilizzato è stato progettato tenendo presente questo aspetto. 

![La progettazione dei primi Giochi Disegna ](images/kippys-escape/kippys-escape-img-01.png)
 *alcuni schizzi iniziali per l'aspetto dell'esperienza*

![Rendering dei rendering delle seconde isole ](images/kippys-escape/kippys-escape-img-02.png)
 *della seconda isola*

Per rimanere entro la pianificazione di produzione breve, abbiamo stabilito che un carattere a virgola mobile potrebbe acquisire finalità ed emozioni senza cicli di animazione rigorosi. Quindi, Kippy è Nato! Emotes alcune espressioni diverse attraverso gli occhi e con gli effetti vocali di un suono minimalista per aiutare il lettore a eseguire l'intera esperienza. 

![Kippy che mostra espressioni diverse tramite gli occhi](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy che mostra espressioni diverse tramite gli occhi*

![Se l'utente impiega troppo tempo per risolvere un rompicapo, Kippy fornirà all'utente un suggerimento](images/kippys-escape/kippys-escape-img-04.gif)

*Se l'utente impiega troppo tempo per risolvere un rompicapo, Kippy fornirà all'utente un suggerimento*

Al di là della progettazione di caratteri e ambienti, abbiamo deciso di impegnarsi per far divertire il gioco. Il rilevamento degli occhi ci ha consentito di avviare gli attributi di materiali e suoni, che hanno evidenziato le parti principali del gioco. L'audio spaziale ha aiutato a far sentire i livelli a casa nell'ambiente del giocatore. La possibilità di acquisire oggetti, pulsanti di push e manipolare i dispositivi di scorrimento consente di coinvolgere i giocatori in modo innovativo. Era importante assicurarsi che questi punti di connessione fossero naturali. 

![La fine del cavo del Bridge si illumina quando l'utente si avvicina](images/kippys-escape/kippys-escape-img-05.gif)

*La fine del cavo del Bridge si illumina quando l'utente si avvicina*

## <a name="building-the-game-mechanics"></a>Creazione dei meccanismi di gioco 

L'escape di Kippy si basa principalmente sui componenti degli strumenti UX della realtà mista per rendere il gioco interattivo, ovvero gli attori di interazione, i controlli dei limiti, i manipolatori, i dispositivi di scorrimento e i pulsanti.   

L' [attore di interazione Hand](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) consente la manipolazione diretta e distante degli ologrammi. All'inizio della sequenza di escape di Kippy, all'utente viene data la possibilità di impostare la posizione del gioco. I raggi mano che si estendono dalla palma dell'utente consentono di modificare facilmente gli ologrammi di grandi dimensioni, come illustrato nel gif riportato di seguito.  

![Gif attore interazione mano](images/kippys-escape/kippys-escape-img-06.gif)

La scena segnaposto può essere trascinata e ruotata utilizzando il componente di [controllo dei limiti](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) degli strumenti UX.  

Nella seconda isola è necessario che l'utente acquisisca le gemme e le inserisca negli slot corrispondenti. Le gemme hanno [manipolatori](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) collegati che consentono all'utente di riprenderle e inserirle. 

![Gif di esempio del manipolatore](images/kippys-escape/kippys-escape-img-07.gif)

Un [pulsante stampabile](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) è la chiave per attivare le bombe da usare sulla terza isola.  

![Gif di esempio del pulsante stampabile](images/kippys-escape/kippys-escape-img-08.gif)

Viene visualizzato un componente [Slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) sulla quarta isola, che attiva il Bridge finale da generare.  

![Gif di esempio del componente Slider](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Ottimizzazione per HoloLens 2 

Con qualsiasi esperienza compilata per l'esecuzione su un dispositivo mobile, è essenziale tenere sotto controllo le prestazioni. Unreal 4,25 include un aggiornamento principale per il supporto per la visualizzazione a più livelli per dispositivi mobili, riducendo significativamente il sovraccarico del rendering e aumentando la frequenza dei fotogrammi. È consigliabile consultare le altre [impostazioni di prestazioni consigliate](performance-recommendations-for-unreal.md) per lo sviluppo HoloLens 2 con Unreal quando si esegue l'ottimizzazione.  

Gli oggetti fisici rimangono comunque costosi per le prestazioni, quindi sono state usate alcune soluzioni intelligenti. Il terzo "Bridge", ad esempio, deve saltare alcuni detriti che bloccano la scala. Invece di avere un impatto forzato sulle pietre come oggetti fisici, la detonazione della bomba attiva uno scambio, cambiando le pietre statiche per un effetto particellare esploso. 

![Esempio ottimizzato per HoloLens 2 gif](images/kippys-escape/kippys-escape-img-10.gif) 

Si ritagliano anche le chiamate di estrazione da oltre 400 a ~ 260 da: 
* Riduzione della complessità della mesh
* Combinazione di mesh
* Rimozione di alcuni elementi di illuminazione dinamica iniziali

Anche se è probabile che si sia fatto di più, abbiamo pensato che era un giusto equilibrio tra prestazioni e qualità visiva.  

## <a name="try-it-out"></a>Verifica 

Avviare il HoloLens 2 e [scaricare](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) l'app dal Microsoft Store oppure clonare il [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) da GitHub e compilare l'app.  

## <a name="about-the-team"></a>Informazioni sul team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack attualmente funziona con esperienze di realtà mista per Microsoft, inclusi i progetti HoloLens 2 e AltspaceVR, e in precedenza era un progettista del team della piattaforma HoloLens.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Wu dell'estate</b><br><i>Producer</i><br>L'estate lavora sulla piattaforma di sviluppo di realtà mista e testa le attività relative ai motori non reali del team.</td>
</tr>
</table>

Grazie speciale per i nostri amici di [Framestore](https://www.framestore.com/) , che ci aiutano a portare la fuga di Kippy. Dallo sviluppo di caratteri, alla progettazione di asset, alla programmazione dei giochi, la loro collaborazione su questo progetto era fondamentale.