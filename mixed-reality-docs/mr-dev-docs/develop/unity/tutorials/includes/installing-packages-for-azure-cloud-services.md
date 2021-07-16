---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224464"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Nel menu Unity selezionare **Finestra** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi verificare che sia installata la versione  >   di **AR Foundation**  >  **4.1.7.**

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Aggiungere AzurespatialAnchors SDK V2.10 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK. Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Windows plug-in XR](#tab/winxr)

Nel menu Unity selezionare **Window** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi  >   selezionare AR Foundation > **versione 4.0.12** e fare clic sul pulsante **Installa** per installare il pacchetto:

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Aggiungere AzurespatialAnchors SDK V2.10 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK. Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

Nel menu Unity selezionare **Window** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi  >   selezionare AR Foundation > **versione 3.1.3** e fare clic sul pulsante **Installa** per installare il pacchetto:

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Aggiungere AzurespatialAnchors SDK V2.7.2 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK. Tutorials.AzureCloudServices.LegacyWSA.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> Se vengono visualizzati avvisi CS0618 che indicano che 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' e 'WorldAnchor.GetNativeSpatialAnchorPtr()' sono obsoleti, è possibile ignorare tali avvisi.

> [!TIP]
> Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.
