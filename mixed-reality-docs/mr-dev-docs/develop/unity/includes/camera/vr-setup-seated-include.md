---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748475"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Usare la [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare **Scala di** destinazione **su Seated:**

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
```

E usare [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Passare alla **sezione Altre impostazioni** delle impostazioni di Windows Store **Player**
2. Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity
3. Selezionare **Realtà virtuale supportata**

Poiché l'oggetto Fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity alimenta tutti i movimenti e la traduzione.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà un oggetto GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma non avrà le impostazioni seguenti applicate correttamente.

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per creare **un'esperienza solo orientamento** o su scala da seduti, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario.  Lo spazio di rilevamento stazionario imposta il sistema di coordinate del mondo di Unity per tenere traccia [del fotogramma stazionario di riferimento.](../../../../design/coordinate-systems.md#spatial-coordinate-systems) Nella modalità di rilevamento stazionario, il contenuto posizionato nell'editor proprio davanti alla posizione predefinita della fotocamera (forward è -Z) verrà visualizzato davanti all'utente all'avvio dell'app.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Per **un'esperienza** pura solo con orientamento, ad esempio un visualizzatore video a 360 gradi (in cui gli aggiornamenti della testa posizionale avrebbero distrutto l'illusione), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking su](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per **un'esperienza su larga scala,** per consentire all'utente di eseguire in seguito una versione più recente dell'origine da seduti, è possibile chiamare [il metodo XR. Metodo InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

Se si sta creando un'esperienza su larga [scala,](../../../../design/coordinate-systems.md)è possibile visualizzare di recente l'origine del mondo di Unity nella posizione head corrente dell'utente chiamando **[XR. Metodo InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**