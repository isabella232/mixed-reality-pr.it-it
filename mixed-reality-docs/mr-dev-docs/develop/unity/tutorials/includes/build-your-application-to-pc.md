---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392614"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Passaggio alla piattaforma di compilazione

Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni compilazione) selezionare **PC, Mac & Linux Standalone** Platform (Piattaforma autonoma Linux) e fare clic sul pulsante **Switch Platform** (Cambia piattaforma) per modificare build platform (Piattaforma di compilazione):

![Passaggio alla piattaforma di compilazione](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Dopo che Unity ha terminato di cambiare piattaforma, fare clic sull'icona x per chiudere la finestra Build Settings (Impostazioni di compilazione).

### <a name="2-set-the-project-settings"></a>2. Impostare le impostazioni del progetto

Nel menu di Unity selezionare Edit Project Settings XR Plug-in Management (Modifica impostazioni progetto XR Plug-in Management) assicurarsi di essere nella scheda Windows Standalone e selezionare la casella di controllo  >    >   OpenXR and **Windows Mixed Reality feature set (Set** di funzionalità **openXR** e Windows Mixed Reality).

![Abilitare OpenXR e il set Windows Mixed Reality funzionalità](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

Nella finestra Project Settings (Impostazioni progetto) selezionare **OpenXR** e assicurarsi di essere nella scheda Windows Standalone e modificare la **modalità di** invio Depth (Profondità) da None (Nessuna) a **Depth 16 Bit (Profondità a 16 bit).**

Nella scheda dei profili di interazione aggiungere il profilo di interazione sguardo **fisso** e il profilo di **interazione con la mano Microsoft** facendo clic sul simbolo +.

![Aggiungere il profilo di interazione con lo sguardo fisso e il profilo di interazione con la mano Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

In **Open XR feature groups (Apri gruppi** di funzionalità XR) > selezionare la casella di controllo  >   **Holographic App Remoting (Comunicazione remota app Holographic).**

![Abilitare Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

Selezionare quindi la casella **Windows Mixed Reality** di controllo e nel gruppo Windows Mixed Reality selezionare la casella di controllo **Holographic App Remoting.**

![Abilitare la Windows Mixed Reality holographic app remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Compilare il progetto Unity

Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante ***Add Open Scenes** _ (Aggiungi scene aperte) per aggiungere la scena corrente alle scene. Nell'elenco Compila fare clic sul pulsante _ *Compila**:

![Finestra Build Settings di Unity con la scena aggiunta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

scegliere un percorso appropriato per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning. Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting. Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra di prompt Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Attendere che Unity completi il processo di compilazione.

![Processo di compilazione di Unity in corso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

Fare doppio clic sul file eseguibile per aprire l'applicazione Holographic Remoting del PC nel PC.

> [!NOTE]
> A causa di alcuni problemi noti nell'app Holographic Remoting per PC compilata come piattaforma UWP, l'app per PC viene compilata come windows autonoma per OpenXR.


# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Configurare le impostazioni del lettore

Nella sezione **XR Settings** (Impostazioni XR) selezionare la casella di controllo **WSA Holographic Remoting Supported** e abilitare Holographic Remoting.

![Finestra XR Settings di Unity con l'opzione WSA Holographic Remoting Supported abilitata](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Compilare il progetto Unity

Dal menu di Unity scegliere File > Build Settings (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante ***Add Open Scenes** _ (Aggiungi scene aperte) per aggiungere la scena corrente alle scene. Nell'elenco Compila fare clic sul pulsante _ *_Compila_** per aprire la finestra Piattaforma UWP (Universal Windows Platform) compilazione:

![Finestra Build Settings di Unity con la scena aggiunta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP) scegliere un percorso adatto per archiviare la compilazione, ad esempio Documenti\MixedRealityLearning. Creare una nuova cartella e assegnarle un nome appropriato, ad esempio PCHolographicRemoting. Fare quindi clic sul pulsante ***Select Folder*** (Seleziona cartella) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra di prompt Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Attendere che Unity completi il processo di compilazione.

![Processo di compilazione di Unity in corso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostarsi all'interno della cartella e fare doppio clic sul file con estensione sln per aprirlo in Visual Studio:

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedicare qualche minuto a verificare che siano installati tutti i componenti indispensabili, come specificato nell'argomento Installare gli strumenti.

Configurare Visual Studio per PC selezionando la configurazione Release, l'architettura x64 e Local Machine (Computer locale) come destinazione:

![Visual Studio configurato per Computer locale](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Fare clic sul pulsante ***Local Machine*** (Computer locale). Viene avviata la compilazione e la distribuzione dell'applicazione nel PC. L'applicazione verrà installata nel PC per impostazione predefinita.
