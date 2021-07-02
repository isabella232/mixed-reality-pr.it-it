---
title: Provider di input
description: Documentazione sui diversi tipi di provider di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176756"
---
# <a name="input-providers"></a><span data-ttu-id="43305-104">Provider di input</span><span class="sxs-lookup"><span data-stu-id="43305-104">Input providers</span></span>

<span data-ttu-id="43305-105">I provider di input vengono registrati nel **profilo provider di servizi registrati,** disponibile nel componente Toolkit realtà mista:</span><span class="sxs-lookup"><span data-stu-id="43305-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="43305-106">Di seguito sono disponibili i provider di input predefiniti, insieme ai controller corrispondenti:</span><span class="sxs-lookup"><span data-stu-id="43305-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="43305-107">Input Provider</span><span class="sxs-lookup"><span data-stu-id="43305-107">Input Provider</span></span> | <span data-ttu-id="43305-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="43305-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="43305-109">Mano simulata</span><span class="sxs-lookup"><span data-stu-id="43305-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="43305-110">Mouse</span><span class="sxs-lookup"><span data-stu-id="43305-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="43305-111">Generic OpenVR, Vive Wand, ViveUckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="43305-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="43305-112">GenericStick</span><span class="sxs-lookup"><span data-stu-id="43305-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="43305-113">Unity Touch Controller</span><span class="sxs-lookup"><span data-stu-id="43305-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="43305-114">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="43305-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="43305-115">Mano articolata WMR, controller WMR, GGV WMR (sguardo fisso, movimento e voce) mano</span><span class="sxs-lookup"><span data-stu-id="43305-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="43305-116">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="43305-116">*None*</span></span> |

<span data-ttu-id="43305-117">I provider di dettatura e riconoscimento vocale non creano controller, ma generano direttamente i propri eventi di input specializzati.</span><span class="sxs-lookup"><span data-stu-id="43305-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="43305-118">È possibile creare provider di input personalizzati implementando [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="43305-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="43305-119">Per altre informazioni, vedere Creazione [di un provider di dati di sistema di input.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="43305-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
