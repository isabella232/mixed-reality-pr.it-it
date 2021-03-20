---
title: Autorizzazione delle modifiche al progetto
description: Informazioni su come autorizzare le modifiche apportate al progetto lo strumento per lo sviluppo HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230773"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="8d86a-104">Autorizzazione delle modifiche al progetto</span><span class="sxs-lookup"><span data-stu-id="8d86a-104">Authorizing project changes</span></span>

<span data-ttu-id="8d86a-105">Prima di modificare il progetto Unity, è necessario rivedere e approvare le modifiche apportate al manifesto e ai file di progetto:</span><span class="sxs-lookup"><span data-stu-id="8d86a-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Richiesta dell'autorizzazione](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="8d86a-107">manifesto</span><span class="sxs-lookup"><span data-stu-id="8d86a-107">Manifest</span></span>

<span data-ttu-id="8d86a-108">Le modifiche al manifesto proposte possono essere visualizzate nella colonna **manifesto** a sinistra.</span><span class="sxs-lookup"><span data-stu-id="8d86a-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="8d86a-109">Il contenuto è esattamente ciò che verrà scritto nel manifesto del progetto (**packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="8d86a-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Anteprima manifesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="8d86a-111">File da copiare nel progetto</span><span class="sxs-lookup"><span data-stu-id="8d86a-111">Files to be copied into the project</span></span>

<span data-ttu-id="8d86a-112">I **file da copiare nella sezione Project** a destra elencano i file specifici del pacchetto di funzionalità che verranno copiati nel progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="8d86a-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Anteprima del manifesto con i file da copiare](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="8d86a-114">Confronta manifesti</span><span class="sxs-lookup"><span data-stu-id="8d86a-114">Compare manifests</span></span>

<span data-ttu-id="8d86a-115">È possibile visualizzare un confronto affiancato dettagliato di tutte le modifiche proposte selezionando **Confronta**:</span><span class="sxs-lookup"><span data-stu-id="8d86a-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Confronta manifesti](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="8d86a-117">Approvazione delle modifiche</span><span class="sxs-lookup"><span data-stu-id="8d86a-117">Approving changes</span></span>

<span data-ttu-id="8d86a-118">Quando vengono approvate le modifiche proposte, i file elencati verranno copiati nel progetto Unity e il manifesto verrà aggiornato con i riferimenti a questi file.</span><span class="sxs-lookup"><span data-stu-id="8d86a-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="8d86a-119">I file del pacchetto di funzionalità (\*. tgz) devono essere aggiunti al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="8d86a-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="8d86a-120">Viene fatto riferimento usando un percorso relativo per consentire ai team di sviluppo di condividere facilmente le funzionalità e le modifiche del manifesto.</span><span class="sxs-lookup"><span data-stu-id="8d86a-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="8d86a-121">Come parte delle modifiche, verrà eseguito il backup del **manifest.jscorrente sul** file.</span><span class="sxs-lookup"><span data-stu-id="8d86a-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d86a-122">Quando si visualizzano i backup del manifesto, il meno recente verrà chiamato **manifest.json. backup**.</span><span class="sxs-lookup"><span data-stu-id="8d86a-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="8d86a-123">I backup più recenti verranno annotati con un valore numerico, a partire da zero (0).</span><span class="sxs-lookup"><span data-stu-id="8d86a-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="8d86a-124">Tornando al passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="8d86a-124">Going back to the previous step</span></span>

<span data-ttu-id="8d86a-125">Se è necessario apportare modifiche alle selezioni delle funzionalità, usare **tornare indietro** per tornare al passaggio di [importazione](importing-features.md) .</span><span class="sxs-lookup"><span data-stu-id="8d86a-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d86a-126">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8d86a-126">See also</span></span>

- [<span data-ttu-id="8d86a-127">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="8d86a-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="8d86a-128">Importazione dei pacchetti selezionati</span><span class="sxs-lookup"><span data-stu-id="8d86a-128">Importing selected packages</span></span>](importing-features.md)
