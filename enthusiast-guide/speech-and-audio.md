---
title: Domande frequenti su voce e audio
description: Riconoscimento vocale e audio Windows Mixed Reality risoluzione dei problemi che vanno oltre la documentazione di supporto per i consumer standard.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Problemi audio, Problemi vocali
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208981"
---
# <a name="speech-and-audio-faqs"></a>Domande frequenti su voce e audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Non è possibile ascoltare alcun suono nel visore o il suono viene riprodotto tramite il computer anziché tramite il visore

* Se il visore vr immersivo non include le cuffia incorporate, connettere le cuffia al jack audio sul visore. Il jack si trova spesso dietro o sotto la visiera o le lenti. Rivolgersi al produttore del visore se non è possibile trovarlo.
* Alcuni visori audio hanno pulsanti fisici per controllare il volume. Se l'audio non funziona, verificare se il volume è disattivato o disattivato.
* L'audio passa al dispositivo di riproduzione Windows predefinito: 
    * Se si tola il visore
    * Capovolgere la visiera verso l'alto
    * Chiudere l'app Portale realtà mista app
    * Quando un'app non viene usata per 15 minuti. 
    * È possibile modificare questa impostazione in Impostazioni > **realtà mista > audio e voce.**
* Assicurarsi che il visore audio sia collegato al jack audio. Il visore Acer, in particolare, può richiedere maggiore attenzione per assicurarsi che il visore audio sia collegato.
* Verificare che il microfono/visore audio sia collegato al visore e non al PC.
* L'Pannello di controllo audio in **Impostazioni > Sistema > audio** mostra solo gli endpoint audio abilitati, non gli endpoint disabilitati. Il dispositivo audio visore sarà disabilitato quando non si indossa il visore. Per visualizzarlo, fare clic con il pulsante destro del mouse nell'Pannello di controllo audio e scegliere "Mostra dispositivi disabilitati". Il nome del dispositivo è "Realtek USB2.0 Audio", che può essere rinominato nella pagina "Proprietà". È possibile eseguire questa operazione sia per le schede di riproduzione che per la registrazione.
* Se l'audio non funziona nelle app di realtà mista, ad esempio con l'app Netflix. Questo problema può essere causato da un problema noto per cui Windows Mixed Reality non viene aggiornato automaticamente in modo che corrisponda alla versione del sistema operativo. Per risolvere questo problema e ottenere la migliore esperienza di realtà mista, passare a Impostazioni > **Update & Security > Windows Update > Check for Updates**.

> [!NOTE]
> * Windows Mixed Reality'audio spaziale funziona meglio con le cuffia integrate o connesse direttamente al visore immersivo. Gli altoparlanti o le cuffia del PC connessi al PC potrebbero non funzionare correttamente per l'audio spaziale.
> * Windows Mixed Reality non supporta l'Bluetooth visore audio.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Si verificano cambiamenti improvvisi del volume, audio perso o ronzio

* Alcune app, come quelle avviate tramite SteamVR, possono perdere l'audio o bloccarsi quando il dispositivo audio cambia all'avvio o all'arresto del Portale realtà mista. Per risolvere il problema, riaprire il Portale realtà mista e riavviare l'app.
* Se un altro dispositivo USB multimediale (ad esempio una web cam) condivide lo stesso hub USB interno o esterno con il visore Windows Mixed Reality, il jack o le cuffia dell'audio del visore possono occasionalmente avere un suono ronzante o nessun audio. Collegare il visore a una porta USB che usa un hub diverso o disconnettere/disabilitare l'altro dispositivo multimediale USB.
* Se si nota un forte rumore dalle cuffia connesse, l'hub USB del PC potrebbe non essere in grado di fornire potenza sufficiente al visore Windows Mixed Reality telefono. In questo caso, determinare un bug [Hub di Feedback](/hololens/hololens-feedback) e provare:
    * rimozione di cavi di estensione
    * usando un HUB USB 3.0 dedicato e alimentato esternamente
    * una porta USB diversa nel PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Il Bluetooth visore audio non funziona come previsto

Microsoft non consiglia di usare Bluetooth visori audio con Windows Mixed Reality. Bluetooth periferiche audio non funzionano correttamente con le esperienze Windows Mixed Reality voce e del suono spaziale. Bluetooth visori audio non possono supportare contemporaneamente l'input del microfono e l'output stereo, quindi non si ode un suono stereo o spazializzato quando lo si usa per gamechat o altri input vocali. Bluetooth visori audio possono influire negativamente sull'esperienza del controller di movimento.

