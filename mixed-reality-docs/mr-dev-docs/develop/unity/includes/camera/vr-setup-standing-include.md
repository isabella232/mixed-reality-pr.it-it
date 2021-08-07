---
ms.openlocfilehash: 47dfba0fe2b64e3b7e03ae62af3de1e1e24bd70b8b1e7e6b2cb40995428dbda2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212322"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Usare la [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare **La** scala di destinazione su **Room** o **Standing**:

![Finestra delle impostazioni MRTK](../../images/mrtk-target-scale.png)

MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un doppio controllo:

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. Nel pannello **Gerarchia** espandere **MixedRealityPlayspace** GameObject e trovare l'oggetto **figlio Main Camera**
2. Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Impostare la modalità di origine di rilevamento in [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

E usare [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Passare alla **sezione Altri Impostazioni** del lettore Windows Store **Impostazioni**
2. Scegliere **Windows Mixed Reality** come dispositivo, che può essere elencato come Windows **Holographic** nelle versioni precedenti di Unity
3. Selezionare **Realtà virtuale supportata**

Poiché l'oggetto Fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity alimenta tutti i movimenti e la traduzione.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà un oggetto GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma non avrà le impostazioni seguenti applicate correttamente.

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per **un'esperienza su larga** **scala** o su scala locale, è necessario posizionare il contenuto rispetto al piano. Il piano dell'utente viene ragione usando la fase spaziale **[,](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** che rappresenta l'origine definita a livello di piano dell'utente e il limite facoltativo della stanza, configurato durante la prima esecuzione.

Per garantire il funzionamento di Unity con il sistema di coordinate globale a livello di piano, è possibile impostare e testare che Unity sta usando il tipo di spazio di rilevamento RoomScale:

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

* Se SetTrackingSpaceType restituisce true, Unity ha commutato correttamente il sistema di coordinate del mondo per tenere traccia del [fotogramma della fase di riferimento.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)
* Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame di fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente. Anche se un valore restituito falso non è comune, può verificarsi se la fase è impostata in una stanza diversa e il dispositivo viene spostato nella stanza corrente senza che l'utente configura una nuova fase.

Dopo che l'app ha impostato correttamente il tipo di spazio di rilevamento RoomScale, sul piano y=0 verrà visualizzato il contenuto posizionato sul piano y=0. L'origine a 0, 0, 0 sarà la posizione specifica sul piano in cui si trovava l'utente durante la configurazione della stanza, con -Z che rappresenta la direzione in avanti che stava affrontando durante la configurazione.