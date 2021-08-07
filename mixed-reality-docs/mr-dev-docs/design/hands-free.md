---
title: Mani libere
description: Informazioni sulle difficoltà che gli utenti possono affrontare con un'interfaccia hands-and-controllers e su varie alternative hands-free.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, hands-free, sguardo, miraggio dello sguardo, interazione, progettazione, visore di realtà mista, visore windows di realtà mista, visore di realtà virtuale, HoloLens, MRTK, mixed reality Toolkit, input vocale, usabilità
ms.openlocfilehash: 725d8886d21b42ee4643680c0dc91c1d29c25f8409b0ed0828256564dde7545c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213535"
---
# <a name="hands-free"></a>Mani libere

## <a name="scenarios"></a>Scenari

Come descritto nella panoramica del modello di [interazione,](interaction-fundamentals.md)dopo aver identificato gli utenti e i relativi obiettivi, chiedersi quali problemi ambientali o situazioni potrebbero affrontare mentre lavorano per svolgere le proprie attività. Ad esempio, molti utenti devono usare le mani per raggiungere i propri obiettivi reali e hanno difficoltà a interagire con un'interfaccia basata su mani e controller.

Ecco alcuni scenari specifici: 
* Farsi guidare nello svolgimento di un'attività mentre si hanno le mani occupate
* Fare riferimento a materiali mentre si hanno le mani occupate
* Affaticamento delle mani
* Guanti che non consentono il tracciamento
* Trasportare qualcosa con le mani
* Difficoltà sociale quando si usano movimenti di grandi dimensioni della mano
* Spazi ristretti

## <a name="hands-free-modalities"></a>Modalità hands-free

### <a name="voice-input"></a>[Input vocale](voice-input.md)

L'uso della voce per comando e controllo di un'interfaccia offre un modo pratico per usare hands-free e usare i tasti di scelta rapida per ignorare più passaggi, se necessario. Con l'input vocale, l'utente può leggere il nome di qualsiasi pulsante ad alta voce per attivarlo _("vedere, pronunciarlo")_ e conversare con un agente digitale che può eseguire automaticamente le attività.

### <a name="gaze-and-dwell"></a>[Sguardo fisso e attesa](gaze-and-dwell.md)

In alcune situazioni senza mani, l'uso della voce non è ideale o addirittura possibile. Gli ambienti di fabbrica, la privacy o le norme sociali ad alto volume possono essere tutti vincoli. Il modello gaze + dwell consente all'utente di spostarsi all'interno di un'app senza alcun input aggiuntivo a parte lo sguardo dell'occhio o della testa: l'utente continua semplicemente a guardare (con la testa o gli occhi) verso la destinazione e vi passa un momento per attivarla. Per altre informazioni sulle considerazioni relative alla progettazione individuale per lo sguardo e l'ingoiamento, vedere sguardo oculare [e](gaze-and-dwell-eyes.md) sguardo e sguardo con la [testa e soffermarsi.](gaze-and-dwell-head.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>Transizione in ingresso e in uscita da hands-free

Per questi scenari, liberare le mani dall'interazione con gli ologrammi per l'esecuzione di comandi e la navigazione può essere un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a una maggiore praticità che l'utente può passare da e verso in qualsiasi momento. 

Se l'applicazione richiede che sia sempre usata in modalità hands-free, sia usando i comandi vocali personalizzati o il singolo comando vocale "select", assicurarsi di creare le sistemazioni appropriate nell'interfaccia utente. 

Se l'utente di destinazione deve passare da mani a mani libere a propria discrezione, è importante tenere in considerazione i principi seguenti.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si supponga che l'utente sia già nella modalità a cui si vuole passare
Ad esempio, se l'utente è in fabbrica, guarda un riferimento video sul suo HoloLens e decide di prendere una chiave inglese per iniziare a lavorare, molto probabilmente inizierà a lavorare senza dover premere un pulsante. Può richiamare una sessione vocale con un comando vocale, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "select".

L'utente può: 
* Passare alla modalità hands-free con hands-free
* Passare alle mani con le mani
* Passare al controller usando un controller 

### <a name="create-redundant-ways-to-switch-modes"></a>Creare modi ridondanti per cambiare modalità

Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità. Non dovrebbe esserci un solo modo per passare da e verso una modalità. 

Di seguito sono riportati alcuni esempi: 
* Pulsante per avviare le interazioni vocali
* Comando vocale a cui eseguire la transizione, usando lo sguardo rivolto verso la testa e

### <a name="add-a-dash-of-drama"></a>Aggiungere un tocco di scena

Un cambio di modalità è un problema importante. È importante che quando si verificano queste transizioni si tratta di un passaggio esplicito, anche di notevole impatto, per far sapere all'utente cosa è successo. 

## <a name="usability-checklist"></a>Elenco di controllo per l'usabilità

**L'utente può eseguire qualsiasi operazione, end-to-end e hands-free?**
* Ogni utente che interagisce deve essere hands-free accessibile
* Assicurarsi che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio ridimensionamento, posizionamento, scorrimento rapido, tocco e così via.
* Assicurarsi che l'utente abbia sempre il controllo sicuro di presenza, posizionamento e dettaglio dell'interfaccia utente
    * Come uscire dall'interfaccia utente
    * Indirizzamento dell'interfaccia utente fuori campo (FOV)
    * Quanto si vede, dove, quando

**I meccanismi dell'interazione vengono insegnati e rinforzati con le giuste convenienze?**

L'utente comprende ...
* ... In quale modalità sono presenti?
* ... Cosa possono fare in questa modalità?
* ... Qual è lo stato corrente?
* ... Come è possibile eseguire la transizione?
    
**L'interfaccia utente è ottimizzata per il hands-free?**   

* Esempio: gli affordance dwell non sono incorporati nei modelli 2D tipici
* Esempio: la destinazione vocale è migliore con l'evidenziazione degli oggetti
* Esempio: le interazioni vocali sono migliori con i sottotitoli che devono essere attivati

## <a name="see-also"></a>Vedi anche

* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
