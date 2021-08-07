---
ms.openlocfilehash: 78596197af6c2e7c329e7a7c99281f8debee13b973a212709f5be1ec34e04eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212295"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Seguire questa [esercitazione dettagliata per](../../tutorials/mr-learning-base-01.md) aggiungere e configurare automaticamente l'Toolkit realtà mista nel progetto Unity. È anche possibile usare direttamente la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) da MRTK per Unity e impostare **Scala di** destinazione su **Mondo:**

![Finestra delle impostazioni MRTK](../../images/mrtk-target-scale.png)

MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un doppio controllo:

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. Nel pannello **Gerarchia** espandere **MixedRealityPlayspace** GameObject e trovare l'oggetto **figlio Main Camera**
2. Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Impostare la modalità di origine di rilevamento in [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

È possibile usare [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) per HoloLens, che funziona meglio con ancoraggi e ARKit/ARCore.

![Sessione ar nella gerarchia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> Per la sessione AR e le funzionalità correlate è necessario installare AR Foundation.

È anche possibile applicare manualmente le modifiche della fotocamera senza usare ARSession:

1. Selezionare **Fotocamera principale** nel pannello **Gerarchia**
1. Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro Inspector (Controllo) in Unity*

1. Aggiungere **un oggetto TrackedPoseDriver** alla **fotocamera principale**

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Selezionare **Fotocamera principale** nel pannello **Gerarchia**
1. Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro Inspector (Controllo) in Unity*

1. Passare alla **sezione Altri Impostazioni** del lettore Windows Store **Impostazioni**
1. Scegliere **Windows Mixed Reality** come dispositivo, che può essere elencato come Windows **Holographic** nelle versioni precedenti di Unity
1. Selezionare **Realtà virtuale supportata**

Poiché l'oggetto Fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity alimenta tutti i movimenti e la traduzione.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, conterrà un oggetto GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma potrebbe non avere le impostazioni applicate correttamente.