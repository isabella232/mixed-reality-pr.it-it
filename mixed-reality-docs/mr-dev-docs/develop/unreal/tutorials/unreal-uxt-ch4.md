---
title: 4. Rendere la scena interattiva
description: Parte 4 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 08/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: a4ad1879e73c85e25e5de675a4180f57361691a9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702397"
---
# <a name="4-making-your-scene-interactive"></a>4. Rendere la scena interattiva

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente hai aggiunto un asset ARSession, il pedone e la modalità gioco per completare la configurazione della realtà mista per l'app di scacchi. Questa sezione è dedicata al plug-in open source [UX Tools di Mixed Reality Toolkit](https://github.com/microsoft/MixedReality-UXTools-Unreal), che include gli strumenti necessari per rendere la scena interattiva. Alla fine della sezione sarai in grado di spostare i pezzi sulla scacchiera con l'input dell'utente. 

## <a name="objectives"></a>Obiettivi

* Download del plug-in UX Tools di Mixed Reality Toolkit 
* Aggiunta di attori di interazione manuale sulla punta delle dita
* Creazione e aggiunta di manipolatori agli oggetti nella scena
* Uso della simulazione dell'input per convalidare il progetto

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>Download del plug-in UX Tools di MRTK
Prima di iniziare a usare l'input dell'utente, è necessario aggiungere il plug-in al progetto.

1.  Nella [pagina delle versioni](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) di UX Tools per la realtà mista su GitHub passare alla versione UX Tools for Unreal v0.9.0 e scaricare **UXTools.0.9.0.zip** . Decomprimere i file.

2.  Crea una nuova cartella denominata **Plugins** (Plug-in) nella cartella radice del progetto. Copia il plug-in UXTools decompresso in questa cartella e riavvia l'editor Unreal. 

![Creare una cartella dei plug-in del progetto](images/unreal-uxt/4-plugins.PNG)

3.  Il plug-in UX Tools include una cartella Content (Contenuto) con sottocartelle per i componenti, tra cui **Buttons** (Pulsanti), **Input Simulation** (Simulatori di input) e **Pointers** (Puntatori), oltre a una cartella C++ Classes (Classi C++) con codice aggiuntivo.  

> [!NOTE]
> Se non viene visualizzata la sezione **UXTools Content** (Contenuto UXTools) in **Content Browser** (Browser contenuto), fai clic su **View Options > Show Plugin Content** (Opzioni visualizzazione > Mostra contenuto plug-in). 

![Mostra contenuto plug-in](images/unreal-uxt/4-showplugincontent.PNG)

Una volta installato il plug-in, è possibile iniziare a usare gli strumenti che include, partendo dagli attori di interazione manuale.

## <a name="spawning-hand-interaction-actors"></a>Generazione di attori di interazione manuale
L'interazione manuale con gli elementi UX avviene con gli attori di interazione manuale, che creano e guidano i puntatori e gli oggetti visivi per le interazioni da vicino e da lontano.
- Le *interazioni da vicino* avvengono pizzicando gli elementi tra l'indice e il pollice oppure colpendoli con la punta del dito. 
- Le *interazioni da lontano* avvengono puntando un raggio dalla mano virtuale su un elemento e premendo indice e pollice insieme.

In questo caso, l'aggiunta di un attore di interazione manuale a **MRPawn** consentirà di:
- Aggiungere un cursore sulla punta degli indici del pedone.
- Specificare eventi di input della mano articolata che possono essere manipolati tramite il pedone.
- Prevedere eventi di input di interazione da lontano tramite raggi che si estendono dai palmi delle mani virtuali.

Per comprendere appieno questi concetti, è consigliabile leggere la [documentazione](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.9.x/Docs/HandInteraction.md) relativa alle interazioni manuali prima di proseguire. 

Quando sei pronto, apri il progetto **MRPawn** e passa a **Event Graph** (Grafico eventi). 

1. Trascina e rilascia il segnaposto di esecuzione da **Event BeginPlay** (Evento BeginPlay) per inserire un nuovo nodo. 
    * Seleziona **Spawn Actor from Class** (Genera attore da classe), fai clic sull'elenco a discesa accanto al segnaposto **Class** (Classe) e cerca **Uxt Hand Interaction Actor** (Attore di interazione manuale Uxt).  

2. Generare un secondo **Uxt Hand Interaction Actor** (Attore di interazione manuale Uxt), questa volta impostando **Hand** (Mano) su **Right** (Destra). All'avvio dell'evento, verrà generato un attore di interazione manuale Uxt su ogni mano. 

La finestra **Event Graph** (Grafico eventi) dovrebbe risultare analoga alla seguente:

![Generare attori di interazione manuale Uxt](images/unreal-uxt/4-spawnactor.PNG)

Entrambi gli attori di interazione manuale Uxt devono avere proprietari e posizioni di trasformazione iniziale. La trasformazione iniziale non è rilevante perché gli attori di interazione manuale passano alle mani virtuali non appena sono visibili (questo comportamento è incluso nel plug-in UX Tools). La funzione `SpawnActor`, tuttavia, richiede un input di trasformazione per evitare un errore del compilatore, quindi useremo i valori predefiniti. 

