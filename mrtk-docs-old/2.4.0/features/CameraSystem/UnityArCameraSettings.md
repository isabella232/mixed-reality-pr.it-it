---
title: UnityArCameraSettings
description: Documentazione per usare la fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, videocamera AR,
ms.openlocfilehash: b5547d800fcae78138554d5998b37738770ab16c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688211"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="a4234-104">Provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="a4234-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="a4234-105">Il provider di impostazioni della fotocamera AR Unity è un componente sperimentale MRTK che consente l'esecuzione di applicazioni di realtà miste in dispositivi Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="a4234-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="a4234-106">Opzioni del provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="a4234-106">Unity AR camera settings provider options</span></span>

![Configurazione delle impostazioni della fotocamera AR Unity](../Images/CameraSystem/UnityArSettingsConfiguration.png)

<span data-ttu-id="a4234-108">Per una guida su come aggiungere il provider alla scena: [come configurare MRTK per iOS e Android](../CrossPlatform/UsingARFoundation.md)</span><span class="sxs-lookup"><span data-stu-id="a4234-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../CrossPlatform/UsingARFoundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="a4234-109">Impostazioni di rilevamento</span><span class="sxs-lookup"><span data-stu-id="a4234-109">Tracking settings</span></span>

<span data-ttu-id="a4234-110">Il provider di impostazioni della fotocamera AR Unity consente le opzioni di configurazione per la modalità di esecuzione del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="a4234-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="a4234-111">Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera AR di Unity.</span><span class="sxs-lookup"><span data-stu-id="a4234-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="a4234-112">**Genera origine**</span><span class="sxs-lookup"><span data-stu-id="a4234-112">**Pose Source**</span></span>

<span data-ttu-id="a4234-113">L'origine della definizione definisce i tipi disponibili di pose di rilevamento di realtà aumentata.</span><span class="sxs-lookup"><span data-stu-id="a4234-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="a4234-114">In generale, questi valori vengono mappati a un componente del dispositivo in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a4234-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="a4234-115">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="a4234-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="a4234-116">Opzione</span><span class="sxs-lookup"><span data-stu-id="a4234-116">Option</span></span> | <span data-ttu-id="a4234-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a4234-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a4234-118">Center</span><span class="sxs-lookup"><span data-stu-id="a4234-118">Center</span></span> | <span data-ttu-id="a4234-119">Occhio centrale di un dispositivo montato a capo.</span><span class="sxs-lookup"><span data-stu-id="a4234-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="a4234-120">Fotocamera a colori</span><span class="sxs-lookup"><span data-stu-id="a4234-120">Color Camera</span></span> | <span data-ttu-id="a4234-121">Fotocamera a colori di un dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="a4234-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="a4234-122">Head</span><span class="sxs-lookup"><span data-stu-id="a4234-122">Head</span></span> | <span data-ttu-id="a4234-123">Occhio a capo di un dispositivo montato in testa, spesso leggermente al di sopra dell'occhio centrale.</span><span class="sxs-lookup"><span data-stu-id="a4234-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="a4234-124">Occhio sinistro</span><span class="sxs-lookup"><span data-stu-id="a4234-124">Left Eye</span></span> | <span data-ttu-id="a4234-125">L'occhio sinistro di un dispositivo montato in testa.</span><span class="sxs-lookup"><span data-stu-id="a4234-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="a4234-126">Pose a sinistra</span><span class="sxs-lookup"><span data-stu-id="a4234-126">Left Pose</span></span> | <span data-ttu-id="a4234-127">Il controller della mano sinistra.</span><span class="sxs-lookup"><span data-stu-id="a4234-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="a4234-128">Occhio a destra</span><span class="sxs-lookup"><span data-stu-id="a4234-128">Right Eye</span></span> | <span data-ttu-id="a4234-129">Occhio destro di un dispositivo montato in testa.</span><span class="sxs-lookup"><span data-stu-id="a4234-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="a4234-130">Pose a destra</span><span class="sxs-lookup"><span data-stu-id="a4234-130">Right Pose</span></span> | <span data-ttu-id="a4234-131">Il controller della mano destra.</span><span class="sxs-lookup"><span data-stu-id="a4234-131">The right hand controller pose.</span></span> |

