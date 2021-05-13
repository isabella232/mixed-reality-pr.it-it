---
title: OculusQuestMRTK
description: Documentazione da configurare per Oculus Quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Oculus Quest,
ms.openlocfilehash: 9350ed7c8426c3bb31cf41493056fb6fc1e26107
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852436"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a>Come configurare Oculus Quest in MRTK usando la pipeline XR SDK

È [necessaria una oculus quest.](https://www.oculus.com/quest/)

Il supporto di MRTK per Oculus Quest viene fornito tramite due origini diverse, la pipeline XR di Unity e il pacchetto Oculus Integration Unity. Il **provider di dati Oculus XRSDK** consente l'uso di entrambe le origini e deve essere usato per usare MRTK in Oculus Quest.

La [pipeline XR di Unity consente l'uso](https://docs.unity3d.com/Manual/XR.html) di controller Oculus Touch e il tracciamento della testa con Oculus Quest.
Questa pipeline è lo standard per lo sviluppo di applicazioni XR in Unity 2019.3 e versioni diverse. Per usare questa pipeline, assicurarsi di usare **Unity 2019.3 o versione più recente.**

Il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) consente l'uso del **tracciamento delle** mani con Oculus Quest.
Questo provider  di dati NON usa la pipeline XR o la pipeline **XR** legacy di Unity, ma poiché i controller e il headtracking vengono gestiti dalla pipeline XR di Unity, è necessario seguire i passaggi descritti in Configurazione del progetto per **Oculus Quest** per assicurarsi di usare la pipeline **XR** e non la pipeline XR legacy **deprecata.** 

## <a name="setting-up-project-for-the-oculus-quest"></a>Configurazione del progetto per Oculus Quest

1. Seguire [questa procedura](https://developer.oculus.com/documentation/unity/book-unity-gsg/) per assicurarsi che il progetto sia pronto per la distribuzione in Oculus Quest.

1. Assicurarsi che [nel dispositivo sia](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) abilitata la modalità sviluppatore. L'installazione dei driver Oculus ADB è facoltativa.

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>Configurazione della pipeline XR per Oculus Quest

1. Assicurarsi che il **plug-in Oculus XR** sia installato in **Window --> Gestione pacchetti**

    ![Pacchetto plug-in Oculus XR](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Assicurarsi che il provider di plug-in Oculus sia incluso nel progetto selezionando Edit **--> Project Settings --> XR Plug-in Management --> Plug-in Providers (Modifica --> Project Settings --> XR Plug-in Management --> Plug-in Providers)** (Modifica impostazioni progetto -> XR Plug-in Management -- provider plug-in di >)

    ![Provider di plug-in Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configurazione del pacchetto Oculus Integration Unity per abilitare il handtracking

1. Scaricare e [importare Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) da Unity Asset Store. La versione più recente testata per il funzionamento è 20.0.0. Le versioni precedenti sono disponibili in questo [archivio](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Passare a Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules (Integra moduli di Oculus Integration Unity). Questa operazione aggiornerà gli asmdef con le definizioni e i riferimenti necessari per il funzionamento del codice Oculus Quest pertinente. Aggiornerà anche il file csc per filtrare gli avvisi obsoleti prodotti dagli asset di Oculus Integration. Il repo MRTK contiene un file csc che converte gli avvisi in errori. Questa conversione interrompe il MRTK-Quest di configurazione.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Nella cartella Oculus importata (si trova in Assets/Oculus) è presente un oggetto che può essere creato tramite script denominato OculusProjectConfig. In questo file di configurazione è necessario impostare HandTrackingSupport su "Controllers and Hands".

    ![Oculus Integration Controller And Hands](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configurazione della scena

1. Creare una nuova scena unity o aprire una scena preesiste, ad esempio HandInteractionExamples
1. Aggiungere MRTK alla scena passando a **Mixed Reality Toolkit** Aggiungi alla scena e  >  **configura**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Uso di Oculus XR SDK provider di dati

1. Configurare il profilo per l'uso di **Oculus XR SDK provider di dati**
    - Se non si intende modificare i profili di configurazione
        - Modificare il profilo in DefaultXRSDKConfigurationProfile e passare a Compilare e [distribuire il progetto in Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - In caso contrario, seguire questa procedura:
        - Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.

        ![Clonare il profilo](../images/cross-platform/CloneProfile.png)

        - Selezionare il profilo **di configurazione** dell'input

        ![Profilo di configurazione di input](../images/cross-platform/InputConfigurationProfile.png)

        - Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.

        ![Clonare il profilo di sistema di input](../images/cross-platform/CloneInputSystemProfile.png)

        - Aprire la **sezione Provider di** dati di input, selezionare Aggiungi **provider di dati** nella parte superiore per aggiungere un nuovo provider di dati alla fine dell'elenco.  Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**

        ![Oculus Add XRSDK provider di dati](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. Oculus XR SDK provider di dati un prefab OVR Camera Rig che configura automaticamente il progetto con un dispositivo OVR Camera Rig e mani OVR per indirizzare correttamente l'input. L'aggiunta manuale di un dispositivo di videocamera OVR alla scena richiederà la configurazione manuale delle impostazioni e dell'input.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Compilare e distribuire il progetto in Oculus Quest

1. Collegare Oculus Quest tramite un cavo USB 3.0 -> USB C
1. Passare a **Impostazioni di compilazione > file**
1. Modificare la distribuzione in **Android**
1. Assicurarsi che Oculus Quest sia selezionato come dispositivo di esecuzione applicabile

    ![Dispositivo di esecuzione Oculus](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Selezionare Build and Run (Compila ed esegui)
    - È probabile che si verifichi il set di errori di compilazione seguente quando si seleziona *Compila ed esegui* la prima volta. Dovrebbe essere possibile eseguire correttamente la distribuzione selezionando Compila *ed esegui di* nuovo.

    ![Errori di compilazione previsti di Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Accettare la _richiesta Consenti debug USB_ dall'interno della ricerca
1. Visualizzare la scena all'interno di Oculus Quest

## <a name="removing-oculus-integration-from-the-project"></a>Rimozione dell'integrazione oculus dal progetto

1. Passare a Mixed Reality Toolkit > Oculus > Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Consentire l'aggiornamento di Unity quando i riferimenti in Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef e altri file vengono modificati in questo passaggio
1. Chiudere Unity
1. Chiudere Visual Studio, se è aperto
1. Aprire Esplora file e passare alla radice del progetto UNITY MRTK
1. Eliminare la directory UnityProjectName/Library
1. Eliminare la directory UnityProjectName/Assets/Oculus
1. Eliminare il file UnityProjectName/Assets/Oculus.meta
1. Riaprire Unity

## <a name="common-errors"></a>Errori comuni

### <a name="quest-not-recognized-by-unity"></a>Ricerca non riconosciuta da Unity

Assicurarsi che i percorsi Android siano configurati correttamente. Se si continuano a riscontrare problemi, seguire questa [guida](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Modificare > preferenze > strumenti esterni > Android**

![Configurazione degli strumenti Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
