---
title: Sguardo fisso e commit
description: Informazioni sul modello di input sguardo fisso e commit.
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Tracciamento oculare, Realtà mista, Input, Sguardo fisso, Selezione oculare della destinazione, HoloLens 2, Selezione con gli occhi, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, sguardo
ms.openlocfilehash: 1f337d3cbc1f82b4f69194d4b903687be067f9d6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "97847876"
---
# <a name="eye-gaze-and-commit"></a>Sguardo fisso e commit

_Sguardo fisso e commit_ è un modello di input speciale di tipo [sguardo e commit](gaze-and-commit.md) che comporta la selezione di un oggetto con il semplice sguardo. È possibile agire sulla destinazione con un input di _commit_ secondario, ad esempio un movimento con la mano, un comando vocale o un input da periferica, ad esempio un controller di gioco. 

Con HoloLens 2 hai l'incredibile opportunità di eseguire la sequenza _sguardo e commit_ in modo più rapido e pratico usando lo sguardo fisso anziché il puntamento con la testa. Per estendere il comune modello di interazione [puntamento con la testa e commit](gaze-and-commit.md): 
1. Guardare una destinazione 
2. Per confermare l'intenzione di selezionare tale destinazione, usare esplicitamente uno degli input secondari seguenti:  
   - Movimento con la mano (ad esempio una simulazione del tocco)
   - Pressione di un pulsante (ad esempio su una tastiera Bluetooth o su un dispositivo clicker)
   - Comando vocale (ad esempio, "Seleziona")
   - Attesa (ovvero l'utente deve semplicemente continuare a guardare la destinazione da selezionare)

Lo sguardo fisso tuttavia ha un comportamento diverso da quello del puntamento con la testa per vari aspetti e presenta alcune problematiche specifiche. Nelle [linee guida di progettazione per l'uso dello sguardo fisso](eye-tracking.md) vengono riepilogati i vantaggi generali e le problematiche dell'uso del tracciamento oculare come input nell'app olografica. In questa sezione vengono trattate le considerazioni relative alla progettazione specifiche per l'uso di _sguardo fisso e commit_.
Prima di tutto i nostri occhi si muovono con una rapidità incredibile e sono un mezzo straordinario per individuare velocemente una destinazione all'interno della visualizzazione. Lo sguardo fisso è la soluzione ideale per eseguire rapide azioni di sguardo fisso e commit, soprattutto se combinate con commit rapidi come quelli effettuati tramite simulazione del tocco o pressione di un pulsante.
   
## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Linee guida di progettazione per sguardo fisso e commit

**Non mostrare un cursore**: se è quasi impossibile interagire senza un cursore quando si usa il puntamento con la testa, il cursore diventa rapidamente un elemento di distrazione e di disturbo quando si usa lo sguardo fisso. Invece di servirsi di un cursore per indicare all'utente se il tracciamento oculare funziona e se la destinazione che sta guardando è stata rilevata correttamente, usare evidenziazioni visive non eccessive.

**Cercare di fornire un feedback poco invasivo e graduale da visualizzare al passaggio del puntatore**: un feedback visivo ritenuto utile quando si usa il puntamento con la testa può risultare orribile e opprimente quando si usa lo sguardo fisso. Ricordarsi che gli occhi si muovono molto rapidamente e che si spostano velocemente da un punto all'altro del campo visivo. Rapide e improvvise variazioni dell'evidenziazione (attivata/disattivata) possono produrre un feedback tremolante quando ci si guarda attorno. Pertanto, quando fornisci un feedback da visualizzare al passaggio del puntatore, è consigliabile usare un'evidenziazione graduale, che scompaia altrettanto gradualmente quando si distoglie lo sguardo. Questo significa che all'inizio il feedback sarà appena distinguibile quando si guarda una destinazione. Nel giro di 500-1000 millisecondi l'evidenziazione aumenterà di intensità. Mentre gli utenti alle prime armi possono continuare a guardare la destinazione per essere certi che il sistema l'abbia determinata correttamente, gli utenti esperti possono guardare ed eseguire il commit rapidamente senza attendere che il feedback compaia con la massima intensità. È anche consigliabile applicare un effetto graduale quando il feedback visualizzato al passaggio del puntatore deve scomparire mediante dissolvenza. Le ricerche svolte hanno dimostrato come le rapide variazioni di movimento e contrasto siano rilevabili dalla vista periferica, ovvero nell'area del campo visivo che non si sta guardando.
Non è necessario che l'effetto dissolvenza finale avvenga con la stessa lentezza dell'effetto iniziale di evidenziazione graduale. Questo fattore è fondamentale solo in caso di evidenti variazioni di contrasto o colore per l'evidenziazione. Se il feedback visualizzato al passaggio del puntatore è inizialmente impercettibile, è probabile che non si noti alcuna differenza.

**Cercare di ottenere la sincronizzazione dei segnali dello sguardo fisso e del commit**: la sincronizzazione dei segnali di input non è essenziale per un uso di base delle simulazioni del tocco e delle pressioni dei pulsanti. È necessario cercare di ottenerla se si intende usare azioni di commit più complesse che possono comportare lunghi comandi vocali o movimenti della mano complicati. Immagina di guardare una destinazione e di pronunciare un lungo comando vocale. Considerando il tempo necessario per pronunciare il comando e il tempo impiegato dal sistema per rilevarlo, nel frattempo lo sguardo in genere si è spostato su una nuova destinazione presente nella scena. Avvisare pertanto gli utenti che potrebbero dover continuare a guardare la destinazione fino al riconoscimento del comando oppure gestire l'input in modo da determinare l'inizio del comando e l'elemento che l'utente stava guardando.

## <a name="see-also"></a>Vedere anche

* [Interazione basata sullo sguardo] (eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2] (eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
