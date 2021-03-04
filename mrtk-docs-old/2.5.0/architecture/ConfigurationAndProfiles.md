---
title: Configurazione e profili
description: Modifica dei profili in MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profilo MRTK
ms.openlocfilehash: 3c2c76e60fd6f8ad8b09ea5e4f6bea6bde78b132
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783757"
---
# <a name="configuration-and-profiles"></a><span data-ttu-id="1a890-104">Configurazione e profili</span><span class="sxs-lookup"><span data-stu-id="1a890-104">Configuration and profiles</span></span>

<span data-ttu-id="1a890-105">Non tutti i singoli consumer di MRTK vorranno comportarsi nello stesso modo, ad alcuni desideri che la mesh spaziale venga eseguita nei dispositivi AR che la supportano.</span><span class="sxs-lookup"><span data-stu-id="1a890-105">Not every single consumer of the MRTK will want it to behave the same way - some will want to have the spatial mesh running when on AR devices that support it.</span></span> <span data-ttu-id="1a890-106">In alcuni casi potrebbe essere necessario visualizzare la visualizzazione diagnostica in qualsiasi momento e in alcuni casi può essere utile solo quando l'utente dice un comando Voice.</span><span class="sxs-lookup"><span data-stu-id="1a890-106">Some may want the diagnostic visualization on all the time, and some may only want it on when the user says a voice command.</span></span>

<span data-ttu-id="1a890-107">Il MRTK deve essere configurabile per supportare un'ampia gamma di tali requisiti e usa un concetto denominato "Profiles" a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="1a890-107">The MRTK needs to be configurable in order to support a wide range of those requirements, and it uses a concept called 'profiles' to accomplish this.</span></span>

## <a name="what-is-a-profile"></a><span data-ttu-id="1a890-108">Che cos'è un profilo?</span><span class="sxs-lookup"><span data-stu-id="1a890-108">What is a profile?</span></span>

