---
title: UsingARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR core, AR Kit
ms.openlocfilehash: 4a0e57fa3f8b00ac9867689b9c8fe49a560dbe11
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685954"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Come configurare MRTK per iOS e Android [sperimentale]

## <a name="install-required-packages"></a>Installare i pacchetti necessari

1. Scaricare e importare il pacchetto **Microsoft. MixedReality. Toolkit. Unity. Foundation** , da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o da [Gestione pacchetti Unity](../../configuration/usingupm.md)

1. In Gestione pacchetti Unity (UPM) installare i pacchetti seguenti:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Commenti |
    | --- | --- | --- |
    | Fondazione AR  <br/> Versione: 1.5.0-Preview 6 | Fondazione AR  <br/> Versione: 1.5.0-Preview 6 | Per Unity 2018,4, questo pacchetto è incluso come anteprima. Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Plug-in ARCore XR <br/> Versione: 2.1.2 | Plug-in ARKit XR <br/> Versione: 2.1.2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondazione AR  <br/> Versione: 2.1.8 |  Fondazione AR  <br/> Versione: 2.1.8 |
    | Plug-in ARCore XR <br/> Versione: 2.1.11 | Plug-in ARKit XR <br/> Versione: 2.1.9 |

    **Unity 2020.1. x (attualmente non supportato formalmente, incluso solo a scopo informativo)**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondazione AR  <br/> Versione: 3.1.3 |  Fondazione AR  <br/> Versione: 3.1.3 |
    | Plug-in ARCore XR <br/> Versione: 3.1.4 | Plug-in ARKit XR <br/> Versione: 3.1.3 |

1. Aggiornare le definizioni di script di MRTK Unity richiamando la voce di menu: **mixed reality Toolkit > Utilities > unity > Update scripting definisce**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Abilitazione del provider di impostazioni della fotocamera AR Unity

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Selezionare **copia e Personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.

    ![Clona profilo MRTK](../images/camera-system/CloneProfileARFoundation.png)

1. Selezionare **Clone** accanto al profilo della fotocamera.

    ![Clona profilo della fotocamera MRTK](../images/camera-system/CloneCameraProfileARFoundation.png)

1. Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .

    ![Espandi provider di impostazioni](../images/camera-system/ExpandProviders.png)

1. Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.

    ![Espandi nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

1. Selezionare il provider di impostazioni della fotocamera AR Unity

    ![Selezionare il provider di impostazioni AR Unity](../images/camera-system/SelectUnityArSettings.png)

    Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera AR Unity: [Unity AR camera Provider Settings](../camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Questa installazione controlla (all'avvio dell'applicazione) se i componenti di AR Foundation si trovano nella scena. In caso contrario, vengono aggiunti automaticamente per fare in modo che funzioni con ARCore e ARKit.
> Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.
> Per ulteriori informazioni sui componenti e sull'installazione di AR Foundation, consultare la [documentazione](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Creazione di una scena per dispositivi Android e iOS

1. Assicurarsi di aver aggiunto il provider di impostazioni della fotocamera Unity alla scena.

1. Passa alla piattaforma Android o iOS nelle impostazioni di compilazione Unity

    Quando si passa alla piattaforma, viene visualizzata la finestra di configurazione del progetto MRTK con le impostazioni per la piattaforma scelta.  Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.

    Impostazioni di configurazione del progetto iOS

    ![strumento di configurazione del progetto iOS](../images/camera-system/MRTKProjectConfigurator.png)

1. Non sono previsti passaggi aggiuntivi dopo il passaggio alla piattaforma per Android.

1. Se la piattaforma è iOS, modificare > impostazioni progetto > lettore > altre impostazioni, sotto l'intestazione Ottimizzazione, **deselezionare** Rimuovi codice motore

    ![Impostazioni iOS](../images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > Deselezionando il codice del motore di striping si tratta della soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).  Stiamo lavorando a una soluzione a lungo termine.

1. Compilare ed eseguire la scena

## <a name="see-also"></a>Vedi anche

- [Impostazioni della fotocamera AR Unity](../camera-system/unity-ar-camera-settings.md)
