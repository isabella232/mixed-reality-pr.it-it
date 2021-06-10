---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748470"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Seguire questa [esercitazione dettagliata per aggiungere](../../tutorials/mr-learning-base-01.md) e configurare automaticamente Mixed Reality Toolkit nel progetto Unity. È anche possibile usare direttamente la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare La scala **di** destinazione su **World:**

![Finestra delle impostazioni di MRTK](../../images/mrtk-target-scale.png)

MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un controllo doppio:

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. Nel pannello **Hierarchy (Gerarchia)** espandi **MixedRealityPlayspace** GameObject e trova l'oggetto figlio Main Camera **(Fotocamera** principale)
2. Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Impostare la modalità di origine di rilevamento in [XRInputSubsystem.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html) Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Puoi usare [ARSession per](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) le applicazioni HoloLens, che funziona meglio con gli ancoraggi e ARKit/ARCore.

![Sessione AR nella gerarchia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> Ar Session e le funzionalità correlate necessitano dell'installazione di AR Foundation.

È anche possibile applicare manualmente le modifiche della fotocamera senza usare ARSession:

1. Selezionare **Main Camera (Fotocamera** principale) nel **pannello Hierarchy (Gerarchia)**
1. Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro Inspector (Controllo) in Unity*

1. Aggiungere **trackedPoseDriver** alla fotocamera **principale**

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Selezionare **Main Camera (Fotocamera** principale) nel **pannello Hierarchy (Gerarchia)**
1. Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro Inspector (Controllo) in Unity*

1. Passare alla **sezione Altre impostazioni** delle impostazioni di Windows Store **Player**
1. Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity
1. Selezionare **Virtual Reality Supported (Realtà virtuale supportata)**

Poiché l'oggetto Main Camera viene automaticamente contrassegnato come fotocamera, Unity alimenta tutti i movimenti e le traduzioni.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando crei una nuova scena in Unity, conterrà un GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma potrebbe non avere le impostazioni applicate correttamente.