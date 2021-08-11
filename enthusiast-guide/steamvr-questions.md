---
title: Domande frequenti su SteamVR
description: SteamVR Windows Mixed Reality risoluzione dei problemi che vanno oltre la documentazione del supporto clienti standard.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, SteamVR
ms.openlocfilehash: 0fb9c07dda8fe354966403bc9c6a21acb600e61cb943c270eb9c87f5ec2fb89a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199497"
---
# <a name="steamvr-faqs"></a>Domande frequenti su SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Come si possono riprodurre giochi di SteamVR nel visore Windows Mixed Reality visore

1. [Scaricare e installare SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe) L'esercitazione su SteamVR dovrebbe essere avviata automaticamente all'avvio di SteamVR.
2. Connessione il visore al PC e accendere i controller di movimento.
3. Dopo Windows Mixed Reality la home page e i controller sono visibili, aprire l'app Steam sul desktop.
4. Usare l'app Steam per avviare un gioco di SteamVR dalla libreria di Steam. Per avviare giochi di SteamVR senza spegnere il visore, trovarli e avviarli in **Start Windows Mixed Reality'> All Apps (Tutte le app).**

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Viene visualizzato il messaggio "Per usare SteamVR con Windows Mixed Reality, è necessario installare l'aggiornamento Windows più recente" o "Windows Developer Mode Required"

1. Assicurarsi che nel PC sia in esecuzione la versione più recente di Windows 10. Passare **a Impostazioni > System > About**(Informazioni su) e in "Windows specifications" (Specifiche del sistema operativo) assicurarsi che "OS Build" sia 16299.64 o versione successiva.
2. Assicurarsi di non avere aggiornamenti in attesa di download o installazione. Passare a **Impostazioni > Aggiornamento & sicurezza > Windows e** selezionare "Controlla aggiornamenti". Potrebbe essere necessario controllare più volte finché non sono disponibili altri aggiornamenti e quindi riavviare il PC.

## <a name="steamvr-is-crashing-after-updating-windows"></a>Si verifica un arresto anomalo di SteamVR dopo l'aggiornamento Windows

Alcune versioni precedenti di Windows Mixed Reality per SteamVR non sono più compatibili con Windows. Per assicurarsi che la versione di Windows Mixed Reality per SteamVR sia aggiornata:

1. Nella libreria di Steam passare a **Software > Windows Mixed Reality per SteamVR.**
2. Fare clic con il pulsante destro del mouse su di esso e scegliere "Proprietà".
3. Selezionare la scheda "Aggiorna" e "Mantieni sempre aggiornata l'applicazione".
4. Forzare l'aggiornamento andando alla scheda "File locali" e selezionando "Verifica integrità dei file dell'applicazione".
5. Riavviare Steam e SteamVR.

Se l'arresto anomalo di SteamVR si arresta ancora dopo l'aggiornamento, è possibile che nel computer Windows Mixed Reality per SteamVR. Per confermare:

1. Individuarlo ```%localappdata%\openvr\openvrpaths.vrpath``` e aprirlo in Blocco note.
2. Nelle sezioni "Driver esterni" cercare più voci per "MixedRealityVRDriver"
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se vengono visualizzati più voci, rimuovere la voce precedente delle due voci. Dopo aver creato una sola voce, non deve più essere presente una virgola alla fine della riga. Ad esempio:
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
3. Avviare di nuovo l'esperienza di SteamVR e i controller dovrebbero tornare alla normalità.
4. Se i problemi persistono, inviare commenti e [suggerimenti Hub di Windows Feedback](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) nella categoria Realtà mista e includere SteamVR nel riepilogo.

I controller di movimento verranno utilizzati in modo diverso in giochi diversi. Ecco alcune nozioni di base per iniziare:
* Per aprire il dashboard di Steam, premere direttamente verso il basso sulla levetta a sinistra.
* Per uscire da un gioco di SteamVR e tornare Windows Mixed Reality home, premere il Windows pulsante. Selezionare quindi il pulsante Home di Mixed Reality visualizzato sullo schermo.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>I controller sinistro e destro vengono invertiniti in SteamVR

Avviare il gioco con i controller spenti e quindi accendere il controller a sinistra, seguito da quello destro.

## <a name="my-games-are-running-slowly"></a>I giochi vengono eseguiti lentamente

1. Assicurarsi che il PC soddisfi le specifiche di SteamVR Windows Mixed Reality e del gioco in uso.
2. Nella Portale realtà mista sul desktop selezionare "Sospendi" per arrestare l'anteprima del desktop.
3. Passare **a Impostazioni > System > About** (Informazioni su) e in "Windows specifications" (Specifiche del sistema operativo) assicurarsi che "OS Build" sia 16299.64 o versione successiva.
4. Assicurarsi che il PC abbia i driver di grafica più recenti ("Controlla aggiornamenti" in Windows Update).
5. Controllare "Gestione attività" per vedere quali altri processi potrebbero utilizzare le risorse nel PC.
6. Verificare se Steam sta scaricando un gioco in background, che usa le risorse e rende i giochi non eseguiti in modo scadente.
7. Una piccola classe di app che non hanno una finestra visibile (ad esempio, La home page di SteamVR) ha un problema di prestazioni noto. La maggior parte delle app non rientra in questa categoria e una correzione sarà disponibile in un aggiornamento futuro.

Se si verificano ancora problemi di prestazioni imprevisti, inviare commenti e suggerimenti [usando](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)il Hub di Windows Feedback . Assicurarsi di seguire le istruzioni per includere [una traccia delle prestazioni di SteamVR.](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>In SteamVR viene visualizzato un errore di composizione,ad esempio "Shared IPC Compositor Connessione Failed (400)").

Questo problema può verificarsi se il visore visore e il monitor primario sono su due schede video diverse. Collegare il monitor allo stesso adattatore del visore e configurarlo come monitoraggio primario nell'app Impostazioni app > **Sistema > Display**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Il contenuto di SteamVR viene visualizzato nel posto sbagliato, ad esempio sotto il pavimento o sopra la testa

Reimpostare la posizione:

1. Selezionare la levetta personale del controller sinistro per visualizzare il dashboard di SteamVR.
2. Selezionare il pulsante "Impostazioni".
3. Selezionare "Reset Seated Position".

## <a name="my-steam-app-closed-unexpectedly"></a>L'app Steam è stata chiusa in modo imprevisto

L'app Disattesa verrà chiusa se:

* Bloccare lo schermo del PC
* Rimuovere il visore
* Cambiare utente
* Il PC passa alla modalità sospensione
