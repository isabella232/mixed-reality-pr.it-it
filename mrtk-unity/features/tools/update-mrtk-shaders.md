---
title: Strumento di aggiornamento shader
description: Documentazione su come aggiornare gli shader standard MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647091"
---
# <a name="updating-shaders"></a><span data-ttu-id="00e2f-104">Aggiornamento degli shader</span><span class="sxs-lookup"><span data-stu-id="00e2f-104">Updating Shaders</span></span>

<span data-ttu-id="00e2f-105">A partire dalla versione 2.6.0, il controllo delle versioni degli shader MRTK viene effettuato tramite MRTK. File Shaders.sentinel.</span><span class="sxs-lookup"><span data-stu-id="00e2f-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="00e2f-106">Quando si esegue l'aggiornamento a una nuova versione di MRTK, potrebbe essere visualizzato il messaggio seguente.</span><span class="sxs-lookup"><span data-stu-id="00e2f-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Richiesta di aggiornamento shader](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="00e2f-108">Selezionando **Sì** si indica a MRTK di sovrascrivere il contenuto degli shader   >  **MRTK** degli asset  >   con la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="00e2f-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="00e2f-109">Se **si seleziona No,** i file correnti verranno mantenuti.</span><span class="sxs-lookup"><span data-stu-id="00e2f-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="00e2f-110">**Ignore** creerà un file ( `IgnoreUpdateCheck.sentinel` ) in   >  **Assets MRTK**  >  **Shaders**, che elimina i controlli futuri degli aggiornamenti dello shader.</span><span class="sxs-lookup"><span data-stu-id="00e2f-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00e2f-111">Quando si sovrascriveno i file shader, tutte le modifiche personalizzate andranno perse.</span><span class="sxs-lookup"><span data-stu-id="00e2f-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="00e2f-112">Assicurarsi di eseguire il backup di tutti i file shader modificati prima dell'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="00e2f-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="00e2f-113">Se il progetto è stato configurato per l'uso della pipeline di rendering universale (URP, Universal Render Pipeline), in precedenza Lightweight Render Pipeline (LWRP), esegui di nuovo **Mixed Reality** > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span><span class="sxs-lookup"><span data-stu-id="00e2f-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="00e2f-114">In è anche possibile verificare la disponibilità di aggiornamenti dello shader in qualsiasi momento usando **Mixed Reality** Toolkit Utilities Check for Shader Updates (Verifica la disponibilità di aggiornamenti dello shader) sulla barra dei  >    >    >   menu dell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="00e2f-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Verificare la disponibilità di aggiornamenti dello shader](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="00e2f-116">**Controlla aggiornamenti shader ignora** il `IgnoreUpdateCheck.sentinel` file e consente l'aggiornamento dello shader su richiesta.</span><span class="sxs-lookup"><span data-stu-id="00e2f-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="00e2f-117">La verifica degli aggiornamenti dello shader non è necessaria quando si importano i file UNITYPACKAGE di MRTK.</span><span class="sxs-lookup"><span data-stu-id="00e2f-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