## <a name="sound-isnt-coming-from-expected-directions"></a>Il suono non proviene dalle direzioni previste

La Windows Mixed Reality Home include il suono spaziale (audio che sembra derivare dalle applicazioni che si trovano nella home page). Quando ci si volta e ci si avvicina o si allontana da ogni app, la direzione e il livello del suono cambieranno per aumentare il senso di realistico. Di seguito sono riportati alcuni possibili motivi per indicazioni sonore impreviste:

* Se si apre e si riproduce musica da un'app di musica con supporto per il sottofondo (ad esempio Groove Musica) in casa e quindi si apre un'esperienza VR immersiva come un gioco, il suono dell'app per la musica si incrocia dal suono spaziale allo stereo. Potrebbe sembrare più forte perché non c'è più distanza tra l'utente e il suono.
* Se l'Cortana è stata abilitata nel PC prima di usare il visore Windows Mixed Reality, è possibile che il suono spaziale applicato alle app nella Windows Mixed Reality home. Per risolvere questo problema, disattivare "Consenti Cortana di rispondere a Hey Cortana" in **Impostazioni > Cortana** sul desktop prima di avviare Windows Mixed Reality o abilitare "Windows Sonic per cuffie":
    1. Passare alla finestra Dell'app desktop in Windows Mixed Reality home page.
    2. Fare clic con il pulsante sinistro del mouse sull'icona del parlante sulla barra delle applicazioni desktop e selezionarla nell'elenco dei dispositivi audio.
    3. Fare clic con il pulsante destro del mouse sull'icona del parlante sulla barra delle applicazioni desktop e scegliere "Windows Sonic per cuffie" nel menu "Configurazione del parlante".
    4. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).

## <a name="speech-commands-are-not-working-as-expected"></a>I comandi vocali non funzionano come previsto

* Per usare i comandi vocali, le impostazioni vocali e della lingua nel PC devono essere impostate su una lingua [supportata in Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Per controllare le impostazioni relative Windows voce e lingua, selezionare Impostazioni > **Time & language > Region & language** e Impostazioni > Time & language > **Speech**.
* Se l'headset non ha un microfono incorporato, è necessario collegare le cuffia con un microfono al visore o al PC. Per fare in modo che l'input del microfono commuti automaticamente al visore quando lo si indossa, passare **a Impostazioni > Realtà** mista > Audio e voce e attivare "Quando indossi il visore, passa al microfono visore".
* Alcuni visori audio hanno un pulsante fisico per disattivare e riattivare il microfono. Se i comandi vocali non funzionano, verificare se il microfono è disattivato.
* I visori audio con un microfono che pentola dal cavo dell'auricolare non sono molto utilizzati per i comandi vocali in ambienti con rumore ambientale.
* Cortana può essere lenta la prima volta che viene richiamata in una Portale realtà mista sessione. Passare a **Impostazioni > Cortana > Talk to Cortana** (Consenti Cortana rispondere a Hey Cortana) sia abilitato.
* In alcuni PC, il guadagno di acquisizione vocale predefinito per il microfono connesso con visore potrebbe essere impostato su un valore troppo basso. Se si verificano comandi vocali o dettatura inaffidabili, eseguire lo strumento di risoluzione dei problemi di Configurazione microfono:
    1. Passare all'app Desktop nella casa Windows Mixed Reality mentre si indossa il visore (per influire sul microfono che si usa per Windows Mixed Reality).
    2. Passare a **Impostazioni > ora & lingua > voce**.
    3. Selezionare "Informazioni di base" nella sezione "Microfono".
    4. Selezionare l'endpoint appropriato nella procedura guidata per la risoluzione dei problemi.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ho un solo visore audio e voglio usarlo sia per desktop che per il visore

Se si ha un solo visore audio e non si dispone di un visore con le cuffia incorporate, connettere il visore audio al PC anziché al visore. Disattivare quindi l'opzione "Passa all'audio del visore" nelle impostazioni Portale realtà mista video.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Si vuole passare a Dolby Atmos for Headphones

Windows Mixed Reality ambienti e le relative app usano Windows Sonic per cuffie audio spaziale, che è personalizzata per le esperienze di realtà mista. Altre tecnologie di audio spaziale, ad esempio Dolby Atmos for Headphones, possono essere applicate per app a schermo intero come giochi di SteamVR, ma non per gli ambienti e le app della shell di Windows Mixed Reality (ad esempio, l'inserimento di un Web browser sulla parete del Casa sulla scogliera o sky sky) progettate usando il suono spaziale e l'acustica di Windows Sonic per cuffie.