---
title: Finestra Di compilazione
description: Documentazione sull'uso della finestra di compilazione in MRTK per Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, compilazione, finestra di compilazione, strumenti
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176151"
---
# <a name="build-window"></a><span data-ttu-id="3b01a-104">Finestra Di compilazione</span><span class="sxs-lookup"><span data-stu-id="3b01a-104">Build window</span></span>
![Compilare & flusso di distribuzione](images/MRTK_BuildWindow0.png)

<span data-ttu-id="3b01a-106">La finestra di compilazione di MRTK semplifica la compilazione & distribuire i MRTK-Unity progetto.</span><span class="sxs-lookup"><span data-stu-id="3b01a-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="3b01a-107">Con un solo clic del pulsante, è possibile compilare il progetto Unity e generare Visual Studio soluzione(. SLN), pacchetto app UWP(. APPX) e installare il pacchetto dell'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3b01a-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="3b01a-108">Opzioni di compilazione di Unity</span><span class="sxs-lookup"><span data-stu-id="3b01a-108">Unity Build Options</span></span>
![Finestra di compilazione - Opzioni di compilazione di Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="3b01a-110">Queste scene sono del progetto Unity Build Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="3b01a-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="3b01a-111">È possibile modificare il tipo di dispositivo di destinazione usando il menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="3b01a-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="3b01a-112">Opzioni di compilazione appx</span><span class="sxs-lookup"><span data-stu-id="3b01a-112">Appx Build Options</span></span>
![Finestra Di compilazione - Opzioni di compilazione di Appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="3b01a-114">Questa scheda mostra la configurazione per la Visual Studio soluzione.</span><span class="sxs-lookup"><span data-stu-id="3b01a-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="3b01a-115">Per HoloLens 2 funzionalità di input di tracciamento oculare, selezionare **l'opzione Gaze Input Capability (Funzionalità di input sguardo** fisso).</span><span class="sxs-lookup"><span data-stu-id="3b01a-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="3b01a-116">È possibile assegnare il file con estensione glb nel campo Modello di avvio app **3D** per l'icona di avvio di app 3D personalizzata.</span><span class="sxs-lookup"><span data-stu-id="3b01a-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="3b01a-117">Per altre informazioni, vedere Linee guida per la progettazione dell'utilità di avvio di app [3D.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)</span><span class="sxs-lookup"><span data-stu-id="3b01a-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="3b01a-118">Per impostazione predefinita, **l'incremento** automatico è selezionato in Opzioni di controllo delle versioni.</span><span class="sxs-lookup"><span data-stu-id="3b01a-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="3b01a-119">Le versioni di AppX verranno incrementate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3b01a-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="3b01a-120">Opzioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="3b01a-120">Deploy Options</span></span>
![Finestra Di compilazione - Opzioni di distribuzione 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="3b01a-122">In questa scheda è possibile connettersi al dispositivo immettendo nome utente e password per il Portale di dispositivi.</span><span class="sxs-lookup"><span data-stu-id="3b01a-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="3b01a-123">Nella parte inferiore della pagina è possibile trovare l'elenco dei pacchetti dell'app creati.</span><span class="sxs-lookup"><span data-stu-id="3b01a-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

