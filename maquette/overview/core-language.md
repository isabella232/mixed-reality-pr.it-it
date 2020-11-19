---
title: Linguaggio di base
description: Informazioni sui dettagli del linguaggio di base di maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realtà mista di Windows, maquette, prototipi, realtà mista, realtà virtuale, VR, MR, feedback, hub di feedback, bug
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935538"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="9d0eb-104">Dettagli del linguaggio di base di MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="9d0eb-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="9d0eb-105">![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span><span class="sxs-lookup"><span data-stu-id="9d0eb-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="9d0eb-106">Accesso all' `Maquette` oggetto e allo spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="9d0eb-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="9d0eb-107">Maquette espone gli oggetti interni e le interfacce in JavaScript tramite l' `Maquette` oggetto e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="9d0eb-108">Questa funzionalità è descritta nell' [oggetto maquette e nella documentazione dello spazio dei nomi](https://www.maquette.ms/doc_staging/objects/Maquette.html) .</span><span class="sxs-lookup"><span data-stu-id="9d0eb-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="9d0eb-109">L' `Maquette` oggetto dispone di funzioni di primo livello per semplificare l'interazione con maquette e per semplificare la risoluzione dei problemi ripetuti.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="9d0eb-110">Questa operazione è descritta nella documentazione di [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span><span class="sxs-lookup"><span data-stu-id="9d0eb-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="9d0eb-111">Avvio e caricamento di maquette</span><span class="sxs-lookup"><span data-stu-id="9d0eb-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="9d0eb-112">Maquette caricherà e valuterà file JavaScript specifici per abilitare la configurazione, l'installazione e l'inizializzazione nei momenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="9d0eb-113">Durante l'avvio di maquette:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="9d0eb-114">Ogni volta che viene caricato un progetto:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="9d0eb-115">I progetti caricano i rispettivi script di progetto:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="9d0eb-116">Implementazione di JavaScript</span><span class="sxs-lookup"><span data-stu-id="9d0eb-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="9d0eb-117">L'interprete JavaScript usato in Maquette è basato su [o Jint](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="9d0eb-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="9d0eb-118">O Jint è compatibile con ECMAScript 5,1 e supporta [estensioni aggiuntive da ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="9d0eb-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="9d0eb-119">L'estensione `.mqjs` viene usata per distinguere i file JavaScript Maquette dal normale linguaggio JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d0eb-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9d0eb-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->