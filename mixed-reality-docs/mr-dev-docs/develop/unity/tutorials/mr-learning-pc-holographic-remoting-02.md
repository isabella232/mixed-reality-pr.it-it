---
title: Creare un'applicazione Holographic Remoting per PC
description: In questo corso viene illustrato come creare un'applicazione per PC per usare in remoto un'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, holographic remoting per PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: fd357b0b487b948afb6ae15c9e84362e2bc1ef90
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007331"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creazione di un'applicazione Holographic Remoting per PC

In questa esercitazione si apprenderà come creare un'app Holographic Remoting per PC e connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per Holographic Remoting
* Imparare a compilare e distribuire l'applicazione con Visual Studio
* Sviluppare un'applicazione Holographic Remoting e connetterla a HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>Configurazione della scena per Holographic Remoting

In questa sezione si configurerà il progetto in modo da trasmettere l'esperienza di realtà mista al dispositivo HoloLens 2 dal PC in tempo reale tramite una connessione Wi-Fi.

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab) e selezionare e trascinare il prefab **HolographicRemoting** nella scena.

![Unity con il prefab HolographicRemoting appena creato ancora selezionato](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Compilare l'applicazione nel PC

L'app Holographic Remoting è ora pronta per la compilazione nel PC. Attenersi ai passaggi seguenti e apportare queste modifiche per compilare l'applicazione nel PC.

### <a name="1-set-the-player-settings"></a>1. Configurare le impostazioni del lettore

Nel menu di Unity scegliere Edit (Modifica) > Project Settings (Impostazioni del progetto) per visualizzare la finestra Player Settings (Impostazioni lettore).

Nella finestra Project Settings (Impostazioni del progetto) espandere **Publishing Settings** (Impostazioni di pubblicazione), scorrere verso il basso fino alla sezione **Capabilities** (Funzionalità) e selezionare la casella di controllo della funzionalità mostrata di seguito, in aggiunta alle funzionalità esistenti.

* Client e server Internet
* Client e server di rete privata

Nella sezione **XR Settings** (Impostazioni XR) selezionare la casella di controllo **WSA Holographic Remoting Supported** e abilitare Holographic Remoting.

![Finestra XR Settings di Unity con l'opzione WSA Holographic Remoting Supported abilitata](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Compilare il progetto Unity

Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **_Add Open Scenes_* _ (Aggiungi scene aperte) per aggiungere la scena corrente alle scene. Nell'elenco Build (Compilazione) fare clic sul _*_pulsante Build_*_ (Compila) per aprire la finestra Build Universal Windows Platform (Compilazione UWP):

![Finestra Build Settings di Unity con la scena aggiunta](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP) scegliere un percorso adatto per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning. Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting. Fare quindi clic sul pulsante _*_Select Folder_*_ (Seleziona cartella) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra di prompt Select Folder](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Attendere che Unity completi il processo di compilazione.

![Processo di compilazione di Unity in corso](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostarsi all'interno della cartella e fare doppio clic sul file con estensione sln per aprirlo in Visual Studio:

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedicare qualche minuto a verificare che siano installati tutti i componenti indispensabili, come specificato nell'argomento Installare gli strumenti.

Configurare Visual Studio per PC selezionando la configurazione Release, l'architettura x64 e Local Machine (Computer locale) come destinazione:

![Visual Studio configurato per Computer locale](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Fare clic sul pulsante _*_Computer locale_*_. Viene avviata la compilazione e la distribuzione dell'applicazione nel PC. L'applicazione verrà installata nel PC per impostazione predefinita.

## <a name="testing-holographic-remoting-remote-application"></a>Test di un'applicazione remota Holographic Remoting

Per connettere l'applicazione PC a HoloLens 2, seguire questa procedura:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Installare l'applicazione Remoting Player nel dispositivo HoloLens 2

_ In HoloLens 2 aprire l'app dello Store e cercare "**Remoting Player**".
* Selezionare l'app **Remoting Player**.
* Toccare **Install** (Installa) per scaricare e installare l'app.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Connettere l'app del PC Holographic Remoting a Remoting Player

* Avviare **Remoting Player** in HoloLens.
* Prendere nota dell'**indirizzo IP** di HoloLens. Verrà visualizzato come ologramma da **Remoting Player** non appena viene avviato.
* Aprire l'applicazione Holographic Remoting per PC nel PC in uso.
* Una volta avviata l'applicazione, immettere l'**indirizzo IP** e fare clic sul pulsante **Connect** (Connetti) per connettersi.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come creare un'app remota Holographic Remoting e connetterla a HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista. Dopo aver connesso HoloLens all'applicazione PC Holographic Remoting, si noterà che l'esperienza di realtà mista è in streaming nel dispositivo HoloLens 2.
