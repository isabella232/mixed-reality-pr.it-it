---
title: Sistema di scena Attività iniziali
description: Pagina di destinazione per il sistema di scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144303"
---
# <a name="scene-system-overview"></a><span data-ttu-id="c6629-104">Panoramica del sistema di scena</span><span class="sxs-lookup"><span data-stu-id="c6629-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="c6629-105">Quando usare il sistema di scena</span><span class="sxs-lookup"><span data-stu-id="c6629-105">When to use the scene system</span></span>

<span data-ttu-id="c6629-106">Se il progetto è costituito da una singola scena, il sistema di scena probabilmente non è necessario.</span><span class="sxs-lookup"><span data-stu-id="c6629-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="c6629-107">È particolarmente utile quando si verificano una o più delle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6629-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="c6629-108">Il progetto include più scene.</span><span class="sxs-lookup"><span data-stu-id="c6629-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="c6629-109">Si è usati per il caricamento di una singola scena, ma non è possibile eliminare l'istanza MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="c6629-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="c6629-110">Si vuole un modo semplice per caricare in modo additivo più scene per costruire l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="c6629-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="c6629-111">Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="c6629-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="c6629-112">Si vuole mantenere l'illuminazione coerente e prevedibile in tutte le scene.</span><span class="sxs-lookup"><span data-stu-id="c6629-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="c6629-113">Risorse di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="c6629-113">Scene System Resources</span></span>

<span data-ttu-id="c6629-114">Per impostazione predefinita, scene system usa una coppia di oggetti scena (DefaultManagerScene e DefaultLighting scena).</span><span class="sxs-lookup"><span data-stu-id="c6629-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="c6629-115">Se non è possibile trovare una di queste scene, verrà visualizzato un messaggio nel controllo del profilo del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="c6629-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Messaggio delle risorse predefinite](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="c6629-117">! [Nota] Se il progetto usa scene di gestione e illuminazione personalizzate, questo messaggio può essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="c6629-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="c6629-118">Le sezioni seguenti descrivono ora come risolvere questo messaggio, in base al metodo usato per importare Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c6629-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="c6629-119">Unity Gestione pacchetti (UPM)</span><span class="sxs-lookup"><span data-stu-id="c6629-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="c6629-120">Nei pacchetti UPM di Mixed Reality Toolkit le risorse di sistema della scena vengono in pacchetto come esempio.</span><span class="sxs-lookup"><span data-stu-id="c6629-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="c6629-121">Poiché i pacchetti UPM non sono modificabili, Unity non è in grado di aprire il file della scena necessario a meno che non vengano importati in modo esplicito nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c6629-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="c6629-122">Per importare, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="c6629-122">To import use the following steps:</span></span>

- <span data-ttu-id="c6629-123">Selezionare **Finestra**  >  **Gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="c6629-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="c6629-124">Selezionare **Mixed Reality Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="c6629-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="c6629-125">Individuare **le risorse di sistema della** scena nella **sezione** Esempi</span><span class="sxs-lookup"><span data-stu-id="c6629-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importare le risorse di sistema della scena](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="c6629-127">Selezionare **Importa**</span><span class="sxs-lookup"><span data-stu-id="c6629-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="c6629-128">File di asset (con estensione unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c6629-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="c6629-129">Se la cartella SceneSystemResources è stata eliminata o è stata deselezionata durante l'importazione, è possibile recuperarla seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="c6629-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="c6629-130">Selezionare **Assets** Import Package Custom Package  >  **(Importa pacchetto**  >  **personalizzato)**</span><span class="sxs-lookup"><span data-stu-id="c6629-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="c6629-131">Aprire il **pacchetto Microsoft.MixedReality.Toolkit.Foundation**</span><span class="sxs-lookup"><span data-stu-id="c6629-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="c6629-132">Assicurarsi che **Services/SceneSystem/SceneSystemResources** e tutte le opzioni figlio siano selezionate</span><span class="sxs-lookup"><span data-stu-id="c6629-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Reimportare le risorse di sistema della scena](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="c6629-134">Selezionare **Importa**</span><span class="sxs-lookup"><span data-stu-id="c6629-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="c6629-135">Come usare il sistema della scena</span><span class="sxs-lookup"><span data-stu-id="c6629-135">How to use the scene system</span></span>

- [<span data-ttu-id="c6629-136">Tipi di scena</span><span class="sxs-lookup"><span data-stu-id="c6629-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="c6629-137">Caricamento della scena di contenuto</span><span class="sxs-lookup"><span data-stu-id="c6629-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="c6629-138">Monitoraggio del caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="c6629-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="c6629-139">Caricamento della scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="c6629-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="c6629-140">Impostazioni dell'editor</span><span class="sxs-lookup"><span data-stu-id="c6629-140">Editor settings</span></span>

<span data-ttu-id="c6629-141">Per impostazione predefinita, scene system applica diversi comportamenti nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="c6629-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="c6629-142">Se si trova uno di questi comportamenti con la mano pesante, questi possono essere disabilitati nella sezione **Impostazioni editor** del profilo del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="c6629-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="c6629-143">`Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto.</span><span class="sxs-lookup"><span data-stu-id="c6629-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="c6629-144">Disabilitare questa opzione se si vuole il controllo totale sulle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="c6629-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="c6629-145">`Editor Enforce Scene Order:` Se true, il servizio garantisce che la scena di gestione sia visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto.</span><span class="sxs-lookup"><span data-stu-id="c6629-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="c6629-146">Disabilitare questa opzione se si vuole il controllo totale sulla gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="c6629-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="c6629-147">`Editor Manage Loaded Scenes:` Se true, il servizio garantisce che il gestore, il contenuto e le scene di illuminazione siano sempre caricati.</span><span class="sxs-lookup"><span data-stu-id="c6629-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="c6629-148">Disabilitare se si vuole il controllo totale sulle scene caricate nell'editor.</span><span class="sxs-lookup"><span data-stu-id="c6629-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="c6629-149">`Editor Enforce Lighting Scene Types:` Se true, il servizio garantisce che solo i componenti correlati all'illuminazione definiti in siano consentiti `PermittedLightingSceneComponentTypes` nelle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="c6629-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="c6629-150">Disabilitare se si vuole il controllo totale sul contenuto delle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="c6629-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Impostazioni dell'editor del sistema di scena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