1. Trascina e rilascia il segnaposto fuori da uno dei segnaposto **Spawn Transform** (Genera trasformazione) per inserire un nuovo nodo. 
    * Cerca il nodo **Make Transform** (Crea trasformazione) e quindi trascina **Return Value** (Valore restituito) su **Spawn Transform** (Genera trasformazione) dell'altra mano, in modo che entrambi i nodi **SpawnActor** (Genera attore) siano connessi. 

2.  Fai clic sulla **freccia in giù** nella parte inferiore di entrambi i nodi **SpawnActor** (Genera attore) per visualizzare il segnaposto **Owner** (Proprietario).    
    * Trascina il segnaposto fuori da uno dei segnaposto **Owner** (Proprietario) e rilascialo per inserire un nuovo nodo. 
    * Cerca **self** e seleziona la variabile **Get a reference to self** (Ottieni riferimento a Self), quindi crea un collegamento tra il nodo di riferimento dell'oggetto **Self** e il segnaposto **Owner** (Proprietario) dell'altro attore di interazione manuale. 
3. Infine, selezionare la casella **Show Near Cursor on Grab Targets** (Mostra cursore di prossimità sui target di cattura) per entrambi gli attori di interazione manuale. In questo modo, verrà visualizzato un cursore sui target di cattura quando il dito indice si avvicina e risulterà più facile vedere la posizione del dito rispetto al target.
    * **Compila** , **Salva** e torna alla finestra principale. 

Assicurati che le connessioni corrispondano allo screenshot seguente, ma trascina liberamente i nodi per rendere più leggibile il progetto

![Configurazione completa dell'attore di interazione manuale Uxt](images/unreal-uxt/4-fingerptrs.PNG) 

Per altre informazioni sull'attore di interazione manuale specificato nel plug-in UX Tools di MRTK, consulta la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html).

Ora le mani virtuali nel progetto sono in grado di selezionare gli oggetti, ma non possono ancora manipolarli. L'ultima attività prima di testare l'app consiste nell'aggiungere i componenti del manipolatore agli attori nella scena.

## <a name="attaching-manipulators"></a>Collegamento di manipolatori

Un manipolatore è un componente che risponde agli input della mano articolata e può essere afferrato, ruotato o spostato. Quando si applica la trasformazione del manipolatore a quella degli attori, gli attori possono essere manipolati direttamente. 

1. Apri il progetto **Board** (Tavola), fai clic su **Add Component** (Aggiungi componente) e cerca **Uxt Generic Manipulator** (Manipolatore generico Uxt) nel pannello **Components** (Componenti).

![Aggiungere un manipolatore generico](images/unreal-uxt/4-addmanip.PNG)

2. Espandi la sezione **Generic Manipulator** (Manipolatore generico) nel panello **Details** (Dettagli). Da qui puoi impostare la manipolazione a una mano o a due mani, la modalità di rotazione e i movimenti uniformi. Seleziona la modalità desiderata e quindi **Compile** (Compila) e **Save** (Salva) per salvare la tavola. 

![Impostare la modalità](images/unreal-uxt/4-setrotmode.PNG)

3. Ripeti i passaggi precedenti per l'attore **WhiteKing** (Re bianco).

Per altre informazioni sui componenti del manipolatore disponibili nel plug-in UX Tools di MRTK, consulta la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Test della scena
Ottimo! A questo punto puoi testare l'app con le nuove mani virtuali e l'input utente. Premi **Play** (Gioca) nella finestra principale e vedrai due mani con mesh fornite dal plug-in UX Tools di MRTK, con i raggi della mano che si estendono dal palmo. Puoi controllare le mani e le relative interazioni nel modo seguente:
- Tieni premuto **ALT di sinistra** per controllare la **mano sinistra** e **MAIUSC di sinistra** per controllare la **mano destra** . 
- Sposta il mouse per muovere la mano e scorri con la **rotellina del mouse** per spostare la mano **avanti** o **indietro** . 
- Fai clic con il pulsante sinistro del mouse per **pizzicare** e con il pulsante centrale del mouse per **picchiettare con le dita** . 

> [!NOTE]
> La simulazione di input potrebbe non funzionare se sono collegati più visori VR al computer. In caso di problemi, provare a scollegare gli altri visori VR. 

![Mani simulate nel riquadro di visualizzazione](images/unreal-uxt/4-handsim.PNG)

Prova a usare le mani simulate per sollevare, spostare e appoggiare il re bianco e manipolare la scacchiera. Prova a usare l'interazione da vicino e da lontano. Tieni presente che, quando le mani si avvicinano abbastanza da poter afferrare direttamente la scacchiera e il re, il raggio della mano scompare e viene sostituito con un cursore a forma di dito sulla punta dell'indice. 

Per altre informazioni sulla funzionalità delle mani simulate fornita dal plug-in UX Tools di MRTK, consulta la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/InputSimulation.html).

Ora che le mani virtuali possono interagire con gli oggetti, puoi passare all'esercitazione successiva e aggiungere interfacce utente ed eventi.

[Sezione successiva: 5. Aggiunta di un pulsante e reimpostazione delle posizioni della parte](unreal-uxt-ch5.md)
