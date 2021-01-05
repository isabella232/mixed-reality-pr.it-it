---
title: Domande frequenti su sintesi vocale e audio
description: Risoluzione dei problemi della realtà mista di Windows vocale e audio che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, problemi audio, problemi di sintesi vocale
ms.openlocfilehash: d685190248dd17792f941cf53e3a57499cd3e662
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725892"
---
# <a name="speech-and-audio-faqs"></a>Domande frequenti su sintesi vocale e audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Non è possibile udire alcun suono nell'auricolare o riprodurre un suono nel computer anziché nell'auricolare

* Se la cuffia a immersione non include le cuffie predefinite, connettere le cuffie al jack audio sull'auricolare. Il Jack è spesso posizionato dietro o sotto la visiera o le lenti dell'auricolare. Se non è possibile trovarlo, rivolgersi al produttore dell'auricolare.
* Alcune cuffie audio dispongono di pulsanti fisici per controllare il volume. Se l'audio non funziona, controllare per verificare se il volume è disattivato o disattivato.
* Audio passerà al dispositivo Windows playback predefinito: 
    * Se si toglie l'auricolare
    * Capovolgere la visiera verso l'alto
    * Chiudere l'app del portale per la realtà mista
    * Quando un'app non è stata usata per 15 minuti. 
    * È possibile modificare questa impostazione in **impostazioni > realtà mista > audio e sintesi vocale.**
* Assicurarsi che la cuffia audio sia collegata all'audio Jack. In particolare, l'auricolare Acer potrebbe richiedere maggiore attenzione per assicurarsi che la cuffia audio sia collegata.
* Verificare che la cuffia audio/microfono sia collegata all'auricolare e non al PC.
* Il pannello di controllo audio in **impostazioni > sistema > audio** Mostra solo gli endpoint audio abilitati, non gli endpoint disabilitati. Il dispositivo audio Headset verrà disabilitato quando non si utilizza l'auricolare. Per visualizzarlo, fare clic con il pulsante destro del mouse nel pannello di controllo audio e scegliere "Mostra dispositivi disabilitati". Il nome del dispositivo è "Realtek USB 2.0 audio", che può essere rinominato nella pagina "Properties". Questa operazione può essere eseguita sia per le schede di riproduzione che di registrazione.
* Se l'audio non funziona in app a realtà mista, ad esempio, con l'app Netflix. Questa situazione potrebbe essere causata da un problema noto in cui la realtà mista di Windows non viene aggiornata automaticamente in modo da corrispondere alla versione del sistema operativo. Per risolvere questo problema e ottenere la migliore esperienza di realtà mista, passare a **impostazioni > aggiorna & sicurezza > Windows Update > verificare la disponibilità di aggiornamenti**.

> [!NOTE]
> * L'audio spaziale della realtà mista di Windows funziona meglio con le cuffie incorporate o connesse direttamente all'auricolare immersivo. Gli altoparlanti PC o le cuffie connesse al PC potrebbero non funzionare correttamente per l'audio spaziale.
> * La realtà mista di Windows non supporta le cuffie audio Bluetooth.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Si verificano modifiche improvvise del volume, audio perso o ronzio

* Alcune app, come quelle avviate tramite SteamVR, possono perdere audio o bloccarsi quando il dispositivo audio cambia quando si avvia o si arresta il portale di realtà mista. Per risolvere il problema, riaprire il portale per la realtà mista e riavviare l'app.
* Se un altro dispositivo USB multimediale, ad esempio una web cam, condivide lo stesso hub USB interno o esterno con l'auricolare della realtà mista di Windows, le cuffie o i jack audio della cuffia potrebbero occasionalmente avere un segnale acustico o nessun audio. Collegare la cuffia a una porta USB che usa un hub diverso oppure disconnettere/disabilitare l'altro dispositivo multimediale USB.
* Se si nota un forte aumento del rumore dalle cuffie connesse, l'hub USB del PC potrebbe non essere in grado di fornire una potenza sufficiente per l'auricolare della realtà mista di Windows. In tal caso, archiviare un bug dell' [Hub di feedback](https://docs.microsoft.com/hololens/hololens-feedback) e provare a:
    * rimozione di cavi di estensione
    * uso di un HUB USB 3,0 Basato su esterno dedicato
    * una porta USB diversa del PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>La cuffia audio Bluetooth non funziona come previsto

Microsoft non consiglia di usare cuffie audio Bluetooth con la realtà mista di Windows. Le periferiche audio Bluetooth non funzionano bene con le esperienze di audio e spaziali della realtà mista di Windows. Le cuffie audio Bluetooth non supportano l'input del microfono e l'output stereo allo stesso tempo, quindi non si riceverà un suono stereo o spaziale quando lo si usa per gamechat o altro input vocale. Le cuffie audio Bluetooth possono anche influire negativamente sull'esperienza del controller di movimento.

