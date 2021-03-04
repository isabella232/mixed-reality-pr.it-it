---
title: SceneSystemSceneTypes
description: Documentazione su diversi tipi di scena in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: af56ceaca2960512c9f2a7e0b2b405bad9306621
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781592"
---
# <a name="scene-types"></a><span data-ttu-id="bd4ed-104">Tipi di scena</span><span class="sxs-lookup"><span data-stu-id="bd4ed-104">Scene types</span></span>

<span data-ttu-id="bd4ed-105">Le scene sono state divise in tre tipi e ogni tipo ha una funzione diversa.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Sistema di scena nella gerarchia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="bd4ed-107">Scene di contenuto</span><span class="sxs-lookup"><span data-stu-id="bd4ed-107">Content scenes</span></span>

<span data-ttu-id="bd4ed-108">Queste sono le scene che vengono usate per gestire.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="bd4ed-109">Tutti i tipi di contenuto possono essere archiviati in essi e possono essere caricati o scaricati in qualsiasi combinazione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="bd4ed-110">Le scene di contenuto sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="bd4ed-111">Tutte le scene incluse nell'array del profilo `Content Scenes` possono essere caricate o scaricate dal servizio.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="bd4ed-112">Scene di gestione</span><span class="sxs-lookup"><span data-stu-id="bd4ed-112">Manager scenes</span></span>

<span data-ttu-id="bd4ed-113">Una singola scena con un'istanza di MixedRealityToolkit obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="bd4ed-114">Questa scena verrà caricata prima all'avvio e rimarrà caricata per la durata dell'app.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="bd4ed-115">La scena del responsabile può inoltre ospitare altri oggetti che non devono mai essere eliminati definitivamente.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="bd4ed-116">Si tratta dell'alternativa preferita a DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="bd4ed-117">Per abilitare questa funzionalità, archiviare il `Use Manager Scene` profilo e trascinare un oggetto scena nel `Manager Scene` campo.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="bd4ed-118">Scene di illuminazione</span><span class="sxs-lookup"><span data-stu-id="bd4ed-118">Lighting scenes</span></span>

<span data-ttu-id="bd4ed-119">Set di scene che archivia le informazioni sull'illuminazione e gli oggetti di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="bd4ed-120">È possibile caricare solo un oggetto alla volta e le relative impostazioni possono essere combinate durante i caricamenti per le transizioni con illuminazione uniforme.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="bd4ed-121">Le impostazioni di illuminazione di Unity, luce ambientale, Skybox e così via, possono essere difficili da gestire quando si usa il caricamento di additivi perché sono legate a singole scene e il comportamento di sostituzione non è semplice.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="bd4ed-122">In pratica questo può causare confusione quando le risorse vengono create in condizioni di illuminazione che non vengono ottenute in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Impostazioni di illuminazione del sistema di scena 1](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="bd4ed-124">Il sistema di scena USA scene di illuminazione per assicurarsi che queste impostazioni rimangano coerenti indipendentemente dalle scene caricate o attive, sia in modalità di modifica che in modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="bd4ed-125">Per abilitare questa funzionalità, archiviare il `Use Lighting Scene` profilo e popolare la `Lighting Scenes` matrice.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="bd4ed-126">Impostazioni di illuminazione memorizzate nella cache</span><span class="sxs-lookup"><span data-stu-id="bd4ed-126">Cached lighting settings</span></span>

<span data-ttu-id="bd4ed-127">Il profilo archivia le copie memorizzate nella cache delle impostazioni di illuminazione mantenute nelle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="bd4ed-128">Se queste impostazioni cambiano nelle scene di illuminazione, sarà necessario aggiornare la cache per assicurarsi che l'illuminazione venga visualizzata come previsto in modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="bd4ed-129">Nel profilo verrà visualizzato un avviso quando si sospetta che le impostazioni memorizzate nella cache non siano aggiornate.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="bd4ed-130">Se si fa clic su `Update Cached Lighting Settings` , si caricherà ogni scena di illuminazione, si estraggono le impostazioni e quindi le si archivia nel profilo.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Impostazioni di illuminazione del sistema di scena 2](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="bd4ed-132">Comportamento dell'editor</span><span class="sxs-lookup"><span data-stu-id="bd4ed-132">Editor behavior</span></span>

<span data-ttu-id="bd4ed-133">Un vantaggio dell'uso di scene di illuminazione è la consapevolezza che i contenuti sono illuminati correttamente durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="bd4ed-134">A questo scopo, il servizio di scena manterrà una scena di illuminazione sempre caricata e copierà le impostazioni di illuminazione della scena nella scena attiva corrente.\*</span><span class="sxs-lookup"><span data-stu-id="bd4ed-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="bd4ed-135">È possibile modificare la scena di illuminazione che viene caricata aprendo il [controllo del servizio](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities) del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities)</span></span> <span data-ttu-id="bd4ed-136">In modalità di modifica è possibile eseguire istantaneamente la transizione tra le scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="bd4ed-137">In modalità di riproduzione è possibile visualizzare in anteprima le transizioni.</span><span class="sxs-lookup"><span data-stu-id="bd4ed-137">In play mode, you can preview transitions.</span></span>

![Controllo di sistema della scena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="bd4ed-139">\**Nota: in genere la scena attiva determina le impostazioni di illuminazione nell'editor. Tuttavia, si sceglie di non usare questa funzionalità per applicare le impostazioni di illuminazione, perché la scena attiva è anche la posizione in cui vengono inseriti gli oggetti appena creati per impostazione predefinita e gli scenari di illuminazione possono contenere solo componenti di illuminazione. Al contrario, le impostazioni correnti della scena di illuminazione vengono automaticamente copiate nelle impostazioni della scena attiva. Tenere presente che questa operazione comporterà la sovrascrittura delle impostazioni di illuminazione della scena del contenuto.*</span><span class="sxs-lookup"><span data-stu-id="bd4ed-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
