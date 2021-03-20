---
title: Creazione della prima applicazione HoloLens Unreal
description: Informazioni su come configurare correttamente un progetto irreale con gli oggetti scena e le interazioni di input per lo sviluppo di realtà mista HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99421430"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Creazione della prima applicazione HoloLens Unreal

Questa guida illustra come ottenere la prima app per la realtà mista in esecuzione in HoloLens in Unreal Engine. Nella tradizione di "Hello World", verrà creata una semplice app che visualizza un cubo sullo schermo. Per renderlo più utile, verrà creato anche il primo gesto per ruotare il cubo e uscire dall'applicazione. 

## <a name="objectives"></a>Obiettivi

* Avviare un progetto HoloLens
* Abilitare i plug-in corretti
* Creare un asset di dati ARSessionConfig
* Configurare gli input del movimento
* Creazione di un livello di base
* Implementare un movimento di pizzico

## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto

Prima di tutto, è necessario un progetto su cui lavorare. Se si sviluppa in Unreal per la prima volta, è necessario [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic.

1. Avvia Unreal Engine
2. Nelle **categorie nuovo progetto** selezionare **giochi** e fare clic su **Avanti**:

![Finestra progetti recenti aperta con giochi evidenziati](images/unreal-quickstart-img-01.png)

3. Selezionare il modello **vuoto** e fare clic su **Avanti**:

![Finestra del browser del progetto non reale con modello vuoto evidenziato](images/unreal-quickstart-img-02.png)

4. Nelle **impostazioni del progetto** impostare **C++, Scalable 3D o 2D, mobile/tablet** e **nessun contenuto iniziale**, quindi scegliere un percorso di salvataggio e fare clic su **Crea progetto**

> [!NOTE] 
> Per essere pronti a usare il plug-in OpenXR in un secondo momento, si usa un progetto C++ anziché un progetto di progetto. Questa Guida introduttiva usa il plug-in OpenXR predefinito incluso in Unreal Engine. È tuttavia consigliabile scaricare e usare il plug-in Microsoft OpenXR ufficiale. Per questo è necessario che il progetto sia un progetto C++.

![Finestra Impostazioni progetto con opzioni di progetto, prestazioni, piattaforma di destinazione e contenuto iniziale evidenziato](images/unreal-quickstart-img-03.png)

Il nuovo progetto dovrebbe aprirsi automaticamente nell'editor Unreal, il che significa che si è pronti per la sezione successiva.

## <a name="enabling-required-plugins"></a>Abilitazione dei plug-in necessari

Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.

1. Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.
* Scorrere fino a **HoloLens** e selezionare **abilitato**

![Finestra plug-in con la sezione della realtà aumentata aperta e HoloLens evidenziata](images/unreal-quickstart-img-04.png)

2. Digitare **OpenXR** nella casella di ricerca in alto a destra e abilitare i plug-in **OpenXR** e **OpenXRMsftHandInteraction** :

![Finestra plug-in con OpenXR abilitato](images/unreal-quickstart-img-05.jpg)

![Finestra plug-in con l'interazione della mano Open XR MSFT abilitata](images/unreal-quickstart-img-06.jpg)

3. Riavviare l'editor

> [!NOTE]
> Questa esercitazione USA OpenXR, ma i due plug-in installati in precedenza non forniscono attualmente il set completo di funzionalità per lo sviluppo di HoloLens. Il plug-in HandInteraction sarà sufficiente per il gesto "pizzico" che verrà usato in un secondo momento, ma se si vogliono superare le nozioni di base, è necessario [scaricare il plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal)-in OpenXR.

Con i plug-in abilitati, è possibile concentrarsi sulla compilazione con contenuto.

## <a name="creating-a-level"></a>Creazione di un livello

L'attività successiva consiste nel creare una configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.

1. Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto). La scena predefinita nel viewport ora è vuota
2. Dalla scheda **modalità** selezionare **Basic** e trascinare **PlayerStart** nella scena
* Nella scheda **Dettagli** impostare **percorso** su **X = 0, Y = 0** e **Z = 0** per inserire l'utente al centro della scena all'avvio dell'app

![Scena dell'editor non reale con la posizione e l'avvio del giocatore aggiunti](images/unreal-quickstart-img-07.png)

3. Dalla scheda di **base** trascinare un **cubo** nella scena
* Imposta la **posizione** del cubo su **X = 50, Y = 0** e **Z = 0** per posizionare il cubo 50 cm dal lettore all'inizio
* Modificare la **scala** del cubo in **X = 0,2, Y = 0,2** e **Z = 0,2** 

Il cubo non sarà visibile finché non viene aggiunta una luce alla scena, che è l'ultima attività da eseguire prima del test.

4. Nel pannello **modalità** passare alla scheda **luci** e trascinare una **luce direzionale** nella scena
* Posizionare la luce sopra **PlayerStart** in modo che sia possibile visualizzarla

![Scena dell'editor non reale con aggiunta di cubo e luce direzionale](images/unreal-quickstart-img-08.png)

5. Passare a **File > Salva corrente**, assegnare un nome al livello **principale** e selezionare **Salva** .

Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione. Quando avrai terminato di ammirare il tuo lavoro, premi ESC per arrestare l'applicazione.

![Scena in modalità di riproduzione con il cubo al centro della schermata](images/unreal-quickstart-img-09.png)

Ora che la scena è configurata, consente di prepararsi per alcune interazioni di base in AR. Prima di tutto, è necessario creare una sessione AR ed è possibile aggiungere progetti per abilitare l'interazione manuale.

## <a name="adding-a-session-asset"></a>Aggiunta di un asset della sessione

Le sessioni AR in Unreal non funzionano da sole. Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:

1. Nel **browser del contenuto** selezionare **Aggiungi nuovo > varie > asset di dati** e verificare di essere al livello della cartella del contenuto radice
2. Selezionare **ARSessionConfig**, fare clic su **Seleziona** e denominare l'asset **ARSessionConfig**:

![Selezionare la finestra classe di asset di dati aperta con l'asset di configurazione della sessione AR evidenziato](images/unreal-quickstart-img-10.png)

2. Fare doppio clic su **ARSessionConfig** per aprirlo, **salvare** con tutte le impostazioni predefinite e tornare alla finestra principale:

![Finestra Dettagli asset di configurazione della sessione AR](images/unreal-quickstart-img-11.png)

Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina. In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello. La connessione dell'asset ARSessionConfig in Level Blueprint (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.

3. Dalla barra degli strumenti dell'editor selezionare Blueprints **> progetto Open level**:

![Menu progetto aperto con l'opzione progetto Open level evidenziato](images/unreal-quickstart-img-12.png)

4. Trascinare il nodo di esecuzione (icona a sinistra) dell' **evento BeginPlay** e Release
* Cercare il **nodo di avvio della sessione AR** e premere INVIO
* Fare clic sull'elenco a discesa **Seleziona asset** in **configurazione della sessione** e scegliere l'asset **ARSessionConfig**

![Grafico del progetto con inizio riproduzione evento connesso alla funzione Avvia sessione AR](images/unreal-quickstart-img-13.png)

5. Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**. 
* Trascinare il pin di esecuzione e il rilascio, quindi cercare un nodo di **sessione stop AR** e premere INVIO 
* Premere **Compila**, quindi **salvare** e tornare alla finestra principale

> [!IMPORTANT]
> Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.

![Nodo evento finale associato alla funzione di sessione stop AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Impostazione degli input

1. Selezionare **Modifica impostazioni progetto >** e passare al **motore > input**
2. Selezionare l' **+** icona accanto a **mapping azioni** e creare azioni **RightPinch** e **LeftPinch** :

![Associazione delle impostazioni di input con i mapping delle azioni di tocco a destra e a sinistra evidenziati](images/unreal-quickstart-img-15.jpg)

3. Eseguire il mapping delle azioni **RightPinch** e **LeftPinch** alla rispettiva azione di **interazione della mano OpenXR MSFT** :

![Mapping delle azioni con opzioni di interazione della mano Open XR MSFT evidenziate](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Impostazione di movimenti

Ora che sono stati impostati gli input, è possibile arrivare alla parte interessante: aggiungere movimenti. Consente di ruotare il cubo a destra e uscire dall'applicazione in un pizzico di sinistra.

1. Aprire il **progetto Level** e aggiungere un **InputAction RightPinch** e **InputAction LeftPinch**
* Connettere l'evento Pinch a destra a un **AddActorLocalRotation** con il **cubo** come destinazione e **rotazione delta** impostati su **X = 0, Y = 0** e **Z = 20**. Il cubo verrà ora ruotato di 20 gradi ogni volta che si pizzica
* Connetti l'evento di tocco a sinistra per **chiudere il gioco**

![Livello Bluprint aperto con azioni di input per gli eventi di pizzico a destra e a sinistra](images/unreal-quickstart-img-17.jpg)

2. Nelle impostazioni di **trasformazione** del cubo impostare **mobilità** su **mobile** in modo che possa essere spostata dinamicamente:

![Impostazioni trasformare con proprietà Mobility evidenziate](images/unreal-quickstart-img-18.jpg)

A questo punto, si è pronti per distribuire e testare l'applicazione.