## <a name="sound-isnt-coming-from-expected-directions"></a>Il suono non è proveniente dalle direzioni previste

La Home realtà mista di Windows include il suono spaziale (audio che sembra provenga dalle applicazioni presenti nella Home Page). Man mano che ci si sposta e si passa da un'app all'altra, la direzione e il livello audio vengono modificati per aumentare il senso di realismo. Di seguito sono riportate alcune possibili cause di indicazioni non previste:

* Se si apre e si riproduce musica da un'app musicale in grado di supportare in background (ad esempio Groove Music) a casa e si apre un'esperienza di VR immersiva come un gioco, l'audio dalle dissolvenze delle app musicali da un suono spaziale a uno stereo. Potrebbe sembrare più rumoroso perché non c'è più nessuna distanza tra l'utente e il suono.
* Se Cortana è stato abilitato nel PC prima di usare l'auricolare con la realtà mista di Windows, è possibile perdere il suono spaziale applicato alle app nella Home realtà mista di Windows. Per risolvere il problema, disattivare "Let Cortana rispondere a Hey Cortana" in **Settings > Cortana** sul desktop prima di avviare la realtà mista di Windows o abilitare "Windows Sonic per le cuffie":
    1. Passare alla finestra app desktop nella Home page della realtà mista di Windows.
    2. Fare clic sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionarla nell'elenco dei dispositivi audio.
    3. Fare clic con il pulsante destro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare "Windows Sonic per le cuffie" nel menu "impostazione del relatore".
    4. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).

## <a name="speech-commands-are-not-working-as-expected"></a>I comandi di sintesi vocale non funzionano come previsto

* Per usare i comandi vocali, le impostazioni vocali e della lingua del PC devono essere impostate su una [lingua supportata in realtà mista di Windows](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Per verificare le impostazioni relative alla lingua e al linguaggio Windows, selezionare **impostazioni > ora & lingua > area & lingua** e **Impostazioni > lingua & lingua > voce**.
* Se la cuffia non ha un microfono incorporato, sarà necessario associare le cuffie con un microfono alla cuffia o al PC. Per fare in modo che l'input del microfono passa automaticamente all'auricolare quando lo si indossa, passare a **impostazioni > realtà mista > audio e vocale** e attivare "quando si indossa la cuffia, passare alla cuffia auricolare".
* Alcune cuffie audio hanno un pulsante fisico per disattivare e disattivare il microfono. Se i comandi di sintesi vocale non funzionano, verificare se il microfono è disattivato.
* Le cuffie audio con un microfono che penzola dal cavo di auricolari non vengono eseguite correttamente per i comandi vocali negli ambienti con rumore di ambiente.
* Cortana può essere lento la prima volta che viene richiamato in una sessione del portale per realtà mista. Passare a **impostazioni > Cortana > comunicare con Cortana** e assicurarsi che "Let Cortana Rispondi a Hey Cortana" sia abilitato.
* In alcuni PC, il guadagno predefinito di acquisizione voce per il microfono collegato all'auricolare può essere impostato su un valore troppo basso. Se si riscontrano comandi vocali o dettature non affidabili, eseguire la risoluzione dei problemi di installazione del microfono:
    1. Passare all'app desktop nella Home realtà mista di Windows con la cuffia (per influire sul microfono usato per la realtà mista di Windows).
    2. Passare a **impostazioni > ora & lingua > voce**.
    3. Selezionare "Get Started" nella sezione "Microphone".
    4. Selezionare l'endpoint appropriato nella procedura guidata per la risoluzione dei problemi.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ho una sola cuffia audio e voglio usarla sia per il desktop sia per la cuffia

Se è presente una sola cuffia audio e non è presente una cuffia con cuffie predefinite, connettere la cuffia audio al PC anziché l'auricolare. Disattivare quindi "passa a audio cuffia" nelle impostazioni del portale per la realtà mista.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Desidero passare a Dolby Atmos per le cuffie

Gli ambienti di realtà mista di Windows e le relative app utilizzano la tecnologia audio spaziale Windows Sonic per le cuffie, che è personalizzata per le esperienze di realtà miste. È possibile applicare altre tecnologie audio spaziali, ad esempio Dolby Atmos per le cuffie, per app a schermo intero come SteamVR, ma non per le app e gli ambienti della shell della realtà mista di Windows, ad esempio l'inserimento di un Web browser sul muro di Cliff House o Sky Loft, progettati con Windows Sonic per le cuffie acustiche e acustici spaziali.
