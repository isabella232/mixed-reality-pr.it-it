---
title: Installazione di Maquette
description: Informazioni su come installare e configurare Maquette in VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipazione, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Feedback, Hub di Feedback, bug
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214772"
---
# <a name="installing-maquette"></a>Installazione di Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Logo ](../images/MaquetteIcon.png) Installazione di MaquetteScript

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Lo sviluppo maquetteScript viene eseguito principalmente all'interno di VSCode. MaquetteScript può essere eseguito da script contenuti nei `.mqjs` file e anche tramite una speciale interfaccia di estensione di VSCode. L'integrazione tra VSCode e Maquette per abilitare l'interfaccia di estensione viene eseguita con un'estensione VSCode MaquetteScript.

## <a name="installing-the-vscode-extension"></a>Installazione dell'estensione VSCode

* Scaricare e installare [VSCode.](https://code.visualstudio.com) 

L'estensione JavaScript Maquette è in [Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)

* Eseguire la [procedura di installazione per l'estensione](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Abilitazione dello scripting

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Per rendere accessibili gli script durante la versione non definitiva:

* Inserire un file con il nome `scripting.enabled` nella directory Users Documents per Maquette in: `~/Documents/Maquette/Settings` .

Dopo l'installazione, gli script verranno disabilitati per impostazione predefinita per motivi di sicurezza.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Per abilitare l'esecuzione dello script, attivarlo nella scheda principale della finestra complementare o nel file di impostazioni JSON.

![Abilitazione di script in VS Code](images/IntroductionEnableScripting.png)