<span data-ttu-id="1a890-109">I profili archiviano le impostazioni di configurazione per i servizi.</span><span class="sxs-lookup"><span data-stu-id="1a890-109">Profiles store configuration settings for services.</span></span> <span data-ttu-id="1a890-110">Vengono usati per controllare quali servizi vengono eseguiti e come si comportano durante l'esecuzione di tali servizi.</span><span class="sxs-lookup"><span data-stu-id="1a890-110">You use them to control which services are run and how those services behave while running.</span></span> <span data-ttu-id="1a890-111">Sono archiviati come asset [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1a890-111">They're stored as [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets in your project.</span></span> <span data-ttu-id="1a890-112">È possibile visualizzare e modificare un profilo selezionandola nella finestra del progetto.</span><span class="sxs-lookup"><span data-stu-id="1a890-112">You can view and edit a profile by selecting it in your project window.</span></span>

<span data-ttu-id="1a890-113">Ad esempio, il MRTK ha un servizio della fotocamera, che applicherà proprietà diverse alla fotocamera principale, a seconda che lo schermo sia o meno trasparente (come nel caso di un HoloLens) o opaco (come nel caso di un auricolare VR).</span><span class="sxs-lookup"><span data-stu-id="1a890-113">For example, the MRTK has a camera service, which will apply different properties to the main camera, depending on whether or not the display is transparent (like in the case of a HoloLens) or opaque (like in the case of a VR headset).</span></span> <span data-ttu-id="1a890-114">Al servizio della fotocamera viene assegnato un [profilo della fotocamera](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs), che contiene le diverse impostazioni trasparenti e opache.</span><span class="sxs-lookup"><span data-stu-id="1a890-114">The camera service is given a [camera profile](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs), which contains those different transparent vs. opaque settings.</span></span>

<span data-ttu-id="1a890-115">Un esempio di profilo più complesso è il [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs).</span><span class="sxs-lookup"><span data-stu-id="1a890-115">An example of a more complex profile is the the [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs).</span></span>
<span data-ttu-id="1a890-116">Alcune delle proprietà di tale profilo, ad esempio le entità MixedRealityInputDataProviderConfiguration, controllano gli oggetti di cui verrà creata un'istanza in fase di esecuzione. questo è il modo in cui il sistema di input sa come creare sottosistemi di input OpenVR, WMR e Unity.</span><span class="sxs-lookup"><span data-stu-id="1a890-116">Some of the properties on that profile (such as the MixedRealityInputDataProviderConfiguration entities) control the objects that will be instantiated at runtime - this is how the input system knows how to create OpenVR, WMR and Unity input subsystems.</span></span> <span data-ttu-id="1a890-117">Questo profilo non è solo un set di proprietà che configura se una particolare funzionalità secondaria di input è abilitata o disabilitata, ma è anche un meccanismo di inserimento che MRTK userà per "nuove" altre classi in fase di esecuzione, ad esempio il profilo di sistema di input contiene un elenco di "provider di dati di input" con informazioni sul tipo serializzato. questi oggetti vengono creati dal sistema di input in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1a890-117">This profile is not just a set of properties that configures if a particular input sub-feature is enabled or disabled - it's also an injection mechanism that the MRTK will use to "new" other classes at runtime (for example, the input system profile contains a list of 'Input Data Providers' which has serialized type information - these objects are instantiated by the input system at runtime)</span></span>

<span data-ttu-id="1a890-118">Le configurazioni del profilo sono inizialmente disattivate perché sono configurate con i profili predefiniti di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a890-118">Profile configurations are initially greyed out because they're set up with MRTK's default profiles.</span></span>
<span data-ttu-id="1a890-119">Possono essere modificati solo dopo la clonazione per assicurarsi che i profili personalizzati non vadano perduti dopo un aggiornamento della versione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a890-119">They can only be modified after cloning to ensure that customized profiles won't be lost after a MRTK version update.</span></span>

## <a name="modifying-profiles"></a><span data-ttu-id="1a890-120">Modifica di profili</span><span class="sxs-lookup"><span data-stu-id="1a890-120">Modifying profiles</span></span>

<span data-ttu-id="1a890-121">Sebbene i profili possano essere modificati singolarmente (passando all'asset serializzato di ScriptableObject), sono generalmente accessibili tramite il controllo MRTK dell'oggetto scena MixedRealityToolkit radice.</span><span class="sxs-lookup"><span data-stu-id="1a890-121">While profiles can be individually modified (by going to the serialized asset of the ScriptableObject), they are generally accessed through the MRTK inspector of the root MixedRealityToolkit scene object.</span></span>

![Profilo](../features/Images/Profiles/input_profile.png)

<span data-ttu-id="1a890-123">L'immagine precedente Mostra il volume delle impostazioni. si noti che ogni opzione a sinistra mostrerà la configurazione per il servizio corrispondente.</span><span class="sxs-lookup"><span data-stu-id="1a890-123">The picture above shows the sheer volume of settings - note that each option on the left will show the configuration for its corresponding service.</span></span>

### <a name="camera"></a><span data-ttu-id="1a890-124">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="1a890-124">Camera</span></span>

<span data-ttu-id="1a890-125">Contiene le impostazioni del tipo per visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1a890-125">Contains per-display type settings.</span></span> <span data-ttu-id="1a890-126">Usato per applicare diversi livelli di impostazioni di qualità, clip e rendering in base al tipo di visualizzazione in cui viene eseguita l'applicazione (ad esempio, AR vs VR).</span><span class="sxs-lookup"><span data-stu-id="1a890-126">Used to apply different levels of quality, clip, and rendering settings based on the type of display that the application is run on (i.e. AR vs VR).</span></span>

### <a name="input"></a><span data-ttu-id="1a890-127">Input</span><span class="sxs-lookup"><span data-stu-id="1a890-127">Input</span></span>

<span data-ttu-id="1a890-128">Profilo più grande del sottosistema più complesso del MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a890-128">The largest profile for the most complex subsystem of the MRTK.</span></span> <span data-ttu-id="1a890-129">I vari sottosistemi di input verranno trattati nella documentazione del [sistema di input](InputSystem/Terminology.md) .</span><span class="sxs-lookup"><span data-stu-id="1a890-129">The various subsystems of input will be covered in the [Input System](InputSystem/Terminology.md) documentation itself.</span></span>

### <a name="teleport"></a><span data-ttu-id="1a890-130">Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="1a890-130">Teleport</span></span>

<span data-ttu-id="1a890-131">Questo profilo controlla il funzionamento del sistema di teleportation, che è principalmente un concetto VR.</span><span class="sxs-lookup"><span data-stu-id="1a890-131">This profile controls how the teleportation system works, which is primarily a VR concept.</span></span>

### <a name="spatial-mapping"></a><span data-ttu-id="1a890-132">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="1a890-132">Spatial mapping</span></span>

<span data-ttu-id="1a890-133">Questo profilo controlla il funzionamento del sistema Mesh spaziale (ad esempio, questo sistema è responsabile dell'avvio del sistema che eseguirà il rendering delle mesh spaziali in un dispositivo AR).</span><span class="sxs-lookup"><span data-stu-id="1a890-133">This profile controls how the spatial mesh system works (i.e. this system is responsible for starting the system that will render the spatial meshes on an AR device).</span></span> <span data-ttu-id="1a890-134">Principalmente un concetto AR.</span><span class="sxs-lookup"><span data-stu-id="1a890-134">Primarily an AR concept.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="1a890-135">Diagnostica</span><span class="sxs-lookup"><span data-stu-id="1a890-135">Diagnostics</span></span>

<span data-ttu-id="1a890-136">Consente di controllare lo strumento prestazioni visive che mostra un contatore di framerate, insieme all'utilizzo di memoria di base.</span><span class="sxs-lookup"><span data-stu-id="1a890-136">This controls the visual performance tool that shows a framerate counter, along with basic memory utilization.</span></span>

### <a name="scene-system"></a><span data-ttu-id="1a890-137">Sistema di scena</span><span class="sxs-lookup"><span data-stu-id="1a890-137">Scene system</span></span>

<span data-ttu-id="1a890-138">Questo controlla un sistema attualmente non abilitato per impostazione predefinita progettato per semplificare l'uso di scenari multiscena.</span><span class="sxs-lookup"><span data-stu-id="1a890-138">This controls a currently not-enabled-by-default system that is designed to make multi-scene scenarios easier to work with.</span></span>

### <a name="extensions"></a><span data-ttu-id="1a890-139">Estensioni</span><span class="sxs-lookup"><span data-stu-id="1a890-139">Extensions</span></span>

<span data-ttu-id="1a890-140">Questo profilo vuoto per impostazione predefinita è il punto di estensione in cui i consumer possono scrivere e quindi inserire i propri oggetti di cui verrà creata un'istanza ed eseguiti dal runtime di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a890-140">This empty-by-default profile is the extension point where consumers can write and then plug in their own objects that will be instantiated and run by the MRTK runtime.</span></span>

### <a name="editor"></a><span data-ttu-id="1a890-141">Editor</span><span class="sxs-lookup"><span data-stu-id="1a890-141">Editor</span></span>

<span data-ttu-id="1a890-142">Contiene le impostazioni generali per i comportamenti solo dell'editor di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1a890-142">Contains general settings for editor-only behaviors of the MRTK.</span></span>
