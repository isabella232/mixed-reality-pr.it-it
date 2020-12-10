---
title: Punto focale in Unity
description: Ottimizzazione manuale della stabilità degli ologrammi in Unity impostando il punto di attivazione
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto focale, piano di messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, riproiezione, LSR, buffer di profondità, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: d2708dcf39f1d2c67ab1abf69f8330f9dd536ab0
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010272"
---
# <a name="focus-point-in-unity"></a>Punto focale in Unity

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

Usare il [punto di interesse](../platform-capabilities-and-apis/hologram-stability.md#reprojection) per fornire a HoloLens un suggerimento su come stabilizzare al meglio gli ologrammi attualmente in fase di visualizzazione.

Se si vuole impostare il punto di messa a fuoco in Unity, è necessario impostare ogni fotogramma usando *HolographicSettings. SetFocusPointForFrame ()*. Quando il punto di attivazione non è impostato per un frame, viene usato il piano di stabilizzazione predefinito.

> [!NOTE]
> Per impostazione predefinita, i nuovi progetti Unity hanno l'opzione "Abilita condivisione buffer di profondità" impostata.  Con questa opzione, un'app Unity in esecuzione in una cuffia desktop immersiva o un HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 (RS4) o versione successiva invierà il buffer di profondità a Windows per ottimizzare automaticamente la stabilità dell'ologramma, senza che l'app specifichi un punto di interesse:
> * In un auricolare desktop immersivo, verrà abilitata la riproiezione basata sulla profondità per pixel.
> * In una HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 o versione successiva, verrà analizzato il buffer di profondità per selezionare automaticamente un piano di stabilizzazione ottimale.
>
> Entrambi gli approcci dovrebbero fornire una qualità dell'immagine ancora migliore senza lavoro esplicito da parte dell'app per selezionare un punto di interesse per ogni frame.  Si noti che se si specifica un punto di interesse manualmente, che sostituisce il comportamento automatico descritto in precedenza, e in genere ridurrà la stabilità degli ologrammi.  In genere, è necessario specificare un punto di messa a fuoco manuale solo quando l'app è in esecuzione in un HoloLens che non è ancora stato aggiornato all'aggiornamento di Windows 10 aprile 2018.

### <a name="example"></a>Esempio

Esistono diversi modi per impostare il punto di interesse, come suggerito dagli overload disponibili nella funzione statica *SetFocusPointForFrame* . Di seguito è riportato un semplice esempio per impostare il piano di attivazione sull'oggetto fornito per ogni frame:

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
> Il semplice codice precedente può ridurre la stabilità dell'ologramma se l'oggetto con stato attivo termina dietro l'utente. È in genere consigliabile impostare **[Abilita condivisione buffer di profondità](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** anziché specificare manualmente un punto di interesse.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista. Da qui è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [Perdita del tracciamento](tracking-loss-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.

### <a name="see-also"></a>Vedere anche
* [Piano di stabilizzazione](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
