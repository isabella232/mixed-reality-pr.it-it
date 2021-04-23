---
title: Funzionalità supportate del plug-in OpenXR in Unity
description: Scoprire le funzionalità supportate da OpenXR per lo sviluppo di realtà mista in Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: e6756df7f082e56b029b6e82e06d960ba39ed04a
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894001"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Funzionalità supportate da OpenXR in Realtà mista in Unity

Il **pacchetto plug-in OpenXR** di realtà mista è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per HoloLens 2 e Windows Mixed Reality visori. Prima di continuare, assicurarsi che il progetto Unity sia [configurato per OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>Attività supportate

Sono attualmente supportate le funzionalità seguenti:

* Supporta le applicazioni UWP per HoloLens 2 e ottimizzare per HoloLens 2 modello di applicazione.
* Supporta le applicazioni VR Win32 per Windows Mixed Reality visore con i profili controller più recenti e la comunicazione remota delle app olografiche.
* Rilevamento della scalabilità globale con ancoraggi e spazio non associato.
* [Ancorare l'API di archiviazione per rendere persistenti](spatial-anchors-in-unity.md) gli ancoraggi HoloLens 2 archiviazione locale.
* [Controller di movimento e interazioni con la mano,](#motion-controller-and-hand-interactions)incluso il nuovo controller HP Reverb G2.
* Tracciamento articolato della mano usando 26 giunzioni e input del raggio delle giunzioni.
* Interazione con lo sguardo fisso HoloLens 2.
* Individuazione della fotocamera foto/video (PV) HoloLens 2.
* Acquisizione realtà mista il rendering del terzo occhio tramite la fotocamera fotovoltaico.
* Supporta ["Play" per HoloLens 2'app Holographic Remoting,](#holographic-remoting-in-unity-editor-play-mode)consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.
* Compatibile con MRTK Unity 2.5.3 e versioni più recente tramite il supporto del [provider MrTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatibile con Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o versione successiva.
* (Aggiunta nella versione 0.1.3) Supporta [l'app desktop Holographic Remoting](holographic-remoting-desktop.md) da un'app autonoma di Windows compilata e distribuita.
* (Aggiunto nella versione 0.1.4) Supporta il [rilevamento del codice a qr](#qr-codes) in HoloLens2 tramite SpatialGraphNode
* (Aggiunto nella versione 0.2.0) Supporta **l'ancoraggio** nella comunicazione remota olografica
* (Aggiunto nella versione 0.2.0) Supporta le **giunzioni delle mani e il tracciamento della mesh delle mani**
* (Aggiunto nella versione 0.2.0) Supporta **ARPlaneSubsystems per** il rilevamento del piano e posizionare l'ologramma **usando ARRaycastManager.**
* (0.9.0) Supporta **XRMeshSubsystem** e **ARMeshManager** per il mapping spaziale.
* (Aggiunto nella versione 0.9.0) Supporta il plug-in Azure Spatial Anchors SDK per Windows. Per altre informazioni, vedere il progetto di esempio [Mixed Reality + OpenXR Azure Spatial Anchors su GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Aggiunto nella versione 0.9.1) Supporta l'app desktop Holographic Remoting da un'app UWP windows compilata e distribuita.

## <a name="holographic-remoting-setup"></a>Configurazione di Holographic Remoting

1. Prima di tutto, è [necessario installare l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2
2. Eseguire l'app Holographic Remoting Player HoloLens 2 per visualizzare il numero di versione e l'indirizzo IP a cui connettersi
    * Per usare il plug-in OpenXR è necessaria la versione 2.4 o successiva

    ![Screenshot del lettore Holographic Remoting in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting in modalità di riproduzione dell'editor unity

La creazione di un progetto Unity UWP Visual Studio progetto e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 può richiedere del tempo. Una soluzione consiste nell'abilitare la funzionalità Holographic Editor Remoting, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 in rete. Questo scenario evita il sovraccarico dovuto alla compilazione e alla distribuzione di un pacchetto UWP in un dispositivo remoto.

1. Seguire la procedura descritta in [Holographic Remoting setup (Configurazione di Holographic Remoting)](#holographic-remoting-setup)
2. Aprire **Edit -> Project Settings**(Modifica -impostazioni progetto), passare a XR plug-in Management (Gestione **plug-in XR)** e selezionare la casella Windows Mixed Reality **set di funzionalità:**

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](images/openxr-features-img-02.png)

3. Espandere la **sezione Funzionalità** in **OpenXR** e selezionare **Mostra tutto**
4. Selezionare la casella **di controllo Holographic Editor Remoting** e immettere l'indirizzo IP che si ottiene dall'app Holographic Remoting:

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con funzionalità evidenziate](images/openxr-features-img-03.png)

È ora possibile fare clic sul pulsante "Play" (Riproduci) per riprodurre l'app Unity nell'app Holographic Remoting in HoloLens. È anche possibile [collegare Visual Studio a Unity per](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) eseguire il debug di script C# in modalità di riproduzione.

> [!NOTE]
> A causa della versione 0.1.0, il runtime di Holographic Remoting non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.  Questa funzionalità sarà disponibile nelle versioni future.

## <a name="motion-controller-and-hand-interactions"></a>Interazioni con il controller di movimento e la mano

Per informazioni di base sulle interazioni di realtà mista in Unity, vedere il Manuale [di Unity per l'input XR di Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) Questa documentazione di Unity illustra i mapping dagli input specifici del controller a input **più** generalizzabili, il modo in cui gli input XR disponibili possono essere identificati e categorizzati, come leggere i dati da questi input e altro ancora.

Il plug-in OpenXR di realtà mista offre profili di interazione di input aggiuntivi, mappati a **InputFeatureUsage** standard, come descritto di seguito:

| InputFeatureUsage | Controller HP Reverb G2 (OpenXR) | Mano holoLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick - Fare clic su | |
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

Per informazioni sull'uso dell'aptica nel sistema XR Input di Unity, la documentazione è disponibile nel manuale [Unity per Unity XR Input - Haptics.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="qr-codes"></a>Codici QR

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice. Per altri dettagli, vedere la documentazione sul rilevamento [del codice a livello](../platform-capabilities-and-apis/qr-code-tracking.md) di codice.  Quando si usa il plug-in OpenXR, afferrare [ `SpatialGraphNodeId` l'oggetto dall'API AR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e usare `Microsoft.MixedReality.OpenXR.SpatialGraphNode` l'API per individuare il codice a qr.

Per riferimento, è stato creato un progetto di esempio di rilevamento a livello di codice [in GitHub](https://github.com/yl-msft/QRTracking) con una spiegazione più dettagliata dell'utilizzo per l'API . [ `SpatialGraphNode` ](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)

## <a name="whats-coming-soon"></a>Novità in arrivo

I problemi seguenti e le funzionalità mancanti sono noti con il plug-in OpenXR di realtà mista **versione 0.9.2.** Stiamo lavorando a queste soluzioni e rilasceremo correzioni e nuove funzionalità nelle prossime versioni.

* **ARM64 è** l'unica piattaforma supportata per HoloLens 2 app. La **piattaforma ARM** sarà disponibile in una versione futura.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando si sospende e si riprende un'app Unity HoloLens 2, l'app non può riprendere correttamente, con 4 puntini di rotazione nella visualizzazione HoloLens.

* Impostare **Modalità di invio profondità** su Nessuna **nelle** impostazioni del progetto OpenXR come soluzione alternativa
