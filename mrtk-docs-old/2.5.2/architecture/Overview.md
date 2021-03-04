---
title: Panoramica dell'architettura
description: Panoramica dell'architettura di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, architettura MRTK
ms.openlocfilehash: a40905284215c3b616f4db645e12ca92e1e5fe01
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783736"
---
# <a name="architecture-overview"></a><span data-ttu-id="c0d5c-104">Panoramica dell'architettura</span><span class="sxs-lookup"><span data-stu-id="c0d5c-104">Architecture overview</span></span>

<span data-ttu-id="c0d5c-105">Per un'introduzione generale al contenuto di MRTK, le informazioni sull'architettura contenute in questo documento consentiranno di comprendere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c0d5c-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="c0d5c-106">Componenti di MRTK e modalità di connessione</span><span class="sxs-lookup"><span data-stu-id="c0d5c-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="c0d5c-107">Concetti introdotti da MRTK che potrebbero non esistere in Vanilla Unity</span><span class="sxs-lookup"><span data-stu-id="c0d5c-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="c0d5c-108">Come funzionano alcuni dei sistemi più grandi, ad esempio l'input.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="c0d5c-109">Questa sezione non ha lo scopo di insegnare come eseguire le attività, ma piuttosto come strutturare tali attività e perché.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="c0d5c-110">Molti destinatari, un Toolkit</span><span class="sxs-lookup"><span data-stu-id="c0d5c-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="c0d5c-111">MRTK non dispone di un singolo gruppo di destinatari uniformi.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="c0d5c-112">È stato scritto per supportare casi di utilizzo compresi tra la prima volta gli hackathon, i singoli utenti che compilano esperienze condivise complesse per le aziende.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="c0d5c-113">È possibile che siano stati scritti codice e API che sono ottimizzati per uno più degli altri (ad esempio, alcune parti di MRTK sembrano più ottimizzate per "un solo clic su Configura"), ma è importante notare che alcune di queste sono più per motivi cronologici e di riapprovvigionamento.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="c0d5c-114">Man mano che MRTK si evolve, le funzionalità create devono essere progettate per la scalabilità in modo da supportare la gamma di casi d'uso.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="c0d5c-115">MRTK dispone inoltre di requisiti per la scalabilità normale tra le esperienze VR e AR.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="c0d5c-116">Dovrebbe essere facile creare applicazioni che si riferiscono normalmente al comportamento quando vengono distribuite in un HoloLens 2 o HoloLens 1 e dovrebbe essere semplice compilare applicazioni destinate a OpenVR e WMR (e altre piattaforme).</span><span class="sxs-lookup"><span data-stu-id="c0d5c-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="c0d5c-117">Sebbene a volte il team possa concentrare un'iterazione particolare su un sistema o una piattaforma specifica, l'obiettivo a lungo termine è creare un'ampia gamma di supporto per ogni persona che sviluppa esperienze di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="c0d5c-118">Suddivisione di alto livello</span><span class="sxs-lookup"><span data-stu-id="c0d5c-118">High level breakdown</span></span>

<span data-ttu-id="c0d5c-119">MRTK è una raccolta di strumenti che consentono di ottenere rapidamente un'esperienza di realtà mista (MR), nonché un Framework applicazione con opinioni sul proprio Runtime, su come deve essere esteso e su come deve essere configurato.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="c0d5c-120">A un livello elevato, il MRTK può essere suddiviso nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c0d5c-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Diagramma della panoramica dell'architettura](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="c0d5c-122">Il MRTK contiene anche un altro set di utilità di recupero delle buste che non hanno dipendenze dal resto del MRTK (per elencarne alcune: strumenti di compilazione, risolutori, fattori di influenza audio, utilità di smussamento e renderer di riga)</span><span class="sxs-lookup"><span data-stu-id="c0d5c-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="c0d5c-123">Il resto della documentazione dell'architettura compilerà il massimo, a partire dal Framework e dal runtime, avanzando a sistemi più interessanti e complessi, ad esempio l'input.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="c0d5c-124">Per continuare con la panoramica dell'architettura, vedere il sommario.</span><span class="sxs-lookup"><span data-stu-id="c0d5c-124">Please see the table of contents to continue with the architectural overview.</span></span>
