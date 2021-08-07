---
title: Coach mano
description: Informazioni su come le mani 3D vengono attivate usando il ricevitore della mano quando il sistema non rileva le mani dell'utente per assisterle.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, hand- hand, visore VR immersive, MRTK, mani, mani di aiuto, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: baf1dab7d73f4e5fca9078717b43dab7b71632f4aa7c36dcac280c029b05d58b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208526"
---
# <a name="hand-coach"></a>Coach mano

![Esempio: Hand hand hand](images/HandCoach/MRTK_handCoach.jpg)<br>

Il data mining della mano attiva le mani modellate in 3D quando il sistema non rileva le mani dell'utente. Questa funzionalità è un componente di "formazione" che consente di guidare l'utente quando il movimento non è stato insegnato. Se gli utenti non hanno eseguito il movimento specificato per un periodo, le mani scorreranno a ciclo continuo con un ritardo. È possibile usare il taser mano per rappresentare la pressione di un pulsante o la selezione di un ologramma.  

## <a name="hand-coach-provided"></a>Hand hand hand provided

Il modello di interazione corrente rappresenta un'ampia gamma di controlli di movimento, ad esempio scorrimento, selezione da lontano e tocco vicino. Di seguito è riportato un elenco completo dei movimenti della mano esistenti forniti in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK:</a>

:::row:::
    :::column:::
       ![Esempio di selezione da vicino](images/HandCoach/NearSelect.gif)<br>
       **Esempio di selezione da vicino - Usato per mostrare come selezionare pulsanti o chiudere oggetti con interazione**<br>
    :::column-end:::
    :::column:::
       ![Esempio di air tap](images/HandCoach/AirTap.gif)<br>
        **Esempio di tocco d'aria: usato per mostrare come selezionare oggetti molto distorsi**<br>
    :::column-end:::
    :::column:::
       ![Esempio di spostamento](images/HandCoach/Move.gif)<br>
       **Esempio di spostamento di un oggetto nello spazio usato per mostrare come spostare un ologramma nello spazio**<br>
    :::column-end:::
    :::column:::
       ![Esempio di rotazione](images/HandCoach/Rotate.gif)<br>
       **Esempio di Rotate-Used per mostrare come ruotare ologrammi o oggetti**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Esempio di scalabilità](images/HandCoach/Scale.gif)<br>
       **Esempio di scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli**<br>
    :::column-end:::
    :::column:::
       ![Esempio di Palm Up](images/HandCoach/PalmUp.gif)<br>
        **Esempio di Palm up - Suggested use (Esempio di Palm up- Uso consigliato) per visualizzare i menu delle mani**<br>
    :::column-end:::
    :::column:::
       ![Esempio di HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Esempio di capovolgimento della mano: un altro modo per visualizzare i menu a mano**<br>
    :::column-end:::
    :::column:::
       ![Esempio di scorrimento](images/HandCoach/Scoll.gif)<br>
       **Esempio di scorrimento: usato per scorrere un elenco o un documento lungo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Concetti relativi alla progettazione

Per Hololens2, abbiamo progettato interazioni con la mano basate su movimenti istintivo e naturale della mano. Si ritiene che questi elementi siano intuitivi per la maggior parte degli utenti, quindi non sono stati creati momenti dedicati di apprendimento del movimento. È stata invece creata la mano per aiutare gli utenti a conoscere questi movimenti se si bloccano o non hanno familiarità con le interazioni con gli ologrammi. Senza un momento di apprendimento, abbiamo ritenuto che mostrare agli utenti come eseguire un'azione dimostrando che sarebbe stata l'opzione migliore. È stato rilevato che gli utenti erano in grado di capire il movimento, ma che erano necessarie alcune indicazioni. Se si rileva che un utente non interagisce con un oggetto per un periodo di tempo, viene attivato un ricevitore della mano che dimostra il posizionamento corretto della mano e del dito. 

### <a name="intuitive"></a>intuitivo

Quando si animano le mani, dovrebbe essere ovvio e non deve causare confusione. L'animazione manuale è una rappresentazione del movimento che si sta tentando di chiedere all'utente di comprendere. 

Ad esempio, se si vuole che un utente premo un pulsante, viene attivata una mano che preme un pulsante.

![Esempio: Hand near tap](images/HandCoach/NearSelect_unity.gif)<br>
*Hand Hand Demonstrating Near Tapping a Gem (Hand Hand Che illustra il tocco vicino a una gemma)*  

### <a name="hand-scale"></a>Scala manuale

Sono state testate varie dimensioni delle mani con i menu dell'interfaccia utente e si è provato che, se le mani fossero vere per le dimensioni, si è provato una sensazione minacing. Se erano troppo piccoli, era difficile vedere e comprendere il movimento. 

**Voice over e mani**

Non aspettarsi che gli utenti possano ascoltare un set di istruzioni tramite voice over e guardare istruzioni diverse tramite Hand hand hand. Sequenziare le istruzioni per aiutare gli utenti a concentrarsi e a concorrere per la loro attenzione per ridurre il sovraccarico sensoriale.


## <a name="can-i-create-my-own"></a>È possibile crearne di personalizzati?

superato. Ti invitiamo a creare un movimento unico per il tuo gioco e a contribuire alla community.
È stato fornito un file Maya di una mano con tag che può essere usato per l'app, che può essere scaricato qui: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a>

![Esempio di mani animate in Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Esempio di hand poking animato di una casella in Maya*


**Strumento di creazione consigliato**

Tra gli autori 3D, molti scelgono di usare Maya di [Autodesk,](https://www.youtube.com/watch?v=q0K3n0Gf8mA) che può usare HoloLens per trasformare il modo in cui vengono creati gli asset. Il file hands fornito è un file binario Maya, quindi è consigliabile usare Maya per animare ed esportare le mani. Se si preferisce usare un altro programma 3D, ecco <b>un . FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> scaricare HandCoachMRTK_FBX.zip </a> per creare la configurazione del controller. 

Se si usa il file maya Hand scaricabile fornito, è consigliabile ridimensionare le mani in Unity a 0.6.

![Esempio: hand rig in Maya](images/HandCoach/MayaExample.png)<br>
*Mani in mano*

### <a name="technical-specs"></a>Specifiche tecniche

*   Il file a due mani è disponibile in formato Ascii Maya
*    La mano destra e la mano sinistra sono disponibili in formato binario Maya
*   Impostare il file Maya su 24 FPS
*   All'interno del file sono presenti una mano sinistra e una destra, che possono essere usate per i movimenti con due mani o con una sola mano. La mano destra sarà visibile solo per impostazione predefinita.
*   È consigliabile lasciare un buffer di circa 10 fotogrammi all'inizio e alla fine per le dissolvenze
*   Se si anima un oggetto con una destinazione specificata, è consigliabile aggiungere un'animazione a una casella Predefinita o Null.
*   Se la mano anima un oggetto fisico, ad esempio una casella, è consigliabile non animare la traduzione in Maya, ma attendere di animarla in Unity o nel codice.
*   L'animazione visibile deve essere di 1,5 secondi per poter trasmettere informazioni significative
*   Quando si è soddisfatti dell'animazione:
    *   Selezionare tutti i giunzioni e bakere i fotogrammi chiave
    *   Eliminare i controller, selezionare i giunzioni e la mesh ed esportare come FBX
    *  Se sono presenti più animazioni, è possibile usare l'esportatore di giochi incorporato di Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Esportazione da Maya

Quando si è soddisfatti dell'animazione
* Selezionare tutti i giunzioni: selezionare > gerarchia

     ![Esempio: Gerarchia nel menu](images/HandCoach/Hierarchy.png)<br>
* Eseguire il bake dell'animazione: passare all'animazione >'animazione > bake

     ![Esempio: Bake Animation Menu Location](images/HandCoach/BakeAnimation.png)<br>
* Eliminare l'oggetto Controller Rig: Outliner > MainR_Grp o MainL_Grp

     ![Esempio: Posizione del menu del rig del controller](images/HandCoach/ControllerRig.png)<br>

* Esporta come FBX: selezionare JNT + Mesh: File > Esporta selezione (casella di opzione) > Esporta selezione

     ![Esempio: Export selection Menu Location (Esporta posizione menu di selezione)](images/HandCoach/OptionBox.png)<br>

     ![Esempio: Posizione del menu](images/HandCoach/SelectionExport.png)<br>

     ![Esempio: Percorso del menu Opzioni di esportazione](images/HandCoach/FBXSelection.png)<br>


 Quando si esegue l'esportazione come FBX e si importa in Unity, ridimensionare le mani a 0,6. È stato rilevato che si tratta di un equilibrio perfetto per la visualizzazione delle mani. 

![Esempio: Unity Impostazioni](images/HandCoach/HandHintScale.png)<br>
*Unity Impostazioni per HandCoach_R prefab trovato in MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementazione di Hands nel progetto Unity

### <a name="best-practices"></a>Procedure consigliate

* È consigliabile ridimensionare le mani in Unity a 0,6
* Le mani devono essere riprodotte due volte e, se non vengono completate, vengono continuamente riprodotte a ciclo continuo fino al completamento del movimento. Le mani devono essere cicliate due volte per assicurarsi che l'utente sia in grado di registrarsi e visualizzare il movimento. Le mani devono dissolversi tra i cicli. 
 *  Se le mani dell'utente sono visibili dalle fotocamere HL2, ma gli utenti non stanno eseguendo l'interazione necessaria, le mani verranno visualizzate dopo 10 secondi.
*   Se le mani dell'utente NON sono visibili dalle fotocamere HL2, le mani verranno visualizzate dopo 5 secondi.  
*   Se le mani dell'utente vengono monitorate visibilmente dalle fotocamere HL2 al centro dell'animazione, l'animazione verrà completata e dissolvenza.
*   Se si include voice over, è consigliabile che corrisponda al movimento della mano.
*   Se non hai insegnato le mani almeno una volta, ripeti il movimento solo se viene rilevato che l'utente è bloccato.
*   Se posizioni specifiche del dito/mano sono critiche, assicurarsi che gli utenti possano vedere chiaramente queste sfumature nell'animazione. Provare a angolare le mani in modo che le parti più importanti siano chiaramente visibili. 
* Se si nota una distorsione sulle mani, è necessario passare alle impostazioni di qualità di Unity per aumentare il numero di elementi. 
 Passare a Edit > Project Impostazioni > Quality > Other > Blend Weights (Modifica > qualità di Unity). Assicurarsi che siano selezionati "4 puntini" per visualizzare Smooth Joints (Giunzioni uniformi).

   ![Esempio: finestra Project Impostazioni](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>Da evitare

* Ridimensionamento delle mani troppo grande
* posizionamento delle mani troppo vicino all'utente
* Le mani devono essere insegnate una sola volta. L'over teaching può causare confusione e confusione
* Per scaricarlo in Unity, scaricare la versione più recente di MRTK qui: https://github.com/microsoft/MixedRealityToolkit-Unity
  * Materiale: Teaching_Hand2
  * Script: fare riferimento alle linee guida di MRTK per <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> mrtk hand- </a>
  * Impostazione per progetto
    * Scena impostata su UWP: le istruzioni sono disponibili nella pagina [Configurare unity Project](../develop/unity/Configure-Unity-Project.md) per Windows Mixed Reality

## <a name="see-also"></a>Vedi anche

* [Concetti fondamentali sull'interazione](interaction-fundamentals.md)
* [Processo di creazione di asset](asset-creation-process.md)
* [Movimenti](./interaction-fundamentals.md)
* [Installare gli strumenti](../develop/install-the-tools.md)
* [Configurare unity Project](../develop/unity/Configure-Unity-Project.md)
* [Panoramica dello sviluppo per Unity](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)