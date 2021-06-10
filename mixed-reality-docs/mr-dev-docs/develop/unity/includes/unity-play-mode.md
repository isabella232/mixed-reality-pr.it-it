---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345110"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. In HoloLens passare al Microsoft Store e **installare** l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. In HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Modifica** e selezionare **Project Settings (Impostazioni progetto).**
1. Selezionare **XR Plug-in Management (Gestione plug-in XR).**
1. Verificare che **la scheda Windows Autonomo** sia selezionata, trovare **OpenXR** **e Windows Mixed Reality set** di funzionalità nell'elenco e selezionare le relative caselle di controllo.
1. Passare quindi al menu **Finestra,** espandere il sottomenu **XR** e selezionare **OpenXR Editor Remoting.**
1. Fare clic **su Abilita comunicazione remota dell'editor.**
1. Se viene **visualizzato il pulsante Enable Missing Dependencies** (Abilita dipendenze mancanti), fare clic anche su di questo pulsante. La casella di errore sopra il pulsante descrive le funzionalità che sta abilitando e perché.
1. Per **Nome host remoto** immettere l'indirizzo IP di HoloLens.
   1. Modificare le altre impostazioni in base alle esigenze.
   1. L'editor tenterà di connettersi dopo l'avvio della modalità di riproduzione.
1. Seleziona il **pulsante Play** (Riproduci) per avviare la modalità di riproduzione e provare l'app in HoloLens.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

1. In HoloLens passare al Microsoft Store e **installare** l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. In HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Modifica** e selezionare **Project Settings (Impostazioni progetto).**
1. Selezionare **XR Plug-in Management (Gestione plug-in XR).**
1. Verificare che **la scheda Windows Autonomo** sia selezionata, Windows Mixed Reality nell'elenco e selezionare la relativa casella di controllo. 
1. Passare quindi al menu **Finestra,** espandere il sottomenu **XR** e selezionare Comunicazione remota del plug-in **Windows XR.**
1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.
1. Per **Computer remoto** immettere l'indirizzo IP di HoloLens.
1. Per connettersi:
   1. Per connettersi manualmente, **deselezionare Connetti durante la** riproduzione e selezionare **Connetti.** Lo stato **della connessione dovrebbe** essere modificato in **Connesso** e la schermata sarà vuota in HoloLens.
   1. Per connettersi automaticamente, selezionare **Connetti durante la riproduzione.** L'editor tenterà di connettersi dopo l'avvio della modalità di riproduzione.
1. Seleziona il **pulsante Play** (Riproduci) per avviare la modalità di riproduzione e provare l'app in HoloLens.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

1. In HoloLens passare al Microsoft Store e **installare** l'app **[Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. In HoloLens avviare l'app **Holographic Remoting Player.**
1. In Unity passare al menu **Finestra,** espandere il sottomenu **XR** e selezionare **Holographic Emulation (emulazione olografica)** contrassegnato come deprecato in Unity 2019.
1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.
1. Impostare **La versione** del dispositivo in base a se si usa un dispositivo HoloLens di prima generazione o un HoloLens 2.
1. Per **Computer remoto** immettere l'indirizzo IP di HoloLens.
1. Selezionare **Connetti**. Lo stato **della connessione dovrebbe** essere modificato in **Connesso** e la schermata sarà vuota in HoloLens.
1. Seleziona il **pulsante Play** (Riproduci) per avviare la modalità di riproduzione e provare l'app in HoloLens.
