---
title: Note sulla versione del plug-in OpenXR di Realtà mista
description: Rimanere aggiornati sulle note sulla versione più recenti e sugli aggiornamenti al plug-in OpenXR di Realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394647"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="541f8-104">Note sulla versione del plug-in OpenXR di Realtà mista</span><span class="sxs-lookup"><span data-stu-id="541f8-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="541f8-105">1.0.0 - Versione corrente</span><span class="sxs-lookup"><span data-stu-id="541f8-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="541f8-106">Correzione di un bug per cui un oggetto XRAnchorSubsystem viene sempre avviato all'avvio dell'app indipendentemente dalla versione di ARAnchorManager presente.</span><span class="sxs-lookup"><span data-stu-id="541f8-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="541f8-107">Correzione di un bug per cui la modalità di nuovaproiezione non funzionava correttamente.</span><span class="sxs-lookup"><span data-stu-id="541f8-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="541f8-108">1.0.0-preview.2 - 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="541f8-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="541f8-109">Dipende dal plug-in OpenXR 1.2.2 di Unity.</span><span class="sxs-lookup"><span data-stu-id="541f8-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="541f8-110">Modifica delle funzionalità di Holographic Remoting in in singoli gruppi di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="541f8-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="541f8-111">Correzione di un bug per cui "Applica HoloLens 2 impostazioni del progetto" modifica lo spazio colore del progetto.</span><span class="sxs-lookup"><span data-stu-id="541f8-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="541f8-112">Questa operazione non è più necessaria dopo il plug-in Unity OpenXR 1.2.0.</span><span class="sxs-lookup"><span data-stu-id="541f8-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="541f8-113">Correzione di un bug per cui un dispositivo di input viene connesso senza disconnessione dopo la sospensione e la ripresa dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="541f8-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="541f8-114">Aggiunta del supporto per il rilevamento di plug-in e stati di rilevamento correnti tramite ARSession.</span><span class="sxs-lookup"><span data-stu-id="541f8-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="541f8-115">Correzione di un bug per cui il prefab ARFoundation "AR Default Plane" non era visibile.</span><span class="sxs-lookup"><span data-stu-id="541f8-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="541f8-116">1.0.0-preview.1 - 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="541f8-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="541f8-117">Supporta le estensioni MSFT di comprensione della scena OpenXR anziché le estensioni di anteprima.</span><span class="sxs-lookup"><span data-stu-id="541f8-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="541f8-118">Il rilevamento del piano HoloLens 2 non richiede più versioni di anteprima dei runtime OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="541f8-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="541f8-119">0.9.5 - 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="541f8-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="541f8-120">Dipende dal plug-in OpenXR 1.2.0 di Unity</span><span class="sxs-lookup"><span data-stu-id="541f8-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="541f8-121">Adattato alla nuova interfaccia utente della funzionalità (in OpenXR Plugin 1.2.0) per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="541f8-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="541f8-122">Correzione di un bug per cui il provider di fotocamere localizzate non annullava correttamente la registrazione.</span><span class="sxs-lookup"><span data-stu-id="541f8-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="541f8-123">Pulizia di alcuni utilizzi aggiuntivi di [Preserve].</span><span class="sxs-lookup"><span data-stu-id="541f8-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="541f8-124">Aggiornare il nome "HP Reverb G2 Controller (OpenXR)" nell'interfaccia utente del sistema di input.</span><span class="sxs-lookup"><span data-stu-id="541f8-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="541f8-125">0.9.4 - 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="541f8-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="541f8-126">Dipende dal plug-in OpenXR 1.2.0 di Unity.</span><span class="sxs-lookup"><span data-stu-id="541f8-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="541f8-127">Aggiunta della nuova API C# per ottenere il modello glTF del controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="541f8-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="541f8-128">Aggiunta di una nuova API C# per ottenere le configurazioni di visualizzazione abilitate e impostare le impostazioni di nuova progetto.</span><span class="sxs-lookup"><span data-stu-id="541f8-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="541f8-129">Aggiunta di una nuova API C# per impostare impostazioni aggiuntive per il calcolo delle mesh con XRMeshSubsystem.</span><span class="sxs-lookup"><span data-stu-id="541f8-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="541f8-130">Aggiunta della nuova API C# per configurare e sottoscrivere gli eventi di riconoscimento dei movimenti.</span><span class="sxs-lookup"><span data-stu-id="541f8-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="541f8-131">Aggiunta della finestra di dialogo >comunicazione remota di XR->Editor di Windows.</span><span class="sxs-lookup"><span data-stu-id="541f8-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="541f8-132">Aggiunta del supporto ARM per le applicazioni UWP HoloLens.</span><span class="sxs-lookup"><span data-stu-id="541f8-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="541f8-133">0.9.3 - 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="541f8-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="541f8-134">Correzione di un bug per cui la connessione remota holographic non è affidabile</span><span class="sxs-lookup"><span data-stu-id="541f8-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="541f8-135">Correzione di un bug per cui le prestazioni di rendering vr sono sotto-ottimali dopo l'aggiornamento al plug-in OpenXR 1.1.1 di Unity.</span><span class="sxs-lookup"><span data-stu-id="541f8-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="541f8-136">0.9.2 - 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="541f8-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="541f8-137">Il rilevamento del piano HoloLens 2 nella versione del plug-in 0.9.1 funzionerà con la versione 105 del runtime di anteprima di Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="541f8-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="541f8-138">Il rilevamento del piano HoloLens 2 nella versione del plug-in 0.9.2 funzionerà con la versione 106 del runtime di anteprima di Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="541f8-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="541f8-139">Sono stati rimossi alcuni callback inutilizzati da InputProvider per impedire che chiamate come XRInputSubsystem.\* GetTrackingOriginMode (che non sono gestite dal sistema di input) restituiranno esito positivo con valori fuorvianti.</span><span class="sxs-lookup"><span data-stu-id="541f8-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="541f8-140">Suddividere la versione deprecata di XRAnchorStore nel proprio file per evitare l'avviso della console unity.</span><span class="sxs-lookup"><span data-stu-id="541f8-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="541f8-141">0.9.1 - 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="541f8-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="541f8-142">Dipende dal plug-in OpenXR 1.1.1 di Unity.</span><span class="sxs-lookup"><span data-stu-id="541f8-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="541f8-143">Aggiunta del supporto per l'applicazione Holographic Remoting per la piattaforma UWP.</span><span class="sxs-lookup"><span data-stu-id="541f8-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="541f8-144">Correzione di UnityException in cui XRAnchorStore tentava di ottenere un'istanza delle impostazioni all'esterno del thread principale.</span><span class="sxs-lookup"><span data-stu-id="541f8-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="541f8-145">0.9.0 - 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="541f8-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="541f8-146">Aggiunta del supporto per il mapping spaziale tramite XRMeshSubsystem e ARMeshManager.</span><span class="sxs-lookup"><span data-stu-id="541f8-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="541f8-147">Aggiunta di una nuova API C# per ottenere handle OpenXR per supportare altri pacchetti Unity che utilizzano estensioni OpenXR.</span><span class="sxs-lookup"><span data-stu-id="541f8-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="541f8-148">Aggiunta di una nuova API C# per l'interoperabilità con le API Windows.Perception per supportare altri pacchetti Unity che utilizzano le API WinRT perception.</span><span class="sxs-lookup"><span data-stu-id="541f8-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="541f8-149">Sono stati rimossi i profili di interazione dalle funzionalità Windows Mixed Reality set di funzionalità, in modo che gli sviluppatori possano scegliere i controller del movimento con cui hanno testato.</span><span class="sxs-lookup"><span data-stu-id="541f8-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="541f8-150">Aggiunta del validator della funzionalità di comunicazione remota dell'editor Holographic per consentire agli utenti di configurare correttamente la comunicazione remota dell'editor.</span><span class="sxs-lookup"><span data-stu-id="541f8-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="541f8-151">Correzione di un bug per cui l'editor di Unity si arresta in modo anomalo quando si esce dalla modalità remota dell'editor Holographic dopo un errore di connessione.</span><span class="sxs-lookup"><span data-stu-id="541f8-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="541f8-152">Correzione di un bug per cui trame alfa non premoltimulate comportano prestazioni non ottimali in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="541f8-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="541f8-153">Correzione di un bug per cui il tracciamento delle mani non si trovava correttamente quando l'origine della scena era a livello del piano.</span><span class="sxs-lookup"><span data-stu-id="541f8-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="541f8-154">Correzione di un bug per cui il tracciamento della mesh manuale scompare dopo l'uscita e il caricamento di una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="541f8-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="541f8-155">Correzione di un bug per cui il provider di fotocamere localizzate non ha eseguito correttamente la pulizia.</span><span class="sxs-lookup"><span data-stu-id="541f8-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="541f8-156">Lo spazio dei nomi dell'API XRAnchorStore è stato modificato in Microsoft.MixedReality.OpenXR.</span><span class="sxs-lookup"><span data-stu-id="541f8-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>