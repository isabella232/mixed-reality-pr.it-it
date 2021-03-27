---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636323"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Seguire questa [esercitazione dettagliata](../../tutorials/mr-learning-base-01.md) per aggiungere e configurare automaticamente il Toolkit di realtà mista nel progetto Unity. È anche possibile usare direttamente la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) da MRTK per Unity e impostare la scala di **destinazione** su **World**:

![Finestra Impostazioni MRTK](../../images/mrtk-target-scale.png)

MRTK deve gestire automaticamente la posizione dei playspace e della fotocamera, ma è consigliabile eseguire il doppio controllo:

![Playspace MRTK](../../images/mrtk-playspace.png)

1. Nel pannello **gerarchia** espandere il GameObject **MixedRealityPlayspace** e trovare l'oggetto figlio della **fotocamera principale**
2. Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Impostare la modalità di origine del rilevamento su [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

È possibile usare [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) per le applicazioni HoloLens, che funziona meglio con gli ancoraggi e con ARKit/ARCore.

![Sessione AR nella gerarchia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> Per la sessione AR e le funzionalità correlate è necessario che sia installato AR Foundation.

È anche possibile applicare manualmente le modifiche della fotocamera senza usare ARSession:

1. Selezionare la **fotocamera principale** nel pannello **gerarchia**
1. Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro controllo in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro controllo in Unity*

1. Aggiungere un **TrackedPoseDriver** alla **fotocamera principale**

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Selezionare la **fotocamera principale** nel pannello **gerarchia**
1. Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**

   ![Fotocamera nel riquadro controllo in Unity](../../images/maincamera-350px.png)  
   *Fotocamera nel riquadro controllo in Unity*

1. Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**
1. Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity
1. Selezione della **realtà virtuale supportata**

Poiché l'oggetto fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity è in tutto lo spostamento e la traduzione.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma potrebbe non avere le impostazioni applicate correttamente.