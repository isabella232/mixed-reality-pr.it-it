---
title: Creazione della prima applicazione HoloLens Unreal
description: Informazioni su come configurare correttamente un progetto Unreal con oggetti scena e interazioni di input per HoloLens sviluppo di realtà mista.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, editor Unreal, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 07ec2760d691938015619d097d214d205cdbab78f250ff9dd8a793dd27f10c4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209607"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Creazione della prima applicazione HoloLens Unreal

Questa guida illustra come eseguire la prima app di realtà mista HoloLens in Unreal Engine. Nella tradizione di "Hello World", si creerà una semplice app che visualizza un cubo sullo schermo. Per renderlo più utile, si creerà anche il primo movimento per ruotare il cubo e uscire dall'applicazione. 

## <a name="objectives"></a>Obiettivi

* Avviare un HoloLens Project
* Abilitare i plug-in corretti
* Creare un asset di dati ARSessionConfig
* Configurare gli input dei movimenti
* Creare un livello di base
* Implementare un movimento di avvicinamento delle dita

## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto

Prima di tutto, è necessario un progetto su cui lavorare. Se si sviluppa in Unreal per la prima volta, è necessario [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic.

1. Avvia Unreal Engine
2. In **Nuove categorie Project selezionare** **Giochi e** fare clic su **Avanti:**

![Finestra Progetti recenti aperta con Giochi evidenziato](images/unreal-quickstart-img-01.png)

3. Selezionare il **modello Vuoto** e fare clic su **Avanti:**

![Finestra del browser del progetto Unreal con il modello Vuoto evidenziato](images/unreal-quickstart-img-02.png)

4. Nel Project Impostazioni impostare **C++, Scalable 3D or 2D, Mobile/Tablet** e **No Starter Content**(Nessun contenuto iniziale), quindi scegliere un percorso di salvataggio e fare clic su **Crea** Project

> [!NOTE] 
> Si sta usando un progetto C++ anziché un progetto Blueprint per poter usare il plug-in OpenXR in un secondo momento. Questa guida introduttiva usa il plug-in OpenXR predefinito fornito con Unreal Engine. È tuttavia consigliabile scaricare e usare il plug-in Microsoft OpenXR ufficiale. Ciò richiede che il progetto sia un progetto C++.

![Project impostazioni predefinite con opzioni di progetto, prestazioni, piattaforma di destinazione e contenuto iniziale evidenziate](images/unreal-quickstart-img-03.png)

Il nuovo progetto dovrebbe aprirsi automaticamente nell'editor Unreal, il che significa che si è pronti per la sezione successiva.

## <a name="enabling-required-plugins"></a>Abilitazione dei plug-in necessari

Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.

1. Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.
* Scorrere verso il basso **fino HoloLens** e selezionare **Abilitato**

![Finestra Plug-in con la sezione realtà aumentata aperta e HoloLens evidenziata](images/unreal-quickstart-img-04.png)

2. Digitare **OpenXR** nella casella di ricerca in alto a destra e abilitare i plug-in **OpenXR** e **OpenXRMsftHandInteraction:**

![Finestra Plug-in con OpenXR abilitato](images/unreal-quickstart-img-05.jpg)

![Finestra Plug-in con Open XR Msft Hand Interaction abilitato](images/unreal-quickstart-img-06.jpg)

3. Riavviare l'editor

> [!NOTE]
> Questa esercitazione usa OpenXR, ma i due plug-in installati in precedenza non forniscono attualmente il set completo di funzionalità per HoloLens sviluppo. Il plug-in HandInteraction sarà sufficiente per il movimento "Pinch" che userai più avanti, ma se vuoi andare oltre le nozioni di base dovrai scaricare il [plug-in OpenXR.](https://github.com/microsoft/Microsoft-OpenXR-Unreal)

Con i plug-in abilitati, è possibile concentrarsi sul riempimento con contenuto.

## <a name="creating-a-level"></a>Creazione di un livello

L'attività successiva consiste nel creare una configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.

1. Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto). La scena predefinita nel viewport dovrebbe ora essere vuota
2. Nella scheda **Modalità** selezionare **Basic e** trascinare **PlayerStart** nella scena
* Nella scheda **Dettagli**  impostare Posizione su **X = 0, Y = 0** e **Z = 0** per posizionare l'utente al centro della scena all'avvio dell'app

![Scena dell'editor unreal con posizione e inizio del giocatore aggiunti](images/unreal-quickstart-img-07.png)

3. Dalla scheda **Basic** trascinare un **cubo** nella scena
* Impostare Posizione del  cubo su **X = 50, Y = 0** e **Z = 0** per posizionare il cubo a 50 cm di distanza dal giocatore all'inizio
* Modificare la scala **del** cubo in **X = 0,2, Y = 0,2** e **Z = 0,2** 

Il cubo non sarà visibile finché non viene aggiunta una luce alla scena, che è l'ultima attività da eseguire prima del test.

4. Nel pannello **Modalità** passare alla scheda **Luci** e trascinare una **luce direzionale** nella scena
* Posizionare la luce sopra **PlayerStart** in modo da poterla visualizzare

![Scena dell'editor unreal con cubo e luce direzionale aggiunti](images/unreal-quickstart-img-08.png)

5. Passare a **File > Salva corrente,** assegnare al livello il nome **Main** e selezionare **Salva**

Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione. Quando avrai terminato di ammirare il tuo lavoro, premi ESC per arrestare l'applicazione.

![Scena in modalità di riproduzione con il cubo al centro dello schermo](images/unreal-quickstart-img-09.png)

Ora che la scena è stata impostata, è possibile prepararla per alcune interazioni di base in AR. Prima di tutto, è necessario creare una sessione ar e aggiungere progetti per abilitare l'interazione manuale.

## <a name="adding-a-session-asset"></a>Aggiunta di un asset di sessione

Le sessioni AR in Unreal non funzionano da sole. Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:

1. In **Content Browser** selezionare **Add New > Miscellaneous > Data Asset** e assicurarsi di essere a livello della cartella Content radice
2. Selezionare **ARSessionConfig,** fare clic **su Seleziona** e assegnare all'asset il nome **ARSessionConfig**:

![Finestra pick data asset class aperta con l'asset di configurazione della sessione AR evidenziato](images/unreal-quickstart-img-10.png)

2. Fare doppio clic **su ARSessionConfig** per aprirlo, **salvare** con tutte le impostazioni predefinite e tornare alla finestra Principale:

![Finestra dei dettagli dell'asset di configurazione della sessione AR](images/unreal-quickstart-img-11.png)

Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina. In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello. La connessione dell'asset ARSessionConfig in Level Blueprint (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.

3. Dalla barra degli strumenti dell'editor selezionare **Progetti > Progetto open level**:

![Menu Progetto aperto con l'opzione progetto di livello aperto evidenziata](images/unreal-quickstart-img-12.png)

4. Trascinare il nodo di esecuzione (icona a forma di freccia rivolta a sinistra) da **Event BeginPlay** e rilasciare
* Cercare il nodo **Avvia sessione AR e** premere INVIO
* Fare clic **sull'elenco a** discesa Seleziona asset in **Configurazione sessione** e scegliere l'asset **ARSessionConfig**

![Grafico del progetto con la riproduzione di inizio evento connessa alla funzione di avvio della sessione ar](images/unreal-quickstart-img-13.png)

5. Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**. 
* Trascinare il pin di esecuzione e rilasciare, quindi cercare un **nodo Arresta sessione AR** e premere INVIO 
* Fare **clic su** Compila, quindi su **Salva** e tornare alla finestra Principale

> [!IMPORTANT]
> Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.

![Nodo di riproduzione finale dell'evento collegato alla funzione di arresto della sessione ar](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Configurazione degli input

1. Selezionare **Modifica > Project Impostazioni** e passare all'input > **motore**
2. Selezionare **+** l'icona accanto **a Mapping azioni e** creare azioni **RightPinch** e **LeftPinch:**

![Associazione delle impostazioni di input con i mapping delle azioni di avvicinamento delle dita a destra e a sinistra evidenziati](images/unreal-quickstart-img-15.jpg)

3. Eseguire il **mapping delle azioni RightPinch** **e LeftPinch** di alle rispettive azioni di interazione manuale **di OpenXR Msft:**

![Mapping delle azioni con le opzioni di interazione manuale Open XR Msft evidenziate](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Configurazione dei movimenti

Dopo aver creato gli input, è possibile ottenere la parte interessante: Aggiunta di movimenti. Ruotare il cubo a destra avvicinando le dita e chiudendo l'applicazione a sinistra.

1. Aprire il **progetto Level e** aggiungere **inputAction RightPinch** e **InputAction LeftPinch**
* Connessione'evento di avvicinamento delle dita a destra a **un oggetto AddActorLocalRotation** con **cube** come destinazione e **Rotazione differenziale** impostata su **X = 0, Y = 0** e **Z = 20.** Il cubo ruota ora di 20 gradi ogni volta che si avvicina un dito
* Connessione'evento di avvicinamento delle dita a sinistra **in Esci da gioco**

![Livello bluprint aperto con azioni di input per gli eventi di avvicinamento delle dita a destra e a sinistra](images/unreal-quickstart-img-17.jpg)

2. Nelle impostazioni di trasformazione **del** cubo impostare **Mobility** su **Movable** in modo che possa essere spostato dinamicamente:

![Impostazioni tranform con la proprietà mobility evidenziata](images/unreal-quickstart-img-18.jpg)

A questo punto, si è pronti per distribuire e testare l'applicazione.