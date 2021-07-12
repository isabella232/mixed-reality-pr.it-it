---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603726"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:

> [!div class="nextstepaction"]
> [Configurare un nuovo progetto OpenXR con MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Se si aggiorna un progetto MRTK esistente a **OpenXR,** è prima di tutto necessario aggiornare MRTK-Unity alla versione più recente (versione 2.7.2 o successiva) per ottenere correzioni chiave per la compatibilità con il plug-in OpenXR di realtà mista.  Usare [mixed reality feature tool](../../welcome-to-mr-feature-tool.md) per eseguire l'aggiornamento alla versione più recente di MRTK e quindi seguire la procedura di configurazione [manuale di OpenXR riportata di seguito.](#manual-setup-without-mrtk) Per informazioni più dettagliate sulla migrazione di un progetto MRTK esistente a [OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK .

> [!NOTE]
> Quando si esegue l'aggiornamento da una versione precedente di MRTK precedente alla **2.5.3,** assicurarsi che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:

> [!div class="nextstepaction"]
> [Configurare un nuovo progetto Windows XR con MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Per iniziare a usare un **nuovo progetto Unity** con MRTK, iniziare dal passaggio 2 dell'esercitazione su MRTK:

> [!div class="nextstepaction"]
> [Configurare un nuovo progetto XR legacy con MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)