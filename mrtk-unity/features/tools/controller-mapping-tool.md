---
title: Strumento di mapping del controller
description: Documentazione sullo strumento di mapping dei controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176174"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="3e67d-104">Strumento di mapping del controller</span><span class="sxs-lookup"><span data-stu-id="3e67d-104">Controller mapping tool</span></span>

<span data-ttu-id="3e67d-105">Lo strumento di mapping del controller è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'asse di input Unity e i mapping dei pulsanti per un controller hardware (ad esempio, un controller del movimento).</span><span class="sxs-lookup"><span data-stu-id="3e67d-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="3e67d-106">Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware.</span><span class="sxs-lookup"><span data-stu-id="3e67d-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="3e67d-107">Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.</span><span class="sxs-lookup"><span data-stu-id="3e67d-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Strumento di mapping del controller](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="3e67d-109">Uso dello strumento di mapping del controller</span><span class="sxs-lookup"><span data-stu-id="3e67d-109">Using the controller mapping tool</span></span>

<span data-ttu-id="3e67d-110">Per iniziare a usare lo strumento di mapping del controller, passare a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** e aprire la **scena ControllerMappingTool.**</span><span class="sxs-lookup"><span data-stu-id="3e67d-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="3e67d-111">Dopo che la scena è stata caricata, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3e67d-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="3e67d-112">Per esaminare i mapping di Unity per un controller:</span><span class="sxs-lookup"><span data-stu-id="3e67d-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="3e67d-113">Connessione il controller</span><span class="sxs-lookup"><span data-stu-id="3e67d-113">Connect the controller</span></span>
- <span data-ttu-id="3e67d-114">Premere ogni pulsante e spostare ogni asse</span><span class="sxs-lookup"><span data-stu-id="3e67d-114">Press each button and move each axis</span></span>
- <span data-ttu-id="3e67d-115">Si notino i mapping nella visualizzazione</span><span class="sxs-lookup"><span data-stu-id="3e67d-115">Note the mappings in the display</span></span>
- <span data-ttu-id="3e67d-116">Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller</span><span class="sxs-lookup"><span data-stu-id="3e67d-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="3e67d-117">Lo strumento di mapping del controller non usa Microsoft Mixed Reality Toolkit componenti.</span><span class="sxs-lookup"><span data-stu-id="3e67d-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="3e67d-118">Comunica direttamente con Unity per determinare e visualizzare i mapping dei controlli.</span><span class="sxs-lookup"><span data-stu-id="3e67d-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="3e67d-119">Visualizzazione di tutti i controlli</span><span class="sxs-lookup"><span data-stu-id="3e67d-119">All controls display</span></span>

<span data-ttu-id="3e67d-120">Il pannello di visualizzazione di grandi dimensioni segnala lo stato di tutti gli assi e i pulsanti di input di Unity definiti (ad esempio: Asse 10, Pulsante 3).</span><span class="sxs-lookup"><span data-stu-id="3e67d-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="3e67d-121">Questo pannello offre una visualizzazione completa dello stato del controller.</span><span class="sxs-lookup"><span data-stu-id="3e67d-121">This panel provides a complete view of the state of the controller.</span></span>

![Visualizzazione di tutti i controlli](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="3e67d-123">Visualizzazione dei controlli attivi</span><span class="sxs-lookup"><span data-stu-id="3e67d-123">Active controls display</span></span>

<span data-ttu-id="3e67d-124">Il pannello di visualizzazione più piccolo e ristretto mostra l'asse di input di Unity e i pulsanti che si trova in uno stato attivo (ad esempio, viene premuto un pulsante).</span><span class="sxs-lookup"><span data-stu-id="3e67d-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="3e67d-125">La visualizzazione dei controlli attivi offre una visualizzazione di riepilogo facile da leggere dello stato del controller.</span><span class="sxs-lookup"><span data-stu-id="3e67d-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Visualizzazione dei controlli attivi](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="3e67d-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3e67d-127">See also</span></span>

- [<span data-ttu-id="3e67d-128">Creazione di un provider di dati del sistema di input</span><span class="sxs-lookup"><span data-stu-id="3e67d-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="3e67d-129">Strumento InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="3e67d-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
