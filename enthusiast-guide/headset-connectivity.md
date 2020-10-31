---
title: Domande frequenti sulla connettività auricolare
description: Connettività auricolare risoluzione dei problemi di connettività dell'auricolare di Windows
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, auricolare
appliesto:
- Windows 10
ms.openlocfilehash: 25b42377d92273573da909ab52d67578eb6469ec
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132075"
---
# <a name="headset-connectivity-faqs"></a>Domande frequenti sulla connettività auricolare

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Il computer non dispone di una porta di visualizzazione e/o HDMI

Potrebbe essere necessario utilizzare un adapter. Per un elenco degli adapter supportati, fare clic [qui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>È possibile usare cavi di estensione USB o HDMI e/o DisplayPort con auricolari per la realtà mista di Windows

Gli auricolari per la realtà mista di Windows non supportano ufficialmente l'uso di cavi di estensione USB, HDMI o DisplayPort. L'uso di questi cavi può influire in modo significativo sull'esperienza di realtà mista a causa delle variazioni nell'integrità del segnale risultante e dell'alimentazione del bus tra il controller USB del PC e l'auricolare della realtà mista. Se la visualizzazione della cuffia è brevemente visualizzata in una schermata blu, il portale di realtà misto e nero viene riavviato o completamente deenumerato durante l'uso o se l'audio della cuffia viene ritagliato o si è verificato un problema oppure se l'auricolare si sposta tra il nero e la visualizzazione corretta, provare a usare l'auricolare senza cavi di estensione.

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Viene visualizzato l'errore "controllare il cavo di visualizzazione"

* Se si usano schede per connettere l'auricolare al PC, verificare che supportino la realtà mista di Windows (la scheda deve essere in grado di supportare 4K). Provare anche a connettere l'adattatore al PC prima di connettere l'auricolare alla scheda.
* Provare a usare una porta HDMI e/o DisplayPort diversa.
* Connettere la cuffia a DisplayPort 1,2 o versione successiva o HDMI 1,4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.
* Se il PC dispone di grafica sia integrata che discreta, assicurarsi di usare la porta HDMI e/o DisplayPort sulla scheda grafica attiva. Questo potrebbe significare che è necessario connettere la visualizzazione del PC a una porta non HDMI.
* Se il PC dispone di grafica sia integrata che discreta e la grafica integrata è precedente e non supporta la realtà mista di Windows, provare a disabilitare la GPU integrata.
* Connettere un monitor PC alla porta HDMI e/o DisplayPort del PC. Assicurarsi che i driver grafici siano aggiornati. Scaricare e installare le interfacce da AMD, NVIDIA o Intel direttamente, perché saranno probabilmente più recenti rispetto a quelle pubblicate per Windows Update.
* Se un monitor esterno è collegato a una porta HDMI, provare a connetterlo a una DisplayPort e usare la porta HDMI per l'auricolare.
* Assicurarsi di aver collegato il cavo HDMI dell'auricolare a una porta "HDMI out" del PC, non a una porta "HDMI in".
* Windows potrebbe non essere in grado di rilevare la connessione del cavo di visualizzazione. Aprire il Device Manager e verificare se la cuffia è elencata in "monitoraggi". In caso contrario, selezionare **azione > analizza modifiche hardware** . 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Un messaggio indica che l'auricolare è stato inserito

Quando si usa l'auricolare, la realtà mista di Windows potrebbe richiedere alcuni secondi per ricaricare lo spazio. Se il messaggio non viene rimosso, assicurarsi che l'adesivo protettivo sia stato rimosso dal sensore di prossimità, che si trova all'interno dell'auricolare tra le lenti. Se il problema persiste, contattare il produttore dell'auricolare.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un messaggio indica "Connetti l'auricolare", ma ho collegato l'auricolare

- Assicurarsi che i cavi USB e HDMI e/o DisplayPort del dispositivo headset siano connessi alle porte corrette del computer. Ecco come identificare le porte corrette:

    - Le porte USB 3,0 hanno un logo speciale con un contrassegno "SS" (che indica "SuperSpeed"). Il pezzo interno della porta è generalmente blu, mentre le porte USB 2,0 precedenti sono in genere nere o bianche all'interno.
    - Se il computer dispone di due porte HDMI e/o DisplayPort, utilizzare quello che si connette alla scheda grafica, non alla scheda madre del computer. Non è sempre ovvio, ma le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova a usare una porta e non funziona, provare l'altra.

- Scollegare i cavi USB e HDMI e/o DisplayPort dall'auricolare per assicurarsi che siano connessi in modo sicuro. Quando si collega il cavo USB, provare a non sospendere l'inserimento del cavo USB.
- Se viene visualizzato l'enumerazione parziale dell'auricolare (una serie di dispositivi USB viene enumerata, ma non è presente in "cuffie a realtà mista" in Device Manager), provare con un hub USB 3,0 alimentato esternamente.
- Accedere al sito Web del produttore dell'auricolare e aggiornare i driver e il firmware per l'auricolare.
- Connettere la cuffia a un altro PC e aprire Device Manager. Anche se il PC non è completamente compatibile con la realtà mista di Windows, è possibile verificare se l'auricolare viene enumerato. Se la cuffia non viene enumerata in più PC, potrebbe verificarsi un problema hardware.

Nota per gli utenti della superficie: le versioni precedenti del software di aggiornamento del firmware dell'hub USB Surface Dock e Surface Book non sono compatibili con le cuffie con realtà mista. Se viene visualizzato il messaggio "Connetti la cuffia" in un PC Surface, verificare se i dispositivi segnalano un errore "codice 10: Impossibile avviare il dispositivo" in Device Manager. In tal caso, [rimuovere il driver in conflitto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Questa operazione deve essere eseguita solo una volta.

Nota per gli utenti di Windows 10 N: se il PC esegue Windows 10 N, verrà visualizzato l'errore "codice 28: la classe di installazione non è presente o non è valida" in Device Manager dopo l'inserimento dell'auricolare in realtà mista. Le edizioni di Windows 10 non sono supportate dalla realtà mista di Windows. Per ulteriori informazioni, seguire queste [istruzioni](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) .

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un messaggio indica che "controllare il cavo USB" o "velocità USB insufficiente"

* Assicurarsi di usare una porta USB 3,0 supportata nel PC:

    * Verificare che il cavo USB dell'auricolare sia collegato a tutti i modi.
    * Eseguire il [portale per la realtà mista di Windows](install-windows-mixed-reality.md#launch-mixed-reality-portal) per verificare che il controller USB 3,0 del PC sia supportato.
    * Connettere la cuffia alle altre porte USB 3,0 nel PC. Alcuni PC hanno più di un controller USB 3,0.
    * Scollegare temporaneamente tutti i dispositivi USB collegati al PC e connettere solo l'auricolare.
    * Nei PC personalizzati, anche se una porta può essere contrassegnata come porta USB 3,0, potrebbe essere connessa a un controller USB 2,0. Con la cuffia connessa, aprire Device Manager, individuare e fare clic su uno dei dispositivi enumerati dall'auricolare, quindi passare a **visualizza > dispositivi per connessione** .
* Provare la cuffia in un altro computer. Se l'altro PC non è completamente compatibile con la realtà mista di Windows, archiviare Device Manager per verificare se viene visualizzato il messaggio "velocità USB insufficiente". Se non viene enumerata correttamente su più PC, l'auricolare potrebbe essere difettoso.
* Rimuovere le estensioni o gli hub tra la cuffia e il computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Non è stato possibile avviare il portale di realtà mista dopo aver collegato l'auricolare

È possibile che la cuffia non sia stata rilevata correttamente a causa di un problema sottostante. Avviare il portale di realtà mista manualmente e cercare eventuali messaggi di errore visualizzati.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>L'auricolare smette di funzionare quando il PC passa alla modalità di sospensione o ibernazione o quando si riavvia il PC con la cuffia collegata

1. Aprire Device Manager e verificare che la cuffia sia elencata in "dispositivi realtà misti".
2. Selezionare la cuffia in "Mixed Reality Devices" e verificare che lo stato del dispositivo indichi che il dispositivo funziona correttamente.
3. Se viene visualizzato un errore "codice 43" che indica che il dispositivo ha smesso di funzionare o se l'auricolare non è elencato in "dispositivi con realtà mista", scollegare e ricollegare il cavo USB dell'auricolare. Microsoft sta esaminando un potenziale problema di interoperabilità di software/driver che può causare questo errore. Questo problema interessa un numero ridotto di PC e dovrebbe essere risolto in un aggiornamento futuro al driver della cuffia per la realtà mista.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Il mio auricolare causa la generazione di un controllo bug (schermata blu) quando il PC viene sospeso o in modalità di ibernazione

Assicurarsi di trovarsi nel driver 10.0.19041.2034 o versione successiva.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Non è stato possibile installare automaticamente il driver headset quando è stato inserito il dispositivo headset

Nei nuovi PC o nei PC con una copia di Windows 10 appena installata, il driver della cuffia potrebbe essere accodato dietro altri aggiornamenti di Windows e potrebbe non essere installato immediatamente.

1. Passare a **Start > Device Manager** e cercare "Mixed Reality Devices" per la cuffia. Lo stato del dispositivo indicherà che il dispositivo funziona correttamente.
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Aggiorna driver".

Se l'operazione non è stata completata, provare a disinstallare il driver:

1. Passare a **Start > Device Manager** e cercare "Mixed Reality Devices" per la cuffia. Lo stato del dispositivo indicherà che il dispositivo funziona correttamente.
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Disinstalla dispositivo".
3. Nella nuova finestra popup visualizzata selezionare la casella di controllo "Elimina il software driver per il dispositivo" e quindi selezionare "Disinstalla".
4. Al termine, scollegare l'auricolare dal PC e collegarlo di nuovo. Windows Update ora scaricherà e installerà un nuovo driver.

Nota: se si dispone di una versione N di Windows, sarà necessario passare a un'edizione regolare di Windows 10 per usare la realtà mista di Windows.