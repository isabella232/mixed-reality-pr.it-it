---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984260"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8d30b-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="8d30b-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="8d30b-102">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="8d30b-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Percorso del menu Build Settings... di Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="8d30b-104">Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):</span><span class="sxs-lookup"><span data-stu-id="8d30b-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata in sostituzione della piattaforma Standalone](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="8d30b-106">Attendi che Unity completi il passaggio all'altra piattaforma:</span><span class="sxs-lookup"><span data-stu-id="8d30b-106">Wait for Unity to finish switching the platform:</span></span>

![Passaggio di Unity all'altra piattaforma in corso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="8d30b-108">Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):</span><span class="sxs-lookup"><span data-stu-id="8d30b-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Finestra Build Settings di Unity con l'icona di chiusura evidenziata](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8d30b-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8d30b-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="8d30b-111">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="8d30b-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Percorso del menu Build Settings... di Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="8d30b-113">Nella finestra Impostazioni di compilazione **selezionare** piattaforma UWP (Universal Windows Platform) e:</span><span class="sxs-lookup"><span data-stu-id="8d30b-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="8d30b-114">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="8d30b-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="8d30b-115">Impostare **Architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="8d30b-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="8d30b-116">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="8d30b-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="8d30b-117">Impostare **Versione SDK di destinazione** su Versione più recente **installata**</span><span class="sxs-lookup"><span data-stu-id="8d30b-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="8d30b-118">Impostare **Versione minima della piattaforma** su **10.0.18362**</span><span class="sxs-lookup"><span data-stu-id="8d30b-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="8d30b-119">Impostare **Visual Studio versione più recente** **installata**</span><span class="sxs-lookup"><span data-stu-id="8d30b-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="8d30b-120">Impostare **Compila ed Esegui su** dispositivo **USB**</span><span class="sxs-lookup"><span data-stu-id="8d30b-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="8d30b-121">Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="8d30b-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="8d30b-122">Fare clic sul pulsante Cambia piattaforma</span><span class="sxs-lookup"><span data-stu-id="8d30b-122">Click the Switch Platform button</span></span>


![Impostazioni di compilazione unity con piattaforma UWP (Universal Windows Platform) impostazioni predefinite](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="8d30b-124">Al termine del passaggio della piattaforma da parte di Unity, fare clic sull'icona **x rossa** per chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="8d30b-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="8d30b-125">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="8d30b-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="8d30b-126">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="8d30b-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Percorso del menu Build Settings... di Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="8d30b-128">Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):</span><span class="sxs-lookup"><span data-stu-id="8d30b-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata in sostituzione della piattaforma Standalone](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="8d30b-130">Attendi che Unity completi il passaggio all'altra piattaforma:</span><span class="sxs-lookup"><span data-stu-id="8d30b-130">Wait for Unity to finish switching the platform:</span></span>

![Passaggio di Unity all'altra piattaforma in corso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="8d30b-132">Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):</span><span class="sxs-lookup"><span data-stu-id="8d30b-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Finestra Build Settings di Unity con l'icona di chiusura evidenziata](../images/mr-learning-base/base-02-section2-step1-4.png)
