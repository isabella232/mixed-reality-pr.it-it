---
title: Profiles
description: Profili di documentazione in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profili,
ms.openlocfilehash: 322f2b800f62f42fa3d5e60dc6142b106c8a396a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782414"
---
# <a name="profiles"></a><span data-ttu-id="88973-104">Profiles</span><span class="sxs-lookup"><span data-stu-id="88973-104">Profiles</span></span>

<span data-ttu-id="88973-105">Uno dei modi principali in cui è configurato il MRTK consiste nell'usare i molti profili disponibili nel pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="88973-105">One of the main ways that the MRTK is configured is through the many profiles available in the foundation package.</span></span> <span data-ttu-id="88973-106">L' [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) oggetto principale in una scena avrà il profilo attivo, che è essenzialmente un ScriptableObject.</span><span class="sxs-lookup"><span data-stu-id="88973-106">The main [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object in a scene will have the active profile, which is essentially a ScriptableObject.</span></span> <span data-ttu-id="88973-107">Il profilo di configurazione di MRTK di livello superiore contiene i dati di sottoprofilo per ogni core dei sistemi principali principali, ognuno dei quali è progettato per configurare il comportamento dei sottosistemi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="88973-107">The top level MRTK Configuration Profile contains sub-profile data for each core of the primary core systems, each of which are designed to configure the behavior of their corresponding sub-systems.</span></span> <span data-ttu-id="88973-108">Inoltre, questi sottoprofili sono anche oggetti gestibili tramite script e possono quindi contenere riferimenti ad altri oggetti profilo a un livello inferiore.</span><span class="sxs-lookup"><span data-stu-id="88973-108">Furthermore, these sub-profiles are also Scriptable Objects and thus can contain references to other profile objects one level below them.</span></span> <span data-ttu-id="88973-109">Esiste essenzialmente un intero albero di profili connessi che costituiscono le informazioni di configurazione per l'inizializzazione dei sottosistemi e delle funzionalità di MRTK.</span><span class="sxs-lookup"><span data-stu-id="88973-109">There is essentially an entire tree of connected profiles that make up the configuration information for how to initialize the MRTK sub-systems and features.</span></span>

<span data-ttu-id="88973-110">Il comportamento del sistema di input, ad esempio, è regolato da un profilo di sistema di input, ad esempio `DefaultMixedRealityInputSystemProfile` (assets/MRTK/SDK/Profiles).</span><span class="sxs-lookup"><span data-stu-id="88973-110">For example, the Input system's behavior is governed by an input system profile, for example the `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).</span></span> <span data-ttu-id="88973-111">È consigliabile modificare sempre le risorse del profilo ScriptableObject tramite il controllo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="88973-111">It's highly recommended to always modify the profile ScriptableObject assets via the in-editor inspector.</span></span>

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<span data-ttu-id="88973-112"><sup>Controllo profilo</sup></span><span class="sxs-lookup"><span data-stu-id="88973-112"><sup>Profile Inspector</sup></span></span>

> [!NOTE]
> <span data-ttu-id="88973-113">Sebbene sia previsto che i profili possano essere scambiati in fase di esecuzione, [attualmente non funziona](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)</span><span class="sxs-lookup"><span data-stu-id="88973-113">While it is intended that profiles can be swapped out at runtime, this [currently does not work](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)</span></span>

## <a name="default-profile"></a><span data-ttu-id="88973-114">Profilo predefinito</span><span class="sxs-lookup"><span data-stu-id="88973-114">Default profile</span></span>

<span data-ttu-id="88973-115">MRTK fornisce un set di profili predefiniti che coprono la maggior parte delle piattaforme e degli scenari supportati da MRTK.</span><span class="sxs-lookup"><span data-stu-id="88973-115">The MRTK provides a set of default profiles which cover most platforms and scenarios that the MRTK supports.</span></span> <span data-ttu-id="88973-116">Ad esempio, quando si seleziona `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles), sarà possibile provare scenari in VR (OpenVR, WMR) e HoloLens (1 e 2).</span><span class="sxs-lookup"><span data-stu-id="88973-116">For example, when you select the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) you will be able to try out scenarios on VR (OpenVR, WMR) and HoloLens (1 and 2).</span></span>

<span data-ttu-id="88973-117">Si noti che poiché si tratta di un profilo di utilizzo generale, non è ottimizzato per un particolare caso di utilizzo.</span><span class="sxs-lookup"><span data-stu-id="88973-117">Note that because this is a general use profile, it's not optimized for any particular use case.</span></span> <span data-ttu-id="88973-118">Se si desidera disporre di impostazioni più efficienti/specifiche che siano migliori su altre piattaforme, vedere gli altri profili seguenti, che sono leggermente modificati per migliorare le rispettive piattaforme.</span><span class="sxs-lookup"><span data-stu-id="88973-118">If you want to have more performant/specific settings that are better on other platforms, see the other profiles below, which are slightly tweaked to be better on their respective platforms.</span></span>

## <a name="hololens-2-profile"></a><span data-ttu-id="88973-119">Profilo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="88973-119">HoloLens 2 profile</span></span>

<span data-ttu-id="88973-120">MRTK fornisce anche un profilo predefinito ottimizzato per la distribuzione e il testing in HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (assets/MRTK/SDK/Profiles/HoloLens2).</span><span class="sxs-lookup"><span data-stu-id="88973-120">The MRTK also provides a default profile that is optimized for deployment and testing on the HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).</span></span>

<span data-ttu-id="88973-121">Quando viene richiesto di scegliere un profilo per l'oggetto MixedRealityToolkit, usare questo profilo anziché il profilo selezionato predefinito.</span><span class="sxs-lookup"><span data-stu-id="88973-121">When prompted to choose a profile for the MixedRealityToolkit object, use this profile instead of the default selected profile.</span></span>

<span data-ttu-id="88973-122">Le differenze principali tra il profilo HoloLens2 e il profilo predefinito sono:</span><span class="sxs-lookup"><span data-stu-id="88973-122">The key differences between the HoloLens2 profile and the Default Profile are:</span></span>

<span data-ttu-id="88973-123">**Disabilitato** Funzionalità</span><span class="sxs-lookup"><span data-stu-id="88973-123">**Disabled** Features:</span></span>

- [<span data-ttu-id="88973-124">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="88973-124">Boundary System</span></span>](../boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="88973-125">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="88973-125">Teleport System</span></span>](../teleport-system/teleport-system.md)
- [<span data-ttu-id="88973-126">Sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="88973-126">Spatial Awareness System</span></span>](../spatial-awareness/spatial-awareness-getting-started.md)
- <span data-ttu-id="88973-127">[Visualizzazione Mesh mano](../input/hand-tracking.md) (a causa dell'overhead delle prestazioni)</span><span class="sxs-lookup"><span data-stu-id="88973-127">[Hand mesh visualization](../input/hand-tracking.md) (due to performance overhead)</span></span>

<span data-ttu-id="88973-128">**Abilitato** Sistemi</span><span class="sxs-lookup"><span data-stu-id="88973-128">**Enabled** Systems:</span></span>

- <span data-ttu-id="88973-129">Il [provider di rilevamento degli occhi](../input/eye-tracking/eye-tracking-main.md)</span><span class="sxs-lookup"><span data-stu-id="88973-129">The [Eye Tracking provider](../input/eye-tracking/eye-tracking-main.md)</span></span>
- <span data-ttu-id="88973-130">Simulazione dell'input oculare</span><span class="sxs-lookup"><span data-stu-id="88973-130">Eye input simulation</span></span>

<span data-ttu-id="88973-131">Le impostazioni del profilo della fotocamera sono impostate in modo da corrispondere alla qualità dell'editor e alla qualità del lettore.</span><span class="sxs-lookup"><span data-stu-id="88973-131">Camera profile settings are set to match so that the editor quality and player quality are the same.</span></span> <span data-ttu-id="88973-132">Si tratta di un profilo diverso dal profilo della fotocamera predefinito, in cui le visualizzazioni opache sono impostate su una qualità superiore.</span><span class="sxs-lookup"><span data-stu-id="88973-132">This is different from the default camera profile where Opaque displays are set to a higher quality.</span></span> <span data-ttu-id="88973-133">Questa modifica significa che la qualità nell'Editor sarà inferiore, che corrisponderà più a quanto verrà visualizzato nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88973-133">This change means that in-editor quality will be lower, which will more closely match what will be rendered on the device.</span></span>
  
> [!NOTE]
> <span data-ttu-id="88973-134">Il sistema di riconoscimento spaziale è disattivato per impostazione predefinita in base ai commenti e suggerimenti dei client. si tratta di una visualizzazione interessante per vedere inizialmente, ma in genere è disattivata per evitare la distrazione visiva e l'ulteriore impatto sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="88973-134">The Spatial Awareness system is turned off by default based on client feedback - it is an interesting visualization to see initially but is typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span> <span data-ttu-id="88973-135">Il sistema può essere riabilitato seguendo le istruzioni riportate [qui](../spatial-awareness/spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="88973-135">The system can be re-enabled by following the [instructions here](../spatial-awareness/spatial-awareness-getting-started.md).</span></span>
