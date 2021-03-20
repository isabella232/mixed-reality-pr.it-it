---
title: InputProviders
description: Documentazione su diversi tipi di provider di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 56b182f81e2dd1277050b8b1b3f7a7d7434ac92a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683394"
---
# <a name="input-providers"></a><span data-ttu-id="37ac0-104">Provider di input</span><span class="sxs-lookup"><span data-stu-id="37ac0-104">Input providers</span></span>

<span data-ttu-id="37ac0-105">I provider di input sono registrati nel **profilo dei provider di servizi registrati**, disponibile nel componente del Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="37ac0-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Registerd Service">

<span data-ttu-id="37ac0-106">Questi sono i provider di input disponibili, insieme ai controller corrispondenti:</span><span class="sxs-lookup"><span data-stu-id="37ac0-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="37ac0-107">Provider di input</span><span class="sxs-lookup"><span data-stu-id="37ac0-107">Input Provider</span></span> | <span data-ttu-id="37ac0-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="37ac0-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="37ac0-109">Mano simulata</span><span class="sxs-lookup"><span data-stu-id="37ac0-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="37ac0-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="37ac0-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="37ac0-111">Generic OpenVR, vive Wand, vive Knuckles, Oculus touch, Oculus remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="37ac0-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="37ac0-112">Joystick generico</span><span class="sxs-lookup"><span data-stu-id="37ac0-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="37ac0-113">Controller tocco Unity</span><span class="sxs-lookup"><span data-stu-id="37ac0-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="37ac0-114">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="37ac0-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="37ac0-115">Mano articolata WMR, controller WMR, WMR GGV (sguardi, movimenti e voce)</span><span class="sxs-lookup"><span data-stu-id="37ac0-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="37ac0-116">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="37ac0-116">*None*</span></span> |

<span data-ttu-id="37ac0-117">I provider di dettatura e sintesi vocale non creano controller, generano direttamente eventi di input specifici.</span><span class="sxs-lookup"><span data-stu-id="37ac0-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="37ac0-118">I provider di input personalizzati possono essere creati implementando l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="37ac0-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="37ac0-119">Per ulteriori informazioni, vedere [creazione di un provider di dati di sistema di input](CreateDataProvider.md).</span><span class="sxs-lookup"><span data-stu-id="37ac0-119">For more information, please see [creating an input system data provider](CreateDataProvider.md).</span></span>
