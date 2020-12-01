---
title: WinRT in Unreal
description: Panoramica del plug-in di audio spaziale per Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, Guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, WinRT, DLL
ms.openlocfilehash: 722add1601013d206ffface84d3a53cf3a9d89f9
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354445"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="e2907-104">WinRT in Unreal</span><span class="sxs-lookup"><span data-stu-id="e2907-104">WinRT in Unreal</span></span>

<span data-ttu-id="e2907-105">Nel corso dello sviluppo di HoloLens potrebbe essere necessario scrivere una funzionalità usando WinRT.</span><span class="sxs-lookup"><span data-stu-id="e2907-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="e2907-106">Se ad esempio si apre una finestra di dialogo di file in un'applicazione HoloLens, è necessario FileSavePicker nel file di intestazione WinRT/Windows. storage. Pickers. h.</span><span class="sxs-lookup"><span data-stu-id="e2907-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="e2907-107">WinRT è supportato nel sistema di compilazione Unreal dalla versione 4,26 e successive.</span><span class="sxs-lookup"><span data-stu-id="e2907-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="e2907-108">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="e2907-108">Next Development Checkpoint</span></span>

<span data-ttu-id="e2907-109">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="e2907-109">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e2907-110">Da qui è possibile passare a qualsiasi [argomento](unreal-development-overview.md#3-platform-capabilities-and-apis) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.</span><span class="sxs-lookup"><span data-stu-id="e2907-110">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e2907-111">Distribuzione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="e2907-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="e2907-112">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e2907-112">See also</span></span>
* [<span data-ttu-id="e2907-113">API C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="e2907-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="e2907-114">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="e2907-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="e2907-115">Librerie di terze parti non reali</span><span class="sxs-lookup"><span data-stu-id="e2907-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
