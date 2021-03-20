---
title: HandPhysicsServiceOverview
description: documentazione per usare il servizio di estensione della fisica della mano in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 94489eb16466a23ca45d36c8e08ddff65edcd723
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692678"
---
# <a name="hand-physics-extension-service"></a>Servizio di estensione fisica della mano

Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.

## <a name="enabling-the-extension"></a>Abilitazione dell'estensione

Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider. Fare clic `Register a new Service Provider` per aggiungere una nuova configurazione. Nel campo tipo di componente selezionare HandPhysicsService. Nel campo profilo di configurazione selezionare il profilo fisico della mano predefinito incluso nell'estensione.

## <a name="profile-options"></a>Opzioni profilo

### <a name="hand-physics-layer"></a>Livello di fisica della mano

Controlla il livello a cui verranno indirizzati i giunti a cui è stata creata un'istanza.

Mentre per il servizio viene usato per impostazione predefinita il livello "default" (0), è consigliabile usare un livello separato per gli oggetti fisici della mano. In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.

### <a name="finger-tip-kinematic-body-prefab"></a>Prefabbricato del corpo cinematica del finger tip

Controlla la creazione di un'istanza del prefabbricato a portata di mano. Affinché il servizio funzioni come previsto, il prefabbricato richiede:

- Un componente rigidbody con l'abilitazione della funzionalità cinematica
- Un Collider
- Componente `JointKinematicBody`

### <a name="use-palm-kinematic-body"></a>USA corpo cinematica Palm

Controlla se il servizio tenterà di creare un'istanza di una prefabbricata sul giunto di Palm.

### <a name="palm-kinematic-body-prefab"></a>Prefabbricato del corpo di Palm cinematico

Quando `UsePalmKinematicBody` è abilitato, si tratta della prefabbricata di cui verrà creata un'istanza. Analogamente a `FingerTipKinematicBodyPrefab` questa prefabbricata è necessario:

- Un componente rigidbody con l'abilitazione della funzionalità cinematica
- Un Collider
- Componente `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Come usare il servizio

Una volta abilitata, usare la proprietà di qualsiasi Collider `IsTrigger` per ricevere eventi di collisione da tutte le 10 cifre (e Palms se sono abilitate).
