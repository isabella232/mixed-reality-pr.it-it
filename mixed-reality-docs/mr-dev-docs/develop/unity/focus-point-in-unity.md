---
title: Punto focale in Unity
description: Informazioni su come ottimizzare manualmente la stabilità dell'ologramma in Unity impostando il punto di interesse per HoloLens e Windows Mixed Reality visori immersive.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, focus point, focus plane, stabilization plane, stabilization point, reprojection, LSR, depth buffer, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 91fba310cf86f145174512c4c1e23d69907d2f57f48f3fe1992b417eb283235f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203593"
---
# <a name="focus-point-in-unity"></a>Punto focale in Unity

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

Usare il [punto di](../platform-capabilities-and-apis/hologram-stability.md#reprojection) messa a HoloLens con un suggerimento su come stabilizzare al meglio gli ologrammi attualmente visualizzati.

Se si vuole impostare il punto di messa a fuoco in Unity, è necessario impostarlo per ogni fotogramma usando *HolographicSettings.SetFocusPointForFrame()*. Quando il punto di messa a fuoco non è impostato per un frame, viene usato il piano di stabilizzazione predefinito.

> [!NOTE]
> Per impostazione predefinita, per i nuovi progetti Unity è impostata l'opzione "Abilita condivisione buffer di profondità".  Con questa opzione, un'app Unity in esecuzione su un visore desktop immersivo o un HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 (RS4) o versione successiva invierà il buffer di profondità a Windows per ottimizzare automaticamente la stabilità dell'ologramma, senza che l'app specifica un punto di interesse:
> * In un visore desktop immersivo, ciò consentirà la riproiezione basata sulla profondità per pixel.
> * In un HoloLens l'aggiornamento Windows 10 aprile 2018 o versione successiva, verrà analizzato il buffer di profondità per scegliere automaticamente un piano di stabilizzazione ottimale.
>
> Entrambi gli approcci dovrebbero offrire una qualità dell'immagine ancora migliore senza il lavoro esplicito dell'app per selezionare un punto attivo per ogni fotogramma.  Si noti che se si specifica manualmente un punto di messa a fuoco, questo eseguirà l'override del comportamento automatico descritto in precedenza e in genere ridurrà la stabilità dell'ologramma.  In genere, è necessario specificare un punto di attivazione manuale solo quando l'app è in esecuzione in un HoloLens che non è ancora stato aggiornato all'aggiornamento Windows 10 aggiornamento di aprile 2018.

### <a name="example"></a>Esempio

Esistono molti modi per impostare il punto di messa a fuoco, come suggerito dagli overload disponibili nella funzione statica *SetFocusPointForFrame.* Di seguito è riportato un semplice esempio per impostare il piano di messa a fuoco sull'oggetto fornito per ogni fotogramma:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> Il semplice codice precedente può ridurre la stabilità dell'ologramma se l'oggetto con lo stato attivo termina dietro l'utente. È in genere consigliabile impostare **[Abilita condivisione buffer di](camera-in-unity.md#sharing-depth-buffers)** profondità anziché specificare manualmente un punto di attivazione.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui, è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [Perdita del tracciamento](tracking-loss-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Distribuire in HoloLens o Windows Mixed Reality visori immersive](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.

### <a name="see-also"></a>Vedere anche

* [Piano di stabilizzazione](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
