---
title: Servizio di fisica manuale
description: documentazione per usare il servizio di estensione fisica manuale in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176255"
---
# <a name="hand-physics-service"></a>Servizio di fisica manuale

![Servizio di estensione fisica della mano](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con le mani articolate.

## <a name="enabling-the-extension"></a>Abilitazione dell'estensione

Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider. Fare `Register a new Service Provider` clic per aggiungere una nuova configurazione. Nel campo tipo di componente selezionare HandPhysicsService. Nel campo Profilo di configurazione selezionare il profilo di fisica della mano predefinito incluso nell'estensione.

## <a name="profile-options"></a>Opzioni del profilo

### <a name="hand-physics-layer"></a>Livello di fisica della mano

Controlla il livello a cui verranno associati i giunzioni delle mani di cui è stata creata un'istanza.

Anche se per impostazione predefinita il servizio è il livello "predefinito" (0), è consigliabile usare un livello separato per gli oggetti di fisica manuale. In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycast non accurati.

### <a name="finger-tip-kinematic-body-prefab"></a>Prefab del corpo cinematico con punta del dito

Controlla il prefab di cui viene creata un'istanza a punta del dito. Per il funzionamento previsto del servizio, il prefab richiede:

- Componente rigidbody con isKinematic abilitato
- Un collisore
- Componente `JointKinematicBody`

### <a name="use-palm-kinematic-body"></a>Usare il corpo kinematico del palmo

Controlla se il servizio tenterà di creare un'istanza di un prefab sull'giunzione del palmo.

### <a name="palm-kinematic-body-prefab"></a>Prefab del corpo kinematico di mano

Quando `UsePalmKinematicBody` è abilitato, questo è il prefab di cui verrà creata un'istanza. Proprio come `FingerTipKinematicBodyPrefab` , questo prefab richiede:

- Componente rigidbody con isKinematic abilitato
- Un collisore
- Componente `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Come usare il servizio

Una volta abilitata, usare la proprietà di qualsiasi collisore per ricevere gli eventi di collisione da `IsTrigger` tutte le 10 cifre (e palmi se sono abilitati).