<span data-ttu-id="a4234-132">Il valore predefinito per l'origine della posa è la **fotocamera a colori**, per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.</span><span class="sxs-lookup"><span data-stu-id="a4234-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="a4234-133">**Tipo di rilevamento**</span><span class="sxs-lookup"><span data-stu-id="a4234-133">**Tracking Type**</span></span>

<span data-ttu-id="a4234-134">Il tipo di rilevamento definisce le porzioni della funzione che verranno utilizzate per il rilevamento.</span><span class="sxs-lookup"><span data-stu-id="a4234-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="a4234-135">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="a4234-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="a4234-136">Opzione</span><span class="sxs-lookup"><span data-stu-id="a4234-136">Option</span></span> | <span data-ttu-id="a4234-137">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a4234-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a4234-138">Posizione</span><span class="sxs-lookup"><span data-stu-id="a4234-138">Position</span></span> | <span data-ttu-id="a4234-139">Posizione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4234-139">The position of the device.</span></span> |
| <span data-ttu-id="a4234-140">Rotazione</span><span class="sxs-lookup"><span data-stu-id="a4234-140">Rotation</span></span> | <span data-ttu-id="a4234-141">Rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4234-141">The rotation of the device.</span></span> |
| <span data-ttu-id="a4234-142">Rotazione e posizione</span><span class="sxs-lookup"><span data-stu-id="a4234-142">Rotation And Position</span></span> | <span data-ttu-id="a4234-143">Posizione e rotazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4234-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="a4234-144">Il valore predefinito per il tipo di rilevamento è **rotazione e posizione**, per abilitare l'esperienza di rilevamento più avanzata.</span><span class="sxs-lookup"><span data-stu-id="a4234-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="a4234-145">**Tipo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="a4234-145">**Update Type**</span></span>

<span data-ttu-id="a4234-146">Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei frame, verranno campionati i dati di post.</span><span class="sxs-lookup"><span data-stu-id="a4234-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="a4234-147">Le opzioni disponibili sono descritte nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="a4234-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="a4234-148">Opzione</span><span class="sxs-lookup"><span data-stu-id="a4234-148">Option</span></span> | <span data-ttu-id="a4234-149">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a4234-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a4234-150">Prima del rendering</span><span class="sxs-lookup"><span data-stu-id="a4234-150">Before Render</span></span> | <span data-ttu-id="a4234-151">Appena prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="a4234-151">Just before rendering.</span></span> |
| <span data-ttu-id="a4234-152">Aggiornamento</span><span class="sxs-lookup"><span data-stu-id="a4234-152">Update</span></span> | <span data-ttu-id="a4234-153">Durante la fase di aggiornamento del frame.</span><span class="sxs-lookup"><span data-stu-id="a4234-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="a4234-154">Aggiornare e prima del rendering</span><span class="sxs-lookup"><span data-stu-id="a4234-154">Update And Before Render</span></span> | <span data-ttu-id="a4234-155">Durante la fase di aggiornamento e immediatamente prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="a4234-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="a4234-156">Il valore predefinito per il tipo di rilevamento è **Update e before render** per abilitare la latenza di rilevamento più bassa.</span><span class="sxs-lookup"><span data-stu-id="a4234-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4234-157">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a4234-157">See also</span></span>

- [<span data-ttu-id="a4234-158">Panoramica del sistema di fotocamere</span><span class="sxs-lookup"><span data-stu-id="a4234-158">Camera System Overview</span></span>](CameraSystemOverview.md)
- [<span data-ttu-id="a4234-159">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="a4234-159">Creating a Camera Settings Provider</span></span>](CreateSettingsProvider.md)
