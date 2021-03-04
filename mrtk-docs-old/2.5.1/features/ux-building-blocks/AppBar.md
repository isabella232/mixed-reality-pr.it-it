---
title: AppBar
description: Panoramica sulla barra dell'app in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, barra dell'app,
ms.openlocfilehash: d45ad8c7e0eafb89eae11d8bf4a61afdfc1006bd
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783222"
---
# <a name="app-bar"></a><span data-ttu-id="4e013-104">Barra dell'app</span><span class="sxs-lookup"><span data-stu-id="4e013-104">App bar</span></span>

![Barra dell'app](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="4e013-106">La barra dell'app è un componente dell'interfaccia utente usato insieme allo script di [controllo dei limiti](BoundsControl.md) .</span><span class="sxs-lookup"><span data-stu-id="4e013-106">App bar is a UI component that is used together with the [bounds control](BoundsControl.md) script.</span></span> <span data-ttu-id="4e013-107">Aggiunge i controlli Button a un oggetto con l'intenzione di modificarlo.</span><span class="sxs-lookup"><span data-stu-id="4e013-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="4e013-108">Utilizzando il pulsante ' Adjust ', l'interfaccia di controllo dei limiti per un oggetto può essere disattivata.</span><span class="sxs-lookup"><span data-stu-id="4e013-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="4e013-109">Il pulsante "Rimuovi" deve rimuovere l'oggetto dalla scena.</span><span class="sxs-lookup"><span data-stu-id="4e013-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="4e013-110">Come usare la barra dell'app</span><span class="sxs-lookup"><span data-stu-id="4e013-110">How to use app bar</span></span>

<span data-ttu-id="4e013-111">Trascinare e rilasciare `AppBar` (assets/MRTK/SDK/features/UX/precasers/AppBar/AppBar. prefabricable) nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="4e013-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="4e013-112">Nel pannello Inspector del componente, assegnare un oggetto con un controllo Bounds come rettangolo di selezione di *destinazione* a cui aggiungere la barra dell'app.</span><span class="sxs-lookup"><span data-stu-id="4e013-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="4e013-113">**Importante:** L'opzione di attivazione del controllo dei limiti per l'oggetto di destinazione deve essere ' Activate manually '.</span><span class="sxs-lookup"><span data-stu-id="4e013-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Setup 2">
