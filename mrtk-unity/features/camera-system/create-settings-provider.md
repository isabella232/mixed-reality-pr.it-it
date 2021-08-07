---
title: Creazione di un provider di impostazioni della fotocamera
description: Provider di dati per le impostazioni della fotocamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5efab728905cd9885bf49f54b1939f3957cc5815af00dc816a4044a3f659b3bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210702"
---
# <a name="creating-a-camera-settings-provider"></a>Creazione di un provider di impostazioni della fotocamera

Il sistema camera è un sistema estendibile per fornire il supporto per le configurazioni della fotocamera specifiche della piattaforma. Per aggiungere il supporto per una nuova configurazione della fotocamera, potrebbe essere necessario un provider di impostazioni personalizzato.

> [!NOTE]
> Il codice sorgente completo usato in questo esempio è disponibile nella **cartella MRTK/Providers/UnityAR.**

## <a name="namespace-and-folder-structure"></a>Spazio dei nomi e struttura di cartelle

I provider di dati possono essere distribuiti in uno dei due modi seguenti:

1. Componenti aggiuntivi di terze parti
1. Parte di Microsoft Mixed Reality Toolkit

Il processo di approvazione per l'invio di nuovi provider di dati al modulo MRTK varia caso per caso e verrà comunicato al momento della proposta iniziale. Le proposte possono essere inviate creando un nuovo problema relativo al [ *tipo di richiesta* di funzionalità](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Componenti aggiuntivi di terze parti

**Namespace**

I provider di dati devono disporre di uno spazio dei nomi per attenuare potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome dell'azienda che produce il componente aggiuntivo
- Area funzionale

Ad esempio, un provider di impostazioni della fotocamera creato e spedito dalla società Contoso può essere *"Contoso.MixedReality.Toolkit. Camera"*.

**Struttura di cartelle**

È consigliabile che il codice sorgente per i provider di dati sia disponibile in una gerarchia di cartelle, come illustrato nell'immagine seguente.

![Esempio di struttura di cartelle](../images/camera-system/ExampleProviderFolderStructure.png)

Dove la cartella *ContosoCamera* contiene l'implementazione del provider di dati, la cartella *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor unity) e la cartella *Profiles* contiene uno o più oggetti pre-creati da script del profilo.

### <a name="mrtk-submission"></a>Invio di MRTK

**Namespace**

Se un provider di impostazioni della fotocamera viene inviato [al repository Toolkit realtà](https://github.com/Microsoft/MixedRealityToolkit-Unity)mista, lo spazio dei nomi deve iniziare con Microsoft.MixedReality.  Toolkit (ad esempio: *Microsoft.MixedReality.Toolkit. CameraSystem*).

**Struttura di cartelle**

Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: MRTK/Providers/UnityAR).

## <a name="define-the-camera-settings-object"></a>Definire l'oggetto impostazioni della fotocamera

Il primo passaggio per la creazione di un provider di impostazioni della fotocamera consiste nel determinare il tipo di dati (ad esempio mesh o piani) che fornirà alle applicazioni.

Tutti gli oggetti dati spaziali devono implementare [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) l'interfaccia .

## <a name="implement-the-settings-provider"></a>Implementare il provider di impostazioni

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe di base

Tutti i provider di impostazioni della fotocamera devono implementare l'interfaccia , che [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) specifica la funzionalità minima richiesta dal sistema di fotocamera. La base MRTK include la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe che fornisce un'implementazione predefinita della funzionalità richiesta.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave per la creazione di un provider di impostazioni della fotocamera consiste nell'applicare [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) l'attributo alla classe . Questo passaggio consente di impostare il profilo e le piattaforme predefinite per il provider di dati, se selezionati nel profilo camera system, nonché nome, percorso della cartella e altro ancora.

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

Dopo aver definito la classe, il passaggio successivo consiste nel fornire l'implementazione [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) dell'interfaccia .

> [!NOTE]
> La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe , tramite la classe , fornisce [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) implementazioni vuote per i metodi [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) . I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Non tutti i provider di impostazioni richiederanno implementazioni per tutti questi metodi. È altamente consigliato e `Destroy()` deve essere implementato come `Initialize()` minimo.

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica del provider di impostazioni implementando [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Questa parte del provider di dati sarà in genere specifica della configurazione della fotocamera.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel modello di realtà mista Toolkit i provider di dati vengono configurati tramite [profili](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo deve rispecchiare le opzioni di configurazione selezionabili dallo sviluppatore. Anche tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.

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

L'attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il `CreateAssetMenu` menu Create   >  **Assets**  >  **Mixed Reality Toolkit** Profiles (Crea asset di realtà mista Toolkit  >  **profili).**

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo del profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe .

`CustomEditor`L'attributo indica a Unity il tipo di asset a cui si applica il controllo.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Creare definizioni di assembly

L'Toolkit di realtà mista usa i file di definizione dell'assembly ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre il tempo di compilazione.

È consigliabile creare file di definizione dell'assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di](#namespace-and-folder-structure) cartelle nell'esempio precedente, saranno presenti due file asmdef per il provider di dati ContosoCamera.

La prima definizione di assembly è per il provider di dati. Per questo esempio, si chiamerà ContosoCamera e si trova nella cartella *ContosoCamera* dell'esempio. Questa definizione di assembly deve specificare una dipendenza da Microsoft.MixedReality. Toolkit e qualsiasi altro assembly da cui dipende.

La definizione dell'assembly ContosoCameraEditor specificherà il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella *cartella ContosoCamera\Editor.* Questa definizione di assembly conterrà un riferimento all'assembly ContosoCamera, nonché:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Dopo la creazione, il provider di dati può essere registrato con il sistema Camera da usare nell'applicazione.

![Selezione del provider di impostazioni della fotocamera](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti hanno i dettagli specifici della creazione di pacchetti e della distribuzione lasciati alle preferenze dello sviluppatore. È probabile che la soluzione più comune sia generare un file unitypackage e distribuirsi tramite Unity Asset Store.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo inserirà e lo distribuirà come parte delle offerte MRTK.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamera](camera-system-overview.md)
- [Classe `BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` Interfaccia](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` Interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
