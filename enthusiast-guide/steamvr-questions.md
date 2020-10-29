---
title: Domande frequenti su SteamVR
description: Risoluzione avanzata dei problemi di Windows Mixed Reality che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, SteamVR
ms.openlocfilehash: 0e355fc5035d7966f52642058d2f0ecc91b88351
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685732"
---
# <a name="steamvr-faqs"></a>Domande frequenti su SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>In che modo è possibile riprodurre I giochi SteamVR nell'auricolare della realtà mista di Windows?

1. [Scaricare e installare SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). L'esercitazione su SteamVR dovrebbe essere avviata automaticamente all'avvio di SteamVR.
2. Connettere l'auricolare al PC e accendere i controller di movimento.
3. Quando la Home realtà mista di Windows è stata caricata e i controller sono visibili, aprire l'app Steam sul desktop.
4. Usare l'app Steam per avviare un gioco SteamVR dalla libreria di Steam. Per avviare giochi SteamVR senza togliere l'auricolare, trovarli e avviarli in Windows Real Reality ' s **Start > tutte le app** . 

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Un messaggio indica che "per usare SteamVR con la realtà mista di Windows, è necessario installare la versione più recente di Windows Update" o "Windows Developer Mode required".

1. Verificare che il PC esegua la versione più recente di Windows 10. Passare a **impostazioni > sistema > informazioni su** e in "specifiche Windows" assicurarsi che "Build sistema operativo" sia 16299,64 o superiore.
2. Assicurarsi che non siano presenti aggiornamenti in attesa di download o di installazione. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e selezionare "Verifica disponibilità aggiornamenti". Potrebbe essere necessario controllare più volte fino a quando non sono disponibili altri aggiornamenti e riavviare il PC.

## <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR si arresta in modo anomalo dopo l'aggiornamento di Windows.

Alcune versioni precedenti della realtà mista di Windows per SteamVR non sono più compatibili con Windows. Per assicurarsi che la versione di realtà mista di Windows per SteamVR sia aggiornata:
1. Nella libreria di Steam passare a **Software > realtà mista di Windows per SteamVR** .
2. Fare clic con il pulsante destro del mouse su di esso e passare a "Properties".
3. Selezionare la scheda "Aggiorna" e "Mantieni sempre aggiornata l'applicazione".
4. Forzare l'aggiornamento passando alla scheda "file locali" e selezionando "Verifica integrità dei file dell'applicazione".
5. Riavviare Steam e SteamVR.

Se SteamVR si arresta in modo anomalo dopo l'aggiornamento, è possibile che nel computer siano presenti due installazioni della realtà mista di Windows per SteamVR. Per verificare se questo è il caso:
1. Individuare ```%localappdata%\openvr\openvrpaths.vrpath``` e aprire il blocco note.
2. Nella sezione "driver esterni" cercare più voci per "MixedRealityVRDriver" 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se vengono visualizzate più voci, rimuovere le precedenti delle due voci. Quando si dispone di una sola voce, non dovrebbe più essere presente una virgola alla fine della riga. Ad esempio:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salvare il file e chiuderlo.
5. Riavviare Steam e SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>I controller non funzionano come previsto in SteamVR.

1. Chiudere SteamVR.
2. Tornare alla Home page della realtà mista di Windows e verificare che i controller funzionino.
3. Avviare di nuovo l'esperienza SteamVR e riportare i controller alla normalità.
4. Se i problemi permangono, inviare commenti e suggerimenti sui file usando l' [Hub feedback Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) nella categoria realtà mista e includere SteamVR nel riepilogo.

Si noti che i controller di movimento verranno usati in modo diverso in giochi diversi. Di seguito sono riportate alcune informazioni di base per iniziare:
* Per aprire il dashboard di Steam, premere il pulsante destro del mouse sul levetta di sinistra.
* Per uscire da un gioco SteamVR e tornare alla Home page della realtà mista di Windows, premere il pulsante Windows. Quindi selezionare il pulsante Home realtà mista visualizzato sullo schermo.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>I controller sinistro e destro sono invertiti in SteamVR.

Avviare il gioco con i controller e quindi accendere il controller di sinistra, seguito da quello destro.

## <a name="my-games-are-running-slowly"></a>I miei giochi vengono eseguiti lentamente.

1. Verificare che il PC soddisfi le specifiche per SteamVR in realtà mista di Windows e per il gioco SteamVR che si sta riproducendo.
2. Nel portale per la realtà mista sul desktop selezionare "Sospendi" per arrestare l'anteprima del desktop.
3. Passare a **impostazioni > sistema > informazioni su** e in "specifiche Windows", assicurarsi che "compilazione sistema operativo" sia 16299,64 o successiva.
4. Verificare che nel computer siano presenti i driver grafici più recenti ("Verifica disponibilità aggiornamenti" in Windows Update).
5. Controllare "Task Manager" per visualizzare gli altri processi che potrebbero richiedere risorse sul PC.
6. Verificare se il download di un gioco è in background. In questo modo è possibile utilizzare le risorse e far funzionare i giochi.
7. Una piccola classe di app che non dispongono di una finestra visibile (ad esempio, SteamVR Home), presenta un problema di prestazioni noto. La maggior parte delle app non rientra in questa categoria e una correzione sarà disponibile in un aggiornamento futuro.

Se si verificano ancora problemi di prestazioni imprevisti, inviare commenti e suggerimenti tramite l' [Hub feedback di Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Assicurarsi di seguire le istruzioni per [includere una traccia delle prestazioni di SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR Mostra un errore del Compositor (ad esempio, "Shared IPC compositor Connect failed (400)").

Questo problema può verificarsi se l'auricolare e il monitor primario si trovano su due schede video diverse. Alleghi il monitor alla stessa scheda della cuffia e configuri il monitoraggio in modo che sia il monitor primario in **impostazioni app > sistema > visualizzare** .

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Il contenuto di SteamVR viene visualizzato nella posizione sbagliata, ad esempio sotto il piano o sopra la mia testa.

Reimposta la posizione: 
1. Fare clic su levetta del controller di sinistra per visualizzare il "dashboard di SteamVR".
2. Selezionare il pulsante "Settings" (impostazioni).
3. Selezionare "Reimposta posizione posizionata".

## <a name="my-steam-app-closed-unexpectedly"></a>L'app Steam è stata chiusa in modo imprevisto.

L'app Steam verrà chiusa se si blocca lo schermo del PC, si rimuove l'auricolare, si comportano gli utenti o se il PC passa alla modalità sospensione.
