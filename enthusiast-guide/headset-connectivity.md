---
title: Domande frequenti sulla connettività visore
description: La connettività del visore Windows Mixed Reality risoluzione dei problemi di connettività con visore che va oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Visore
appliesto:
- Windows 10
ms.openlocfilehash: ed8708d39953e79d445f3794d335d9a9451c9bf9fe8c2fca1feb792ee3f9b2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189223"
---
# <a name="headset-connectivity-faqs"></a>Domande frequenti sulla connettività visore

## <a name="my-headset-will-not-wake-up"></a>Il visore non si riattiva

Se il visore è in sospensione e si fa clic sul pulsante di riattivazione non funziona, riavviare il PC.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Il computer non ha una porta HDMI e/o display

Potrebbe essere necessario usare un adapter. Fare [clic qui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) per un elenco di schede supportate.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>È possibile usare cavi di estensione USB o HDMI e/o DisplayPort con Windows Mixed Reality visori

Windows Mixed Reality visori non supportano ufficialmente l'uso di cavi di estensione USB, HDMI o DisplayPort. Se si usano questi cavi, l'esperienza di realtà mista potrebbe essere interessata da variazioni nell'integrità del segnale e nell'alimentazione del bus tra il controller USB del PC e il visore di realtà mista. Provare a usare il visore senza cavi di estensione se:

* Lo schermo del visore visualizza brevemente uno schermo blu e diventa nero e Portale realtà mista riavvio o completamente denumerato durante l'uso
* L'audio del visore si taglia o diventa glitchy
* Lo sfarfallio del visore tra il nero e lo schermo corretto

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Viene visualizzato l'errore "Controllare il cavo video"

* Se si usano adattatori per connettere il visore al PC, assicurarsi che supportino Windows Mixed Reality e supportino 4K. Provare anche a connettere l'adattatore al PC prima di connettere il visore all'adattatore.
* Provare a usare una porta HDMI o DisplayPort diversa.
* Connessione visore a DisplayPort 1.2 o versione successiva o HDMI 1.4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.
* Se il PC ha grafica integrata e discreta, assicurarsi di usare la porta HDMI o DisplayPort nella scheda grafica attiva. Ciò potrebbe significare che sarà necessario connettere lo schermo del PC a una porta non HDMI.
* Se il PC ha grafica integrata e discreta e la grafica integrata è meno recente e non Windows Mixed Reality, provare a disabilitare la GPU integrata.
* Connessione un monitor PC alla porta HDMI o DisplayPort del PC. Assicurarsi che i driver di grafica siano aggiornati. Scaricare e installare i driver direttamente da AMD, Nvidia o Intel, perché probabilmente saranno più recenti di quelli pubblicati in Windows Update.
* Se si dispone di un monitor esterno collegato a una porta HDMI, provare a collegarlo a un displayport e usare la porta HDMI per il visore.
* Assicurarsi di aver collegato il cavo HDMI del visore a una porta "HDMI out" sul PC, non a una porta "HDMI in".
* Windows potrebbe non essere in grado di rilevare la connessione del cavo di visualizzazione. Aprire Gestione dispositivi e verificare se il visore è elencato in "Monitoraggi". In caso contrario, selezionare **Azione > ricerca delle modifiche hardware**.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Viene visualizzato il messaggio "Put on your headset" but I have my headset on

Quando si mette il visore, Windows Mixed Reality potrebbero essere necessari alcuni secondi per ricaricare lo spazio. Se questo messaggio non viene visualizzato, assicurarsi che l'sticker di protezione sia stato rimosso dal sensore di prossimità all'interno del visore tra le lenti. Se il problema persiste, contattare il produttore del visore.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Viene visualizzato il messaggio "Connessione visore" ma è stato collegato il visore

- Assicurarsi che i cavi USB e HDMI o DisplayPort del visore siano collegati alle porte corrette del PC. Ecco come identificare le porte corrette:

    - Le porte USB 3.0 hanno un logo speciale con un segno "SS" (che indica "SuperSpeed"). La parte interna della porta è in genere blu, ma le porte USB 2.0 meno recenti sono in genere nere o nere all'interno.
    - Se il computer ha due porte HDMI o DisplayPort, usare quella che si connette alla scheda grafica, non alla scheda madre del computer. Non è sempre ovvio, anche se le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova una porta e non funziona, provare l'altra.

- Scollegare e collegare i cavi USB e HDMI o DisplayPort dal visore per assicurarsi che siano connessi in modo sicuro. Quando si collega il cavo USB, provare a non sospendere l'inserimento del cavo USB.
- Provare un hub USB 3.0 alimentato esternamente se viene mostrata l'enumerazione parziale del visore, ad esempio una serie di dispositivi USB enumerati, ma niente in "Visori di realtà mista" in Gestione dispositivi.
- Passare al sito Web del produttore del visore e aggiornare i driver e il firmware per il visore.
- Connessione il visore in un altro PC e aprire Gestione dispositivi. Anche se il PC non è completamente compatibile con Windows Mixed Reality, è possibile verificare se il visore è enumerato. Se il visore non esegue l'enumerazione in più PC, potrebbe verificarsi un problema hardware.

