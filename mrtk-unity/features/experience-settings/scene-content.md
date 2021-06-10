---
title: Contenuto scena
description: Documentazione sul componente contenuto della scena di realtà mista
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647855"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="55cfd-104">Contenuto della scena di realtà mista</span><span class="sxs-lookup"><span data-stu-id="55cfd-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="55cfd-105">Quando si aggiunge MRTK a una scena, viene `MixedRealitySceneContent` creato un gameobject.</span><span class="sxs-lookup"><span data-stu-id="55cfd-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="55cfd-106">Questo oggetto funge da luogo dedicato in cui posizionare e creare un'istanza del contenuto di realtà mista per garantire la scalabilità appropriata in molte esperienze diverse.</span><span class="sxs-lookup"><span data-stu-id="55cfd-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="55cfd-107">Il gameobject ha un monobehavior **MixedRealitySceneContent** equivalente, che può essere configurato tramite il **parametro Alignment Type.**</span><span class="sxs-lookup"><span data-stu-id="55cfd-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="55cfd-108">Questo parametro può assumere i valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="55cfd-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="55cfd-109">*AlignWithExperienceScale:* allinea il contenuto  in base alla scala dell'esperienza di destinazione e **all'offset** del contenuto impostati nelle impostazioni dell'esperienza [del profilo di configurazione](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="55cfd-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="55cfd-110">*AlignWithHeadHeight:* allinea il contenuto alla posizione y della testa dell'utente, ovvero alla posizione della fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="55cfd-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Oggetto contenuto scena realtà mista creato nell'editor](../images/experience-settings/MixedRealitySceneContent.png)