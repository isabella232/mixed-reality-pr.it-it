---
title: Domande frequenti sull'installazione
description: Funzionalità avanzate di risoluzione dei problemi di Windows per le domande di installazione che vanno oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, installazione, Home realtà mista di Windows, portale di realtà mista di Windows
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 979967d6841d8fa64cf1d6cf3ae532b736ed3bd1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93121932"
---
# <a name="setup-faqs"></a>Domande frequenti sull'installazione 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>Il portale per la realtà mista non si apre quando si collega l'auricolare.

Il portale per la realtà mista, l'app che consente di configurare la realtà mista di Windows, è progettata per l'apertura automatica quando si collega un auricolare compatibile. Se non si apre, passare a Start e digitare "Mixed Reality Portal" nella casella di ricerca per aprire l'app. Se non si riesce a trovare il portale di realtà mista, questo potrebbe significare che è necessario eseguire [l'aggiornamento alla versione più recente di Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Ricerca per categorie scegliere tra "seduti e in piedi" e "tutte le esperienze"?

Se si sceglie "seduto e in piedi", durante l'installazione dell'auricolare o in un secondo momento, si userà l'auricolare senza un limite. È possibile rimanere in attesa o in primo luogo, ma in caso contrario sarà necessario rimanere in un'unica posizione, perché non ci saranno limiti per evitare ostacoli fisici. Alcune app possono essere progettate per funzionare con un limite, quindi è possibile che non sia possibile usarle o che non si abbia la stessa esperienza se vengono usate senza un limite. Vedere ["Qual è il limite e perché è necessario crearne uno?"](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one).

Se si sceglie "tutte le esperienze", si configurerà un limite ed è possibile usare app ed esperienze che funzionano con un limite, oltre a quelli che non ne richiedono uno. 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>Impara la realtà mista non è stata eseguita al primo avvio e ho avuto diritto a casa di realtà mista di Windows.

È possibile eseguire di nuovo l'esperienza di apprendimento attenendosi alla [procedura di ripetizione dell'esecuzione](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>I miei controller non vengono visualizzati nella mia Home realtà mista di Windows.

Assicurarsi che i controller dispongano di batterie complete e che siano abbinati correttamente usando Bluetooth. Provare a spegnere e accendere i controller usando il pulsante Windows. Se i controller non sono ancora visibili, provare a annullare l'associazione e a riassociare ogni controller: 
* Se la cuffia ha una radio predefinita, usare l'app complementare fornita con la cuffia per disaccoppiare, quindi associare nuovamente i controller (il portale per la realtà mista può aiutare a trovare l'app complementare corretta). 
* Se i controller sono abbinati al PC, passare a **dispositivi > impostazioni Bluetooth >** per disaccoppiare i controller e associarli di nuovo. 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>Il piano di casa della realtà mista di Windows non sembra essere all'altezza corretta.

Selezionare **inizia > regolazione del piano** , che viene avviata quando si inserisce l'app in tutto il mondo, per apportare modifiche durante l'uso dell'auricolare. In questa app si verrà indirizzati all'uso del touch pad (Motion controller) o del riquadro direzione (gamepad) per regolare l'altezza del piano. Quando il piano è corretto, usare il pulsante Windows per tornare alla Home page.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>Non è possibile visualizzare un'anteprima di ciò che viene visualizzato nell'auricolare sul desktop.

Il portale per la realtà mista di Windows include un pulsante **Riproduci** nella parte inferiore della schermata che consente di visualizzare in anteprima gli elementi visualizzati nell'auricolare sullo schermo del desktop. Per motivi di prestazioni, questa funzionalità è disponibile solo nei PC che eseguono Windows Mixed Reality Ultra (90Hz).

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Si è verificato un messaggio di errore "si è verificato un problema" oppure si sono verificati problemi nel portale di realtà mista
Per ottenere altre informazioni su un codice di errore specifico, vedere [qui](error-codes.md). È anche possibile provare a:

Riavviare la realtà mista di Windows:
1. Scollegare entrambi i cavi auricolare dal PC.
2. Riavvia il PC.
3. Riconnettere l'auricolare.

Verificare che il PC riconosca la cuffia:
1. Selezionare Avvia.
2. Digitare "Device Manager" nella casella di ricerca e selezionarlo nell'elenco. 
3. Espandere "dispositivi in realtà mista" e verificare se l'auricolare è elencato. 

Se non è elencato:
1. Collegare la cuffia a porte diverse sul PC, se disponibile.
2. Verificare la disponibilità degli aggiornamenti software più recenti da Windows Update.
3. Disinstallare e reinstallare la realtà mista di Windows:
    1. Scollegare entrambi i cavi auricolare dal PC.
    2. Selezionare **impostazioni > realtà mista > disinstallare** .
    3. Se i controller di movimento sono abbinati al PC, selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi** per disaccoppiarli. Selezionare ogni controller e "Rimuovi dispositivo". Se i controller sono abbinati all'auricolare, è possibile ignorare questo passaggio.
    4. Collegare la cuffia al PC per reinstallare la realtà mista di Windows.

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Non è possibile indirizzare input (controller, gamepad, mouse/tastiera) in realtà mista di Windows.

Quando si usa l'auricolare, l'input dovrebbe passare automaticamente all'esperienza di realtà mista tramite il sensore di presenza dell'auricolare. Sul desktop verrà visualizzata una barra blu:

![Desktop di Windows con input indirizzato alla cuffia](images/1050px-windowsy.png)

Se l'input non viene attivato automaticamente, è possibile che sia stato disabilitato il cambio automatico di input in **impostazioni > realtà mista > visualizzazione della cuffia > commutazione di input** . È sempre possibile digitare il **tasto Windows + Y** sulla tastiera per impostare manualmente l'input sull'auricolare o tornare al desktop.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante l'avvio della realtà mista, mi sono bloccato a "capovolgere il lato destro e quindi al piano".

Questo passaggio consente all'auricolare di riconoscere lo spazio e di ripristinare i limiti e le pavimentazioni virtuali esistenti. Quando si usa l'auricolare, questo processo di analisi può richiedere fino a 10 secondi. Una volta completata l'operazione, sarà possibile usare la Home realtà mista di Windows o verrà richiesto di configurare di nuovo il limite.

Se il processo di analisi richiede più di 10 secondi, potrebbe essersi verificato un problema con il sensore di prossimità nell'auricolare:
1. Verificare che l'adesivo sia stato rimosso dal sensore di prossimità. Il sensore di prossimità si trova all'interno dell'auricolare approssimativamente dove si trova il centro della fronte.
2. Verificare che il sensore di prossimità accenda l'input dell'auricolare: con il dito, coprire e scoprire il sensore di prossimità alcune volte per verificare che l'input passi all'auricolare. Nella parte superiore del PC verrà visualizzato il banner **tasto Windows + Y** . È possibile passare manualmente l'input all'auricolare in qualsiasi momento digitando il **tasto Windows + Y** sulla tastiera.

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Il controller Xbox non funziona con la realtà mista di Windows.

* Verificare che il controller sia acceso, completamente addebitato e connesso al PC.
* Sostituire le batterie del controller.
* Se si usa un controller Bluetooth, passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che sia associato (dovrebbe essere elencato nella pagina).
