---
ms.openlocfilehash: f55de39af8c9bc59bb23136203bfc093a4e29f1ea9ddc5ccd147f8c81d6f0020
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212315"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Usa la [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e imposta La scala **di destinazione** **su Seated**:

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
```

E usare [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.

![XR rig nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Passare alla **sezione Other Impostazioni** (Altri Impostazioni) del Windows Store Player **Impostazioni**
2. Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity
3. Selezionare **Virtual Reality Supported (Realtà virtuale supportata)**

Poiché l'oggetto Main Camera viene automaticamente contrassegnato come fotocamera, Unity alimenta tutti i movimenti e le traduzioni.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando crei una nuova scena in Unity, conterrà un GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma non ha le impostazioni seguenti applicate correttamente.

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per creare **un'esperienza di solo orientamento** o di **ridimensionamento,** è necessario impostare Unity sul tipo di spazio di tracciamento stazionario. Lo spazio di tracciamento stazionario imposta il sistema di coordinate del mondo di Unity per tenere traccia del [fotogramma stazionario di riferimento](../../../../design/coordinate-systems.md#spatial-coordinate-systems). In modalità di rilevamento stazionario, il contenuto posizionato nell'editor proprio davanti alla posizione predefinita della fotocamera (in avanti è -Z) verrà visualizzato davanti all'utente all'avvio dell'app.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Per **un'esperienza** pura di solo orientamento, ad esempio un visualizzatore video a 360 gradi (in cui gli aggiornamenti della testa posizionale possono insodziarsi), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per **un'esperienza su larga scala,** per consentire all'utente di eseguire in un secondo momento la versione più recente dell'origine, è possibile chiamare [il codice XR. Metodo InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

Se stai creando un'esperienza su larga [scala,](../../../../design/coordinate-systems.md)puoi usare l'origine globale di Unity più recente nella posizione attuale della testa dell'utente chiamando **[XR. Metodo InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**