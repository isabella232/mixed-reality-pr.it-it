---
title: OculusQuestMRTK
description: Documentazione per la configurazione di Oculus quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Oculus quest,
ms.openlocfilehash: 6a4af71e84ef098552d02b14f51b14552f3c3e12
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782700"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xrsdk-pipeline"></a>Come configurare Oculus quest in MRTK usando la pipeline XRSDK

È necessaria una [missione Oculus](https://www.oculus.com/quest/) .

Il supporto di MRTK per l'Oculus missione viene fornito tramite due origini diverse, la pipeline XR di Unity e il pacchetto Oculus Integration Unity. Il **provider di dati Oculus XRSDK** consente l'uso di entrambe le origini e deve essere usato per usare MRTK in Oculus quest.

La [pipeline di Unity XR](https://docs.unity3d.com/Manual/XR.html) consente di usare i controller Oculus touch e il rilevamento Head con l'Oculus quest.
Questa pipeline è lo standard per lo sviluppo di applicazioni XR in Unity 2019,3 e versioni successive. Per usare questa pipeline, assicurarsi di usare **unity 2019,3 o versione successiva**.

Il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) consente di usare il **rilevamento manuale** con l'Oculus quest.
Questo provider di dati **non usa la** pipeline **XR** di Unity o la **pipeline XR legacy**, ma poiché i controller e headtracking sono associati alla pipeline XR di Unity, è necessario seguire la procedura descritta in **impostazione del progetto per la missione Oculus** per assicurarsi che si stia usando la **pipeline XR** e non la pipeline XR **legacy** di cui è stato deprecato.

## <a name="setting-up-project-for-the-oculus-quest"></a>Impostazione del progetto per la missione Oculus

1. Per assicurarsi che il progetto sia pronto per la distribuzione in Oculus quest, seguire [questa procedura](https://developer.oculus.com/documentation/unity/book-unity-gsg/) .

1. Verificare che nel dispositivo sia abilitata la [modalità sviluppatore](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) . L'installazione dei driver Oculus ADB è facoltativa.

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>Impostazione della pipeline XR per Oculus quest

1. Verificare che il **plug-in Oculus XR** sia installato in **Window--> Package Manager**

    ![OculusXRPluginPackage](../Images/CrossPlatform/OculusQuest/OculusXRPluginPackage.png)

1. Verificare che il provider del plug-in Oculus sia incluso nel progetto **modificando > impostazioni progetto--> gestione plug-in XR--> provider plug-in**

    ![OculusPluginProvider](../Images/CrossPlatform/OculusQuest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configurazione del pacchetto Oculus Integration Unity per abilitare handtracking

1. Scaricare e importare l' [integrazione di Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) da Unity Asset Store. La versione più recente testata per funzionare è 20.0.0. Le versioni precedenti sono reperibili in questo [Archivio](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Passare a Mixed Reality Toolkit > Utilities > Oculus > integrare i moduli di Oculus Integration Unity. Questa operazione aggiornerà il asmdefs con le definizioni e i riferimenti necessari per il funzionamento del codice di Oculus missione pertinente. Aggiornerà anche il file CSC per filtrare gli avvisi obsoleti generati dalle risorse di integrazione Oculus. Il repository MRTK contiene un file CSC che converte gli avvisi in errori, questa conversione interrompe il processo di configurazione del MRTK-Quest.

    ![OculusIntegrationAsmdef](../Images/CrossPlatform/OculusQuest/OculusIntegrationAsmdef.png)

1. Nella cartella Oculus importata (dovrebbe trovarsi in asset/Oculus), è presente un oggetto con script denominato OculusProjectConfig. In tale file di configurazione è necessario impostare HandTrackingSupport su "Controllers and hands".

    ![OculusIntegrationControllerAndHands](../Images/CrossPlatform/OculusQuest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Impostazione della scena

1. Creare una nuova scena Unity o aprire una scena preesistente, ad esempio HandInteractionExamples
1. Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**

## <a name="using-the-oculus-xrsdk-data-provider"></a>Uso di Oculus XRSDK provider di dati

1. Configurare il profilo per l'uso di **Oculus XRSDK provider di dati**
    - Se non si intende modificare i profili di configurazione
        - Modificare il profilo in DefaultXRSDKInputSystemProfile e passare a [compilare e distribuire il progetto in Oculus quest](OculusQuestMRTK.md#build-and-deploy-your-project-to-oculus-quest)

    - In caso contrario, seguire questa procedura:
        - Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.

        ![CloneProfile](../Images/CrossPlatform/CloneProfile.png)

        - Selezionare il profilo di configurazione di **input**

        ![InputConfigurationProfile](../Images/CrossPlatform/InputConfigurationProfile.png)

        - Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.

        ![CloneInputSystemProfile](../Images/CrossPlatform/CloneInputSystemProfile.png)

        - Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore e il nuovo provider di dati verrà aggiunto alla fine dell'elenco.  Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**

        ![OculusAddXRSDKDataProvider](../Images/CrossPlatform/OculusQuest/OculusAddDataXRSDKProvider.png)

    - È possibile verificare che i controller Oculus siano rilevati da

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Compila e Distribuisci il progetto in Oculus quest

1. Collegare l'Oculus quest tramite un cavo USB 3,0-> USB
1. Passa a **File > impostazioni di compilazione**
1. Modificare la distribuzione in **Android**
1. Verificare che l'Oculus cerca sia selezionata come dispositivo di esecuzione applicabile

    ![OculusRunDevice](../Images/CrossPlatform/OculusQuest/OculusRunDevice.png)

1. Selezionare Compila ed Esegui
    - Quando si seleziona *Compila ed Esegui* la prima volta, si verificherà probabilmente il set di errori di compilazione seguente. Si dovrebbe essere in grado di distribuire correttamente quando si seleziona *Compila ed Esegui* di nuovo.

    ![OculusExpectedBuildErrors](../Images/CrossPlatform/OculusQuest/OculusExpectedBuildErrors.png)

1. Accettare la richiesta di abilitazione del _debug USB_ dall'interno della ricerca
1. Guarda la tua scena all'interno di Oculus quest

## <a name="removing-oculus-integration-from-the-project"></a>Rimozione dell'integrazione di Oculus dal progetto

1. Passare al Toolkit di realtà mista > Oculus > moduli di integrazione di Oculus di OculusSeparationAsmdef separati. ![](../Images/CrossPlatform/OculusQuest/OculusSeparationAsmdef.png)
1. Consentire l'aggiornamento di Unity come riferimenti in Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef e altri file vengono modificati in questo passaggio
1. Chiudi Unity
1. Chiudere Visual Studio, se è aperto
1. Aprire Esplora file e passare alla radice del progetto MRTK Unity
1. Elimina la directory UnityProjectName/Library
1. Eliminare la directory UnityProjectName/assets/Oculus
1. Eliminare il file UnityProjectName/assets/Oculus. meta
1. Riaprire Unity

## <a name="common-errors"></a>Errori comuni

### <a name="quest-not-recognized-by-unity"></a>Ricerca non riconosciuta da Unity

Assicurarsi che i percorsi Android siano configurati correttamente. Se continui a riscontrare problemi, segui questa [Guida](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Modificare le preferenze di > > strumenti esterni > Android**

![AndroidToolsConfig](../Images/CrossPlatform/OculusQuest/AndroidToolsConfig.png)
