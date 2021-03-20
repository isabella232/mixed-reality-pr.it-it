---
title: Estensioni dell'editor in Unreal
description: Informazioni su come estendere l'editor Unreal Engine con script personalizzati, azioni con script e widget di utilità.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, estensioni dell'editor, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584922"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="33d40-104">Estensioni dell'editor in Unreal</span><span class="sxs-lookup"><span data-stu-id="33d40-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="33d40-105">Unreal fornisce un set completo di funzionalità che consentono di personalizzare il motore in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="33d40-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="33d40-106">Le funzionalità variano da semplice ma limitato a molto potente ma complesso.</span><span class="sxs-lookup"><span data-stu-id="33d40-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="33d40-107">La procedura seguente è elencata in ordine di complessità crescente.</span><span class="sxs-lookup"><span data-stu-id="33d40-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="33d40-108">In generale, è consigliabile raggiungere soluzioni più semplici al problema e esaurirne le opzioni, prima di procedere con un'opzione più complessa.</span><span class="sxs-lookup"><span data-stu-id="33d40-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="33d40-109">Ad esempio, è stato rilevato che lo script di costruzione di base può essere utilizzato in sostituzione dei plug-in nella maggior parte dei casi.</span><span class="sxs-lookup"><span data-stu-id="33d40-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="33d40-110">Script di costruzione</span><span class="sxs-lookup"><span data-stu-id="33d40-110">Construction scripts</span></span>

<span data-ttu-id="33d40-111">È possibile usare gli script di costruzione per eseguire azioni di inizializzazione, che vengono eseguite quando si crea un'istanza del progetto.</span><span class="sxs-lookup"><span data-stu-id="33d40-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="33d40-112">Script per costruzioni utente</span><span class="sxs-lookup"><span data-stu-id="33d40-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="33d40-113">Esempio di progetto</span><span class="sxs-lookup"><span data-stu-id="33d40-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="33d40-114">Esercitazione video</span><span class="sxs-lookup"><span data-stu-id="33d40-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="33d40-115">Azioni con script</span><span class="sxs-lookup"><span data-stu-id="33d40-115">Scripted actions</span></span>

<span data-ttu-id="33d40-116">Le azioni con script sono progetti di utilità dell'editor.</span><span class="sxs-lookup"><span data-stu-id="33d40-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="33d40-117">È possibile avviarli nell'editor di Unreal:</span><span class="sxs-lookup"><span data-stu-id="33d40-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="33d40-118">Fare clic con il pulsante destro del mouse su **Asset** nel browser contenuto</span><span class="sxs-lookup"><span data-stu-id="33d40-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="33d40-119">In alternativa, fare clic con il pulsante destro del mouse su **Actors** nel viewport livello o nel mondo</span><span class="sxs-lookup"><span data-stu-id="33d40-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="33d40-120">Le azioni con script sono particolarmente adatte per i momenti in cui è necessaria la logica del progetto per la consapevolezza contestuale di set di asset o attori.</span><span class="sxs-lookup"><span data-stu-id="33d40-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="33d40-121">In genere, un'azione con script ottiene un elenco di asset o attori selezionati durante l'esecuzione dell'azione, quindi modifica tali oggetti o li considera nel grafico.</span><span class="sxs-lookup"><span data-stu-id="33d40-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="33d40-122">Azioni con script</span><span class="sxs-lookup"><span data-stu-id="33d40-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="33d40-123">Esecuzione di azioni con script all'avvio del progetto</span><span class="sxs-lookup"><span data-stu-id="33d40-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="33d40-124">Widget dell'utilità Editor</span><span class="sxs-lookup"><span data-stu-id="33d40-124">Editor utility widgets</span></span>

<span data-ttu-id="33d40-125">È possibile utilizzare i [widget dell'utilità di editor](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) ogni volta che si desidera aggiungere nuovi elementi dell'interfaccia utente per modificare l'interfaccia utente dell'editor non reale.</span><span class="sxs-lookup"><span data-stu-id="33d40-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="33d40-126">I widget dell'utilità di editor sono basati su UMG (Unreal Motion Graphics), quindi è possibile configurare i widget in un progetto come per qualsiasi altro progetto di widget di UMG.</span><span class="sxs-lookup"><span data-stu-id="33d40-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="33d40-127">Questi widget sono specifici dell'interfaccia utente dell'editor ed è possibile usarli per creare schede dell'editor personalizzate.</span><span class="sxs-lookup"><span data-stu-id="33d40-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="33d40-128">È quindi possibile selezionare queste schede personalizzate dal menu Windows, come si selezionano le schede dell'editor esistente.</span><span class="sxs-lookup"><span data-stu-id="33d40-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="33d40-129">Plug-in</span><span class="sxs-lookup"><span data-stu-id="33d40-129">Plugins</span></span>

<span data-ttu-id="33d40-130">Unreal consente di sviluppare e gestire i [plug](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) -in personalizzati da usare con gli strumenti e il runtime UE4.</span><span class="sxs-lookup"><span data-stu-id="33d40-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="33d40-131">È possibile abilitare o disabilitare i plug-in in qualsiasi momento nell'editor non reale.</span><span class="sxs-lookup"><span data-stu-id="33d40-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="33d40-132">I plug-in possono aggiungere funzionalità di gioco in fase di esecuzione, modificare le funzionalità predefinite del motore, creare nuovi tipi di file ed estendere le funzionalità dell'editor.</span><span class="sxs-lookup"><span data-stu-id="33d40-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

