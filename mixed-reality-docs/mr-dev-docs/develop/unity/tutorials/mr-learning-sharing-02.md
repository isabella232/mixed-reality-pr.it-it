---
title: Configurazione di Photon Unity Networking
description: In questo corso viene illustrato come implementare Photon Unity Network in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, PUN
ms.localizationpriority: high
ms.openlocfilehash: 28776e106b96d1265e435d60e7008b1d88c01060
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702505"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Configurazione di Photon Unity Networking

In questa esercitazione si preparerà l'ambiente per la creazione di un'esperienza condivisa tramite Photon Unity Networking (PUN). Si apprenderà come creare un'app PUN, importare asset di PUN nel progetto Unity e connettere il progetto Unity all'app PUN.

## <a name="objectives"></a>Obiettivi

* Imparare a creare un'app PUN
* Imparare a trovare e importare gli asset di PUN
* Imparare a connettere il progetto Unity all'app PUN

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

Seguire prima di tutto [l'inizializzazione](mr-learning-base-02.md)del progetto e [](mr-learning-base-02.md#adding-hand-interaction-to-an-object) la distribuzione della [](mr-learning-base-02.md#building-your-application-to-your-hololens-2) prima applicazione, esclusa l'aggiunta dell'interazione manuale a un oggetto e la compilazione dell'applicazione alle istruzioni del dispositivo, che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*
2. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform)
3. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Creazione della scena e configurazione di MRTK](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnare alla scena un nome appropriato, ad esempio *MultiUserCapabilities*

Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per:

1. Impostare **MRTK configuration profile** (Profilo di configurazione di MRTK) su **DefaultHoloLens2ConfigurationProfile**
1. Impostare le **opzioni di visualizzazione mesh di consapevolezza spaziale** su **Occlusion** (Occlusione).

## <a name="enabling-additional-capabilities"></a>Abilitazione delle funzionalità aggiuntive

Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):

![Impostazioni del lettore di Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

In **Publishing Settings** (Impostazioni di pubblicazione) scorrere verso il basso fino alla sezione **Capabilities** (Funzionalità) e verificare che siano abilitate le funzionalità **InternetClient**, **Microphone**, **SpatialPerception**, e **GazeInput**, abilitate al passaggio [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project) precedente.

Abilitare quindi le funzionalità aggiuntive seguenti:

* Funzionalità **InternetClientServer**
* Funzionalità **PrivateNetworkClientServer**

![Impostazione delle funzionalità di Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Aggiungere AzurespatialAnchors SDK V2.7.1 al progetto Unity. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)


Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:
 
* [MRTK. HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage)
* [MRTK. HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage)
* [MRTK. HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato di Unity, è possibile fare riferimento alle istruzioni sull'importazione degli [asset dell'esercitazione.](mr-learning-base-04.md#importing-the-tutorial-assets)

> [!NOTE]
> Dopo aver importato il pacchetto di asset dell'esercitazione MultiUserCapabilities, nella finestra della console verranno visualizzati alcuni errori [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) che indicano che manca il tipo o lo spazio dei nomi. Si tratta di un comportamento previsto, che verrà risolto nella prossima sezione quando verranno importati gli asset di PUN.

## <a name="importing-the-pun-assets"></a>Importazione degli asset di PUN

Nel menu di Unity selezionare **Window** > **Asset Store** (Finestra > Store degli asset) per aprire la finestra Asset Store (Store degli asset), cercare e selezionare **PUN 2 - FREE** (PUN 2 - GRATUITO) in Exit Games (Giochi in uscita) e fare clic sul pulsante **Download** (Scarica) per scaricare il pacchetto di asset nell'account Unity.

Al termine del download, fai clic sul pulsante **Import** (Importa) per aprire la finestra Import Unity Package (Importa pacchetto Unity):

![Unity Asset Store con PUN 2 - Free](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![Unity con la finestra per l'importazione di PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Dopo che Unity ha completato il processo di importazione, verrà visualizzata la finestra PUN Wizard (Creazione guidata PUN) con il menu PUN Setup (Configurazione PUN) caricato. Per il momento puoi ignorare o chiudere questa finestra:

![Unity con la finestra per la configurazione di PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>Creazione dell'applicazione PUN

In questa sezione si creerà un account Photon, se non esiste già, e una nuova app PUN.

Passa al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> di Photon ed esegui l'accesso se hai già un account che vuoi usare. In caso contrario, fai clic sul collegamento **Create One** (Creane uno) e segui le istruzioni per la registrazione di un nuovo account:

![Pagina di accesso di Photon](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

Una volta eseguito l'accesso, fai clic sul pulsante **Create a New App** (Crea una nuova app):

![Pagina di benvenuto del dashboard Photon](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

Nella pagina Create a New Application (Crea una nuova applicazione) immetti i valori seguenti:

* In Photon Type (Tipo Photon) selezionare PUN
* In Name (Nome) immetti un nome appropriato, ad esempio _MRTK Tutorials_
* In Description (Descrizione) immetti facoltativamente una descrizione appropriata
* In Url lascia il campo vuoto

Fare quindi clic sul pulsante **Create** (Crea) per creare la nuova app:

![Pagina per la creazione dell'applicazione Photon](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Al termine del processo di creazione, nel dashboard verrà visualizzata la nuova app PUN:

![Pagina dell'applicazione Photon](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Connessione del progetto Unity all'applicazione PUN

In questa sezione si connetterà il progetto Unity all'app PUN creata nella sezione precedente.

Nel dashboard di Photon fai clic sul campo **App ID** (ID app) per visualizzare l'ID dell'app e quindi copialo negli Appunti:

![Pagina dell'applicazione Photon con App Id selezionato](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

Nel menu di Unity seleziona **Window** (Finestra) > **Photon Unity Networking** > **PUN Wizard** (Creazione guidata PUN) per aprire la finestra PUN Wizard (Creazione guidata PUN), fai clic sul pulsante **Setup Project** (Configura progetto) per aprire il menu PUN Setup (Configurazione PUN) ed esegui la configurazione nel modo seguente:

* Nel campo **AppId or Email** (ID app o e-mail) incolla l'ID dell'app PUN copiato nel passaggio precedente

Fai quindi clic sul pulsante **Setup Project** (Configura progetto) per applicare l'ID dell'app:

![Finestra PUN Setup di Unity con AppId compilato](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Dopo che Unity ha terminato il processo di configurazione di PUN, nel menu PUN Setup (Configurazione PUN) verrà visualizzato il messaggio **Done!** (Fatto) e nella finestra Project (Progetto) verrà selezionato automaticamente l'asset **PhotonServerSettings**, in modo che le relative proprietà siano visualizzate nella finestra Inspector (Controllo):

![Finestra PUN Setup di Unity con Setup Project applicato](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>Lezione completata

È stata creata un'app PUN ed è stata connessa al progetto Unity. Il passaggio successivo consiste nel consentire connessioni con altri utenti, in modo che ogni utente possa visualizzare il lavoro svolto dagli altri.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Connessione di più utenti](mr-learning-sharing-03.md)