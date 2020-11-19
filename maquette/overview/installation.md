---
title: Installazione di maquette
description: Informazioni su come installare e configurare maquette in VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realtà mista di Windows, maquette, prototipi, realtà mista, realtà virtuale, VR, MR, feedback, hub di feedback, bug
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935426"
---
# <a name="installing-maquette"></a><span data-ttu-id="8217e-104">Installazione di maquette</span><span class="sxs-lookup"><span data-stu-id="8217e-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="8217e-105">![Installazione del logo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="8217e-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="8217e-106">Lo sviluppo MaquetteScript viene eseguito principalmente in VSCode.</span><span class="sxs-lookup"><span data-stu-id="8217e-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="8217e-107">MaquetteScript può essere eseguito dallo script contenuto nei `.mqjs` file e anche tramite un'interfaccia di estensione VSCode speciale.</span><span class="sxs-lookup"><span data-stu-id="8217e-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="8217e-108">L'integrazione tra VSCode e maquette per abilitare l'interfaccia di estensione viene eseguita con un'estensione MaquetteScript VSCode.</span><span class="sxs-lookup"><span data-stu-id="8217e-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="8217e-109">Installazione dell'estensione VSCode</span><span class="sxs-lookup"><span data-stu-id="8217e-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="8217e-110">Scaricare e installare [VSCode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="8217e-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="8217e-111">L'estensione JavaScript maquette si trova nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="8217e-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="8217e-112">Eseguire la [procedura di installazione per l'estensione](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="8217e-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="8217e-113">Abilitazione degli script</span><span class="sxs-lookup"><span data-stu-id="8217e-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="8217e-114">Per rendere accessibile lo scripting durante la versione non definitiva:</span><span class="sxs-lookup"><span data-stu-id="8217e-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="8217e-115">Inserire un file con il nome `scripting.enabled` nella directory documenti utente per maquette in: `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="8217e-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="8217e-116">Al termine dell'installazione, per motivi di sicurezza verrà disabilitato per impostazione predefinita lo scripting.</span><span class="sxs-lookup"><span data-stu-id="8217e-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="8217e-117">Per abilitare l'esecuzione dello script, attivarlo nella scheda principale della finestra complementare o nel file di impostazioni JSON.</span><span class="sxs-lookup"><span data-stu-id="8217e-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Abilitazione di script in VS Code](images/IntroductionEnableScripting.png)


