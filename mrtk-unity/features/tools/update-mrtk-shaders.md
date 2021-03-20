---
title: ShaderUpdateTool
description: Documentazione su come aggiornare gli shader standard di MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e5ae9f12dfe4af899ae3d25af6dd0f076744b5c5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689381"
---
# <a name="updating-shaders"></a><span data-ttu-id="9e672-104">Aggiornamento degli shader</span><span class="sxs-lookup"><span data-stu-id="9e672-104">Updating Shaders</span></span>

<span data-ttu-id="9e672-105">A partire dalla versione 2.6.0, viene eseguito il controllo delle versioni degli shader MRTK tramite MRTK. File shaders. Sentinel.</span><span class="sxs-lookup"><span data-stu-id="9e672-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="9e672-106">Quando si esegue l'aggiornamento a una nuova versione di MRTK, è possibile che venga visualizzato il messaggio seguente.</span><span class="sxs-lookup"><span data-stu-id="9e672-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Richiedi aggiornamento shader](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="9e672-108">Selezionando **Sì si** indica a MRTK di sovrascrivere il contenuto degli **Asset**  >  **MRTK**  >  **shader** con la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="9e672-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="9e672-109">Se si seleziona No, i file correnti **non** vengono conservati.</span><span class="sxs-lookup"><span data-stu-id="9e672-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="9e672-110">**Ignora** creerà un file ( `IgnoreUpdateCheck.sentinel` ) in **Asset**  >  **MRTK**  >  **shaders**, che eliminerà i controlli di aggiornamento shader futuri.</span><span class="sxs-lookup"><span data-stu-id="9e672-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e672-111">Quando si sovrascrivono i file shader, le eventuali modifiche personalizzate andranno perse.</span><span class="sxs-lookup"><span data-stu-id="9e672-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="9e672-112">Assicurarsi di eseguire il backup dei file shader modificati prima dell'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9e672-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="9e672-113">Se il progetto è stato configurato per l'uso della pipeline di rendering universale (URP), in precedenza Lightweight render pipeline (LWRP) **, eseguire** di nuovo l' >  >
>  **aggiornamento di MRTK standard shader per la pipeline di rendering semplificata**.</span><span class="sxs-lookup"><span data-stu-id="9e672-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="9e672-114">È anche possibile verificare la disponibilità di aggiornamenti dello shader in qualsiasi momento usando le utilità del **Toolkit di realtà mista**  >    >  **per verificare la presenza di aggiornamenti dello shader** sulla barra dei menu dell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="9e672-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Verifica aggiornamenti shader](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="9e672-116">**Controllare se gli aggiornamenti dello shader** ignorano il `IgnoreUpdateCheck.sentinel` file e consentono l'aggiornamento su richiesta dello shader.</span><span class="sxs-lookup"><span data-stu-id="9e672-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="9e672-117">Il controllo degli aggiornamenti dello shader non è obbligatorio quando si importano i file MRTK. file unitypackage Tools.</span><span class="sxs-lookup"><span data-stu-id="9e672-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