> [!NOTE]
> Per gli utenti di Surface: le versioni precedenti del software di aggiornamento del firmware dell'hub USB di Surface Dock e Surface Book sono incompatibili con i visori di realtà mista. Se viene visualizzato un messaggio "Connessione visore" in un PC Surface, verificare se i dispositivi segnalano un errore "Codice 10: Il dispositivo non può essere avviato" in Gestione dispositivi. In tal caso, [rimuovere il driver in conflitto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). È necessario eseguire questa operazione una sola volta.

Nota per gli utenti Windows 10-N: se il PC esegue Windows 10 N, verrà visualizzato un errore "Codice 28: La classe di installazione non è presente o non è valida" in Gestione dispositivi dopo aver collegato il visore di realtà mista. N edizioni di Windows 10 non sono supportate da Windows Mixed Reality. Per altre [informazioni, seguire](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) queste istruzioni.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Viene visualizzato il messaggio "Controllare il cavo USB" o "Velocità USB insufficiente"

* Assicurarsi di usare una porta USB 3.0 supportata nel PC:

    * Assicurarsi che il cavo USB del visore sia collegato in tutto il modo.
    * Eseguire il [Windows Mixed Reality per](install-windows-mixed-reality.md#launch-mixed-reality-portal) assicurarsi che il controller USB 3.0 del PC sia supportato.
    * Connessione il visore alle altre porte USB 3.0 nel PC. Alcuni PC hanno più controller USB 3.0.
    * Disconnettere temporaneamente tutti i dispositivi USB collegati al PC e connettere solo il visore.
    * Nei PC personalizzati, anche se una porta può essere contrassegnata come porta USB 3.0, può essere connessa a un controller USB 2.0. Con il visore connesso, aprire Gestione dispositivi, individuare e fare clic su uno dei dispositivi enumerati dal visore, quindi passare a Visualizza > **dispositivi tramite connessione**.
* Provare il visore in un altro PC. Se l'altro PC non è completamente compatibile con Windows Mixed Reality, verificare in Gestione dispositivi se viene visualizzato il messaggio "Velocità USB insufficiente". Se non viene enumerata correttamente in più PC, il visore potrebbe essere difettoso.
* Rimuovere eventuali extender o hub tra il visore e il computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Il Portale realtà mista non è stato avviato dopo aver collegato il visore

Il visore potrebbe non essere stato rilevato correttamente a causa di un problema sottostante. Avviare il Portale realtà mista manualmente e cercare eventuali messaggi di errore visualizzati.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Il mio visore ha smesso di funzionare quando il PC passa in modalità sospensione o ibernazione o quando si riavvia il PC con il visore collegato

1. Aprire Gestione dispositivi e verificare che il visore sia elencato in "Dispositivi di realtà mista".
2. Selezionare il visore in "Dispositivi di realtà mista" e verificare che lo stato del dispositivo indichi "Il dispositivo funziona correttamente".
3. Se viene visualizzato un errore "Codice 43" che dice che il dispositivo ha smesso di funzionare o se il visore non è elencato in "Dispositivi di realtà mista", scollegare e scollegare il cavo USB del visore. Microsoft sta analizzando un potenziale problema di interoperabilità software/driver, che potrebbe causare questo errore. Questo problema interessa un numero ridotto di PC e dovrebbe essere risolto in un aggiornamento futuro del driver visore realtà mista.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Il mio visore fa sì che il PC generi un controllo dei bug (schermata blu) quando metto il PC in sospensione o quando è in modalità di ibernazione

Assicurarsi di aver installato il driver 10.0.19041.2034 o versione più recente.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Il driver visore non è stato installato automaticamente quando si è collegato il visore

Nei nuovi PC o nei PC con una copia appena installata di Windows 10, il driver visore potrebbe essere accodato dietro altri aggiornamenti Windows e potrebbe non essere installato immediatamente.

1. Passare a **Start > Device Manager (Gestione dispositivi)** e cercare in "Mixed Reality devices" (Dispositivi di realtà mista) per il visore. Lo stato del dispositivo deve indicare che "Il dispositivo funziona correttamente".
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Aggiorna driver".

Se non funzionava, provare a disinstallare il driver:

1. Passare a **Start > Device Manager (Gestione dispositivi)** e cercare in "Mixed Reality devices" (Dispositivi di realtà mista) per il visore. Lo stato del dispositivo deve indicare che "Il dispositivo funziona correttamente".
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Disinstalla dispositivo".
3. Nella nuova finestra popup visualizzata selezionare la casella di controllo "Elimina il software del driver per questo dispositivo" e quindi selezionare "Disinstalla".
4. Al termine, scollegare il visore dal PC e collegarlo nuovamente. Windows L'aggiornamento scarica e installa un nuovo driver.

Nota: se si ha un'edizione N di Windows, è necessario passare a un'edizione regolare di Windows 10 per usare Windows Mixed Reality.