---
title: MigrationWindow
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1ea4e46c5b7d7d3d2d33affbd0811c93e29da11f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694708"
---
# <a name="migration-window"></a><span data-ttu-id="32107-104">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="32107-104">Migration window</span></span>

<span data-ttu-id="32107-105">Quando il MRTK subisce modifiche, è possibile che alcuni componenti vengano deprecati e che vengano introdotti sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="32107-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="32107-106">La finestra migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="32107-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Finestra di migrazione](../Images/MigrationWindow/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="32107-108">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="32107-108">Usage</span></span>

<span data-ttu-id="32107-109">Per aprire la finestra, selezionare la finestra di migrazione utilità del *Toolkit di realtà mista*  >    >  .</span><span class="sxs-lookup"><span data-stu-id="32107-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="32107-110">Una volta aperta la finestra di migrazione, è possibile abilitare le schede di navigazione in modalità selezione scegliendo l'implementazione specifica del componente del gestore di migrazione.</span><span class="sxs-lookup"><span data-stu-id="32107-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modalità di selezione della migrazione](../Images/MigrationWindow/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="32107-112">Modalità oggetto</span><span class="sxs-lookup"><span data-stu-id="32107-112">Object mode</span></span>

<span data-ttu-id="32107-113">Selezionando la scheda oggetti, viene abilitato il campo oggetto in cui l'utente può trascinare e rilasciare gli oggetti gioco dalla scena attualmente aperta o dai prefabbricati dalla cartella del progetto da migrare.</span><span class="sxs-lookup"><span data-stu-id="32107-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="32107-114">Premendo il pulsante Rimuovi *(-)* visualizzato a destra dell'oggetto elencato viene rimosso l'oggetto dall'elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="32107-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="32107-115">Una volta che tutti gli oggetti desiderati sono presenti nell'elenco, se si preme il pulsante *migra* verranno applicate le modifiche richieste dall'implementazione del gestore della migrazione scelta a tutti i componenti della selezione che corrispondono all'implementazione.</span><span class="sxs-lookup"><span data-stu-id="32107-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migrazione selezione](../Images/MigrationWindow/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="32107-117">Modalità scena</span><span class="sxs-lookup"><span data-stu-id="32107-117">Scene mode</span></span>

<span data-ttu-id="32107-118">Consente all'utente di trascinare e rilasciare asset della scena contenenti oggetti da migrare.</span><span class="sxs-lookup"><span data-stu-id="32107-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selezione di scene per la migrazione](../Images/MigrationWindow/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="32107-120">Modalità progetto</span><span class="sxs-lookup"><span data-stu-id="32107-120">Project mode</span></span>

<span data-ttu-id="32107-121">Quando si preme il pulsante *migra* , il componente di destinazione dell'implementazione del gestore della migrazione viene aggiornato per tutte le prefabbricate e le scene del progetto.</span><span class="sxs-lookup"><span data-stu-id="32107-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrazione di un progetto completo](../Images/MigrationWindow/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="32107-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="32107-123">See also</span></span>

- [<span data-ttu-id="32107-124">Aggiornamento da versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="32107-124">Updating from earlier versions</span></span>](../../updates-deployment/Updating.md)
- [<span data-ttu-id="32107-125">Versioni di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="32107-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../packages-releases/ReleaseNotes.md)
- [<span data-ttu-id="32107-126">Roadmap MRTK</span><span class="sxs-lookup"><span data-stu-id="32107-126">MRTK roadmap</span></span>](../../Contributing/Roadmap.md)
