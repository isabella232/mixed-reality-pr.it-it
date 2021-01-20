---
title: Controller di HP Reverb G2 in Unreal
description: Informazioni su come usare i nuovi controller di HP Reverb G2 in OpenXR e SteamVR per le applicazioni di realtà mista non reali.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, headset di realtà mista, auricolare della realtà virtuale
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582682"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="2184b-104">Controller di HP Reverb G2 in Unreal</span><span class="sxs-lookup"><span data-stu-id="2184b-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="2184b-105">Introduzione</span><span class="sxs-lookup"><span data-stu-id="2184b-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2184b-106">Unreal Engine 4,26 e OpenXR o SteamVR sono necessari per accedere al plug-in HP Motion controller, è necessario usare i controller di HP Reverb G2.</span><span class="sxs-lookup"><span data-stu-id="2184b-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="2184b-107">Porting di un'app OpenXR esistente</span><span class="sxs-lookup"><span data-stu-id="2184b-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="2184b-108">Se nel gioco non sono presenti associazioni controller per il controller di realtà misto HP, il runtime di OpenXR tenterà di rimappare i binding esistenti al controller attivo.</span><span class="sxs-lookup"><span data-stu-id="2184b-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will try to remap existing bindings to the active controller.</span></span>  <span data-ttu-id="2184b-109">In questo caso, il gioco ha binding Oculus touch e nessun binding del controller di realtà mista di HP.</span><span class="sxs-lookup"><span data-stu-id="2184b-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Modifica del mapping delle associazioni esistenti quando non esistono associazioni controller](images/reverb-g2-img-04.png)

<span data-ttu-id="2184b-111">Gli eventi verranno comunque attivati, ma se il gioco deve usare binding specifici del controller, ad esempio il pulsante di menu destro, è necessario usare il profilo di interazione con la realtà di HP mixed.</span><span class="sxs-lookup"><span data-stu-id="2184b-111">The events will still fire, but if the game needs to make use of controller-specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="2184b-112">È possibile specificare più associazioni controller per azione per supportare al meglio dispositivi diversi.</span><span class="sxs-lookup"><span data-stu-id="2184b-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Uso di più associazioni controller](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="2184b-114">Aggiunta di mapping di azioni di input</span><span class="sxs-lookup"><span data-stu-id="2184b-114">Adding input action mappings</span></span> 

<span data-ttu-id="2184b-115">Definire una nuova azione ed eseguire il mapping a una delle pressioni dei tasti nella sezione HP Mixed Reality controller.</span><span class="sxs-lookup"><span data-stu-id="2184b-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Definizione di nuove azioni e mapping](images/reverb-g2-img-02.png)

<span data-ttu-id="2184b-117">Il controller di HP Reverb G2 dispone anche di un grip analogico, che può essere usato nei mapping degli assi con il binding "Squeeze Axis".</span><span class="sxs-lookup"><span data-stu-id="2184b-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="2184b-118">È disponibile un'associazione di compressione separata, che deve essere usata per i mapping delle azioni quando il pulsante grip è premuto completamente.</span><span class="sxs-lookup"><span data-stu-id="2184b-118">There's a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Utilizzo delle associazioni dell'asse squeeze](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="2184b-120">Aggiunta di eventi di input</span><span class="sxs-lookup"><span data-stu-id="2184b-120">Adding input events</span></span>

<span data-ttu-id="2184b-121">Fare clic con il pulsante destro del mouse su un progetto e cercare i nuovi nomi di azione del sistema di input per aggiungere gli eventi per queste azioni.</span><span class="sxs-lookup"><span data-stu-id="2184b-121">Right-click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="2184b-122">Il progetto sta rispondendo agli eventi con una stringa di stampa che visualizza lo stato corrente del pulsante e dell'asse.</span><span class="sxs-lookup"><span data-stu-id="2184b-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Progetto che risponde agli eventi e output dello stato corrente del pulsante e dell'asse](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="2184b-124">Uso dell'input</span><span class="sxs-lookup"><span data-stu-id="2184b-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="2184b-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2184b-125">See also</span></span>
* [<span data-ttu-id="2184b-126">Input SteamVR</span><span class="sxs-lookup"><span data-stu-id="2184b-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="2184b-127">Uso di SteamVR con la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="2184b-127">Using SteamVR with Windows Mixed Reality</span></span>](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="2184b-128">Fotocamera Unreal Player</span><span class="sxs-lookup"><span data-stu-id="2184b-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)