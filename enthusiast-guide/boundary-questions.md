---
title: Domande frequenti sul limite
description: Risoluzione Windows Mixed Reality risoluzione dei problemi per le domande sui limiti che vanno oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Limite
appliesto:
- Windows 10
ms.openlocfilehash: c1d6a10ae6ed50f7b9088b26c78cde4ccf8386ea0603c39e107ed23910db9308
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187971"
---
# <a name="boundary-faqs"></a>Domande frequenti sul limite

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>Che cos'è un limite e perché è necessario crearne uno?

Un limite definisce l'area in cui è possibile spostarsi mentre si indossa il visore Windows Mixed Reality visore. È importante creare un limite per evitare gli ostacoli che non è possibile vedere mentre si è in cuffia. Il limite è simile a un contorno bianco all'interno della realtà mista e viene visualizzato quando ci si avvicina. Quando lo si vede, rallentare i movimenti ed evitare di attraversare il limite o di estendere gli arti oltre.

L'area all'interno del limite deve essere esente da mobili, infissi di luce a bassa impiccagione, ventole del controsoffitto e così via, in modo da non urtare o inciampare su nulla. [Informazioni su integrità e sicurezza in Windows Mixed Reality](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>Ricerca per categorie creare un limite?

Quando si configura il visore per la prima volta, l'app di configurazione (Portale realtà mista) esegue i passaggi per creare un limite. Ma è possibile crearne uno in qualsiasi momento:

1. Selezionare **Avvia > Portale realtà mista** sul desktop.
2. Aprire "Menu".
3. Selezionare "Configura limite stanza" per creare un nuovo limite.

Se un altro utente usa il visore, assicurarsi che comprendi il limite e come usarlo. Se si sposta il visore in una nuova posizione, sarà necessario configurare un nuovo limite per lo spazio.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Viene visualizzato un messaggio di errore quando si tenta di creare un limite

* Non avvicinarti troppo a una parete o ad altri ostacoli durante la creazione di un limite.
* Assicurarsi di tenere il visore all'altezza del visore e affrontare il computer mentre si traccia il limite.
* Assicurarsi che il sensore non sia bloccato e che ci sia luce sufficiente.
* Lo spazio di cui si sta tracciando deve essere maggiore di 3 metri quadrati.
* Lo spazio non deve essere troppo grande o troppo complesso. Attenersi a una semplice forma geometrica con torsione e curve.
* Non attraversare il proprio percorso durante la traccia.
* Se ci si blocca in un angolo, ricominciare.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Il sistema non riesce a trovare il limite e viene visualizzata l'interfaccia utente di configurazione

Ciò significa che il sistema di rilevamento non è stato in grado di riconoscere l'ambiente. Se si è in un nuovo ambiente, è necessario impostare il [limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Se il dispositivo è stato usato in precedenza in questo ambiente e si è configurato un limite:

* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi di aver indossato il dispositivo e di aver guardato in giro per la stanza. Il dispositivo deve osservare l'ambiente per sapere dove si trova. Non troverà i limiti se si trova su una scrivania o un tavolo.
* Scollegare il dispositivo, Windows Mixed Reality e collegarlo di nuovo.
* Se qualcosa nell'ambiente è cambiato, il dispositivo potrebbe non riconoscerlo più. Configurare un nuovo limite.

Se questi passaggi non risolvono il problema, eliminare i dati dell'ambiente e configurare nuovamente il limite.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Il sistema mi sta presentando con l'interfaccia utente che mi chiede di scegliere la configurazione per tutte le esperienze o seed/standing e vedo i miei limiti

Il dispositivo sta prendendo troppo tempo per trovare i limiti. È possibile ignorare questo messaggio scegliendo l'opzione per usare un limite e si verrà portati a casa Windows Mixed Reality con i limiti presenti.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>Spesso viene visualizzato il messaggio "I've lost my bounds" (Ho perso i limiti)

Il sistema di rilevamento sta avendo difficoltà a tenere traccia e identificare l'ambiente. In questo stato, il dispositivo non può più visualizzare i limiti. Il visore passa a 3DOF per evitare di urtare le cose nel mondo reale finché non individua nuovamente i limiti. Per risolvere il problema, seguire questa procedura:

1. Assicurarsi che la stanza abbia una luce sufficiente.
2. Eseguire di nuovo l'installazione se la stanza è stata ridecorretta o rimodellata di recente.
3. Scollegare il dispositivo, Windows Mixed Reality e collegarlo di nuovo.
4. Cancellare i dati dell'ambiente e configurare nuovamente il dispositivo.
5. Se il messaggio persiste, contattare il supporto tecnico.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Un messaggio indica che il limite non è stato trovato. Cosa devo fare?

Windows Mixed Reality problemi di identificazione del limite esistente. È possibile creare un nuovo limite oppure usare il dispositivo in modalità "Seated and standing".

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Un messaggio indica "Rilevamento perso" o "Non è presente un limite per questo spazio"

Creare un nuovo limite:

1. Selezionare **Avvia > Portale realtà mista**.
2. Aprire "Menu".
3. Selezionare "Configura limite stanza".

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Il limite è sempre visibile. Come è possibile farlo andare via?

Il limite viene visualizzato quando ci si è vicini. Se il limite include sezioni con una forma stretta o irregolare, è possibile che ci si avvicina. Il limite può essere visualizzato più spesso di quanto si desideri. Provare a creare di nuovo il limite usando una forma più grande e regolare per risolvere il problema:

1. Selezionare **Avvia > Portale realtà mista**.
2. Aprire "Menu".
3. Selezionare "Configura limite stanza".

## <a name="can-i-turn-off-the-boundary-temporarily"></a>È possibile disattivare temporaneamente il limite?

* Selezionare **Avvia > Portale realtà mista**.
* Aprire "Menu".
* Impostare "Boundary" su "Off". Assicurarsi di rimanere in un'unica posizione mentre il limite è spento.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Ricerca per categorie scegliere tra "Seduti e in piedi" e "Tutte le esperienze"?

Se si sceglie "Seduti e in piedi", durante la configurazione del visore o in un secondo momento, si usa il visore senza limiti. È necessario rimanere in un unico punto quando si usa il visore per evitare ostacoli fisici e rischi di inciampo. È possibile sedersi o alzarsi, ma non spostarsi. Tenere presente che gli ostacoli potrebbero essere sovraccarico e intorno a te.

Alcune app potrebbero essere progettate per funzionare con un limite. Potrebbero non funzionare o offrire la stessa esperienza se vengono usate senza un limite.

Se si sceglie "Tutte le esperienze", si configura un limite e si possono usare app ed esperienze che funzionano con e senza un limite.

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Per assistenza, contattare Microsoft](https://support.microsoft.com/contactus/)