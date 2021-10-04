---
title: Domande frequenti su SteamVR
description: La soluzione Windows Mixed Reality risoluzione dei problemi va oltre la documentazione di supporto standard per gli utenti.
author: qianwen
ms.author: v-qianwen
ms.date: 09/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, SteamVR
ms.openlocfilehash: 17ab1709e8a2fc7e3eee70082aef64f0dc23d318
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436801"
---
# <a name="steamvr-faqs"></a>Domande frequenti su SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Come si possono riprodurre giochi Per la riproduzione di video con il visore VR Windows Mixed Reality

1. [Scaricare e installare SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe) L'esercitazione di SteamVR dovrebbe essere avviata automaticamente all'avvio di SteamVR.
2. Connessione il visore VR sul PC e accendere i controller del movimento.
3. Dopo Windows Mixed Reality home page e i controller sono visibili, aprire l'app Steam sul desktop.
4. Usare l'app Steam per avviare un gioco Disatteso dalla libreria Di Lancio. Per avviare i giochi Disatteso di videogiochi senza spegnere il visore VR, individuarli e avviarli in Start Windows Mixed Reality'> **All Apps (Tutte le app).**

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Viene visualizzato il messaggio "Per usare SteamVR con Windows Mixed Reality, è necessario installare la versione più recente di Windows Update" o "è richiesta la modalità Windows developer"

1. Verificare che nel PC sia in esecuzione la versione più recente di Windows 10 o Windows 11. Passare **a Impostazioni > System > About**(Informazioni su) e in "Windows specifications" (Specifiche di Windows) assicurarsi che "OS Build" (Build sistema operativo) sia 16299.64 o versione successiva.
2. Assicurarsi che non siano presenti aggiornamenti in attesa di download o installazione. Passare a **Impostazioni > Update & Security > Windows Update** e selezionare "Check for updates" (Verifica disponibilità aggiornamenti). Potrebbe essere necessario controllare più volte finché non sono disponibili altri aggiornamenti e quindi riavviare il PC.

## <a name="steamvr-is-crashing-after-updating-windows"></a>Si verifica un arresto anomalo di SteamVR dopo l'Windows

Alcune versioni precedenti di Windows Mixed Reality per SteamVR non sono più compatibili con Windows. Per assicurarsi che la versione di Windows Mixed Reality per SteamVR sia aggiornata:

1. Nella libreria Di File system passare a **Software > Windows Mixed Reality for SteamVR**.
2. Fare clic con il pulsante destro del mouse su di esso e passare a "Proprietà".
3. Selezionare la scheda "Aggiorna" e "Mantieni sempre aggiornata l'applicazione".
4. Forzare l'aggiornamento selezionando la scheda "File locali" e selezionando "Verifica l'integrità dei file dell'applicazione".
5. Riavviare Steam e SteamVR.

Se l'arresto anomalo di SteamVR continua a verificarsi dopo l'aggiornamento, è possibile che nel computer Windows Mixed Reality due installazioni di Windows Mixed Reality per SteamVR. Per confermare:

1. Individuarlo ```%localappdata%\openvr\openvrpaths.vrpath``` e aprirlo in Blocco note.
2. Nelle sezioni "driver esterni" cercare più voci per "MixedRealityVRDriver"
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se vengono visualizzati più voci, rimuovere la meno recente delle due voci. Dopo aver creato una sola voce, non dovrebbe più essere presente una virgola alla fine della riga. Ad esempio:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salvare il file e chiuderlo.
5. Riavviare Steam e SteamVR.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>I controller non funzionano come previsto in SteamVR

1. Chiudere SteamVR.
2. Tornare a Windows Mixed Reality home e verificare che i controller funzionino.
3. Avviare di nuovo l'esperienza Disatteso e i controller dovrebbero tornare alla normalità.
4. Se i problemi persistono, inviare commenti [e suggerimenti Hub di Windows Feedback](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) nella categoria Realtà mista e includere SteamVR nel riepilogo.

I controller del movimento verranno utilizzati in modo diverso in giochi diversi. Ecco alcune nozioni di base per iniziare:
* Per aprire il dashboard di Steam, premere direttamente verso il basso sulla levetta sinistra.
* Per uscire da un gioco Disatteso e tornare Windows Mixed Reality home, premere il Windows pulsante. Selezionare quindi il pulsante Mixed Reality Home (Home di Realtà mista) visualizzato sullo schermo.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>I controller sinistro e destro sono invertti in SteamVR

Avviare il gioco con i controller disattivati e quindi accendere il controller sinistro, seguito da quello destro.

## <a name="my-games-are-running-slowly"></a>I miei giochi sono in esecuzione lentamente

1. Assicurarsi che il PC soddisfi le specifiche per SteamVR in Windows Mixed Reality e il gioco che si sta riproducendo.
2. Nella Portale realtà mista desktop selezionare "Sospendi" per arrestare l'anteprima del desktop.
3. Passare **a Impostazioni > System > About** (Informazioni su) e in "Windows specifications" (Specifiche di Windows) assicurarsi che "OS Build" (Build sistema operativo) sia 16299.64 o versione successiva.
4. Assicurarsi che il PC abbia i driver di grafica più recenti ("Verifica la disponibilità di aggiornamenti" in Windows Update).
5. Selezionare "Gestione attività" per vedere quali altri processi potrebbero utilizzare le risorse nel PC.
6. Verificare se Il tempo di esecuzione sta scaricando un gioco in background, che utilizza risorse e rende i giochi poco eseguiti in modo scadente.
7. Una piccola classe di app che non hanno una finestra visibile (ad esempio, Home di SteamVR) ha un problema di prestazioni noto. La maggior parte delle app non rientra in questa categoria e una correzione sarà disponibile in un aggiornamento futuro.

Se si verificano ancora problemi di prestazioni imprevisti, inviare commenti e suggerimenti [usando](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)il Hub di Windows Feedback . Assicurarsi di seguire le istruzioni per includere [una traccia delle prestazioni di SteamVR.](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>In SteamVR viene visualizzato un errore compositor (ad esempio, "Shared IPC Compositor Connessione Failed (400)").

Questo problema può verificarsi se il visore VR e il monitor principale si verificano in due schede video diverse. Collegare il monitor allo stesso adattatore del visore VR e configurarlo come monitor principale nell'app Impostazioni app > **System > Display**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Il contenuto di SteamVR viene visualizzato nella posizione sbagliata, ad esempio sotto il piano o sopra la testa

Reimpostare la posizione:

1. Selezionare la levetta del controller a sinistra per visualizzare il dashboard di SteamVR.
2. Selezionare il pulsante "Impostazioni".
3. Selezionare "Reset Seated Position".

## <a name="my-steam-app-closed-unexpectedly"></a>L'app My Steam è stata chiusa in modo imprevisto

L'app Steam verrà chiusa se:

* Blocco dello schermo del PC
* Rimuovere il visore VR
* Cambiare utente
* Il PC passa alla modalità sospensione
