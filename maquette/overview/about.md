---
title: Informazioni su Maquette
description: Introduzione a maquette e alle relative funzionalità.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realtà mista di Windows, maquette, prototipi, realtà mista, realtà virtuale, VR, MR, feedback, hub di feedback, bug
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935530"
---
# <a name="about-maquette"></a><span data-ttu-id="1351b-104">Informazioni su Maquette</span><span class="sxs-lookup"><span data-stu-id="1351b-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="1351b-105">![Introduzione al logo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="1351b-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="1351b-106">Maquette integra lo standard ECMA 5,1 JavaScript per consentire l'investimento di interattività in Maquette Scenes e gli oggetti che possono essere modificati ed eseguiti dall'interno di VSCode.</span><span class="sxs-lookup"><span data-stu-id="1351b-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="1351b-107">Le proprietà degli oggetti vengono esposte per la lettura e l'impostazione dall'interno di script, metodi di oggetti chiamati e oggetti e eventi di sistema in campo.</span><span class="sxs-lookup"><span data-stu-id="1351b-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="1351b-108">Lo script può anche interagire con maquette tramite oggetti di sistema accessibili tramite script.</span><span class="sxs-lookup"><span data-stu-id="1351b-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="1351b-109">Diversi controlli dell'interfaccia utente con cui l'utente può interagire fanno parte del sistema.</span><span class="sxs-lookup"><span data-stu-id="1351b-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="1351b-110">Questi possono essere aggiunti durante la creazione in maquette o creati e gestiti dall'interno dello script.</span><span class="sxs-lookup"><span data-stu-id="1351b-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="1351b-111">Gli eventi di interazione utente con questi elementi (immissione di dati, clic e così via) vengono esposti anche allo script come eventi.</span><span class="sxs-lookup"><span data-stu-id="1351b-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="1351b-112">Grazie a queste aggiunte, è possibile creare scene semplici e complesse, dagli esperimenti alla visualizzazione dei dati alle esplorazioni di scenari utente di realtà mista per esperienze completamente realizzate in AR o VR.</span><span class="sxs-lookup"><span data-stu-id="1351b-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="1351b-113">video di 60 second'ish</span><span class="sxs-lookup"><span data-stu-id="1351b-113">60 second'ish video</span></span>
* <span data-ttu-id="1351b-114">Scheda titolo voce</span><span class="sxs-lookup"><span data-stu-id="1351b-114">Entry Title Card</span></span>
  * <span data-ttu-id="1351b-115">Creazione di contenuti interattivi di realtà mista in Maquette</span><span class="sxs-lookup"><span data-stu-id="1351b-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="1351b-116">Script/interattività/sistema di interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="1351b-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="1351b-117">VO benvenuto dal team o dalle didascalie video?</span><span class="sxs-lookup"><span data-stu-id="1351b-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="1351b-118">che spiega</span><span class="sxs-lookup"><span data-stu-id="1351b-118">explaining:</span></span>
  * <span data-ttu-id="1351b-119">ragionamento della creazione di script per abilitare la creazione di contenuto Interactive MR</span><span class="sxs-lookup"><span data-stu-id="1351b-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="1351b-120">toccare il modo in cui può essere usato in tratti di pennelli molto ampi</span><span class="sxs-lookup"><span data-stu-id="1351b-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="1351b-121">Creazione di script per Vingette in azione</span><span class="sxs-lookup"><span data-stu-id="1351b-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="1351b-122">Finestra di dialogo composizione</span><span class="sxs-lookup"><span data-stu-id="1351b-122">Composing dialog box</span></span>
  * <span data-ttu-id="1351b-123">Compilazione dell'app dalla struttura (demo dell'app cooking)</span><span class="sxs-lookup"><span data-stu-id="1351b-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="1351b-124">Composizione nel modello fotogrammetria</span><span class="sxs-lookup"><span data-stu-id="1351b-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="1351b-125">Interazione con la guida alla risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="1351b-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="1351b-126">Visualizzazione dello script di debug in VSCode</span><span class="sxs-lookup"><span data-stu-id="1351b-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="1351b-127">Ottenere l'accesso allo script da un oggetto in scena</span><span class="sxs-lookup"><span data-stu-id="1351b-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="1351b-128">E così via...</span><span class="sxs-lookup"><span data-stu-id="1351b-128">Etc...</span></span>
* <span data-ttu-id="1351b-129">Scheda del titolo di riepilogo alla fine</span><span class="sxs-lookup"><span data-stu-id="1351b-129">Summary Title card at end</span></span>
  * <span data-ttu-id="1351b-130">Collegamento a Maquette</span><span class="sxs-lookup"><span data-stu-id="1351b-130">Link to Maquette</span></span>
  * <span data-ttu-id="1351b-131">Come iniziare a usare lo scripting</span><span class="sxs-lookup"><span data-stu-id="1351b-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="1351b-132">Annunci/stato/community</span><span class="sxs-lookup"><span data-stu-id="1351b-132">Announcements/status/community</span></span>
  * <span data-ttu-id="1351b-133">Vedere le informazioni che è possibile eseguire/inviare (?)</span><span class="sxs-lookup"><span data-stu-id="1351b-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="1351b-134">Commenti e suggerimenti e su come offrirti una soluzione migliore</span><span class="sxs-lookup"><span data-stu-id="1351b-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="1351b-135">Per iniziare</span><span class="sxs-lookup"><span data-stu-id="1351b-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="1351b-136">Esempi e app di esempio</span><span class="sxs-lookup"><span data-stu-id="1351b-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="1351b-137">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="1351b-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="1351b-138">Inviare commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="1351b-138">Send us feedback</span></span>

<span data-ttu-id="1351b-139">Ci auguriamo di aver ascoltato le tue esperienze e i risultati.</span><span class="sxs-lookup"><span data-stu-id="1351b-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="1351b-140">Commenti, suggerimenti e segnalazioni di bug sono sempre benvenuti.</span><span class="sxs-lookup"><span data-stu-id="1351b-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="1351b-141">Collegamento <></span><span class="sxs-lookup"><span data-stu-id="1351b-141"><Link?></span></span>