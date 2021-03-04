---
title: Voce
description: configurazione dell'input vocale in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sintesi vocale,
ms.openlocfilehash: 610516df4e9821c361e87394eb30c9f22389fdd6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782859"
---
# <a name="speech"></a><span data-ttu-id="3075d-104">Voce</span><span class="sxs-lookup"><span data-stu-id="3075d-104">Speech</span></span>

![Menu vicino](../images/input/MRTK_Input_Speech.png)

<span data-ttu-id="3075d-106">I provider di input vocale, come l' *input vocale Windows*, non creano alcun controller, ma consentono di definire parole chiave che genereranno eventi di input vocali quando vengono riconosciuti.</span><span class="sxs-lookup"><span data-stu-id="3075d-106">Speech input providers, like *Windows Speech Input*, don't create any controllers but instead allow you to define keywords that will raise speech input events when recognized.</span></span> <span data-ttu-id="3075d-107">Il **profilo dei comandi vocali** nel *profilo di sistema di input* è il punto in cui vengono configurate le parole chiave da riconoscere.</span><span class="sxs-lookup"><span data-stu-id="3075d-107">The **Speech Commands Profile** in the *Input System Profile* is where you configure the keywords to recognize.</span></span> <span data-ttu-id="3075d-108">Per ogni comando è inoltre possibile:</span><span class="sxs-lookup"><span data-stu-id="3075d-108">For each command you can also:</span></span>

- <span data-ttu-id="3075d-109">Selezionare un' **azione di input** a cui eseguire il mapping.</span><span class="sxs-lookup"><span data-stu-id="3075d-109">Select an **input action** to map it to.</span></span> <span data-ttu-id="3075d-110">In questo modo è possibile, ad esempio, usare la parola chiave *Select* per avere lo stesso effetto di un clic del mouse a sinistra, eseguendo il mapping di entrambi alla stessa azione.</span><span class="sxs-lookup"><span data-stu-id="3075d-110">This way you can for example use the keyword *Select* to have the same effect as a left mouse click, by mapping both to the same action.</span></span>
- <span data-ttu-id="3075d-111">Specificare un **codice chiave** che produrrà lo stesso evento vocale quando viene premuto.</span><span class="sxs-lookup"><span data-stu-id="3075d-111">Specify a **key code** that will produce the same speech event when pressed.</span></span>
- <span data-ttu-id="3075d-112">Aggiungere una **chiave di localizzazione** che verrà usata nelle app UWP per ottenere la parola chiave localizzata dalle risorse dell'app.</span><span class="sxs-lookup"><span data-stu-id="3075d-112">Add a **localization key** that will be used in UWP apps to obtain the localized keyword from the app resources.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands Profile">

## <a name="handling-speech-input"></a><span data-ttu-id="3075d-113">Gestione dell'input vocale</span><span class="sxs-lookup"><span data-stu-id="3075d-113">Handling speech input</span></span>

<span data-ttu-id="3075d-114">Lo [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script può essere aggiunto a un GameObject per gestire i comandi vocali usando [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html).</span><span class="sxs-lookup"><span data-stu-id="3075d-114">The [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script can be added to a GameObject to handle speech commands using [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html).</span></span> <span data-ttu-id="3075d-115">Mostra automaticamente l'elenco delle parole chiave definite dal profilo dei **comandi vocali**.</span><span class="sxs-lookup"><span data-stu-id="3075d-115">It automatically shows the list of the defined keywords from the **Speech Commands Profile**.</span></span>

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input Handler1">

<span data-ttu-id="3075d-116">Assegnare l'etichetta facoltativa della descrizione comando **SpeechConfirmationTooltip. prefabbricato** per visualizzare l'etichetta della descrizione comando animata.</span><span class="sxs-lookup"><span data-stu-id="3075d-116">Assign optional **SpeechConfirmationTooltip.prefab** to display animated confirmation tooltip label on recognition.</span></span>

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Speech Input Handler 2">

<span data-ttu-id="3075d-117">In alternativa, gli sviluppatori possono implementare l' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaccia in un componente script personalizzato per [gestire gli eventi di input vocale](InputEvents.md#input-event-interface-example).</span><span class="sxs-lookup"><span data-stu-id="3075d-117">Alternatively, developers can implement the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface in a custom script component to [handle speech input events](InputEvents.md#input-event-interface-example).</span></span>

## <a name="example-scene"></a><span data-ttu-id="3075d-118">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="3075d-118">Example scene</span></span>

<span data-ttu-id="3075d-119">La scena **SpeechInputExample** , in `MRTK/Examples/Demos/Input/Scenes/Speech` , Mostra come usare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="3075d-119">The **SpeechInputExample** scene, in `MRTK/Examples/Demos/Input/Scenes/Speech`, shows how to use speech.</span></span> <span data-ttu-id="3075d-120">È anche possibile ascoltare gli eventi del comando vocale direttamente nello script implementando [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (vedere la tabella dei [gestori di eventi](InputEvents.md)).</span><span class="sxs-lookup"><span data-stu-id="3075d-120">You can also listen to speech command events directly in your own script by implementing [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (see table of [event handlers](InputEvents.md)).</span></span>

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example Scene">
