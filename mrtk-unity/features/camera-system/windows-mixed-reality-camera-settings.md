---
title: Windows Mixed Reality della fotocamera
description: Documentazione per l'Windows Mixed Reality della fotocamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212693"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality provider di impostazioni della fotocamera

Il Windows Mixed Reality delle impostazioni della fotocamera determina il tipo di dispositivo su cui è in esecuzione l'applicazione e applica le impostazioni di configurazione appropriate in base alla visualizzazione (trasparente o opaca).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Abilitazione del provider Windows Mixed Reality impostazioni della fotocamera

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Impostazioni Providers (Provider Impostazioni camera).**

    ![Espandere i provider di impostazioni](../images/camera-system/ExpandProviders.png)

3. Fare **clic su Add Camera Impostazioni Provider** ed espandere la voce New camera settings **(Nuove impostazioni fotocamera) appena** aggiunta.

    ![Espandere il nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

4. Selezionare il provider Windows Mixed Reality camera Impostazioni

    ![Selezionare Windows Mixed Reality provider di impostazioni](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Quando si usa Microsoft Mixed Reality Toolkit profili predefiniti, il provider di impostazioni Windows Mixed Reality fotocamera sarà già abilitato e configurato.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Configurazione del provider di impostazioni Windows Mixed Reality fotocamera

Anche Windows Mixed Reality camera Impostazioni supporta un profilo. Questo profilo offre le opzioni seguenti:

![Windows Mixed Reality delle impostazioni della fotocamera](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Eseguire il rendering dell'acquisizione di realtà mista dalla foto/videocamera

Con questa impostazione su HoloLens 2, è possibile abilitare l'allineamento degli ologrammi nelle acquisizioni di realtà mista. Se abilitata, la piattaforma fornirà un'ulteriore holographicCamera all'app quando viene scattata una foto o un video di acquisizione di realtà mista. Questa holographicCamera fornisce matrici di visualizzazione corrispondenti alla posizione della foto/videocamera e fornisce matrici di proiezione usando il campo di visualizzazione foto/videocamera. In questo modo gli ologrammi, ad esempio le mesh a mano, rimarranno visibilmente allineati nell'output video.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 metodo di riproiezione

Imposta il metodo iniziale per la HoloLens 2 di progetto. Per impostazione predefinita, è consigliabile usare la riproiezione della profondità, in quanto tutte le parti della scena verranno stabilizzate in modo indipendente in base alla distanza dall'utente. Se gli ologrammi appaiono ancora instabili, provare a verificare che tutti gli oggetti hanno inviato correttamente la profondità al buffer di profondità. A volte si tratta di un'impostazione shader. Se la profondità sembra essere inviata correttamente e l'instabilità è ancora presente, provare a stabilizzare automaticamente, che usa il buffer di profondità per calcolare un piano di stabilizzazione. Se un'app non è in grado di inviare dati di profondità sufficienti perché una di queste opzioni sia utilizzabile, la riproiezione planare viene fornita come fallback. Questo metodo sarà basato sui dati del punto di attivazione forniti da un'app [tramite SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)

Per aggiornare il metodo di riproiezione in fase di esecuzione, accedere all'oggetto `WindowsMixedRealityReprojectionUpdater` simile al seguente:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Questa operazione deve essere aggiornata una sola volta e il valore viene riutilizzato per tutti i fotogrammi successivi. Se il metodo verrà aggiornato di frequente, è consigliabile memorizzare nella cache il risultato anziché `EnsureComponent` chiamarlo spesso.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamera](camera-system-overview.md)
- [Creazione di un provider di Impostazioni fotocamera](create-settings-provider.md)
- [Rendering Acquisizione realtà mista dalla fotocamera PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Riprogettazione olografica](/windows/mixed-reality/hologram-stability#reprojection)