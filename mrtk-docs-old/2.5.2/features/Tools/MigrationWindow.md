---
title: MigrationWindow
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a670a3c1fb68037a8ecf8989dd0a84f8e0407e62
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693858"
---
# <a name="migration-window"></a><span data-ttu-id="8f08d-104">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="8f08d-104">Migration window</span></span>

<span data-ttu-id="8f08d-105">Quando il MRTK subisce modifiche, è possibile che alcuni componenti vengano deprecati e che vengano introdotti sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="8f08d-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="8f08d-106">La finestra migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.</span><span class="sxs-lookup"><span data-stu-id="8f08d-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Finestra di migrazione](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="8f08d-108">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="8f08d-108">Usage</span></span>

<span data-ttu-id="8f08d-109">Per aprire la finestra, selezionare la finestra di migrazione utilità del *Toolkit di realtà mista*  >    >  .</span><span class="sxs-lookup"><span data-stu-id="8f08d-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="8f08d-110">Una volta aperta la finestra di migrazione, è possibile abilitare le schede di navigazione in modalità selezione scegliendo l'implementazione specifica del componente del gestore di migrazione.</span><span class="sxs-lookup"><span data-stu-id="8f08d-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modalità di selezione della migrazione](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="8f08d-112">Modalità oggetto</span><span class="sxs-lookup"><span data-stu-id="8f08d-112">Object mode</span></span>

<span data-ttu-id="8f08d-113">Selezionando la scheda oggetti, viene abilitato il campo oggetto in cui l'utente può trascinare e rilasciare gli oggetti gioco dalla scena attualmente aperta o dai prefabbricati dalla cartella del progetto da migrare.</span><span class="sxs-lookup"><span data-stu-id="8f08d-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="8f08d-114">Premendo il pulsante Rimuovi *(-)* visualizzato a destra dell'oggetto elencato viene rimosso l'oggetto dall'elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="8f08d-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="8f08d-115">Una volta che tutti gli oggetti desiderati sono presenti nell'elenco, se si preme il pulsante *migra* verranno applicate le modifiche richieste dall'implementazione del gestore della migrazione scelta a tutti i componenti della selezione che corrispondono all'implementazione.</span><span class="sxs-lookup"><span data-stu-id="8f08d-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migrazione selezione](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="8f08d-117">Modalità scena</span><span class="sxs-lookup"><span data-stu-id="8f08d-117">Scene mode</span></span>

<span data-ttu-id="8f08d-118">Consente all'utente di trascinare e rilasciare asset della scena contenenti oggetti da migrare.</span><span class="sxs-lookup"><span data-stu-id="8f08d-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selezione di scene per la migrazione](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="8f08d-120">Modalità progetto</span><span class="sxs-lookup"><span data-stu-id="8f08d-120">Project mode</span></span>

<span data-ttu-id="8f08d-121">Quando si preme il pulsante *migra* , il componente di destinazione dell'implementazione del gestore della migrazione viene aggiornato per tutte le prefabbricate e le scene del progetto.</span><span class="sxs-lookup"><span data-stu-id="8f08d-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrazione di un progetto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="8f08d-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8f08d-123">See also</span></span>

- [<span data-ttu-id="8f08d-124">Aggiornamento da versioni precedenti</span><span class="sxs-lookup"><span data-stu-id="8f08d-124">Updating from earlier versions</span></span>](../../updates-deployment/Updating.md)
- [<span data-ttu-id="8f08d-125">Versioni di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="8f08d-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../packages-releases/ReleaseNotes.md)
- [<span data-ttu-id="8f08d-126">Roadmap MRTK</span><span class="sxs-lookup"><span data-stu-id="8f08d-126">MRTK roadmap</span></span>](../../Roadmap.md)
