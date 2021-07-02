---
title: Barra dell'app
description: Panoramica sulla barra dell'app in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, barra delle app,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175689"
---
# <a name="app-bar"></a><span data-ttu-id="9479a-104">Barra dell'app</span><span class="sxs-lookup"><span data-stu-id="9479a-104">App bar</span></span>

![Barra dell'app](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="9479a-106">La barra dell'app è un componente dell'interfaccia utente che viene usato insieme allo script [di controllo dei](bounds-control.md) limiti.</span><span class="sxs-lookup"><span data-stu-id="9479a-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="9479a-107">Aggiunge i controlli pulsante a un oggetto con la finalità di modificarlo.</span><span class="sxs-lookup"><span data-stu-id="9479a-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="9479a-108">Usando il pulsante "Regola", l'interfaccia di controllo dei limiti per un oggetto può essere de-/attivata.</span><span class="sxs-lookup"><span data-stu-id="9479a-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="9479a-109">Il pulsante "Rimuovi" dovrebbe rimuovere l'oggetto dalla scena.</span><span class="sxs-lookup"><span data-stu-id="9479a-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="9479a-110">Come usare la barra dell'app</span><span class="sxs-lookup"><span data-stu-id="9479a-110">How to use app bar</span></span>

<span data-ttu-id="9479a-111">Trascinare `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="9479a-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="9479a-112">Nel pannello di controllo del componente assegnare qualsiasi oggetto con un controllo limiti come rettangolo di selezione di destinazione *per* aggiungere la barra dell'app.</span><span class="sxs-lookup"><span data-stu-id="9479a-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="9479a-113">**Importante:** L'opzione di attivazione del controllo dei limiti per l'oggetto di destinazione deve essere "Attiva manualmente".</span><span class="sxs-lookup"><span data-stu-id="9479a-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
