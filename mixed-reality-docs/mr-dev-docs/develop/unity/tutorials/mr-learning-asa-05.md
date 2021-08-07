---
title: Ancoraggi nello spazio di Azure per Android e iOS
description: In questo corso viene illustrato come distribuire un progetto Unity con Mixed Reality Toolkit (MRTK) e Ancoraggi nello spazio di Azure in Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, android, ios, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215804"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Ancoraggi nello spazio di Azure per Android e iOS

Questa esercitazione illustra come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.

## <a name="objectives"></a>Obiettivi

* Imparare a compilare il progetto in un dispositivo Android usando Unity AR Foundation e ARCore XR Plugin
* Imparare a compilare il progetto in un dispositivo iOS usando Unity AR Foundation e ARKit XR Plugin

## <a name="installing-inbuilt-unity-packages"></a>Installazione di pacchetti di Unity incorporati

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configurare MRTK per AR Foundation Camera

In questa sezione verrà illustrato come configurare MRTK per la distribuzione in un dispositivo mobile.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**. Quindi, nella finestra Inspector (Controllo) selezionare la scheda **Camera** (Fotocamera), clonare i profilo della fotocamera e assegnare un nome adatto, ad esempio **AzureSpatialAnchors_ARCameraProfile**:

![Unity con il profilo ARCameraProfile appena creato selezionato](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

Con la **scheda Fotocamera** ancora selezionata nella  finestra Inspector (Controllo), espandere i provider di impostazioni della fotocamera e fare clic su "-" per rimuovere le impostazioni della fotocamera **Windows Mixed Reality** o XR SDK Windows Mixed Reality Camera Setting (Impostazioni fotocamera **XR SDK):**

![Profilo ARCameraProfile di Unity con il nuovo provider di dati aggiunto ](images/mr-learning-asa/asa-05-section2-step1-2.png)

fare clic sul pulsante + Add Camera Setting Provider (+ Aggiungi provider di impostazioni **fotocamera),** quindi espandere il **nuovo provider di dati aggiunto:**

![Fotocamera AR aggiunta per Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

Usando l'elenco a discesa **Type** (Tipo), cambiare il tipo in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![Profilo ARCameraProfile di Unity con il percorso di selezione del tipo di provider di dati](images/mr-learning-asa/asa-05-section2-step1-4.png)

Aggiornare le definizione di scripting unityAR di MRTK richiamando la voce di menu Mixed **Reality**  >  **Toolkit**  >  **Utilities**  >  **UnityAR** > Update Scripting Defines

## <a name="building-your-application-to-your-android-device"></a>Compilazione dell'applicazione in un dispositivo Android

In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo Android.

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente, quindi impostare la piattaforma su Android:

![Finestra Build Settings di Unity con la piattaforma Android selezionata](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).

Chiudere la finestra Build Settings (Impostazioni di compilazione).

Nel menu di Unity selezionare **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project realtà mista per MRTK) per aprire la finestra  >    >    >   **MRTK Project Configurator (Configuratore mrTK Project),**  verificare che tutte le opzioni siano selezionate e quindi fare clic sul pulsante Apply (Applica) per applicare le impostazioni:

![Unity MRTK Project Configurator 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), selezionare **Vulkan** e rimuoverlo facendo clic sul simbolo **"-"** :

![Area Other Settings di Unity con Vulkan selezionato](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione). Quindi, usare un cavo USB, connettere il dispositivo Android al computer e selezionarlo nell'elenco a discesa **Run Device** (Esegui dispositivo):

![Finestra Build Settings di Unity con la scena aggiunta e Run Device selezionato](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Se il dispositivo non è presente nell'elenco a discesa Run Device (Esegui dispositivo), potrebbe essere necessario premere il pulsante Refresh (Aggiorna) accanto all'elenco a discesa.

Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build And Run** (Compila ed esegui) per aprire la finestra Build Android (Compila in Android).

Scegliere il percorso in cui archiviare la build, ad esempio _D:\MixedRealityLearning\Builds_, quindi assegnare un nome adeguato all'apk, ad esempio _MRTKTutorials-AzureSpatialAnchors_, e fare clic sul pulsante **Save** (Salva) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Se nella finestra della console Unity viene visualizzato un errore relativo ai moduli Android SDK, NDK o JDK, è necessario aprire Unity Hub e installare i moduli Android Build Support associati.

Al termine del processo di compilazione, le app dovrebbero essere caricate automaticamente nel dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilazione dell'applicazione in un dispositivo iOS

In questa sezione verrà illustrato come configurare il progetto per la compilazione e la distribuzione in un dispositivo iOS.

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente e impostare la piattaforma su iOS:

![Finestra Build Settings di Unity con la piattaforma iOS selezionata](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Per rivedere la procedura per cambiare piattaforma di compilazione, fare riferimento alle istruzioni contenute in [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform).

Chiudere la finestra Build Settings (Impostazioni di compilazione).

Nel menu di Unity selezionare **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project realtà mista per MRTK) per aprire la finestra  >    >    >   **MRTK Project Configurator (Configuratore mrTK Project),**  verificare che tutte le opzioni siano selezionate e quindi fare clic sul pulsante Apply (Applica) per applicare le impostazioni:

![Finestra MRTK Project Configurator di Unity - iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

Dal menu Unity scegliere **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Player Settings (Impostazioni lettore) e quindi individuare la sezione **Player** >  **Other Settings** (Lettore > Altre impostazioni), deselezionare la casella di controllo **Strip Engine Code** (Rimuovi codice motore) per disabilitarla:

![Area Other Settings di Unity con l'opzione Strip Engine Code disabilitata](images/mr-learning-asa/asa-05-section4-step1-3.png)

Chiudere la finestra Player Settings (Impostazioni lettore) e aprire di nuovo la finestra **Build Settings** (Impostazioni di compilazione).

Nella finestra Build Settings (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene nella compilazione):

![Finestra Build Settings di Unity con la scena aggiunta](images/mr-learning-asa/asa-05-section4-step1-4.png)

Nella finestra delle impostazioni di compilazione fare clic sul pulsante **Build** (Compila) per aprire la finestra Build iOS (Compila in iOS).

Scegliere un percorso appropriato in cui archiviare il progetto Xcode, ad esempio _D:\MixedRealityLearning\Builds_, creare una nuova cartella e assegnarle un nome adatto, ad esempio, _MRTKTutorials-AzureSpatialAnchors_, e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra del prompt di salvataggio - iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

Al termine del processo di compilazione, seguire le istruzioni in [Esportare il progetto Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) per informazioni su come distribuire il progetto Xcode in un dispositivo iOS.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato descritto come compilare il progetto nei dispositivi Android e iOS usando AR Foundation, ARCore XR Plugin e ARKit XR Plugin.
