---
title: UnityArCameraSettings
description: Documentazione per l'uso della fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera AR,
ms.openlocfilehash: 15aacae4cb543a3a94660ef1ab057ad0febcb715
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850417"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="b8b3f-104">Provider di impostazioni della fotocamera AR unity</span><span class="sxs-lookup"><span data-stu-id="b8b3f-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="b8b3f-105">Il provider di impostazioni della fotocamera AR unity è un componente sperimentale di MRTK che consente l'esecuzione di applicazioni di realtà mista in dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="b8b3f-106">Opzioni del provider di impostazioni della fotocamera AR unity</span><span class="sxs-lookup"><span data-stu-id="b8b3f-106">Unity AR camera settings provider options</span></span>

![Configurazione delle impostazioni della fotocamera AR unity](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="b8b3f-108">Per una guida su come aggiungere il provider alla scena: [Come configurare MRTK per iOS e Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="b8b3f-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="b8b3f-109">Impostazioni di rilevamento</span><span class="sxs-lookup"><span data-stu-id="b8b3f-109">Tracking settings</span></span>

<span data-ttu-id="b8b3f-110">Il provider di impostazioni della fotocamera AR unity consente le opzioni di configurazione per la modalità di esecuzione del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="b8b3f-111">Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera AR unity.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="b8b3f-112">**Origine della posizione**</span><span class="sxs-lookup"><span data-stu-id="b8b3f-112">**Pose Source**</span></span>

<span data-ttu-id="b8b3f-113">L'origine della posizione definisce i tipi disponibili di posizioni di rilevamento della realtà aumentata.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="b8b3f-114">In generale, questi valori eseguono il mapping a un componente del dispositivo in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="b8b3f-115">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="b8b3f-116">Opzione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-116">Option</span></span> | <span data-ttu-id="b8b3f-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b8b3f-118">Center</span><span class="sxs-lookup"><span data-stu-id="b8b3f-118">Center</span></span> | <span data-ttu-id="b8b3f-119">L'occhio centrale di un dispositivo montato con la testa.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="b8b3f-120">Fotocamera a colori</span><span class="sxs-lookup"><span data-stu-id="b8b3f-120">Color Camera</span></span> | <span data-ttu-id="b8b3f-121">Fotocamera a colori di un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="b8b3f-122">Head</span><span class="sxs-lookup"><span data-stu-id="b8b3f-122">Head</span></span> | <span data-ttu-id="b8b3f-123">La testa di un dispositivo montato con la testa, spesso leggermente sopra l'occhio centrale.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="b8b3f-124">Occhio sinistro</span><span class="sxs-lookup"><span data-stu-id="b8b3f-124">Left Eye</span></span> | <span data-ttu-id="b8b3f-125">L'occhio sinistro di un dispositivo montato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="b8b3f-126">Pose a sinistra</span><span class="sxs-lookup"><span data-stu-id="b8b3f-126">Left Pose</span></span> | <span data-ttu-id="b8b3f-127">Posizione del controller a sinistra.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="b8b3f-128">Occhio destro</span><span class="sxs-lookup"><span data-stu-id="b8b3f-128">Right Eye</span></span> | <span data-ttu-id="b8b3f-129">L'occhio destro di un dispositivo montato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="b8b3f-130">Posizione a destra</span><span class="sxs-lookup"><span data-stu-id="b8b3f-130">Right Pose</span></span> | <span data-ttu-id="b8b3f-131">La posizione del controller destro.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-131">The right hand controller pose.</span></span> |

<span data-ttu-id="b8b3f-132">Il valore predefinito per l'origine della posizione è **Fotocamera** a colori , per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="b8b3f-133">**Tipo di rilevamento**</span><span class="sxs-lookup"><span data-stu-id="b8b3f-133">**Tracking Type**</span></span>

<span data-ttu-id="b8b3f-134">Il tipo di rilevamento definisce le parti della posizione che verranno usate per il rilevamento.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="b8b3f-135">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="b8b3f-136">Opzione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-136">Option</span></span> | <span data-ttu-id="b8b3f-137">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b8b3f-138">Posizione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-138">Position</span></span> | <span data-ttu-id="b8b3f-139">Posizione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-139">The position of the device.</span></span> |
| <span data-ttu-id="b8b3f-140">Rotazione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-140">Rotation</span></span> | <span data-ttu-id="b8b3f-141">Rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-141">The rotation of the device.</span></span> |
| <span data-ttu-id="b8b3f-142">Rotazione e posizione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-142">Rotation And Position</span></span> | <span data-ttu-id="b8b3f-143">Posizione e rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="b8b3f-144">Il valore predefinito per tipo di rilevamento è **Rotazione e posizione**, per abilitare l'esperienza di rilevamento più completa.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="b8b3f-145">**Tipo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="b8b3f-145">**Update Type**</span></span>

<span data-ttu-id="b8b3f-146">Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei frame, verranno campionati i dati di posizione.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="b8b3f-147">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="b8b3f-148">Opzione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-148">Option</span></span> | <span data-ttu-id="b8b3f-149">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b8b3f-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b8b3f-150">Prima del rendering</span><span class="sxs-lookup"><span data-stu-id="b8b3f-150">Before Render</span></span> | <span data-ttu-id="b8b3f-151">Subito prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-151">Just before rendering.</span></span> |
| <span data-ttu-id="b8b3f-152">Aggiornamento</span><span class="sxs-lookup"><span data-stu-id="b8b3f-152">Update</span></span> | <span data-ttu-id="b8b3f-153">Durante la fase di aggiornamento del frame.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="b8b3f-154">Aggiornamento e prima del rendering</span><span class="sxs-lookup"><span data-stu-id="b8b3f-154">Update And Before Render</span></span> | <span data-ttu-id="b8b3f-155">Durante la fase di aggiornamento e subito prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="b8b3f-156">Il valore predefinito per il tipo di rilevamento è **Aggiorna e prima del rendering** per abilitare la latenza di rilevamento più bassa.</span><span class="sxs-lookup"><span data-stu-id="b8b3f-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b3f-157">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b8b3f-157">See also</span></span>

- [<span data-ttu-id="b8b3f-158">Panoramica del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="b8b3f-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="b8b3f-159">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b8b3f-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
