---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636382"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Usare la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare la **scala di destinazione** su uno **spazio** o su una **posizione**:

![Finestra Impostazioni MRTK](../../images/mrtk-target-scale.png)

MRTK deve gestire automaticamente la posizione dei playspace e della fotocamera, ma è consigliabile eseguire il doppio controllo:

![Playspace MRTK](../../images/mrtk-playspace.png)

1. Nel pannello **gerarchia** espandere il GameObject **MixedRealityPlayspace** e trovare l'oggetto figlio della **fotocamera principale**
2. Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Impostare la modalità di origine del rilevamento su [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

Per un'esperienza **di scalabilità o** **scalabilità**, è necessario inserire il contenuto relativo alla superficie. Si ragiona sul pavimento dell'utente usando la **[fase spaziale](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione.

Per assicurarsi che Unity stia operando con il sistema di coordinate globale a livello di piano, è possibile impostare e verificare che Unity usi il tipo di spazio di rilevamento RoomScale:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Se SetTrackingSpaceType restituisce true, Unity ha cambiato correttamente il sistema di coordinate globali per tenere traccia del [frame della fase di riferimento](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame della fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente. Anche se un valore restituito false non è comune, può verificarsi se la fase è configurata in un'altra stanza e il dispositivo viene spostato nella stanza corrente senza che l'utente configurasse una nuova fase.

Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento. L'origine a 0, 0, 0 corrisponderà alla posizione specifica del piano in cui l'utente si trovava durante l'installazione della stanza, con-Z che rappresenta la direzione in avanti durante l'installazione.