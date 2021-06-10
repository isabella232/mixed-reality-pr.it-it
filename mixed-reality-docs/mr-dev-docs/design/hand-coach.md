---
title: Coach mano
description: Informazioni su come vengono attivate le mani 3D usando il pullman quando il sistema non rileva le mani dell'utente per assisterle.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, hand coach, visore vr immersivo, MRTK, mani, mani di supporto, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600430"
---
# <a name="hand-coach"></a>Coach mano

![Esempio: Hand coach](images/HandCoach/MRTK_handCoach.jpg)<br>

Il pullman attiva le mani modellate 3D quando il sistema non rileva le mani dell'utente. Questa funzionalità è un componente di "insegnamento" che aiuta a guidare l'utente quando il movimento non è stato insegnato. Se gli utenti non hanno eseguito il movimento specificato per un periodo, le mani scorreranno con un ritardo. Il hand coach può essere usato per rappresentare la pressione di un pulsante o la selezione di un ologramma.  

## <a name="hand-coach-provided"></a>Hand coach fornito

Il modello di interazione corrente rappresenta un'ampia gamma di controlli movimento, ad esempio scorrimento, selezione estrema e tocco vicino. Di seguito è riportato un elenco completo dei movimenti della mano esistenti disponibili in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK:</a>

:::row:::
    :::column:::
       ![Esempio di near select](images/HandCoach/NearSelect.gif)<br>
       **Esempio di Near Select - Usato per illustrare come selezionare pulsanti o chiudere oggetti interagiscibili**<br>
    :::column-end:::
    :::column:::
       ![Esempio di Air Tap](images/HandCoach/AirTap.gif)<br>
        **Esempio di Air Tap: usato per mostrare come selezionare oggetti che si sono allontanati**<br>
    :::column-end:::
    :::column:::
       ![Esempio di spostamento](images/HandCoach/Move.gif)<br>
       **Esempio di spostamento di un oggetto nello spazio Usato per mostrare come spostare un ologramma nello spazio**<br>
    :::column-end:::
    :::column:::
       ![Esempio di rotazione](images/HandCoach/Rotate.gif)<br>
       **Esempio di Rotate-Used per mostrare come ruotare ologrammi o oggetti**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Esempio di scalabilità](images/HandCoach/Scale.gif)<br>
       **Esempio di Scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli**<br>
    :::column-end:::
    :::column:::
       ![Esempio di Palm Up](images/HandCoach/PalmUp.gif)<br>
        **Esempio di Palm up - Uso consigliato per visualizzare i menu della mano**<br>
    :::column-end:::
    :::column:::
       ![Esempio di HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Exmaple of Hand Flip : un altro modo per visualizzare i menu a mano**<br>
    :::column-end:::
    :::column:::
       ![Esempio di scorrimento](images/HandCoach/Scoll.gif)<br>
       **Esempio di scorrimento: usato per scorrere un elenco o un documento lungo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Concetti relativi alla progettazione

Per Hololens2, sono state progettate interazioni con la mano in base a movimenti istintiva e naturali della mano. Si ritiene che siano intuitivi per la maggior parte degli utenti, quindi non sono stati creati momenti dedicati di apprendimento dei movimenti. È stato invece creato il hand coach per aiutare gli utenti a conoscere questi movimenti se si bloccano o non hanno familiarità con le interazioni con ologrammi. Senza un momento di apprendimento, si è ritenuto che mostrare agli utenti come eseguire un'azione dimostrando che sarebbe stata l'opzione migliore. È stato rilevato che gli utenti erano in grado di capire il movimento, ma che erano necessarie alcune indicazioni. Se si rileva che un utente non interagisce con un oggetto per un periodo di tempo, viene attivato un hand coach che mostra la corretta posizione di mano e dito. 

### <a name="intuitive"></a>intuitivo

Quando si animano le mani, dovrebbe essere ovvio e non deve causare confusione. L'animazione manuale è una rappresentazione del movimento che si sta tentando di chiedere all'utente di comprendere. 

Ad esempio, se si vuole che un utente premo un pulsante, viene attivata una mano che preme un pulsante.

![Esempio: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)<br>
*Hand Coach che illustra near tapping a gem*  

### <a name="hand-scale"></a>Scalabilità manuale

Sono state testate varie dimensioni della mano con i menu dell'interfaccia utente e si è ritenuto che se le mani fossero vere per le dimensioni, questo ha dato un'impressione minacciante. Se erano troppo piccoli, era difficile vedere e comprendere il movimento. 

**Voice over e hands**

Non aspettarsi che gli utenti possano ascoltare un set di istruzioni tramite voice over e guardare istruzioni diverse tramite Hand coach. Sequenziare le istruzioni per aiutare gli utenti a concentrarsi rispetto alla concorrenza per la loro attenzione per ridurre il sovraccarico sensoriale.


## <a name="can-i-create-my-own"></a>È possibile crearne uno personalizzato?

Sì. Ti invitiamo a creare un movimento unico per il tuo gioco e a contribuire alla community.
È stato fornito un file Maya di una mano <a href="files/HandCoach_MRTK.zip">ritardata</a> che può essere usata per l'app, che può essere scaricato qui: Scaricare HandCoach_MRTK.zip

![Esempio di Mani animate in Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Esempio di hand poking animato di una casella in Maya*


**Strumento di creazione consigliato**

Tra gli artisti 3D, molti scelgono di usare Maya di Autodesk, che può usare [HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono creati gli asset. Il file hands fornito è un file binario Maya, quindi è consigliabile usare Maya per animare ed esportare le mani. Se si preferisce usare un altro programma 3D, ecco <b>un . FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> scaricare HandCoachMRTK_FBX.zip </a> per creare la configurazione del controller. 

Se si usa il file di mano maya scaricabile fornito, è consigliabile ridimensionare le mani in unity fino a 0,6.

![Esempio: hand coach rig in Maya](images/HandCoach/MayaExample.png)<br>
*Mani truccate*

### <a name="technical-specs"></a>Specifiche tecniche

*   Il file a due mani è disponibile in formato Maya Ascii
*    La mano destra e la mano sinistra sono disponibili in formato binario Maya
*   Impostare il file Maya su 24 FPS
*   All'interno del file sono presenti una mano sinistra e una destra, che possono essere usate per i movimenti a due mani o con una sola mano. La mano destra sarà visibile solo per impostazione predefinita.
*   È consigliabile lasciare un buffer di circa 10 fotogrammi all'inizio e alla fine per le dissolvenze
*   Se si anima un oggetto con una destinazione specificata, è consigliabile aggiungere un'animazione a una casella Predefinita o Null.
*   Se la mano anima un oggetto fisico, ad esempio una casella, è consigliabile non animare la traduzione in Maya, ma attendere di animarla in Unity o nel codice.
*   L'animazione visibile deve essere di 1,5 secondi per trasmettere tutte le informazioni significative
*   Quando si è soddisfatti dell'animazione:
    *   Selezionare tutti i giunzioni e bake fotogrammi chiave
    *   Eliminare i controller, selezionare le giunzioni e la mesh ed esportare come FBX
    *  Se sono presenti più animazioni, è possibile usare l'esportatore di giochi incorporato di Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Esportazione da Maya

Dopo aver soddisfatto l'animazione
* Seleziona tutti i giunzioni: selezionare > gerarchia

     ![Esempio: Gerarchia nel menu](images/HandCoach/Hierarchy.png)<br>
* Preparare l'animazione: passare all'animazione > chiave > Bake Animation

     ![Esempio: Bake Animation Menu Location](images/HandCoach/BakeAnimation.png)<br>
* Eliminare il rig controller: outliner > MainR_Grp o MainL_Grp

     ![Esempio: Posizione menu rig controller](images/HandCoach/ControllerRig.png)<br>

* Esporta come FBX: selezionare JNT + Mesh: Selezione > file (casella di opzione) > Esporta selezione

     ![Esempio: Esportare la posizione del menu di selezione](images/HandCoach/OptionBox.png)<br>

     ![Esempio: Posizione menu](images/HandCoach/SelectionExport.png)<br>

     ![Esempio: Percorso del menu Opzioni di esportazione](images/HandCoach/FBXSelection.png)<br>


 Quando si esegue l'esportazione come FBX e si esegue l'importazione in Unity, ridimensionare le mani fino a 0,6. È stato rilevato che si tratta di un equilibrio perfetto per la visualizzazione delle mani. 

![Esempio: Impostazioni di Unity](images/HandCoach/HandHintScale.png)<br>
*Impostazioni unity per HandCoach_R prefab trovato in MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementazione di Hands nel progetto Unity

### <a name="best-practices"></a>Procedure consigliate

* È consigliabile ridimensionare le mani in unity fino a 0,6
* Le mani devono essere riprodotte due volte e, se non sono completate, viene eseguito un ciclo continuo fino al completamento del movimento. Le mani devono essere registrate due volte per assicurarsi che l'utente sia in grado di registrarsi e visualizzare il movimento. Le mani devono dissolvenza in entrata e in uscita tra i cicli. 
 *  Se le mani dell'utente sono visibili dalle fotocamere HL2, ma gli utenti non stanno effettuando l'interazione necessaria, le mani verranno visualizzate dopo 10 secondi.
*   Se le mani dell'utente NON sono visibili dalle fotocamere HL2, le mani verranno visualizzate dopo 5 secondi.  
*   Se le mani dell'utente vengono monitorate in modo visibile dalle fotocamere HL2 al centro dell'animazione, l'animazione verrà completata e dissolvenza in dissolvenza.
*   Se si include voice over, è consigliabile che corrisponda al movimento della mano.
*   Se le mani sono state insegnate almeno una volta, ripetere il movimento solo se viene rilevato che l'utente è bloccato.
*   Se posizioni specifiche del dito o della mano sono fondamentali, assicurarsi che gli utenti possano vedere chiaramente queste sfumature nell'animazione. Provare a angling le mani in modo che le parti più importanti siano chiaramente visibili. 
* Se si nota una distorsione sulle mani, è necessario passare alle impostazioni di Qualità di Unity per aumentare il numero di esche. 
 Passare a Modifica impostazioni > progetto di Unity > qualità > altri pesi > blend. Assicurarsi che sia selezionata l'opzione "4 esche" per visualizzare Smooth Joints (Giunzioni smooth).

   ![Esempio: finestra Impostazioni progetto](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>Da evitare

* Ridimensionamento delle mani troppo grande
* posizionamento delle mani troppo vicino all'utente
* Le mani devono essere insegnate una sola volta. L'over teaching può causare confusione e confusione
* Per scaricarlo in Unity, scaricare la versione più recente di MRTK qui: https://github.com/microsoft/MixedRealityToolkit-Unity
  * Materiale: Teaching_Hand2
  * Script: fare riferimento alle linee guida di MRTK per <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> il hand coach MRTK </a>
  * Impostazione per progetto
    * Scena impostata su UWP: le istruzioni sono disponibili in [Configurare il progetto Unity](../develop/unity/Configure-Unity-Project.md) per Windows Mixed Reality

## <a name="see-also"></a>Vedi anche

* [Nozioni fondamentali sull'interazione](interaction-fundamentals.md)
* [Processo di creazione di asset](asset-creation-process.md)
* [Movimenti](./interaction-fundamentals.md)
* [Installare gli strumenti](../develop/install-the-tools.md)
* [Configurare il progetto Unity](../develop/unity/Configure-Unity-Project.md)
* [Panoramica dello sviluppo per Unity](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)