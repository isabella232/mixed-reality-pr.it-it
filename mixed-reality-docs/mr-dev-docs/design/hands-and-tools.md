---
title: Mani e controller del movimento
description: Informazioni sui modelli di interazione di mani e controller di movimento, che possono rimuovere il limite tra il virtuale e il fisico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controller di movimento, interazione, progettazione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213700"
---
# <a name="hands-and-motion-controllers"></a>Mani e controller del movimento

## <a name="scenarios"></a>Scenari

Dopo aver letto la panoramica [dell'interazione,](interaction-fundamentals.md)è possibile scegliere il modello di interazione tra mano e controller di movimento. Ciò significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico. L'applicazione raggiungerà l'obiettivo di rimuovere il limite tra virtuale e fisico.

Alcuni scenari specifici potrebbero essere:
* Fornire agli Information Worker schermate virtuali 2D con inviti dell'interfaccia utente per visualizzare e controllare il contenuto
* Esercitazioni e guide per i lavoratori di prima linea per le linee di montaggio della fabbrica
* Sviluppare strumenti professionali per l'assistenza e la formazione per professionisti medici  
* Usare oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo 
* Creare servizi e giochi basati sulla posizione usando il mondo reale come sfondo

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalità di mani e controller di movimento

:::row:::
    :::column:::
       [![Manipolazione diretta con le mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipolazione diretta con le mani](direct-manipulation.md)<br>
       Modalità che applica la potenza delle mani che gli utenti possono usare per toccare e manipolare gli ologrammi. Usando esperienze di vita quotidiana e offrendo adeguati servizi visivi, gli utenti possono usare lo stesso modo di manipolare gli oggetti reali per interagire con quelli virtuali.
    :::column-end:::
    :::column:::
       [![Puntamento e commit con le mani](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Puntamento e commit con le mani](point-and-commit.md)<br>
        Questa modalità consente agli utenti di interagire con gli ologrammi a distanza. Consente agli utenti di usare al meglio l'ambiente circostante. Gli utenti possono posizionare gli ologrammi ovunque e accedervi da qualsiasi distanza. I modelli mentali e i movimenti per il controllo e la manipolazione degli ologrammi 2D e 3D sono altamente sincronizzati con quelli della manipolazione diretta.
    :::column-end:::
    :::column:::
       [![Controller del movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Controller del movimento](motion-controllers.md)<br>
       I controller di movimento estendono le funzionalità fisiche dell'utente con interazioni precise su un intervallo di distanze usando una o entrambe le mani. Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono feedback tattile sicuro per varie azioni. Attualmente, i controller di movimento sono disponibili solo per Windows Mixed Reality (WMR). 
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
