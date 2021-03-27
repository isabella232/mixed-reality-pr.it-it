---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636381"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Usare la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) da MRTK per Unity e impostare la **scala di destinazione** su **Seated**:

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
```

E collaborano con [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**
2. Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity
3. Selezione della **realtà virtuale supportata**

Poiché l'oggetto fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity è in tutto lo spostamento e la traduzione.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma le impostazioni non sono state applicate correttamente.

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Per creare un'esperienza di **solo orientamento** o **scalabilità**, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario. Lo spazio di rilevamento fisso imposta il sistema di Coordinate internazionali di Unity per tenere traccia del [frame di riferimento fisso](../../../../design/coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor appena davanti alla posizione predefinita della fotocamera (avanti è-Z) verrà visualizzato davanti all'utente all'avvio dell'app.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *InputTracking*

Per un' **esperienza solo con orientamento** puro, ad esempio un visualizzatore video di 360 gradi (dove gli aggiornamenti delle intestazioni posizionali potrebbero rovinare l'illusione), è possibile impostare [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per un' **esperienza a scalabilità verticale**, per consentire all'utente di ricentrare l'origine in un secondo momento, è possibile chiamare [XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

Se si sta creando un' [esperienza a scalabilità verticale](../../../../design/coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .