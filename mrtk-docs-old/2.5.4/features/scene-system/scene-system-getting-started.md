---
title: SceneSystemGettingStarted
description: Pagina di destinazione per il sistema di scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e43bb401ea3c3175b5cb3805e7edf00d361eb4b6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685124"
---
# <a name="scene-system-overview"></a><span data-ttu-id="bc5eb-104">Panoramica del sistema di scena</span><span class="sxs-lookup"><span data-stu-id="bc5eb-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="bc5eb-105">Quando usare il sistema di scena</span><span class="sxs-lookup"><span data-stu-id="bc5eb-105">When to use the scene system</span></span>

<span data-ttu-id="bc5eb-106">Se il progetto è costituito da un'unica scena, probabilmente il sistema della scena non è necessario.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="bc5eb-107">È particolarmente utile quando si verificano una o più delle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="bc5eb-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="bc5eb-108">Il progetto include più scene.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="bc5eb-109">Si viene usati per il caricamento di una singola scena, ma non è come il modo in cui viene distrutta l'istanza di MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="bc5eb-110">Si vuole un modo semplice per caricare additivamente più scene per costruire la propria esperienza.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="bc5eb-111">Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="bc5eb-112">Si vuole rendere l'illuminazione coerente e prevedibile in tutte le scene.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="bc5eb-113">Risorse di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="bc5eb-113">Scene System Resources</span></span>

<span data-ttu-id="bc5eb-114">Per impostazione predefinita, il sistema di scena usa una coppia di oggetti scene (scena DefaultManagerScene e DefaultLighting).</span><span class="sxs-lookup"><span data-stu-id="bc5eb-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="bc5eb-115">Se una di queste scene non può essere individuata, verrà visualizzato un messaggio nella finestra di controllo profilo del sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Messaggio risorse predefinite](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="bc5eb-117">! Si noti Se il progetto usa la gestione personalizzata e le scene di illuminazione, questo messaggio può essere ignorato.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="bc5eb-118">Le sezioni seguenti descrivono ora per risolvere questo messaggio, in base al metodo usato per importare il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="bc5eb-119">Gestione pacchetti Unity (UPM)</span><span class="sxs-lookup"><span data-stu-id="bc5eb-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="bc5eb-120">Nei pacchetti UPM del Toolkit per realtà mista le risorse di sistema della scena sono assemblate come esempio.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="bc5eb-121">Dato che i pacchetti UPM non sono modificabili, Unity non è in grado di aprire il file della scena necessario, a meno che non vengano importati in modo esplicito nel progetto.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="bc5eb-122">Per eseguire l'importazione, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="bc5eb-122">To import use the following steps:</span></span>

- <span data-ttu-id="bc5eb-123">Selezionare   >  **Gestione pacchetti** Windows</span><span class="sxs-lookup"><span data-stu-id="bc5eb-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="bc5eb-124">Selezionare **mixed reality Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="bc5eb-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="bc5eb-125">Individuare **le risorse di sistema della scena** nella sezione degli **esempi**</span><span class="sxs-lookup"><span data-stu-id="bc5eb-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importa le risorse di sistema della scena](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="bc5eb-127">Selezionare **Importa**</span><span class="sxs-lookup"><span data-stu-id="bc5eb-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="bc5eb-128">File di asset (con estensione file unitypackage Tools)</span><span class="sxs-lookup"><span data-stu-id="bc5eb-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="bc5eb-129">Se la cartella SceneSystemResources è stata eliminata o è stata deselezionata durante l'importazione, è possibile recuperarla attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="bc5eb-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="bc5eb-130">Seleziona **Asset**  >  **Importa** pacchetto  >  **personalizzato** pacchetto</span><span class="sxs-lookup"><span data-stu-id="bc5eb-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="bc5eb-131">Aprire il pacchetto **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="bc5eb-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="bc5eb-132">Verificare che siano selezionate le opzioni **Services/SceneSystem/SceneSystemResources** e All Child</span><span class="sxs-lookup"><span data-stu-id="bc5eb-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Reimportare le risorse di sistema della scena](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="bc5eb-134">Selezionare **Importa**</span><span class="sxs-lookup"><span data-stu-id="bc5eb-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="bc5eb-135">Come usare il sistema di scena</span><span class="sxs-lookup"><span data-stu-id="bc5eb-135">How to use the scene system</span></span>

- [<span data-ttu-id="bc5eb-136">Tipi di scena</span><span class="sxs-lookup"><span data-stu-id="bc5eb-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="bc5eb-137">Caricamento della scena del contenuto</span><span class="sxs-lookup"><span data-stu-id="bc5eb-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="bc5eb-138">Monitoraggio del caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="bc5eb-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="bc5eb-139">Caricamento della scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="bc5eb-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="bc5eb-140">Impostazioni editor</span><span class="sxs-lookup"><span data-stu-id="bc5eb-140">Editor settings</span></span>

<span data-ttu-id="bc5eb-141">Per impostazione predefinita, il sistema di scena impone diversi comportamenti nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="bc5eb-142">Se uno di questi comportamenti è elevato, è possibile disabilitarli nella sezione **Impostazioni editor** del profilo di sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="bc5eb-143">`Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="bc5eb-144">Disabilitare questa impostazione se si desidera il controllo totale sulle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="bc5eb-145">`Editor Enforce Scene Order:` Se true, il servizio assicurerà che la scena del Manager venga visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="bc5eb-146">Disabilitare questa proprietà se si desidera il controllo totale sulla gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="bc5eb-147">`Editor Manage Loaded Scenes:` Se true, il servizio assicurerà che il responsabile, il contenuto e le scene di illuminazione siano sempre caricati.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="bc5eb-148">Disabilitare se si desidera il controllo totale sulle scene caricate nell'editor.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="bc5eb-149">`Editor Enforce Lighting Scene Types:` Se true, il servizio garantirà che solo i componenti correlati all'illuminazione definiti in `PermittedLightingSceneComponentTypes` siano consentiti nelle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="bc5eb-150">Disabilitare se si desidera il controllo totale sul contenuto delle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="bc5eb-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Impostazioni dell'editor di sistema della scena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
