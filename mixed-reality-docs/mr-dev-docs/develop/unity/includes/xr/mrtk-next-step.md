---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603726"
---
# <a name="openxr"></a>[<span data-ttu-id="ee387-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ee387-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ee387-102">Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:</span><span class="sxs-lookup"><span data-stu-id="ee387-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee387-103">Configurare un nuovo progetto OpenXR con MRTK</span><span class="sxs-lookup"><span data-stu-id="ee387-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="ee387-104">Se si aggiorna un progetto MRTK esistente a **OpenXR,** è prima di tutto necessario aggiornare MRTK-Unity alla versione più recente (versione 2.7.2 o successiva) per ottenere correzioni chiave per la compatibilità con il plug-in OpenXR di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ee387-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="ee387-105">Usare [mixed reality feature tool](../../welcome-to-mr-feature-tool.md) per eseguire l'aggiornamento alla versione più recente di MRTK e quindi seguire la procedura di configurazione [manuale di OpenXR riportata di seguito.](#manual-setup-without-mrtk)</span><span class="sxs-lookup"><span data-stu-id="ee387-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="ee387-106">Per informazioni più dettagliate sulla migrazione di un progetto MRTK esistente a [OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK .</span><span class="sxs-lookup"><span data-stu-id="ee387-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ee387-107">Quando si esegue l'aggiornamento da una versione precedente di MRTK precedente alla **2.5.3,** assicurarsi che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="ee387-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ee387-108">Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ee387-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ee387-109">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="ee387-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ee387-110">Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:</span><span class="sxs-lookup"><span data-stu-id="ee387-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee387-111">Configurare un nuovo progetto Windows XR con MRTK</span><span class="sxs-lookup"><span data-stu-id="ee387-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="ee387-112">XR legacy</span><span class="sxs-lookup"><span data-stu-id="ee387-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ee387-113">Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:</span><span class="sxs-lookup"><span data-stu-id="ee387-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee387-114">Configurare un nuovo progetto XR legacy con MRTK</span><span class="sxs-lookup"><span data-stu-id="ee387-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)