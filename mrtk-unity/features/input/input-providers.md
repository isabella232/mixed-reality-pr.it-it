---
title: Provider di input
description: Documentazione sui diversi tipi di provider di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145266"
---
# <a name="input-providers"></a><span data-ttu-id="2bd66-104">Provider di input</span><span class="sxs-lookup"><span data-stu-id="2bd66-104">Input providers</span></span>

<span data-ttu-id="2bd66-105">I provider di input vengono registrati nel profilo dei provider di servizi **registrati,** disponibile nel componente Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="2bd66-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="2bd66-106">Di seguito sono disponibili i provider di input predefiniti, insieme ai controller corrispondenti:</span><span class="sxs-lookup"><span data-stu-id="2bd66-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="2bd66-107">Input Provider</span><span class="sxs-lookup"><span data-stu-id="2bd66-107">Input Provider</span></span> | <span data-ttu-id="2bd66-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="2bd66-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="2bd66-109">Mano simulata</span><span class="sxs-lookup"><span data-stu-id="2bd66-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="2bd66-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="2bd66-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="2bd66-111">Generic OpenVR, Vive Wand, ViveUckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="2bd66-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="2bd66-112">Azzarre generico</span><span class="sxs-lookup"><span data-stu-id="2bd66-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="2bd66-113">Unity Touch Controller</span><span class="sxs-lookup"><span data-stu-id="2bd66-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="2bd66-114">*Nessuna*</span><span class="sxs-lookup"><span data-stu-id="2bd66-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="2bd66-115">Mano articolata WMR, controller WMR, GGV WMR (sguardo fisso, movimento e voce) mano</span><span class="sxs-lookup"><span data-stu-id="2bd66-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="2bd66-116">*Nessuna*</span><span class="sxs-lookup"><span data-stu-id="2bd66-116">*None*</span></span> |

<span data-ttu-id="2bd66-117">I provider di dettatura e riconoscimento vocale non creano controller, ma generano direttamente i propri eventi di input specializzati.</span><span class="sxs-lookup"><span data-stu-id="2bd66-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="2bd66-118">È possibile creare provider di input personalizzati implementando [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="2bd66-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="2bd66-119">Per altre informazioni, vedere Creazione [di un provider di dati di sistema di input.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="2bd66-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
