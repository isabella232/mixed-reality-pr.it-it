---
title: ControllerMappingTool
description: Documentazione sullo strumento di mapping del controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 98280f21b120dbf8a1d77d03239f952d21277704
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783311"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="0183a-104">Strumento di mapping controller</span><span class="sxs-lookup"><span data-stu-id="0183a-104">Controller mapping tool</span></span>

<span data-ttu-id="0183a-105">Lo strumento di mapping del controller è un Runtime (su dispositivo o Editor) che consente agli sviluppatori di determinare rapidamente i mapping degli assi di input e dei pulsanti di Unity per un controller hardware (ad esempio, Motion controller).</span><span class="sxs-lookup"><span data-stu-id="0183a-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="0183a-106">Questo strumento è molto utile per lo sviluppo del supporto per un nuovo controller hardware.</span><span class="sxs-lookup"><span data-stu-id="0183a-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="0183a-107">Può anche essere utile per confermare un problema di mapping del controllo sospetto nella classe di supporto per un controller esistente.</span><span class="sxs-lookup"><span data-stu-id="0183a-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Strumento di mapping controller](../Images/ControllerMappingTool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="0183a-109">Utilizzo dello strumento di mapping dei controller</span><span class="sxs-lookup"><span data-stu-id="0183a-109">Using the controller mapping tool</span></span>

<span data-ttu-id="0183a-110">Per iniziare a usare lo strumento di mapping del controller, passare a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e aprire la scena **ControllerMappingTool** .</span><span class="sxs-lookup"><span data-stu-id="0183a-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="0183a-111">Una volta caricata la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione, oppure compilato ed eseguito in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0183a-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="0183a-112">Per esaminare i mapping di Unity per un controller:</span><span class="sxs-lookup"><span data-stu-id="0183a-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="0183a-113">Connettere il controller</span><span class="sxs-lookup"><span data-stu-id="0183a-113">Connect the controller</span></span>
- <span data-ttu-id="0183a-114">Premere ciascun pulsante e spostare ogni asse</span><span class="sxs-lookup"><span data-stu-id="0183a-114">Press each button and move each axis</span></span>
- <span data-ttu-id="0183a-115">Annotare i mapping nella visualizzazione</span><span class="sxs-lookup"><span data-stu-id="0183a-115">Note the mappings in the display</span></span>
- <span data-ttu-id="0183a-116">Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller</span><span class="sxs-lookup"><span data-stu-id="0183a-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="0183a-117">Lo strumento di mapping del controller non usa i componenti di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="0183a-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="0183a-118">Comunica direttamente con Unity per determinare e visualizzare i mapping dei controlli.</span><span class="sxs-lookup"><span data-stu-id="0183a-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="0183a-119">Visualizzazione di tutti i controlli</span><span class="sxs-lookup"><span data-stu-id="0183a-119">All controls display</span></span>

<span data-ttu-id="0183a-120">Il pannello di visualizzazione di grandi dimensioni segnala lo stato di tutti gli assi e i pulsanti di input Unity definiti, ad esempio asse 10, pulsante 3.</span><span class="sxs-lookup"><span data-stu-id="0183a-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="0183a-121">Questo pannello offre una visualizzazione completa dello stato del controller.</span><span class="sxs-lookup"><span data-stu-id="0183a-121">This panel provides a complete view of the state of the controller.</span></span>

![Visualizzazione di tutti i controlli](../Images/ControllerMappingTool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="0183a-123">Visualizzazione controlli attivi</span><span class="sxs-lookup"><span data-stu-id="0183a-123">Active controls display</span></span>

<span data-ttu-id="0183a-124">Il pannello di visualizzazione più piccolo e ridotto Mostra i pulsanti e cartesiano di input Unity che si trovano in uno stato attivo (ad esempio, viene premuto un pulsante).</span><span class="sxs-lookup"><span data-stu-id="0183a-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="0183a-125">La visualizzazione dei controlli attivi fornisce una visualizzazione riepilogativa di facile lettura dello stato del controller.</span><span class="sxs-lookup"><span data-stu-id="0183a-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Visualizzazione controlli attivi](../Images/ControllerMappingTool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="0183a-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0183a-127">See also</span></span>

- [<span data-ttu-id="0183a-128">Creazione di un provider di dati di sistema di input</span><span class="sxs-lookup"><span data-stu-id="0183a-128">Creating an input system data provider</span></span>](../Input/CreateDataProvider.md)
- [<span data-ttu-id="0183a-129">Strumento InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="0183a-129">InputFeatureUsage tool</span></span>](./InputFeatureUsageTool.md)
