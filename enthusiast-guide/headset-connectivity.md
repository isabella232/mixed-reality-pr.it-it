---
title: Domande frequenti sulla connettività del visore VR
description: La connettività del visore Windows Mixed Reality risoluzione dei problemi di connettività del visore VR che va oltre la documentazione del supporto consumer standard.
author: qianwen
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Visore VR
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 47c726c5beeac0463fe4286bd7a949e4e4d4cc45
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436614"
---
# <a name="headset-connectivity-faqs"></a>Domande frequenti sulla connettività del visore VR

## <a name="my-headset-will-not-wake-up"></a>Il visore VR non si riattiva

Se il visore VR è in sospensione e fare clic sul pulsante di riattivazione non funziona, riavviare il PC.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Il computer non dispone di un HDMI e/o di una porta di visualizzazione

Potrebbe essere necessario usare un adapter. Fare [clic qui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) per un elenco delle schede supportate.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>È possibile usare cavi di estensione USB o HDMI e/o DisplayPort con Windows Mixed Reality visori VR?

Windows Mixed Reality visori VR non supportano ufficialmente l'uso di cavi di estensione USB, HDMI o DisplayPort. Se si usano questi cavi, l'esperienza di realtà mista potrebbe essere interessata da variazioni nell'integrità dei segnali e dalla potenza del bus tra il controller USB del PC e il visore VR di Realtà mista. Provare a usare il visore VR senza cavi di estensione se:

* Il visore VR visualizza brevemente una schermata blu e quindi diventa nero e Portale realtà mista riavvia o denumera completamente durante l'uso
* L'audio del visore VR si taglia o diventa glitch
* Lo sfarfallio del visore VR tra il nero e lo schermo corretto

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Viene visualizzato l'errore "Controllare il cavo video"

* Se si usano adattatori per connettere il visore VR al PC, assicurarsi che supportino Windows Mixed Reality e supportino 4K. Provare anche a connettere l'adattatore al PC prima di collegare il visore VR all'adattatore.
* Provare a usare una porta HDMI o DisplayPort diversa.
* Connessione il visore VR a DisplayPort 1.2 o versione successiva o HDMI 1.4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.
* Se il PC ha grafica integrata e discreta, assicurarsi di usare la porta HDMI o DisplayPort nella scheda grafica attiva. Ciò potrebbe significare che sarà necessario connettere lo schermo del PC a una porta non HDMI.
* Se il PC ha grafica integrata e discreta e la grafica integrata è meno recente e non supporta Windows Mixed Reality, provare a disabilitare la GPU integrata.
* Connessione un monitor PC alla porta HDMI o DisplayPort del PC. Assicurarsi che i driver di grafica siano aggiornati. Scaricare e installare i driver direttamente da AMD, Nvidia o Intel, perché probabilmente saranno più recenti di quelli pubblicati in Windows Update.
* Se si dispone di un monitor esterno collegato a una porta HDMI, provare a collegarlo a un displayport e usare la porta HDMI per il visore VR.
* Assicurarsi di aver collegato il cavo HDMI del visore VR a una porta "HDMI out" sul PC, non a una porta "HDMI in ingresso".
* Windows potrebbe non essere in grado di rilevare la connessione del cavo video. Aprire Gestione dispositivi e verificare se il visore VR è elencato in "Monitor". In caso contrario, selezionare **Azione > cerca modifiche hardware**.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Un messaggio indica "Put on your headset" (Inserisci il visore VR), ma ho il visore VR

Quando si mette il visore VR, Windows Mixed Reality potrebbero essere necessari alcuni secondi per ricaricare lo spazio. Se questo messaggio non viene visualizzato, assicurarsi che l'sticker di protezione sia stato rimosso dal sensore di prossimità all'interno del visore VR tra le lenti. Se il problema persiste, contattare il produttore del visore VR.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un messaggio indica "Connessione visore VR" ma ho collegato il visore VR

- Assicurarsi che i cavi USB e HDMI o DisplayPort del visore VR siano collegati alle porte corrette del PC. Ecco come identificare le porte corrette:

    - Le porte USB 3.0 hanno un logo speciale con un contrassegno "SS" (che indica "SuperSpeed"). La parte interna della porta è in genere blu, ma le porte USB 2.0 meno recenti sono in genere nere o bianchi all'interno.
    - Se il computer ha due porte HDMI o DisplayPort, usare quella che si connette alla scheda grafica, non alla scheda madre del computer. Non è sempre ovvio, ovvero, anche se le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova una porta e non funziona, provare l'altra.

- Scollegare e collegare i cavi USB e HDMI o DisplayPort dal visore VR per assicurarsi che siano connessi in modo sicuro. Quando si collega il cavo USB, provare a non sospenderlo durante l'inserimento del cavo USB.
- Provare un hub USB 3.0 alimentato esternamente se viene visualizzato un'enumerazione parziale del visore VR, ad esempio una serie di dispositivi USB enumerati, ma non in "Visori VR di realtà mista" in Gestione dispositivi.
- Passare al sito Web del produttore del visore VR e aggiornare i driver e il firmware per il visore VR.
- Connessione il visore VR in un altro PC e aprire Gestione dispositivi. Anche se il PC non è completamente compatibile con Windows Mixed Reality, è possibile verificare se il visore VR è enumerato. Se il visore VR non esegue l'enumerazione in più PC, potrebbe verificarsi un problema hardware.

