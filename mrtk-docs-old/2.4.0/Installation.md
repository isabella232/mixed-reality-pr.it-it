---
title: Guida all'installazione
description: Guida per l'installazione di MRTK-Unity in un nuovo progetto.
author: hferrone
ms.author: v-hferrone
ms.date: 09/8/2020
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 775001fe6a73274859230e774a913c0ad71727c1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692968"
---
# <a name="installation-guide"></a>Guida all'installazione

> [!CAUTION]
> Se non si ha familiarità con MRTK o lo sviluppo di realtà mista in Unity, è consigliabile iniziare dall'inizio del [percorso di sviluppo di Unity](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2). Il percorso di sviluppo di Unity è il **punto di partenza consigliato per MRTK**, appositamente creato per illustrare l'installazione, i concetti di base e l'uso di MRTK in Unity.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare a usare il Toolkit di realtà mista, è necessario:

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
* [Unity 2018.4. x, Unity 2019](https://unity3d.com/get-unity/download/archive)

  MRTK supporta entrambi i backend di script IL2CPP e .NET in Unity 2018

* [Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

  Questa operazione è necessaria se si compila un'app UWP per WMR, HoloLens 1 o HoloLens 2. Questa operazione non è necessaria quando si compila per OpenVR.

## <a name="add-mrtk-to-your-unity-project"></a>Aggiungere MRTK al progetto Unity

### <a name="required"></a>Necessario

1. [Ottenere i pacchetti più recenti di MRTK Unity](#get-the-latest-mrtk-unity-packages)
1. [Importare i pacchetti MRTK nel progetto Unity](#import-mrtk-packages-into-your-unity-project)
1. [Passare il progetto Unity alla piattaforma di destinazione](#switch-your-unity-project-to-the-target-platform)
1. [Aggiungere MRTK a una nuova scena o a un nuovo progetto](#add-mrtk-to-a-new-scene-or-new-project)

### <a name="optional"></a>Facoltativo

* [Esercitazioni introduttive](#getting-started-tutorials)
* [Guida introduttiva di XR SDK (unity 2019,3 o versione successiva)](configuration/GettingStartedWithMRTKAndXRSDK.md).
* [Informazioni sui componenti di base di MRTK](#learn-about-the-core-building-blocks-of-mrtk)
* [Eseguire la scena HandInteractionExamples nell'editor di Unity](#run-the-handinteractionexamples-scene-in-the-unity-editor)

### <a name="get-the-latest-mrtk-unity-packages"></a>Ottenere i pacchetti più recenti di MRTK Unity

1. Passare alla <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">pagina della versione MRTK</a>.
1. In asset scaricare:
    * **Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**
    * (**_Facoltativo_**) Microsoft. MixedRealityToolkit. Unity. Extensions. file unitypackage Tools
    * (**_Facoltativo_**) Microsoft. MixedRealityToolkit. Unity. examples. file unitypackage Tools
    * (**_Necessario per gli aggiornamenti da versione a versione, in caso contrario facoltativo_**) Microsoft. MixedRealityToolkit. Unity. Tools. file unitypackage Tools

Per informazioni sui contenuti del pacchetto, vedere [contenuti del pacchetto MRTK](reference-docs/MRTK_PackageContents.md).

Il Toolkit per la realtà mista è disponibile anche per il download in NuGet.org; per informazioni dettagliate, vedere [pacchetti NuGet di MRTK](reference-docs/MRTKNuGetPackage.md).

### <a name="import-mrtk-packages-into-your-unity-project"></a>Importare i pacchetti MRTK nel progetto Unity

1. Creare un nuovo progetto Unity o aprire un progetto esistente. Quando si crea un progetto, assicurarsi di selezionare "3D" come tipo di modello.
1. Importare **Microsoft. MixedRealityToolkit. Unity. Foundation. file unitypackage Tools** scaricati passando a "Asset-> Import package-> Custom Package", selezionare il file con estensione file unitypackage Tools, verificare che tutti gli elementi da importare siano selezionati e quindi selezionare "Import" (importa).
1. (**_Facoltativo_**) Importare **Microsoft. MixedRealityToolkit. Unity. Extensions. file unitypackage Tools** seguendo la stessa procedura del pacchetto di base. Il pacchetto Extensions fornisce un set di componenti facoltativi utili per MRTK.
1. (**_Facoltativo_**) Importare **Microsoft. MixedRealityToolkit. Unity. examples. file unitypackage Tools** seguendo la stessa procedura descritta in precedenza. Il pacchetto degli esempi è facoltativo e contiene utili scenari di dimostrazione per le funzionalità MRTK correnti. **Si noti che il pacchetto di esempi richiede il pacchetto di estensioni.**
1. (**_Necessario per gli aggiornamenti da versione a versione, in caso contrario facoltativo_**) Importare **Microsoft. MixedRealityToolkit. Unity. Tools. file unitypackage Tools** seguendo la stessa procedura del pacchetto di base. Il pacchetto degli strumenti è facoltativo e contiene strumenti utili, ad esempio ExtensionServiceCreator, che migliorano l'esperienza MRTK Developer.

> [!Note]
> Per lo sviluppo di Android e iOS sono necessarie installazioni aggiuntive per i pacchetti. Per ulteriori informazioni, vedere [come configurare MRTK per iOS e Android](CrossPlatform/UsingARFoundation.md).
Dopo aver importato il pacchetto Foundation, è possibile che venga visualizzato un prompt simile al seguente:

![UnitySetupPrompt](features/Images/MRTK_UnitySetupPrompt.png)

MRTK sta tentando di configurare il progetto per la compilazione di soluzioni di realtà mista effettuando le operazioni seguenti:

* Abilitare le impostazioni di XR per la piattaforma corrente (abilitando la casella di controllo XR).
* Forza la serializzazione del testo o i metadati visibili (scelta consigliata per i progetti Unity che usano il controllo del codice sorgente

L'accettazione di queste opzioni è completamente facoltativa, ma consigliata.

Per alcuni prefissi e risorse è necessario TextMesh Pro, vale a dire che è necessario che sia installato il pacchetto TextMesh Pro e gli asset nel progetto (Window-> TextMeshPro-> importare le risorse essenziali di TMP). **Dopo aver importato le risorse di tmp Essentials, è necessario riavviare Unity per visualizzare le modifiche**.

### <a name="switch-your-unity-project-to-the-target-platform"></a>Passare il progetto Unity alla piattaforma di destinazione

Con i pacchetti importati, il passaggio successivo consiste nel selezionare la piattaforma corretta per l'applicazione.

Per creare un' **applicazione HoloLens**, passare al piattaforma UWP (Universal Windows Platform):

1. Apri menu: file > impostazioni di compilazione
1. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma**
1. Fare clic sul pulsante **Switch Platform**

![Switch Platform](features/Images/getting_started/SwitchPlatform.png)

>[!NOTE]
> Il Toolkit di realtà mista chiederà di applicare le modifiche consigliate al progetto quando si seleziona la piattaforma. Ogni volta che la piattaforma viene cambiata, le impostazioni appropriate verranno controllate e richieste, se necessario.

### <a name="add-mrtk-to-a-new-scene-or-new-project"></a>Aggiungere MRTK a una nuova scena o a un nuovo progetto

1. Creare un nuovo progetto Unity o avviare una nuova scena nel progetto corrente.

1. Assicurarsi di aver importato i pacchetti MRTK (si consiglia di basare ed esempi, sebbene gli esempi non siano necessari) attenendosi [alla procedura descritta sopra](#import-mrtk-packages-into-your-unity-project).

1. Dalla barra dei menu selezionare Mixed Reality Toolkit-> Aggiungi a scena e configura

    ![Configura in scena](features/Images/MRTK_ConfigureScene.png)

    Il controllo visualizzerà ora il profilo di configurazione MRTK attualmente attivo e l'elenco a discesa di selezione del profilo, in cui il profilo predefinito è già preselezionato.
    I profili configurano il comportamento dei componenti di base di MRTK e sono descritti in modo più dettagliato nell'articolo sui [profili](features/Profiles/Profiles.md) .

    > [!NOTE]
    >
    > * Se si usa l'SDK XR di Unity in Unity 2019,3 o versione successiva, è consigliabile scegliere "DefaultXRSDKConfigurationProfile". Questo profilo è configurato con i sistemi e i provider di MRTK XR SDK, ove necessario.  
    > * Se si sta iniziando a usare HoloLens o HoloLens 2, è consigliabile scegliere invece "DefaultHoloLens1ConfigurationProfile" o DefaultHoloLens2ConfigurationProfile ".  
    > * Per ulteriori informazioni sulle differenze tra DefaultMixedRealityToolkitConfigurationProfile e DefaultHoloLens2ConfigurationProfile, vedere i [profili](Profiles/Profiles.md#hololens-2-profile) .

    Nella gerarchia della scena verrà visualizzato quanto segue:

    ![Impostazione della scena MRTK](features/Images/MRTK_SceneSetup.png)

    Che contiene gli elementi seguenti:

    * **Toolkit di realtà mista** : il Toolkit stesso, che fornisce il punto di ingresso di configurazione centrale per l'intero Framework.
    * **MixedRealityPlayspace** : l'oggetto padre per la cuffia, che garantisce che i controller e gli auricolari e gli altri sistemi necessari siano gestiti correttamente nella scena.
    * La fotocamera principale viene spostata come elemento figlio in playspace, che consente al playspace di gestire la fotocamera insieme agli SDK

    >[!NOTE]
    > Quando si lavora nella scena, non **spostare la fotocamera principale** (o il **MixedRealityPlayspace**) dall'origine della scena (0, 0, 0).  Questa operazione è controllata da MRTK e da Active SDK. Se è necessario spostare il punto iniziale dei giocatori, **spostare il contenuto della scena e non la fotocamera**.

1. Premere Play e testare la simulazione della mano premendo la **barra spaziatrice**.

A questo punto è possibile eseguire la compilazione e la distribuzione nel dispositivo. Seguire le istruzioni riportate in [compilare e distribuire MRTK](updates-deployment/BuildAndDeploy.md).

### <a name="getting-started-tutorials"></a>Esercitazioni introduttive

Se non si ha familiarità con MRTK o per lo sviluppo di MR, è consigliabile consultare le [esercitazioni introduttive](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) che usano MRTK V2.

### <a name="learn-about-the-core-building-blocks-of-mrtk"></a>Informazioni sui componenti di base di MRTK

Vedere [MRTK 101: come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) per informazioni sui blocchi predefiniti di base.

### <a name="run-the-handinteractionexamples-scene-in-the-unity-editor"></a>Eseguire la scena HandInteractionExamples nell'editor di Unity

L'articolo relativo alla [scena degli esempi di interazione della mano](features/README_HandInteractionExamples.md) è un ottimo punto per ottenere altre informazioni sui controlli e sulle interazioni di UX in MRTK.

[![Scena HandInteractionExample](features/Images/MRTK_Examples.png)](README_HandInteractionExamples.md)

Per provare la scena interazione della mano, seguire questa procedura.

1. Aprire la scena **HandInteractionExamples** sotto `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`

1. Potrebbe essere richiesta l'importazione di "TMP Essentials".

    ![TMP Essentials](features/Images/getting_started/MRTK_GettingStarted_TMPro.png)

    Se viene richiesto, selezionare il pulsante "Importa TMP Essentials". "TMP Essentials" si riferisce al plug-in text mesh Pro, che alcuni esempi di MRTK usano per il rendering del testo migliorato. Per informazioni più dettagliate, vedere il [testo in Unity](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) .

1. Chiudere la finestra di dialogo TMP. Dopo questa operazione è necessario ricaricare la scena. Questa operazione può essere eseguita facendo doppio clic sulla scena nella scheda progetto.

1. Deselezionare o ridurre le dimensioni delle icone 3D nella scheda gizmos della visualizzazione scena per ridurre il disordine della scena

     ![Gizmo](https://user-images.githubusercontent.com/13754172/80819866-a8aed800-8b8a-11ea-8d7b-a3822fdfc907.png)

1. Premere il pulsante Riproduci.

## <a name="using-the-in-editor-hand-input-simulation-to-test-a-scene"></a>Uso della simulazione di input manuale nell'editor per testare una scena

La simulazione di input nell'editor consente di testare il comportamento degli oggetti virtuali in base a un tipo specifico di input, ad esempio [hands](features/InputSimulation/InputSimulationService.md#hand-simulation) o [Eyes](features/EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor).

Come spostarsi nella scena:

* Usare i tasti **W/A/S/D** per spostare la telecamera in avanti, a sinistra, indietro e a destra.
* Usare **Q/E** per spostare la telecamera verticalmente.
* Premere e tenere premuto il **pulsante destro del mouse** per ruotare la telecamera.

Come simulare l'input con mani:

* Premere e tenere premuto la **barra spaziatrice** per abilitare la mano destra.
* Tenendo premuta la barra spaziatrice, spostare il mouse per spostare la mano.
* Utilizzare la **rotellina** del mouse per regolare la profondità della mano.
* Fare clic sul **pulsante sinistro del mouse** per simulare il gesto di avvicinamento delle dita.
* Usare i tasti **T/Y** per rendere la mano persistente nella visualizzazione.
* Tenere premuto il tasto **CTRL** e spostare il mouse per ruotare la mano.

Divertiti a esplorare la scena! Per ulteriori informazioni sui controlli dell'interfaccia utente, vedere [la guida degli esempi di interazione con la mano](features/README_HandInteractionExamples.md). Vedere anche la [documentazione sulla simulazione di input](features/InputSimulation/InputSimulationService.md) per altre informazioni sulla simulazione di input manuale nell'editor in MRTK.

È stata appena usata la prima scena MRTK. Ora è possibile creare esperienze personalizzate...

## <a name="next-steps"></a>Passaggi successivi

Ecco alcuni passaggi successivi suggeriti:

* Vedere [MRTK 101: come usare Mixed Reality Toolkit Unity per le interazioni di base](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) per ottenere informazioni su come ottenere interazioni spaziali comuni, ad esempio le operazioni di cattura, spostamento, ridimensionamento e rotazione.
* Informazioni sui controlli UX disponibili in MRTK nei [blocchi predefiniti dell'interfaccia utente e dell'interazione](features/Experimental/README.md#ux-building-blocks).
* Provare l' [Hub esempi di MRTK](features/README_ExampleHub.md) (i pacchetti dell'app predefiniti sono inclusi nella pagina della versione per praticità)
* Informazioni su come usare il profilo di configurazione di MRTK nella [Guida alla configurazione della realtà mista](out-of-scope/MixedRealityConfigurationGuide.md).
* Informazioni sull' [architettura di MRTK](architecture/Overview.md)
* Informazioni sul [sistema di input di MRTK](features/input/Overview.md)
* Scopri gli [strumenti di MRTK](features/Experimental/README.md#tools) che consentiranno di migliorare la progettazione e lo sviluppo di realtà mista.
* Leggere la [Guida alla simulazione di input](features/InputSimulation/InputSimulationService.md) per apprendere come simulare l'input manuale nell'editor.

## <a name="getting-help"></a>Risorse della Guida

Se si verificano problemi causati da MRTK o in caso di domande su come eseguire un'operazione, sono disponibili alcune risorse che consentono di:

* Per le segnalazioni di bug, inviare [un problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) nel repository GitHub.
* Per domande, rivolgersi a [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o al canale di [reality-Toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) in slack. È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

## <a name="upgrading-from-the-holotoolkit-htkmrtk-v1"></a>Aggiornamento da HoloToolkit (HTK/MRTK V1)

Non esiste un percorso di aggiornamento diretto da HoloToolkit a Mixed Reality toolkit V2 a causa del Framework ricompilato. Tuttavia, è possibile importare il MRTK nel progetto HoloToolkit ed eseguire la migrazione dell'implementazione. Per ulteriori informazioni, vedere la [Guida al porting di HoloToolkit to Mixed Reality Toolkit](updates-deployment/HTKToMRTKPortingGuide.md)

## <a name="getting-started-with-unitys-xr-sdk"></a>Introduzione a XR SDK di Unity

Istruzioni complete e informazioni sono disponibili nella [Guida introduttiva a XR SDK](configuration/GettingStartedWithMRTKAndXRSDK.md).
