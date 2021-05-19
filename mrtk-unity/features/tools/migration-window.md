---
title: Finestra di migrazione
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 8e03848097c313a518f638de591f692ab71f0985
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143869"
---
# <a name="migration-window"></a><span data-ttu-id="f58e7-104">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="f58e7-104">Migration window</span></span>

<span data-ttu-id="f58e7-105">Quando MRTK subisce modifiche, alcuni componenti potrebbero essere deprecati e verranno introdotte sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="f58e7-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="f58e7-106">La finestra di migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="f58e7-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Finestra di migrazione](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="f58e7-108">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="f58e7-108">Usage</span></span>

<span data-ttu-id="f58e7-109">Per aprire la finestra, selezionare *Mixed Reality Toolkit* Utilities Migration Window (Finestra di migrazione delle utilità di Mixed Reality  >    >  Toolkit).</span><span class="sxs-lookup"><span data-stu-id="f58e7-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="f58e7-110">Una volta aperta la finestra di migrazione, le schede di navigazione in modalità di selezione possono essere abilitate scegliendo l'implementazione specifica del componente del gestore della migrazione.</span><span class="sxs-lookup"><span data-stu-id="f58e7-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modalità di selezione della migrazione](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="f58e7-112">Modalità oggetto</span><span class="sxs-lookup"><span data-stu-id="f58e7-112">Object mode</span></span>

<span data-ttu-id="f58e7-113">La selezione della scheda Oggetti consente all'oggetto Campo in cui l'utente può trascinare e rilasciare tutti gli oggetti Game dalla scena o dai prefab attualmente aperti dalla cartella del progetto da migrare.</span><span class="sxs-lookup"><span data-stu-id="f58e7-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="f58e7-114">Se si preme *il pulsante rimuovi (-)* visualizzato a destra dell'oggetto elencato, l'oggetto viene rimosso dall'elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="f58e7-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="f58e7-115">Quando tutti gli oggetti desiderati sono  presenti nell'elenco, premendo il pulsante Migrate (Esegui migrazione) verranno applicate le modifiche richieste dall'implementazione del gestore di migrazione scelta a tutti i componenti nella selezione che corrispondono all'implementazione.</span><span class="sxs-lookup"><span data-stu-id="f58e7-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migrazione della selezione](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="f58e7-117">Modalità scena</span><span class="sxs-lookup"><span data-stu-id="f58e7-117">Scene mode</span></span>

<span data-ttu-id="f58e7-118">Consente all'utente di trascinare e rilasciare gli asset della scena contenenti oggetti di cui eseguire la migrazione.</span><span class="sxs-lookup"><span data-stu-id="f58e7-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selezione di scene per la migrazione](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="f58e7-120">Modalità progetto</span><span class="sxs-lookup"><span data-stu-id="f58e7-120">Project mode</span></span>

<span data-ttu-id="f58e7-121">Se si *preme il pulsante* Esegui migrazione, il componente di destinazione dell'implementazione del gestore di migrazione verrà aggiornato per tutti i prefab e le scene nel progetto.</span><span class="sxs-lookup"><span data-stu-id="f58e7-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrazione di un progetto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="f58e7-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f58e7-123">See also</span></span>

- [<span data-ttu-id="f58e7-124">Aggiornamento da versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="f58e7-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="f58e7-125">Versioni di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="f58e7-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="f58e7-126">Guida di orientamento a MRTK</span><span class="sxs-lookup"><span data-stu-id="f58e7-126">MRTK roadmap</span></span>](../../roadmap.md)
