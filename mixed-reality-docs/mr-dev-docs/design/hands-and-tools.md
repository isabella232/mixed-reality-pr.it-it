---
title: Mani e controller del movimento
description: Informazioni sui modelli di interazione di hands and Motion Controllers, che possono rimuovere il limite tra il virtuale e il fisico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, praticità, controller di movimento, interazione, progettazione, cuffie per realtà mista, cuffie con la realtà mista di Windows, cuffie per realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: e931e5ec11548d9aab0d1dd7f8921dbc7554abab
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702157"
---
# <a name="hands-and-motion-controllers"></a>Mani e controller del movimento
## <a name="scenarios"></a>Scenari
Se si sceglie di adottare questo modello di interazione dopo aver letto la [Panoramica sull'interazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico. L'applicazione è in grado di raggiungere l'obiettivo di rimuovere il limite tra virtuale e fisico.

Alcuni scenari specifici potrebbero essere:
* Fornire agli Information Worker schermate virtuali 2D con inviti dell'interfaccia utente per visualizzare e controllare il contenuto
* Esercitazione e guide per i ruoli di lavoro di prima linea per le linee di assemblaggio Factory
* Sviluppare strumenti professionali per l'assistenza e la formazione per professionisti medici  
* Usare oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo 
* Creare servizi e giochi basati sulla posizione usando il mondo reale come sfondo

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalità di controllo delle mani e del movimento

:::row:::
    :::column:::
       [![Manipolazione diretta con le mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipolazione diretta con le mani](direct-manipulation.md)<br>
       Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi. Sfruttando le esperienze quotidiane e fornendo affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.
    :::column-end:::
    :::column:::
       [![Puntamento e commit con le mani](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Puntamento e commit con le mani](point-and-commit.md)<br>
        Questa modalità consente agli utenti di interagire con gli ologrammi a distanza. Consente agli utenti di sfruttare al meglio i dintorni. Gli utenti possono posizionare gli ologrammi ovunque e continuare ad accedervi da qualsiasi distanza. I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.
    :::column-end:::
    :::column:::
       [![Controller del movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Controller del movimento](motion-controllers.md)<br>
       I controller di movimento sono strumenti che estendono le funzionalità fisiche dell'utente fornendo interazioni precise in un'ampia gamma di distanze durante l'uso di una o entrambe le mani. Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted e commenti tattili per diverse azioni. Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR). 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Mani libere](hands-free.md)
