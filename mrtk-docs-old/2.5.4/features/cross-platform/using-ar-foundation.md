---
title: Uso diARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, AR Core, AR Kit
ms.openlocfilehash: 4fea85981b8f8ff770ffa62906a20f7fa40215e33218a5665c2fa8a88010d07e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219827"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Come configurare MRTK per iOS e Android [Sperimentale]

## <a name="install-required-packages"></a>Installare i pacchetti necessari

1. Scaricare e importare **Microsoft.MixedReality.Toolkit. Pacchetto Unity.Foundation,** da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o dal pacchetto [Unity Gestione pacchetti](../../configuration/usingupm.md)

1. In Unity Gestione pacchetti (UPM) installare i pacchetti seguenti:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Commenti |
    | --- | --- | --- |
    | AR Foundation  <br/> Versione: 1.5.0 - anteprima 6 | AR Foundation  <br/> Versione: 1.5.0 - anteprima 6 | Per Unity 2018.4, questo pacchetto è incluso come anteprima. Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Plug-in ARCore XR <br/> Versione: 2.1.2 | Plug-in ARKit XR <br/> Versione: 2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versione: 2.1.8 |  AR Foundation  <br/> Versione: 2.1.8 |
    | Plug-in ARCore XR <br/> Versione: 2.1.11 | Plug-in ARKit XR <br/> Versione: 2.1.9 |

    **Unity 2020.1.x (attualmente non supportato formalmente, incluso solo a scopo informativo)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versione: 3.1.3 |  AR Foundation  <br/> Versione: 3.1.3 |
    | Plug-in ARCore XR <br/> Versione: 3.1.4 | Plug-in ARKit XR <br/> Versione: 3.1.3 |

1. Aggiornare le regole di scripting di MRTK UnityAR richiamando la voce di menu: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Abilitazione del provider di impostazioni della fotocamera Unity AR

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Selezionare **Copia e personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.

    ![Clonare il profilo MRTK](../images/camera-system/CloneProfileARFoundation.png)

1. Selezionare **Clona** accanto al profilo della fotocamera.

    ![Clonare il profilo della fotocamera MRTK](../images/camera-system/CloneCameraProfileARFoundation.png)

1. Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Impostazioni Providers (Provider Impostazioni camera).**

    ![Espandere i provider di impostazioni](../images/camera-system/ExpandProviders.png)

1. Fare **clic su Add Camera Impostazioni Provider** ed espandere la voce New camera settings **(Nuove impostazioni fotocamera) appena** aggiunta.

    ![Espandere il nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

1. Selezionare il provider di servizi di Impostazioni di Unity AR

    ![Selezionare il provider di impostazioni di Unity AR](../images/camera-system/SelectUnityArSettings.png)

    Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera Unity AR: Provider [di impostazioni fotocamera Unity AR.](../camera-system/unity-ar-camera-settings.md)

> [!NOTE]
> Questa installazione controlla (all'avvio dell'applicazione) se i componenti ar Foundation sono nella scena. In caso contrario, vengono aggiunti automaticamente per farlo funzionare con ARCore e ARKit.
> Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.
> Per altre informazioni sui componenti di AR Foundation e sull'installazione, vedere questa [documentazione.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Creazione di una scena per dispositivi Android e iOS

1. Assicurarsi di aver aggiunto unityAR Camera Impostazioni Provider alla scena.

1. Passare dalla piattaforma ad Android o iOS nella build di Unity Impostazioni

    Quando si cambia piattaforma, verrà visualizzata la finestra Project Configurator MRTK con le impostazioni per la piattaforma scelta.  Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.

    iOS Project Configurator Impostazioni

    ![Configuratore Project iOS](../images/camera-system/MRTKProjectConfigurator.png)

1. Non sono necessari passaggi aggiuntivi dopo il passaggio della piattaforma per Android.

1. Se la piattaforma è iOS, edit > Project Impostazioni > Player > Other Impostazioni( Altro  Impostazioni, sotto l'intestazione Optimization (Ottimizzazione) deselezionare Strip Engine Code (Strip Engine Code)

    ![iOS Impostazioni](../images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > Deselezionare Strip Engine Code è la soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).  Stiamo lavorando a una soluzione a lungo termine.

1. Compilare ed eseguire la scena

## <a name="see-also"></a>Vedi anche

- [Unità AR Camera Impostazioni](../camera-system/unity-ar-camera-settings.md)
