---
ms.openlocfilehash: f7a018d34ee17589ae2e12c2f50f744d736534e2
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114339498"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. Nel HoloLens passare al Microsoft Store **e** installare l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Nel HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Modifica** e **selezionare** Project Impostazioni .
1. Selezionare **Gestione plug-in XR.**
1. Assicurarsi che **Windows la scheda Autonomo,** trovare **OpenXR** **e Windows Mixed Reality funzionalità** nell'elenco e selezionare le relative caselle di controllo.
1. Passare quindi al menu **Finestra,** espandere il sottomenu **XR** e selezionare **OpenXR Editor Remoting**.

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../images/openxr-features-img-02.png)

1. Fare clic **su Abilita comunicazione remota dell'editor**.

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con funzionalità evidenziate](../images/openxr-features-img-03.png)

1. Se viene **visualizzato il pulsante Abilita dipendenze** mancanti, fare clic anche su di questo. La casella di errore sopra il pulsante descrive le funzionalità che abilita e perché.
1. Per **Nome host remoto** immettere l'indirizzo IP del HoloLens.
   1. Modificare altre impostazioni in base alle esigenze.
   1. L'editor tenterà di connettersi dopo l'avvio della modalità di riproduzione.
1. Selezionare il **pulsante Riproduci** per avviare la modalità di riproduzione e provare l'app nel HoloLens. Per eseguire il debug di script C# in modalità di [riproduzione, Visual Studio a Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

> [!NOTE]
> A causa della versione 0.1.0, il runtime di Holographic Remoting non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.  Questa funzionalità sarà disponibile nelle versioni future.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows plug-in XR](#tab/winxr)

1. Nel HoloLens passare al Microsoft Store **e** installare l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Nel HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Modifica** e **selezionare** Project Impostazioni .
1. Selezionare **Gestione plug-in XR.**
1. Assicurarsi che **la scheda PC, Mac & Linux autonomo** sia selezionata, trovare Windows Mixed Reality nell'elenco e selezionare la relativa casella di controllo. 
1. Passare quindi al menu **Finestra,** espandere il sottomenu **XR** e selezionare Windows comunicazione remota **del plug-in XR.**
1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.
1. Per **Computer remoto** immettere l'indirizzo IP del HoloLens.
1. Per connettersi, eseguire una delle seguenti:
   1. Per connettersi manualmente, deselezionare Connessione **su Riproduci** e selezionare **Connessione**. Lo stato **della connessione dovrebbe** essere modificato in **Connesso** e la schermata dovrebbe essere vuota nel HoloLens.
   1. Per connettersi automaticamente, selezionare **Connessione su Riproduci**. L'editor tenterà di connettersi dopo l'avvio della modalità di riproduzione.
1. Selezionare il **pulsante Riproduci** per avviare la modalità di riproduzione e provare l'app nel HoloLens. Per eseguire il debug di script C# in modalità di [riproduzione, Visual Studio a Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

1. Nel HoloLens passare al Microsoft Store **e** installare l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Nel HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Finestra,** espandere il sottomenu **XR** e selezionare **Emulazione olografica** (contrassegnata come deprecata in Unity 2019).
1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.
1. Impostare **Versione del** dispositivo in base a se si usa una versione di prima HoloLens o una HoloLens 2.
1. Per **Computer remoto** immettere l'indirizzo IP del HoloLens.
1. Selezionare **Connetti**. Lo stato **della connessione dovrebbe** essere modificato in **Connesso** e la schermata dovrebbe essere vuota nel HoloLens.
1. Selezionare il **pulsante Riproduci** per avviare la modalità di riproduzione e provare l'app nel HoloLens. Per eseguire il debug di script C# in modalità di [riproduzione, Visual Studio a Unity.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)
