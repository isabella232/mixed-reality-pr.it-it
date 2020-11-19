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
# <a name="installing-maquette"></a>Installazione di maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Installazione del logo ](../images/MaquetteIcon.png) MaquetteScript

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Lo sviluppo MaquetteScript viene eseguito principalmente in VSCode. MaquetteScript può essere eseguito dallo script contenuto nei `.mqjs` file e anche tramite un'interfaccia di estensione VSCode speciale. L'integrazione tra VSCode e maquette per abilitare l'interfaccia di estensione viene eseguita con un'estensione MaquetteScript VSCode.

## <a name="installing-the-vscode-extension"></a>Installazione dell'estensione VSCode

* Scaricare e installare [VSCode](https://code.visualstudio.com). 

L'estensione JavaScript maquette si trova nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Eseguire la [procedura di installazione per l'estensione](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Abilitazione degli script

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Per rendere accessibile lo scripting durante la versione non definitiva:

* Inserire un file con il nome `scripting.enabled` nella directory documenti utente per maquette in: `~/Documents/Maquette/Settings` .

Al termine dell'installazione, per motivi di sicurezza verrà disabilitato per impostazione predefinita lo scripting.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Per abilitare l'esecuzione dello script, attivarlo nella scheda principale della finestra complementare o nel file di impostazioni JSON.

![Abilitazione di script in VS Code](images/IntroductionEnableScripting.png)


