---
title: Compilazione e distribuzione in Android e iOS tramite AR Foundation
description: Documentazione per configurare MRTK per Android e iOS (ARFoundation) in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449740"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a>Compilazione e distribuzione in Android e iOS tramite AR Foundation [Sperimentale]

## <a name="install-required-packages"></a>Installare i pacchetti necessari

1. Scaricare e importare **il pacchetto Microsoft.MixedReality.Toolkit.Unity.Foundation** da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) o [unity Gestione pacchetti](../configuration/usingupm.md)

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

    **Unity 2020.3.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versione: 3.1.3 |  AR Foundation  <br/> Versione: 4.0.12 |
    | Plug-in ARCore XR <br/> Versione: 3.1.4 | Plug-in ARKit XR <br/> Versione: 4.1.7 |

1. Aggiornare le regole di scripting di MRTK UnityAR richiamando la voce di menu: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**

    ![Definizione degli script di aggiornamento](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Abilitazione del provider di impostazioni della fotocamera Unity AR

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. Selezionare **Copia e personalizza per** clonare il profilo MRTK per abilitare la configurazione personalizzata.

    ![Clonare il profilo MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Selezionare **Clona** accanto a Profilo fotocamera.

    ![Clonare il profilo della fotocamera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Settings Providers (Provider di impostazioni** fotocamera).

    ![Espandere i provider di impostazioni](../features/images/camera-system/ExpandProviders.png)

1. Fare **clic su Add Camera Settings Provider (Aggiungi provider** di impostazioni fotocamera) ed espandere la voce New camera settings **(Nuove impostazioni fotocamera)** appena aggiunta.

    ![Espandere il nuovo provider di impostazioni](../features/images/camera-system/ExpandNewProvider.png)

1. Selezionare il provider di impostazioni fotocamera UNITY AR

    ![Selezionare il provider di impostazioni di Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera Unity AR: [Provider di impostazioni fotocamera Unity AR.](../features/camera-system/unity-ar-camera-settings.md)

> [!NOTE]
> Questa installazione controlla (all'avvio dell'applicazione) se i componenti ar Foundation sono nella scena. In caso contrario, vengono aggiunti automaticamente per farlo funzionare con ARCore e ARKit.
> Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.
> Per altre informazioni sui componenti di AR Foundation e sull'installazione, vedere questa [documentazione.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Creazione di una scena per dispositivi Android e iOS

1. Assicurarsi di aver aggiunto unityAR Camera Settings Provider alla scena.

1. Passare dalla piattaforma ad Android o iOS nelle impostazioni di compilazione di Unity

1. Verificare che il provider di gestione plug-in XR associato sia abilitato

    Gestione plug-in iOS XR:  ![ Gestione plug-in XR iOS](../features/images/XRManagementiOS.png)

1. Compilare ed eseguire la scena

## <a name="see-also"></a>Vedi anche

- [Impostazioni della fotocamera unity AR](../features/camera-system/unity-ar-camera-settings.md)
