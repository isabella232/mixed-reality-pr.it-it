---
title: Mani libere
description: Informazioni sulle problematiche che gli utenti possono affrontare con un'interfaccia di controllo e controllo e su diverse alternative gratuite.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, senza contatto, sguardi, obiettivi mirati, interazione, progettazione, cuffie per realtà mista, cuffie di realtà mista di Windows, cuffie per realtà virtuale, HoloLens, MRTK, Toolkit per realtà mista, input vocale, usabilità
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847685"
---
# <a name="hands-free"></a>Mani libere

## <a name="scenarios"></a>Scenari

Come descritto nella [Panoramica del modello di interazione](interaction-fundamentals.md), dopo aver identificato gli utenti e i relativi obiettivi, è possibile chiedersi quali sono le questioni ambientali o di situazione che potrebbero affrontare quando lavorano per svolgere le proprie attività. Molti utenti, ad esempio, devono usare le proprie mani per realizzare gli obiettivi reali e avranno difficoltà a interagire con un'interfaccia basata su hands and controller.

Ecco alcuni scenari specifici: 
* Farsi guidare nello svolgimento di un'attività mentre si hanno le mani occupate
* Fare riferimento a materiali mentre si hanno le mani occupate
* Affaticamento delle mani
* Guanti che non consentono il tracciamento
* Trasportare qualcosa con le mani
* Imbarazzo sociale quando si usano movimenti a mano grande
* Spazi ristretti

## <a name="hands-free-modalities"></a>Modalità senza mani

### <a name="voice-input"></a>[Input vocale](voice-input.md)

L'uso della voce per il comando e il controllo di un'interfaccia offre un modo pratico per lavorare senza mani e per usare i tasti di scelta rapida per ignorare più passaggi, se lo si desidera. Con l'input vocale, l'utente può leggere il nome di qualsiasi pulsante per attivarlo _("visualizzarlo, pronunciarlo")_ e conversare con un agente digitale che può eseguire le attività.

### <a name="gaze-and-dwell"></a>[Sguardo fisso e attesa](gaze-and-dwell.md)

In alcune situazioni senza problemi, l'uso della tua voce non è ideale o addirittura possibile. Gli ambienti di produzione, la privacy o le norme di social networking possono essere tutti vincoli. Il modello di sguardo e di sosta consente all'utente di spostarsi in un'app senza alcun input aggiuntivo, a parte l'occhio o lo sguardo da capo: l'utente continua a guardare la destinazione e si sofferma per un istante per poterlo attivare. Per altre informazioni sulle singole considerazioni di progettazione per lo sguardo + l'abitazione, vedere [Eye-sguardi + soffermarsi](gaze-and-dwell-eyes.md) e [guardare a capo + soffermarsi](gaze-and-dwell-head.md).

## <a name="transitioning-in-and-out-of-hands-free"></a>Transizione all'interno e all'esterno di Hands-Free

Per questi scenari, liberare le mani dall'interazione con gli ologrammi per i comandi e la navigazione può variare da un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a un ulteriore vantaggio che l'utente può eseguire la transizione da e verso l'esterno in qualsiasi momento. 

Se per l'applicazione è necessario che venga sempre utilizzata la funzionalità hands-free, indipendentemente dal fatto che si utilizzi l'uso di Rest, i comandi vocali personalizzati o il singolo comando Voice "Select", assicurarsi di creare le sistemazioni appropriate nell'interfaccia utente. 

Se l'utente di destinazione deve passare da una mano all'altra a propria discrezione, è importante tenere conto dei principi seguenti.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si supponga che l'utente sia già nella modalità a cui si desidera passare
Ad esempio, se l'utente si trova in fabbrica, guardando un riferimento video sulla sua HoloLens e decide di prelevare una chiave per iniziare a lavorare, probabilmente inizierà a lavorare in modo pratico senza dover posizionare la chiave per premere un pulsante. Può richiamare una sessione vocale con un comando Voice, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "Select".

L'utente può: 
* Passa a vivavoce senza intervento
* Passa a mano
* Passare al controller usando un controller 

### <a name="create-redundant-ways-to-switch-modes"></a>Creare modi ridondanti per cambiare modalità

Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità. Non dovrebbe essere presente un unico modo per eseguire la transizione all'interno e all'esterno di una modalità. 

Di seguito sono riportati alcuni esempi: 
* Pulsante per l'inizio delle interazioni vocali
* Un comando vocale a cui passare, usando l'Head-sguardi e l'abitazione

### <a name="add-a-dash-of-drama"></a>Aggiungere un trattino di dramma

Un commodity switch è molto importante. È importante che, quando si verificano queste transizioni, siano uno esplicito, anche un cambio drammatico, per consentire all'utente di sapere cosa è successo. 

## <a name="usability-checklist"></a>Elenco di controllo dell'usabilità

**L'utente può eseguire tutte le operazioni e tutto ciò che si può fare senza alcun intervento end-to-end?**
* Ogni interoperabilità deve essere Hands-Free accessibile
* Assicurarsi che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, l'inserimento, il scorrimento, i colpetti e così via.
* Assicurarsi che l'utente abbia il controllo della presenza, della posizione e del livello di dettaglio dell'interfaccia utente sempre
    * Recupero dell'interfaccia utente
    * Indirizzamento dell'interfaccia utente fuori campo di visualizzazione (FOV)
    * Quanto vedo, dove, quando

**La meccanica dell'interazione viene insegnata e rafforzata con la affordances corretta?**

Informazioni sull'utente...
* ... Modalità di funzionamento
* ... Cosa si può fare in questa modalità?
* ... Qual è lo stato corrente?
* ... In che modo è possibile eseguire la transizione?
    
**L'interfaccia utente è ottimizzata per l'Hand-Free?**   

* Esempio: il affordances di abitazione non è integrato nei modelli 2D tipici
* Esempio: il targeting vocale è migliore con l'evidenziazione degli oggetti
* Esempio: le interazioni vocali sono migliori con le didascalie che devono essere attivate

## <a name="see-also"></a>Vedi anche

* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
