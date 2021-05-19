---
title: Tipi di scena del sistema di scena
description: Documentazione sui diversi tipi di scena in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144575"
---
# <a name="scene-types"></a><span data-ttu-id="97036-104">Tipi di scena</span><span class="sxs-lookup"><span data-stu-id="97036-104">Scene types</span></span>

<span data-ttu-id="97036-105">Le scene sono state suddivise in tre tipi e ogni tipo ha una funzione diversa.</span><span class="sxs-lookup"><span data-stu-id="97036-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Sistema di scena nella gerarchia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="97036-107">Scene di contenuto</span><span class="sxs-lookup"><span data-stu-id="97036-107">Content scenes</span></span>

<span data-ttu-id="97036-108">Queste sono le scene con cui si è usati.</span><span class="sxs-lookup"><span data-stu-id="97036-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="97036-109">Qualsiasi tipo di contenuto può essere archiviato in essi e può essere caricato o scaricato in qualsiasi combinazione.</span><span class="sxs-lookup"><span data-stu-id="97036-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="97036-110">Le scene di contenuto sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="97036-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="97036-111">Tutte le scene incluse nella matrice del `Content Scenes` profilo possono essere caricate/scaricate dal servizio.</span><span class="sxs-lookup"><span data-stu-id="97036-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="97036-112">Scene di gestione</span><span class="sxs-lookup"><span data-stu-id="97036-112">Manager scenes</span></span>

<span data-ttu-id="97036-113">Una singola scena con un'istanza MixedRealityToolkit richiesta.</span><span class="sxs-lookup"><span data-stu-id="97036-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="97036-114">Questa scena verrà caricata per prima all'avvio e rimarrà caricata per tutta la durata dell'app.</span><span class="sxs-lookup"><span data-stu-id="97036-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="97036-115">La scena di gestione può ospitare anche altri oggetti che non devono mai essere distrutti.</span><span class="sxs-lookup"><span data-stu-id="97036-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="97036-116">Questa è l'alternativa preferita a DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="97036-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="97036-117">Per abilitare questa funzionalità, controllare `Use Manager Scene` il profilo e trascinare un oggetto scena nel `Manager Scene` campo .</span><span class="sxs-lookup"><span data-stu-id="97036-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="97036-118">Scene di illuminazione</span><span class="sxs-lookup"><span data-stu-id="97036-118">Lighting scenes</span></span>

<span data-ttu-id="97036-119">Set di scene che archiviano informazioni sull'illuminazione e oggetti di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="97036-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="97036-120">Solo uno può essere caricato alla volta e le relative impostazioni possono essere combinate durante i carichi per transizioni di illuminazione fluide.</span><span class="sxs-lookup"><span data-stu-id="97036-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="97036-121">Le impostazioni di illuminazione di Unity, ad esempio luce ambientale, skybox e così via, possono essere complesse da gestire quando si usa il caricamento additivo perché sono collegate a singole scene e il comportamento di override non è semplice.</span><span class="sxs-lookup"><span data-stu-id="97036-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="97036-122">In pratica questo può causare confusione quando gli asset vengono creati in condizioni di illuminazione che non si ottengono in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="97036-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Impostazioni di illuminazione del sistema della scena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="97036-124">Il sistema scene usa scene di illuminazione per garantire che queste impostazioni rimangano coerenti indipendentemente dalle scene caricate o attive, sia in modalità di modifica che in modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="97036-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="97036-125">Per abilitare questa funzionalità, `Use Lighting Scene` archiviare il profilo e popolare la `Lighting Scenes` matrice.</span><span class="sxs-lookup"><span data-stu-id="97036-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="97036-126">Impostazioni di illuminazione memorizzate nella cache</span><span class="sxs-lookup"><span data-stu-id="97036-126">Cached lighting settings</span></span>

<span data-ttu-id="97036-127">Il profilo archivia copie memorizzate nella cache delle impostazioni di illuminazione mantenute nelle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="97036-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="97036-128">Se queste impostazioni cambiano nelle scene di illuminazione, sarà necessario aggiornare la cache per assicurarsi che l'illuminazione venga visualizzata come previsto in modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="97036-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="97036-129">Il profilo visualizza un avviso quando sospetta che le impostazioni memorizzate nella cache non siano aggiornate.</span><span class="sxs-lookup"><span data-stu-id="97036-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="97036-130">Facendo `Update Cached Lighting Settings` clic su vengono caricate tutte le scene di illuminazione, ne vengono estratte le impostazioni e quindi archiviate nel profilo.</span><span class="sxs-lookup"><span data-stu-id="97036-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Impostazioni di illuminazione memorizzate nella cache del sistema della scena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="97036-132">Comportamento dell'editor</span><span class="sxs-lookup"><span data-stu-id="97036-132">Editor behavior</span></span>

<span data-ttu-id="97036-133">Uno dei vantaggi dell'uso delle scene di illuminazione è sapere che il contenuto viene acceso correttamente durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="97036-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="97036-134">A questo scopo, il servizio scene manterà sempre una scena di illuminazione caricata e copierà le impostazioni di illuminazione della scena nella scena attiva corrente.\*</span><span class="sxs-lookup"><span data-stu-id="97036-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="97036-135">È possibile modificare la scena di illuminazione caricata aprendo il controllo del servizio del [sistema della scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="97036-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="97036-136">In modalità di modifica è possibile eseguire immediatamente la transizione tra scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="97036-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="97036-137">In modalità di riproduzione è possibile visualizzare in anteprima le transizioni.</span><span class="sxs-lookup"><span data-stu-id="97036-137">In play mode, you can preview transitions.</span></span>

![Controllo sistema scena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="97036-139">\**Nota: in genere la scena attiva determina le impostazioni di illuminazione nell'editor. Tuttavia, si sceglie di non usare questa funzionalità per applicare le impostazioni di illuminazione, perché la scena attiva è anche la posizione degli oggetti appena creati per impostazione predefinita e le scene di illuminazione possono contenere solo componenti di illuminazione. Le impostazioni della scena di illuminazione corrente vengono invece copiate automaticamente nelle impostazioni della scena attiva. Tenere presente che ciò comporta la sovrascritta delle impostazioni di illuminazione della scena di contenuto.*</span><span class="sxs-lookup"><span data-stu-id="97036-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
