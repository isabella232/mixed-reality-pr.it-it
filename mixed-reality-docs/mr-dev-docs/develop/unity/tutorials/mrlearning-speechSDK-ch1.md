---
title: Esercitazioni sui servizi vocali di Azure - 1. Integrazione e uso del riconoscimento vocale e della trascrizione
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: a12163dda0a6bf961c6c34ebc35b6e00f491d6ca59c08dfba7c5126e797d089a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214666"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integrazione e uso del riconoscimento vocale e della trascrizione

## <a name="overview"></a>Panoramica

In questa serie di esercitazioni creerai un'applicazione di Realtà mista per esplorare l'uso dei servizi vocali di Azure con HoloLens 2. Al termine di questa serie di esercitazioni, sarai in grado di usare il microfono del tuo dispositivo per trascrivere il parlato in testo in tempo reale, tradurre il parlato in altre lingue e utilizzare la funzionalità Riconoscimento finalità per comprendere i comandi vocali usando l'intelligenza artificiale.

## <a name="objectives"></a>Obiettivi

* Imparare a integrare i servizi vocali di Azure con un'applicazione HoloLens 2
* Imparare a usare il riconoscimento vocale per trascrivere testo

## <a name="prerequisites"></a>Prerequisiti

>[!TIP]
>Se non hai ancora completato la serie di [Esercitazioni introduttive](mr-learning-base-01.md), è consigliabile completare prima queste esercitazioni.

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Alcune funzionalità di programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS installato e il modulo Universal Windows Platform Build Support aggiunto

> [!Important]
> Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin. Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*
2. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Creazione e configurazione della scena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnazione di un nome appropriato, ad esempio *AzureSpeechServices*

Seguire quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni riportate in Modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarsi che il profilo di configurazione di MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di consapevolezza spaziale in **Occlusion**.

## <a name="configuring-the-speech-commands-start-behavior"></a>Configurazione del comportamento di avvio dei comandi vocali

Poiché userai Speech SDK per il riconoscimento vocale e la trascrizione, devi configurare i comandi vocali di MRTK in modo che non interferiscano con le funzionalità di Speech SDK. A tale scopo, puoi modificare il comportamento di avvio dei comandi vocali da Auto Start (Avvio automatico) a Manual Start (Avvio manuale).

Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Input**, clona **DefaultHoloLens2InputSystemProfile** e **DefaultMixedRealitySpeechCommandsProfile** e quindi modifica i comandi vocali di **Start Behavior** (Comportamento di avvio) in **Manual Start** (Avvio manuale):

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a>Configurazione delle funzionalità

Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

Nel Impostazioni di pubblicazione scorrere verso  il basso fino alla sezione Capabilities (Funzionalità) e verificare che le funzionalità **InternetClient**, **Microphone** e **SpatialPerception,** abilitate al momento della creazione del progetto all'inizio dell'esercitazione, siano abilitate. Abilita quindi le funzionalità **InternetClientServer** e **PrivateNetworkClientServer**:

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versione più recente)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK. HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, è possibile fare riferimento alle istruzioni riportate in [Importazione di Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets).

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

È necessario configurare il progetto Unity per pubblicare i plug-in di Riconoscimento vocale di Azure per ARM64. A tale scopo, nella finestra di Project passare ad **Assets**  >  **SpeechSDK**  >  **Plugins** WSA ARM64 (Plug-in SpeechSDK asset)  >  **WSA** ARM64 e selezionare  >   **Microsoft.CognitiveServices.Speech.core plugin (Plug-in Microsoft.CognitiveServices.Speech.core).**

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

Con il **plug-in Microsoft.CognitiveServices.Speech.core** ancora selezionato, nella  finestra di controllo abilitare **WSA Player,** quindi in Impostazioni piattaforma selezionare **UWP** per SDK, **ARM64** per la CPU e fare clic su Applica per applicare queste impostazioni al plug-in.

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

Ripetere questa procedura per ognuno dei plug-in rimanenti:

* **Microsoft.CognitiveServices.Speech.extension.audio.sys**
* **Microsoft.CognitiveServices.Speech.extension.kws**
* **Microsoft.CognitiveServices.Speech.extension.lu**
* **Microsoft.CognitiveServices.Speech.extension.silk_codec**

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione e configurerai il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) per il controllo della scena.

Nella finestra Project (Progetto) passa ad **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Asset > MRTK.Tutorials.AzureSpeechServices > Prefab) e trascina il prefab **Lunarcom** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Con l'oggetto **Lunarcom** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Il componente Lunarcom Controller (Script) (Controller Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **Terminal** nel campo **Terminal** (Terminale) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Terminal in modo da visualizzarne gli oggetti figlio e quindi trascina l'oggetto **ConnectionLight** nel campo **Connection Light** (Luce di connessione) e l'oggetto **OutputText** nel campo **Output Text** (Testo di output) del componente Lunarcom Controller (Script) (Controller Lunarcom - Script):

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Con l'oggetto **Lunarcom** ancora selezionato, espandi l'oggetto Buttons per visualizzarne gli oggetti figlio e quindi nella finestra Inspector (Controllo) espandi l'elenco **Buttons** (Pulsanti), imposta **Size** (Dimensioni) su 3 e trascina gli oggetti **MicButton**, **SatelliteButton** e **RocketButton** rispettivamente nei campi **Element** (Elemento) 0, 1 e 2:

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Connessione del progetto Unity alla risorsa di Azure

Per usare i servizi vocali di Azure, devi creare una risorsa di Azure e ottenere una chiave API per il servizio vocale. Segui le istruzioni contenute in [Provare gratuitamente il servizio Voce](/azure/cognitive-services/speech-service/get-started) e prendi nota dell'area geografica del servizio, (definita anche posizione) e della chiave API (definita anche Key1 o Key2).

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) individua la sezione **Speech SDK Credentials** (Credenziali Speech SDK) del componente **Lunarcom Controller (Script)** (Controller Lunarcom - Script) e configurala come indicato di seguito:

* Nel campo **Speech Service API Key** (Chiave API servizio vocale) immetti la chiave API (Key1 o Key2)
* Nel campo **Speech Service Region** (Area del servizio vocale) immetti l'area geografica del servizio (posizione) usando lettere minuscole e rimuovendo gli spazi

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Uso del riconoscimento vocale per la trascrizione di testo

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Speech Recognizer (Script)** (Riconoscimento vocale Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Il componente Lunarcom Speech Recognizer (Script) (Riconoscimento vocale Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Se ora attivi la modalità gioco, puoi testare il riconoscimento vocale selezionando prima il pulsante del microfono:

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà trascritta nel pannello del terminale:

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Hai implementato il riconoscimento vocale basato su Azure. Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.

Nell'esercitazione successiva apprenderai come eseguire i comandi con il riconoscimento vocale di Azure.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Eseguire comandi con il riconoscimento vocale di Azure](mrlearning-speechSDK-ch2.md)
