---
title: ReleaseNotes
description: versione non della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: cad9f39215dc6f2c33492493a720d2297a498a5d442ea03273c87541c5bcea3a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213159"
---
# <a name="microsoft-mixed-reality-toolkit-254-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.4

- [Novità](#whats-new)
- [Linee guida per l'aggiornamento](../updates-deployment/updating.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues)

> [!IMPORTANT]
> Esiste un problema noto del compilatore che influisce sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64. Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16.8 o successiva. Se non è possibile aggiornare il Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new"></a>Novità

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Correzione di un bug con Oculus Integration quando si usa UPM

Quando si usa UPM, OculusXRSDKDeviceManagerProfile ha sempre i [prefab impostati su Nessuno all'avvio.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160) Questa versione configura Gestione dispositivi in modo che punti a un working set di prefab all'avvio.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Correzione di un problema con OpenXR tramite UPM

Correzione di un problema a causa del quale i provider OpenXR non sono stati aggiunti al link.xml per impostazione predefinita, causando la mancata esecuzione di nuovi progetti sul dispositivo quando si usano OpenXR e MRTK tramite il Gestione pacchetti di Unity. I progetti esistenti che vengono aggiornati dovranno comunque essere aggiunti manualmente.

## <a name="what-was-new-in-253"></a>Novità della versione 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corregge una regressione con Oculus introdotto nella versione 2.5.2

2.5.2 ha introdotto [un problema di compilazione durante l'integrazione di Oculus SDK.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083) Questa versione ripristina il problema.

### <a name="add-support-for-openxr"></a>Aggiungere il supporto per OpenXR

È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR di Realtà mista di Microsoft. Per altre informazioni, vedere la pagina introduttiva di [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)il post del forum di [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentazione di [Microsoft.](https://aka.ms/openxr-unity-install)

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020.2 e versioni successive.
>
> Attualmente supporta solo compilazioni x64 e ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Correzione degli errori di visualizzazione dei limiti

Le visualizzazioni dei limiti, ad esempio il pavimento o le pareti, verranno ora configurate correttamente e visibili in fase di esecuzione in base al profilo limite.

### <a name="msbuild-for-unity-support"></a>MSBuild per il supporto di Unity

Il supporto per MSBuild per Unity è stato rimosso dalla versione 2.5.2, per allinearsi alle nuove linee guida per [i pacchetti di Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Problemi noti

### <a name="openxr"></a>OpenXR

Esiste attualmente un problema noto con Holographic Remoting e OpenXR, in cui le giunzioni delle mani non sono costantemente disponibili.
Inoltre, le scene campione di tracciamento oculare non sono attualmente compatibili, anche se il tracciamento *oculare funziona.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alcune funzionalità dello shader standard Toolkit realtà mista richiedono il pacchetto Foundation

Quando vengono importati tramite il Gestione pacchetti Unity, gli script di utilità dello shader standard MRTK (ad esempio HoverLight.cs) non vengono posizionati insieme allo shader nel pacchetto Asset Standard. Per accedere a questa funzionalità, le applicazioni richiederanno l'importazione del pacchetto Foundation.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera all'arresto

In alcune situazioni,ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache crei nuovamente MainCamera all'arresto. Per altre [informazioni, vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) questo problema.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando gli esempi vengono importati tramite Unity Gestione pacchetti

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Unity Gestione pacchetti generare messaggi FileNotFoundException nella console di Unity. La causa è il percorso del file "mancante" più lungo MAX_PATH (256 caratteri). Per risolvere il problema, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun spazializzatore. L'applicazione non supporterà il suono spaziale

Se un spazializzatore audio non è configurato, viene visualizzato un avviso "Non è stato specificato alcun spazializzatore". Ciò può verificarsi se non è installato alcun pacchetto XR, in quanto Unity include gli spazializzatori in questi pacchetti.

Per risolvere il problema, assicurarsi che:

- **Finestra**  >  **Gestione pacchetti** sono installati uno o più pacchetti XR
- **Realtà mista Toolkit**  >  **Utilità**  >  **Configurare Unity Project** ed effettuare una selezione per **Spazializza audio**

  ![Selezionare Audio Apatializer](../features/images/release-notes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcuni casi, `EyeTrackingDemo-00-RootScene` l'apertura può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto all'annullamento dell'impostazione del profilo di configurazione del servizio di transizione scena. Per risolvere il problema, seguire questa procedura:

- Passare `MixedRealityToolkit` all'oggetto nella gerarchia
- Nella finestra Inspector (Controllo) selezionare `Extensions`
- Se non è espansa, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition">

### <a name="oculus-quest"></a>Oculus Quest

Esiste attualmente un problema noto per l'uso del [plug-in Oculus XR con quando si usano le piattaforme autonome.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)  Per gli aggiornamenti, vedere oculus bug tracker/forums/release notes (Rilevamento bug Oculus/forums/note sulla versione).

Il bug è indicato con questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0+ o 2.1.1+), in cui è stata modificata la dimensione del carattere predefinita per gli elenchi a discesa e la spaziatura dei caratteri in grassetto.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere questo problema, eseguire il downgrade a una versione precedente di TextMeshPro. Per [altri dettagli, vedere #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) problema.
