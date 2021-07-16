---
title: Panoramica dell'architettura
description: Panoramica dell'architettura di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, architettura MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281913"
---
# <a name="architecture-overview"></a><span data-ttu-id="41c08-104">Panoramica dell'architettura</span><span class="sxs-lookup"><span data-stu-id="41c08-104">Architecture overview</span></span>

<span data-ttu-id="41c08-105">Per un'introduzione generale al contenuto di MRTK, le informazioni sull'architettura contenute in questo documento consentono di comprendere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="41c08-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="41c08-106">Grandi parti di MRTK e come si connettono</span><span class="sxs-lookup"><span data-stu-id="41c08-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="41c08-107">Concetti introdotti da MRTK che potrebbero non esistere in Vanilla Unity</span><span class="sxs-lookup"><span data-stu-id="41c08-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="41c08-108">Funzionamento di alcuni dei sistemi più grandi (ad esempio Input)</span><span class="sxs-lookup"><span data-stu-id="41c08-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="41c08-109">Questa sezione non ha lo scopo di illustrare come eseguire le attività, ma piuttosto come tali attività sono strutturate e perché.</span><span class="sxs-lookup"><span data-stu-id="41c08-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="41c08-110">Molti destinatari, un toolkit</span><span class="sxs-lookup"><span data-stu-id="41c08-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="41c08-111">MRTK non ha un singolo pubblico uniforme.</span><span class="sxs-lookup"><span data-stu-id="41c08-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="41c08-112">È stato scritto per supportare casi d'uso che vanno dagli hackathon per la prima volta ai singoli utenti che compilano esperienze complesse e condivise per l'azienda.</span><span class="sxs-lookup"><span data-stu-id="41c08-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="41c08-113">È possibile che siano state scritte alcune API e codice ottimizzati per l'una e l'altra(ad esempio, alcune parti di MRTK sembrano più ottimizzate per la "configurazione con un clic"), ma è importante notare che alcune di queste sono più per motivi cronologici e di risorse.</span><span class="sxs-lookup"><span data-stu-id="41c08-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="41c08-114">Con l'evolversi di MRTK, le funzionalità create devono essere progettate per la scalabilità per supportare la gamma di casi d'uso.</span><span class="sxs-lookup"><span data-stu-id="41c08-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="41c08-115">MRTK ha anche requisiti per ridimensionare correttamente le esperienze vr e AR.</span><span class="sxs-lookup"><span data-stu-id="41c08-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="41c08-116">Dovrebbe essere facile compilare applicazioni che normalmente fallback nel comportamento quando vengono distribuite in un HoloLens 2 O un HoloLens 1 e dovrebbe essere semplice compilare applicazioni che hanno come destinazione OpenVR e WMR (e altre piattaforme).</span><span class="sxs-lookup"><span data-stu-id="41c08-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="41c08-117">Anche se a volte il team può concentrarsi su un'iterazione specifica su un sistema o una piattaforma specifica, l'obiettivo a lungo termine è quello di creare un'ampia gamma di supporto per ogni luogo in cui le persone stanno creando esperienze di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="41c08-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="41c08-118">Suddivisione di alto livello</span><span class="sxs-lookup"><span data-stu-id="41c08-118">High level breakdown</span></span>

<span data-ttu-id="41c08-119">MRTK è sia una raccolta di strumenti per ottenere rapidamente esperienze di realtà mista (MR), sia un framework di applicazioni con opinioni sul proprio runtime, su come deve essere esteso e su come deve essere configurato.</span><span class="sxs-lookup"><span data-stu-id="41c08-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="41c08-120">A livello elevato, il codice MRTK può essere suddiviso nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="41c08-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Diagramma di panoramica dell'architettura](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="41c08-122">MrTK contiene anche un altro set di utilità grab-bag che hanno dipendenze da poco o nessuna sul resto di MRTK (per elencarne alcune: strumenti di compilazione, risolutori, fattori di influenza audio, utilità di smoothing e renderer di linea)</span><span class="sxs-lookup"><span data-stu-id="41c08-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="41c08-123">Il resto della documentazione dell'architettura verrà compilato dal basso, a partire dal framework e dal runtime, fino a sistemi più interessanti e complessi, ad esempio l'input.</span><span class="sxs-lookup"><span data-stu-id="41c08-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="41c08-124">Per continuare con la panoramica dell'architettura, vedere il sommario.</span><span class="sxs-lookup"><span data-stu-id="41c08-124">Please see the table of contents to continue with the architectural overview.</span></span>
