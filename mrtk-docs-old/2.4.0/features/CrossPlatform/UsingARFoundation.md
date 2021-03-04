---
title: UsingARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR core, AR Kit
ms.openlocfilehash: c1d1e9f51304f57e46201972fbb0c419f1f941d7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782281"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Come configurare MRTK per iOS e Android [sperimentale]

## <a name="install-required-packages"></a>Installare i pacchetti necessari

1. Scaricare e importare il pacchetto **Microsoft. MixedReality. Toolkit. Unity. Foundation** , da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [NuGet](../../reference-docs/MRTKNuGetPackage.md)

1. In Gestione pacchetti Unity (UPM) installare i pacchetti seguenti:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Commenti |
    | --- | --- | --- |
    | Fondazione AR  <br/> Versione: 1.5.0-Preview 6 | Fondazione AR  <br/> Versione: 1.5.0-Preview 6 | Per Unity 2018,4, questo pacchetto è incluso come anteprima. Per visualizzare il pacchetto: finestra > gestione pacchetti > avanzate > visualizzare i pacchetti di anteprima|
    | Plug-in ARCore XR <br/> Versione: 2.1.2 | Plug-in ARKit XR <br/> Versione: 2.1.2 | |

    **Unity 2019.3. x**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondazione AR  <br/> Versione: 2.1.4 |  Fondazione AR  <br/> Versione: 2.1.4 |
    | Plug-in ARCore XR <br/> Versione: 2.1.2 | Plug-in ARKit XR <br/> Versione: 2.1.2 |

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Abilitazione del provider di impostazioni della fotocamera AR Unity

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. Selezionare **copia e Personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.

    ![Clona profilo MRTK](../Images/CameraSystem/CloneProfileARFoundation.png)

1. Selezionare **Clone** accanto al profilo della fotocamera.

    ![Clona profilo della fotocamera MRTK](../Images/CameraSystem/CloneCameraProfileARFoundation.png)

1. Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .

    ![Espandi provider di impostazioni](../Images/CameraSystem/ExpandProviders.png)

1. Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.

    ![Espandi nuovo provider di impostazioni](../Images/CameraSystem/ExpandNewProvider.png)

1. Selezionare il provider di impostazioni della fotocamera AR Unity

    ![Selezionare il provider di impostazioni AR Unity](../Images/CameraSystem/SelectUnityArSettings.png)

    Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera AR Unity: [Unity AR camera Provider Settings](../CameraSystem/UnityArCameraSettings.md).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Creazione di una scena per dispositivi Android e iOS

1. Assicurarsi di aver aggiunto il provider di impostazioni della fotocamera Unity alla scena.

1. Passa alla piattaforma Android o iOS nelle impostazioni di compilazione Unity

    Quando si passa alla piattaforma, viene visualizzata la finestra di configurazione del progetto MRTK con le impostazioni per la piattaforma scelta.  Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.

    Impostazioni di configurazione del progetto iOS

    ![strumento di configurazione del progetto iOS](../Images/CameraSystem/MRTKProjectConfigurator.png)

1. Non sono previsti passaggi aggiuntivi dopo il passaggio alla piattaforma per Android.

1. Se la piattaforma è iOS, modificare > impostazioni progetto > lettore > altre impostazioni, sotto l'intestazione Ottimizzazione, **deselezionare** Rimuovi codice motore

    ![Impostazioni iOS](../Images/CameraSystem/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > Deselezionando il codice del motore di striping si tratta della soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).  Stiamo lavorando a una soluzione a lungo termine.

1. Compilare ed eseguire la scena

## <a name="see-also"></a>Vedi anche

- [Impostazioni della fotocamera AR Unity](../CameraSystem/UnityArCameraSettings.md)
