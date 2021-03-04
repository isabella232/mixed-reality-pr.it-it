---
title: UnityArCameraSettings
description: Documentazione per usare la fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, videocamera AR,
ms.openlocfilehash: 22483fcd23c43fa0a558642948459c07409bd648
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782923"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="f0339-104">Provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="f0339-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="f0339-105">Il provider di impostazioni della fotocamera AR Unity è un componente sperimentale MRTK che consente l'esecuzione di applicazioni di realtà miste in dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="f0339-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="f0339-106">Opzioni del provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="f0339-106">Unity AR camera settings provider options</span></span>

![Configurazione delle impostazioni della fotocamera AR Unity](../Images/CameraSystem/UnityArSettingsConfiguration.png)

<span data-ttu-id="f0339-108">Per una guida su come aggiungere il provider alla scena: [come configurare MRTK per iOS e Android](../CrossPlatform/UsingARFoundation.md)</span><span class="sxs-lookup"><span data-stu-id="f0339-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../CrossPlatform/UsingARFoundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="f0339-109">Impostazioni di rilevamento</span><span class="sxs-lookup"><span data-stu-id="f0339-109">Tracking settings</span></span>

<span data-ttu-id="f0339-110">Il provider di impostazioni della fotocamera AR Unity consente le opzioni di configurazione per la modalità di esecuzione del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f0339-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="f0339-111">Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera AR di Unity.</span><span class="sxs-lookup"><span data-stu-id="f0339-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="f0339-112">**Genera origine**</span><span class="sxs-lookup"><span data-stu-id="f0339-112">**Pose Source**</span></span>

<span data-ttu-id="f0339-113">L'origine della definizione definisce i tipi disponibili di pose di rilevamento di realtà aumentata.</span><span class="sxs-lookup"><span data-stu-id="f0339-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="f0339-114">In generale, questi valori vengono mappati a un componente del dispositivo in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f0339-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="f0339-115">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="f0339-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="f0339-116">Opzione</span><span class="sxs-lookup"><span data-stu-id="f0339-116">Option</span></span> | <span data-ttu-id="f0339-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f0339-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f0339-118">Center</span><span class="sxs-lookup"><span data-stu-id="f0339-118">Center</span></span> | <span data-ttu-id="f0339-119">Occhio centrale di un dispositivo montato a capo.</span><span class="sxs-lookup"><span data-stu-id="f0339-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="f0339-120">Fotocamera a colori</span><span class="sxs-lookup"><span data-stu-id="f0339-120">Color Camera</span></span> | <span data-ttu-id="f0339-121">Fotocamera a colori di un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="f0339-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="f0339-122">Head</span><span class="sxs-lookup"><span data-stu-id="f0339-122">Head</span></span> | <span data-ttu-id="f0339-123">Occhio a capo di un dispositivo montato in testa, spesso leggermente al di sopra dell'occhio centrale.</span><span class="sxs-lookup"><span data-stu-id="f0339-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="f0339-124">Occhio sinistro</span><span class="sxs-lookup"><span data-stu-id="f0339-124">Left Eye</span></span> | <span data-ttu-id="f0339-125">L'occhio sinistro di un dispositivo montato in testa.</span><span class="sxs-lookup"><span data-stu-id="f0339-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="f0339-126">Pose a sinistra</span><span class="sxs-lookup"><span data-stu-id="f0339-126">Left Pose</span></span> | <span data-ttu-id="f0339-127">Il controller della mano sinistra.</span><span class="sxs-lookup"><span data-stu-id="f0339-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="f0339-128">Occhio a destra</span><span class="sxs-lookup"><span data-stu-id="f0339-128">Right Eye</span></span> | <span data-ttu-id="f0339-129">Occhio destro di un dispositivo montato in testa.</span><span class="sxs-lookup"><span data-stu-id="f0339-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="f0339-130">Pose a destra</span><span class="sxs-lookup"><span data-stu-id="f0339-130">Right Pose</span></span> | <span data-ttu-id="f0339-131">Il controller della mano destra.</span><span class="sxs-lookup"><span data-stu-id="f0339-131">The right hand controller pose.</span></span> |

<span data-ttu-id="f0339-132">Il valore predefinito per l'origine della posa è la **fotocamera a colori**, per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.</span><span class="sxs-lookup"><span data-stu-id="f0339-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="f0339-133">**Tipo di rilevamento**</span><span class="sxs-lookup"><span data-stu-id="f0339-133">**Tracking Type**</span></span>

<span data-ttu-id="f0339-134">Il tipo di rilevamento definisce le porzioni della funzione che verranno utilizzate per il rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f0339-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="f0339-135">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="f0339-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="f0339-136">Opzione</span><span class="sxs-lookup"><span data-stu-id="f0339-136">Option</span></span> | <span data-ttu-id="f0339-137">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f0339-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f0339-138">Posizione</span><span class="sxs-lookup"><span data-stu-id="f0339-138">Position</span></span> | <span data-ttu-id="f0339-139">Posizione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f0339-139">The position of the device.</span></span> |
| <span data-ttu-id="f0339-140">Rotazione</span><span class="sxs-lookup"><span data-stu-id="f0339-140">Rotation</span></span> | <span data-ttu-id="f0339-141">Rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f0339-141">The rotation of the device.</span></span> |
| <span data-ttu-id="f0339-142">Rotazione e posizione</span><span class="sxs-lookup"><span data-stu-id="f0339-142">Rotation And Position</span></span> | <span data-ttu-id="f0339-143">Posizione e rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f0339-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="f0339-144">Il valore predefinito per il tipo di rilevamento è **rotazione e posizione**, per abilitare l'esperienza di rilevamento più avanzata.</span><span class="sxs-lookup"><span data-stu-id="f0339-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="f0339-145">**Tipo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="f0339-145">**Update Type**</span></span>

<span data-ttu-id="f0339-146">Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei frame, verranno campionati i dati di post.</span><span class="sxs-lookup"><span data-stu-id="f0339-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="f0339-147">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="f0339-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="f0339-148">Opzione</span><span class="sxs-lookup"><span data-stu-id="f0339-148">Option</span></span> | <span data-ttu-id="f0339-149">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f0339-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f0339-150">Prima del rendering</span><span class="sxs-lookup"><span data-stu-id="f0339-150">Before Render</span></span> | <span data-ttu-id="f0339-151">Appena prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="f0339-151">Just before rendering.</span></span> |
| <span data-ttu-id="f0339-152">Aggiorna</span><span class="sxs-lookup"><span data-stu-id="f0339-152">Update</span></span> | <span data-ttu-id="f0339-153">Durante la fase di aggiornamento del frame.</span><span class="sxs-lookup"><span data-stu-id="f0339-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="f0339-154">Aggiornare e prima del rendering</span><span class="sxs-lookup"><span data-stu-id="f0339-154">Update And Before Render</span></span> | <span data-ttu-id="f0339-155">Durante la fase di aggiornamento e immediatamente prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="f0339-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="f0339-156">Il valore predefinito per il tipo di rilevamento è **Update e before render** per abilitare la latenza di rilevamento più bassa.</span><span class="sxs-lookup"><span data-stu-id="f0339-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0339-157">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f0339-157">See also</span></span>

- [<span data-ttu-id="f0339-158">Panoramica del sistema di fotocamere</span><span class="sxs-lookup"><span data-stu-id="f0339-158">Camera System Overview</span></span>](CameraSystemOverview.md)
- [<span data-ttu-id="f0339-159">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f0339-159">Creating a Camera Settings Provider</span></span>](CreateSettingsProvider.md)
