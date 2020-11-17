---
title: Punto focale in Unity
description: Ottimizzazione manuale della stabilità degli ologrammi in Unity impostando il punto di attivazione
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto focale, piano di messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, riproiezione, LSR, buffer di profondità, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 48c0d26e89124b9dbfc1d108354fb6e751e51783
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678690"
---
# <a name="focus-point-in-unity"></a>Punto focale in Unity

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

Il [punto di interesse](../platform-capabilities-and-apis/hologram-stability.md#reprojection) può essere impostato in modo da fornire a HoloLens un suggerimento su come eseguire al meglio la stabilizzazione sugli ologrammi attualmente in fase di visualizzazione.

Se si vuole impostare il punto di messa a fuoco in Unity, è necessario impostare ogni fotogramma usando *HolographicSettings. SetFocusPointForFrame ()*. Se il punto di attivazione non è impostato per un frame, verrà utilizzato il piano di stabilizzazione predefinito.

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

Si noti che il codice precedente può finire a ridurre la stabilità dell'ologramma se l'oggetto con stato attivo termina dietro l'utente.  Questo è il motivo per cui in genere è necessario impostare "Abilita condivisione buffer di profondità" anziché specificare manualmente un punto di interesse.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista. Da qui è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [Perdita del tracciamento](tracking-loss-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.

### <a name="see-also"></a>Vedere anche
* [Piano di stabilizzazione](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
