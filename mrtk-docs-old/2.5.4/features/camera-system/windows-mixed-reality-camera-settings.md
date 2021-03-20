---
title: WindowsMixedRealityCameraSettings
description: Documentazione per usare la fotocamera di realtà mista di Windows in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: a5d261d7ccadcd47b1697dd78f74013a343d1bbc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683064"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Provider di impostazioni della fotocamera per la realtà mista di Windows

Il provider di impostazioni della camera di realtà mista di Windows determina il tipo di dispositivo su cui l'applicazione è in esecuzione e applica le impostazioni di configurazione appropriate in base allo schermo (trasparente o opaco).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Abilitazione del provider di impostazioni della camera di realtà mista di Windows

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .

    ![Espandi provider di impostazioni](../images/camera-system/ExpandProviders.png)

3. Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.

    ![Espandi nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

4. Selezionare il provider di impostazioni della fotocamera per la realtà mista di Windows

    ![Selezionare il provider di impostazioni della realtà mista di Windows](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Quando si usano i profili predefiniti di Microsoft Mixed Reality Toolkit, il provider di impostazioni della fotocamera di realtà mista di Windows verrà già abilitato e configurato.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Configurazione del provider di impostazioni della fotocamera per la realtà mista di Windows

Le impostazioni della fotocamera per la realtà mista di Windows supportano anche un profilo. Questo profilo offre le opzioni seguenti:

![Configurazione delle impostazioni della fotocamera per la realtà mista di Windows](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendering dell'acquisizione di realtà mista dalla fotocamera foto/video

Con questa impostazione in HoloLens 2 è possibile abilitare l'allineamento degli ologrammi nelle acquisizioni della realtà mista. Se abilitata, la piattaforma fornirà un HolographicCamera aggiuntivo all'app quando viene eseguita una foto o un video di acquisizione di realtà mista. Questo HolographicCamera fornisce le matrici di visualizzazione corrispondenti al percorso della fotocamera foto/video e fornisce matrici di proiezione usando il campo foto/video della fotocamera. In questo modo si garantisce che gli ologrammi, ad esempio le maglie della mano, rimangano allineati in modo visibile nell'output del video.

### <a name="hololens-2-reprojection-method"></a>Metodo di riproiezione HoloLens 2

Imposta il metodo iniziale per la riproiezione HoloLens 2. L'indicazione predefinita prevede l'uso della riproiezione di profondità, in quanto tutte le parti della scena verranno stabilizzate in modo indipendente in base alla distanza dall'utente. Se gli ologrammi sembrano ancora instabili, provare a verificare che tutti gli oggetti abbiano inviato correttamente la profondità al buffer di profondità. Questa è talvolta un'impostazione dello shader. Se la profondità sembra essere inviata correttamente e l'instabilità è ancora presente, provare la stabilizzazione autoplanal, che usa il buffer di profondità per calcolare un piano di stabilizzazione. Se un'app non è in grado di inviare dati di profondità sufficienti per una di queste opzioni, la riproiezione piana viene fornita come fallback. Questo metodo sarà basato sui dati del punto di interesse forniti da un'app tramite [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Per aggiornare il metodo di riproiezione in fase di esecuzione, accedere a nel `WindowsMixedRealityReprojectionUpdater` modo seguente:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Questa operazione deve essere aggiornata solo una volta e il valore viene riutilizzato per tutti i frame successivi. Se il metodo verrà aggiornato di frequente, è consigliabile memorizzare nella cache il risultato di `EnsureComponent` invece di chiamarlo spesso.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamere](camera-system-overview.md)
- [Creazione di un provider di impostazioni della fotocamera](create-settings-provider.md)
- [Rendering dell'acquisizione di realtà mista dalla fotocamera PV](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Riproiezione olografica](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#reprojection)
