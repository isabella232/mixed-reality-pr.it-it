---
title: CreateSettingProvider
description: provider di dati per le impostazioni della fotocamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 407a5b2c815f4f7a06daf1ad297bdde42f5d14ae
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683084"
---
# <a name="creating-a-camera-settings-provider"></a>Creazione di un provider di impostazioni della fotocamera

Il sistema della fotocamera è un sistema estensibile per fornire supporto per le configurazioni della fotocamera specifiche della piattaforma. Per aggiungere il supporto per una nuova configurazione della fotocamera, potrebbe essere necessario un provider di impostazioni personalizzato.

> [!NOTE]
> Il codice sorgente completo usato in questo esempio si trova nella cartella **MRTK/Providers/Unity** .

## <a name="namespace-and-folder-structure"></a>Struttura dello spazio dei nomi e della cartella

I provider di dati possono essere distribuiti in uno dei due modi seguenti:

1. Componenti aggiuntivi di terze parti
1. Parte del Toolkit Microsoft Mixed Reality

Il processo di approvazione per gli invii di nuovi provider di dati alla MRTK varia a seconda del caso e verrà comunicato al momento della proposta iniziale di. È possibile inviare proposte creando un nuovo [problema relativo al tipo di *richiesta di funzionalità*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Componenti aggiuntivi di terze parti

**Namespace**

È necessario che i provider di dati dispongano di uno spazio dei nomi per attenuare i potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome della società che produce il componente aggiuntivo
- Area funzionale

Un provider di impostazioni della fotocamera creato e fornito dalla società Contoso, ad esempio, può essere *"contoso. MixedReality. Toolkit. camera"*.

**Struttura di cartelle**

È consigliabile che il codice sorgente per i provider di dati venga disposto in una gerarchia di cartelle, come illustrato nella figura seguente.

![Esempio di struttura di cartelle](../images/camera-system/ExampleProviderFolderStructure.png)

Se la cartella *ContosoCamera* contiene l'implementazione del provider di dati, la cartella dell' *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor Unity) e la cartella *profili* contiene uno o più oggetti di script del profilo predefiniti.

### <a name="mrtk-submission"></a>Invio MRTK

**Namespace**

Se un provider di impostazioni della fotocamera viene inviato al [repository del Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity), lo spazio dei nomi **deve** iniziare con Microsoft. MixedReality. Toolkit (ad esempio: *Microsoft. MixedReality. Toolkit. CameraSystem*).

**Struttura di cartelle**

Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio, MRTK/Providers/Unity).

## <a name="define-the-camera-settings-object"></a>Definire l'oggetto impostazioni della fotocamera

Il primo passaggio nella creazione di un provider di impostazioni della fotocamera consiste nel determinare il tipo di dati (ad esempio, mesh o piani) che fornirà alle applicazioni.

Tutti gli oggetti dati spaziali devono implementare l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interfaccia.

## <a name="implement-the-settings-provider"></a>Implementare il provider di impostazioni

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe base

Tutti i provider di impostazioni della fotocamera devono implementare l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interfaccia, che specifica la funzionalità minima richiesta dal sistema di fotocamere. MRTK Foundation include la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe che fornisce un'implementazione predefinita della funzionalità richiesta.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave per la creazione di un provider di impostazioni della fotocamera consiste nell'applicare l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attributo alla classe. Questo passaggio consente di impostare il profilo e le piattaforme predefiniti per il provider di dati, se selezionato nel profilo di sistema della fotocamera, nonché nome, percorso della cartella e altro ancora.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementare i metodi IMixedRealityDataProvider

Una volta definita la classe, il passaggio successivo consiste nel fornire l'implementazione dell' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.

> [!NOTE]
> La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe, tramite la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornisce implementazioni vuote per i [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) metodi. I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Non tutti i provider di impostazioni richiedono implementazioni per tutti questi metodi. È consigliabile che `Destroy()` e `Initialize()` siano implementati come minimo.

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica del provider di impostazioni mediante l'implementazione di [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Questa parte del provider di dati sarà in genere specifica per la configurazione della fotocamera.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel Toolkit per la realtà mista i provider di dati vengono configurati usando i [profili](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo deve riflettere le opzioni di configurazione selezionabili dallo sviluppatore. Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono anche essere contenute nel profilo.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

L' `CreateAssetMenu` attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu **Crea** i  >    >  profili di **Toolkit di realtà mista**  >   .

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

L' `CustomEditor` attributo informa Unity del tipo di asset a cui si applica il controllo.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Crea definizione/i assembly

Il Toolkit di realtà mista Usa i file di definizione di assembly (con[estensione asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre i tempi di compilazione.

Si consiglia di creare i file di definizione degli assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di cartelle](#namespace-and-folder-structure) nell'esempio precedente, sono presenti due file. asmdef per il provider di dati ContosoCamera.

La prima definizione di assembly è per il provider di dati. Per questo esempio, viene chiamato ContosoCamera e si trova nella cartella *ContosoCamera* dell'esempio. Questa definizione di assembly deve specificare una dipendenza da Microsoft. MixedReality. Toolkit e da tutti gli altri assembly da cui dipende.

La definizione dell'assembly ContosoCameraEditor specifica il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella cartella *ContosoCamera\Editor* Questa definizione di assembly conterrà un riferimento all'assembly ContosoCamera, oltre a:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Una volta creato, il provider di dati può essere registrato con il sistema di fotocamera da usare nell'applicazione.

![Selezione del provider di impostazioni della fotocamera](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti presentano i dettagli specifici della creazione di pacchetti e della distribuzione, a seconda delle preferenze dello sviluppatore. Probabilmente, la soluzione più comune consiste nel generare un file con estensione file unitypackage Tools e distribuirlo tramite l'archivio risorse di Unity.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo comprimerà e lo distribuirà come parte delle offerte di MRTK.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamere](camera-system-overview.md)
- [`BaseCameraSettingsProvider` classe](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` interfaccia](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