> [!NOTE]
> Per gli utenti di Surface: le versioni precedenti di Surface Dock e Surface Book software di aggiornamento del firmware dell'hub USB non sono compatibili con i visori VR di realtà mista. Se viene visualizzato un messaggio "Connessione visore VR" in un Pc Surface, verificare se sono presenti dispositivi che segnalano un errore "Codice 10: Il dispositivo non può essere avviato" in Gestione dispositivi. In tal caso, [rimuovere il driver in conflitto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). È necessario eseguire questa operazione una sola volta.

Nota per gli utenti Windows 10-N e Windows 11-N: se il PC esegue Windows 10-N o Windows 11-N, verrà visualizzato un errore "Codice 28: La classe di installazione non è presente o non è valida" in Gestione dispositivi dopo aver collegato il visore VR di Realtà mista. N edizioni di Windows 10 e Windows 11 non sono supportate da Windows Mixed Reality. Per altre [informazioni,](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) seguire queste istruzioni.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Viene visualizzato il messaggio "Controllare il cavo USB" o "Velocità USB insufficiente"

* Assicurarsi di usare una porta USB 3.0 supportata nel PC:

    * Assicurarsi che il cavo USB del visore VR sia collegato in tutti i modi.
    * Eseguire il [Windows Mixed Reality per](install-windows-mixed-reality.md#launch-mixed-reality-portal) assicurarsi che il controller USB 3.0 del PC sia supportato.
    * Connessione il visore VR alle altre porte USB 3.0 nel PC. Alcuni PC hanno più controller USB 3.0.
    * Disconnettere temporaneamente tutti i dispositivi USB collegati al PC e connettere solo il visore VR.
    * Nei PC personalizzati, anche se una porta può essere contrassegnata come porta USB 3.0, può essere connessa a un controller USB 2.0. Con il visore VR connesso, aprire Gestione dispositivi, individuare e fare clic su uno dei dispositivi enumerati dal visore VR, quindi passare a Visualizza dispositivi **> tramite connessione.**
* Provare il visore VR in un altro PC. Se l'altro PC non è completamente compatibile con Windows Mixed Reality, controllare in Gestione dispositivi se viene visualizzato il messaggio "Velocità USB insufficiente". Se non viene enumerata correttamente in più PC, il visore VR potrebbe essere difettoso.
* Rimuovere eventuali dispositivi extender o hub tra il visore VR e il computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Il Portale realtà mista non è stato avviato dopo aver collegato il visore VR

Il visore VR potrebbe non essere stato rilevato correttamente a causa di un problema sottostante. Avviare il Portale realtà mista manualmente e cercare eventuali messaggi di errore visualizzati.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Il visore VR ha smesso di funzionare quando il PC passa in modalità sospensione o ibernazione o quando si riavvia il PC con il visore VR collegato

1. Aprire Gestione dispositivi e verificare che il visore VR sia elencato in "Dispositivi di realtà mista".
2. Selezionare il visore VR in "Dispositivi di realtà mista" e verificare che lo stato del dispositivo indichi "Il dispositivo funziona correttamente".
3. Se viene visualizzato un errore "Codice 43" che dice che il dispositivo ha smesso di funzionare o se il visore VR non è elencato in "Dispositivi di realtà mista", scollegare e scollegare il cavo USB del visore VR. Microsoft sta esaminando un potenziale problema di interoperabilità software/driver che può causare questo errore. Questo problema interessa un numero ridotto di PC e dovrebbe essere risolto in un aggiornamento futuro del driver per visori VR di realtà mista.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Il visore VR fa sì che il PC generi un controllo bug (schermata blu) quando metto il PC in sospensione o quando è in modalità di ibernazione

Assicurarsi di aver installato il driver 10.0.19041.2034 o versione più recente.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Il driver del visore VR non è stato installato automaticamente quando è stato collegato il visore VR

Nei nuovi PC o nei PC con una copia appena installata di Windows 10 o Windows 11, il driver del visore VR potrebbe essere accodato dietro altri aggiornamenti Windows e potrebbe non essere installato immediatamente.

1. Passare a **Start > Device Manager (Avvia Gestione dispositivi)** e cercare il visore VR in "Mixed Reality devices" (Dispositivi di realtà mista). Lo stato del dispositivo deve indicare che "Il dispositivo funziona correttamente".
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Aggiorna driver".

Se il problema non è stato corretto, provare a disinstallare il driver:

1. Passare a **Start > Device Manager (Avvia Gestione dispositivi)** e cercare il visore VR in "Mixed Reality devices" (Dispositivi di realtà mista). Lo stato del dispositivo deve indicare che "Il dispositivo funziona correttamente".
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Disinstalla dispositivo".
3. Nella nuova finestra popup visualizzata selezionare la casella di controllo "Elimina il software driver per questo dispositivo" e quindi selezionare "Disinstalla".
4. Al termine, scollegare il visore VR dal PC e collegarlo di nuovo. Windows L'aggiornamento scarica e installa un nuovo driver.

Nota: se si ha un'edizione N di Windows, è necessario passare a una normale edizione di Windows 10 o Windows 11 per usare Windows Mixed Reality.