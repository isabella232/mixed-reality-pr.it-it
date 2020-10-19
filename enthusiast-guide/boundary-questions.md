---
title: Domande frequenti sui limiti
description: Funzionalità avanzate di risoluzione dei problemi di Windows per le domande sui limiti che vanno oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, limite
appliesto:
- Windows 10
ms.openlocfilehash: 9ddf9c7f7c5f36567e6968f619dabead9107731d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174398"
---
# <a name="boundary-faqs"></a>Domande frequenti sui limiti

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>Che cos'è un limite e perché è necessario crearne uno?

Un limite definisce l'area in cui è possibile spostarsi mentre è in uso l'auricolare della realtà mista di Windows. È importante creare un limite che consenta di evitare gli ostacoli che non possono essere visualizzati durante l'auricolare. Il limite sembra essere un contorno bianco all'interno di realtà mista e viene visualizzato quando ci si avvicina. Quando viene visualizzato, rallentare i movimenti ed evitare di oltrepassare il limite o di estendere gli arti al di là.

L'area all'interno del limite deve essere libera di mobili, impianti di illuminazione a bassa pendenza, ventilatori a soffitto e così via. Informazioni [sull'integrità e sulla sicurezza in realtà mista di Windows](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>Ricerca per categorie creare un limite?

Quando si configura per la prima volta l'auricolare, l'app di installazione (portale per la realtà mista) illustra i passaggi necessari per creare un limite. Ma è possibile crearne uno in qualsiasi momento:

1. Selezionare **avvia > portale per la realtà mista** sul desktop.
2. Aprire "menu".
3. Selezionare "Configura limite spazio" per creare un nuovo limite.

Se un altro utente usa la cuffia, assicurarsi che sia in grado di comprendere il limite e come usarlo. Se si sposta l'auricolare in una nuova posizione, è necessario configurare un nuovo limite che funzioni per tale spazio.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Viene ricevuto un messaggio di errore quando si tenta di creare un limite

* Non avvicinarsi troppo alla parete o ad altre ostruzioni durante la creazione di un limite.
* Assicurarsi di mantenere l'auricolare all'altezza della vita ed esaminare il computer mentre si tracciano i limiti.
* Verificare che il sensore non sia bloccato e che la luce sia sufficiente.
* Lo spazio che si sta tracciando deve essere maggiore di tre metri quadrati.
* Lo spazio non deve essere troppo grande o troppo complicato. Attenersi a una forma geometrica semplice senza numerose torsioni e giri.
* Non attraversare il proprio percorso mentre si esegue la traccia.
* Se ci si blocca in un angolo, ricominciare.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Il sistema non è in grado di trovare il limite e viene visualizzata l'interfaccia utente del programma di installazione

Ciò significa che il sistema di rilevamento non è stato in grado di riconoscere l'ambiente. Se ci si trova in un nuovo ambiente, è necessario configurare il [limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Se in precedenza è stato usato il dispositivo in questo ambiente e si è configurato un limite:

* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi di aver indossato il dispositivo e di aver esaminato la stanza. Il dispositivo deve osservare l'ambiente per conoscerne la posizione. Non troverà i limiti se si trova su una scrivania o una tabella.
* Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegarlo.
* Se un elemento dell'ambiente è stato modificato, potrebbe non essere più riconosciuto dal dispositivo. Configurare un nuovo limite.

Se questi passaggi non risolvono il problema, eliminare i dati dell'ambiente e configurare di nuovo il limite.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Il sistema sta presentando l'interfaccia utente che mi chiede di scegliere la configurazione per tutte le esperienze o in piedi e I limiti

Il dispositivo impiega troppo tempo per trovare i limiti. È possibile ignorare questo messaggio scegliendo l'opzione per l'utilizzo di un limite e verrà visualizzata la Home realtà mista di Windows con i limiti presenti.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>Spesso viene visualizzato un messaggio che informa che ho perso i limiti

Il sistema di rilevamento è in fase di rilevamento e identifica l'ambiente. In questo stato, il dispositivo non può più visualizzare i limiti e la cuffia passa a 3DOF per evitare di inserirsi nel mondo reale fino a quando non individua di nuovo i limiti. Per risolvere il problema:

1. Assicurarsi che la stanza disponga di una luce sufficiente.
2. Eseguire di nuovo l'installazione se è stata recentemente ridecorata o rimodellata la chat room.
3. Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegarlo.
4. Cancellare i dati dell'ambiente e configurare di nuovo il dispositivo.
5. Se il messaggio viene mantenuto, contattare il supporto tecnico.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Un messaggio indica che il limite non è stato trovato. Cosa devo fare?

La realtà mista di Windows potrebbe avere problemi nell'identificare il limite esistente. È possibile creare un nuovo limite oppure è possibile usare il dispositivo in modalità "seduti e in piedi".

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Un messaggio indica che il rilevamento è stato perso o che non è disponibile un limite per questo spazio.

È necessario creare un nuovo limite. Per eseguire questa operazione:

1. Selezionare **avvia > portale per la realtà mista**.
2. Aprire "menu".
3. Selezionare "Configura limite spazio".

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Il limite è sempre visibile. Come è possibile fare in modo che vada via?

Il limite viene visualizzato quando ci si avvicina. Se il limite include le sezioni con una forma stretta o irregolare, è possibile che ci si avvicini e che la causa appaia, più spesso di quanto si desideri. Per risolvere il problema, provare a creare di nuovo il limite usando una forma più grande e più regolare. Per eseguire questa operazione:

1. Selezionare **avvia > portale per la realtà mista**.
2. Aprire "menu".
3. Selezionare "Configura limite spazio".

## <a name="can-i-turn-off-the-boundary-temporarily"></a>È possibile disattivare temporaneamente il limite?

* Selezionare **avvia > portale per la realtà mista**.
* Aprire "menu".
* Attivare "Boundary" su "off". Assicurarsi di rimanere in un'unica posizione mentre il limite è disattivato.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Ricerca per categorie scegliere tra "seduti e in piedi" e "tutte le esperienze"?

Se si sceglie "seduto e in piedi" durante l'installazione della cuffia o in un secondo momento, si userà l'auricolare senza un limite. Ciò significa che è necessario rimanere in un punto qualsiasi quando si usa la cuffia, in modo da evitare ostacoli fisici e rischi di inciampare. È possibile rimanere attivi, ma non sarà possibile spostarsi tra loro. Tenere presente che gli ostacoli potrebbero comportare un sovraccarico.

Alcune app possono essere progettate per funzionare con un limite, quindi è possibile che non sia possibile usarle o che non abbiano la stessa esperienza se vengono usate senza un limite.

Se scegli "tutte le esperienze", configurerai un limite e potrai usare app ed esperienze che funzionano con un limite, oltre a quelli che non ne richiedono uno.

## <a name="see-also"></a>Vedere anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)