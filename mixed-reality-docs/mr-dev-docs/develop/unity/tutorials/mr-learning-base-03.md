---
title: Esercitazioni introduttive - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questa esercitazione illustra come configurare i profili di Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, consapevolezza spaziale
ms.localizationpriority: high
ms.openlocfilehash: 3b44ba6c4eac3cf7b42d15c8fb19d42676b10a4a
ms.sourcegitcommit: 5017f309827c1d20df4ce656d105a1a49ba7942c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106011140"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="10f92-105">3. Configurazione dei profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="10f92-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="10f92-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="10f92-106">Overview</span></span>

<span data-ttu-id="10f92-107">In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="10f92-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="10f92-108">I <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">profili di MRTK</a> sono profili annidati in una struttura ad albero che costituiscono le informazioni di configurazione per la modalità di inizializzazione dei sistemi e delle funzionalità di MRTK.</span><span class="sxs-lookup"><span data-stu-id="10f92-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="10f92-109">Il profilo di primo livello, quello di configurazione, contiene profili annidati per ognuno dei sistemi core principali.</span><span class="sxs-lookup"><span data-stu-id="10f92-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="10f92-110">Ogni profilo annidato è progettato per la configurazione del comportamento del sistema corrispondente.</span><span class="sxs-lookup"><span data-stu-id="10f92-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="10f92-111">Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="10f92-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="10f92-112">Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="10f92-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="10f92-113">Come rilevato quando è stato distribuito il progetto in HoloLens 2 nell'[esercitazione precedente](mr-learning-base-02.md#congratulations), la mesh <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> è una raccolta di mesh che rappresentano la geometria dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="10f92-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="10f92-114">Si tratta di una visualizzazione utile nella fase iniziale, ma che in genere è disabilitata per evitare distrazioni a livello visivo e l'impatto aggiuntivo che produrrebbe sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="10f92-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="10f92-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="10f92-115">Objectives</span></span>

* <span data-ttu-id="10f92-116">Imparare a personalizzare e configurare i profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="10f92-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="10f92-117">Nascondere il mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="10f92-118">Modifica delle opzioni di visualizzazione di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="10f92-119">Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="10f92-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="10f92-120">Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="10f92-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="10f92-121">Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="10f92-122">Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="10f92-123">Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="10f92-124">Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="10f92-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="10f92-125">per impostazione predefinita, i profili di MRTK non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="10f92-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="10f92-126">Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati.</span><span class="sxs-lookup"><span data-stu-id="10f92-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="10f92-127">Sono disponibili diversi livelli annidati di profili.</span><span class="sxs-lookup"><span data-stu-id="10f92-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="10f92-128">È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.</span><span class="sxs-lookup"><span data-stu-id="10f92-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="10f92-129">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="10f92-129">Congratulations</span></span>

<span data-ttu-id="10f92-130">In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.</span><span class="sxs-lookup"><span data-stu-id="10f92-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10f92-131">Esercitazione successiva: 4. Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="10f92-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)