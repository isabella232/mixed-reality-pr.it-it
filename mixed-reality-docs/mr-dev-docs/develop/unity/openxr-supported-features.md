---
title: Funzionalità supportate dal plug-in OpenXR in Unity
description: Scopri le funzionalità supportate da OpenXR per lo sviluppo di realtà mista in Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: c9d52f9529cabeaf912fffa6efc6599a9041a929
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112398054"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Funzionalità supportate da Mixed Reality OpenXR in Unity

Il **pacchetto mixed reality openxr plugin** è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per HoloLens 2 e Windows Mixed Reality visori VR. Prima di continuare, verificare che il progetto Unity sia [configurato per OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>Attività supportate

Sono attualmente supportate le funzionalità seguenti:

* Supporta le applicazioni UWP per HoloLens 2 e l'ottimizzazione per HoloLens 2 modello applicativo.
* Supporta le applicazioni VR Win32 per Windows Mixed Reality visore VR con i profili controller più recenti e la comunicazione remota delle app olografiche.
* Rilevamento della scalabilità globale con Ancoraggi e Spazio non associato.
* [Ancoraggio dell'API di archiviazione per rendere persistenti](spatial-anchors-in-unity.md) gli ancoraggi HoloLens 2 archiviazione locale.
* [Interazioni tra controller del movimento e mano,](#motion-controller-and-hand-interactions)incluso il nuovo controller HP Reverb G2.
* Tracciamento delle mani articolato con 26 giunzioni e input del raggio delle giunzioni.
* Interazione con lo sguardo fisso HoloLens 2.
* Individuazione della fotocamera/video (PV) HoloLens 2.
* Acquisizione realtà mista il rendering del terzo occhio tramite la fotocamera PV.
* Supporta ["Play" per HoloLens 2'app Holographic Remoting,](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.
* Compatibile con MRTK Unity 2.5.3 e versioni più recente tramite il supporto del [provider MRTK OpenXR.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Compatibile con Unity [ARFoundation 4.0 o](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) versione successiva.
* (Aggiunto nella versione 0.1.3) Supporta [l'app desktop Holographic Remoting](holographic-remoting-desktop.md) da un'app autonoma di Windows compilata e distribuita.
* (Aggiunto nella versione 0.1.4) Supporta il [rilevamento del codice a qr](#qr-codes) in HoloLens2 tramite SpatialGraphNode
* (Aggiunto nella versione 0.2.0) Supporta **l'ancoraggio** nella comunicazione remota olografica
* (Aggiunto nella versione 0.2.0) Supporta le **giunzioni delle mani e il tracciamento della mesh delle mani**
* (Aggiunto nella versione 0.2.0) Supporta **ARPlaneSubsystems per** il rilevamento del piano e posizionare l'ologramma **usando ARRaycastManager.**
* (0.9.0) Supporta **XRMeshSubsystem** e **ARMeshManager** per il mapping spaziale.
* (Aggiunto nella versione 0.9.0) Supporta il plug-in Azure Spatial Anchors SDK per Windows. Per altre informazioni, vedere il progetto di esempio [Mixed Reality + OpenXR Azure Spatial Anchors su GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Aggiunto nella versione 0.9.1) Supporta l'app desktop Holographic Remoting da un'app UWP windows compilata e distribuita.
* (Aggiunto nella versione 0.9.4) Supporta la piattaforma ARM oltre ad ARM64 per HoloLens 2 applidato.

## <a name="motion-controller-and-hand-interactions"></a>Interazioni con il controller del movimento e la mano

Per informazioni di base sulle interazioni di realtà mista in Unity, visita il manuale [di Unity per l'input XR di Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) Questa documentazione di Unity illustra i mapping dagli input specifici del controller a input **più** generalizzabili, il modo in cui gli input XR disponibili possono essere identificati e classificati, come leggere i dati da questi input e altro ancora.

Il plug-in OpenXR di realtà mista fornisce profili di interazione di input aggiuntivi, mappati a **inputFeatureUsage** standard, come descritto di seguito:

| InputFeatureUsage | Controller HP Reverb G2 (OpenXR) | Mano HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Azzarre - Clic | |
| trigger | Trigger  | |
| Presa | Presa | Tocco o tassetto |
| primaryButton | [X/A] - Premere | Simulazione del tocco |
| secondaryButton | [Y/B] - Premere | |
| controllo gripButton | Grip - Press | |
| triggerButton | Trigger - Premere | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>Punti di punta e punti di agatura

È possibile accedere a due set di posizioni tramite interazioni di input OpenXR:

* Posizione del controllo per il rendering degli oggetti nella mano
* L'obiettivo è puntare al mondo.

Altre informazioni su questa progettazione e sulle differenze tra le due posizioni sono disponibili in [OpenXR Specification - Input Subpaths (Specifica openXR - Percorsi secondari di input).](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)

Le posizioni fornite da InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutte la posizione del triangolo OpenXR.  InputFeatureUsages correlati alle posizioni del controllo sono definiti in [CommonUsages di Unity.](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)

Le posizioni fornite da InputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** e **PointerAngularVelocity** rappresentano tutte la posizione dell'obiettivo OpenXR.  Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire i propri InputFeatureUsages come indicato di seguito:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Aptics

Per informazioni sull'uso degli aptici nel sistema XR Input di Unity, la documentazione è disponibile in [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)(Manuale di Unity per l'input XR di Unity - Aptics).

## <a name="qr-codes"></a>Codici QR

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice. Per altri dettagli, vedere la documentazione sul rilevamento [del codice a codici a](../platform-capabilities-and-apis/qr-code-tracking.md) qr.  Quando si usa il plug-in OpenXR, recuperare [ `SpatialGraphNodeId` dall'API di](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) domande e risposte e usare l'API `Microsoft.MixedReality.OpenXR.SpatialGraphNode` per individuare il codice a chiave.

Per riferimento, è in [gitHub](https://github.com/yl-msft/QRTracking) un progetto di esempio di rilevamento delle domande e risposte con una spiegazione più dettagliata dell'utilizzo per [ `SpatialGraphNode` l'API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando sospendi e riprendi un'app Unity in HoloLens 2, l'app non può riprendere correttamente, con la conseguenza che nella visualizzazione HoloLens vengono visualizzati 4 puntini di rotazione.

* Impostare **Modalità di invio profondità** su Nessuna **nelle** impostazioni del progetto OpenXR come soluzione alternativa
