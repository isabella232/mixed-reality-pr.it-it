---
title: Sguardo fisso e attesa
description: Panoramica del modello di input sguardo fisso e attesa, inclusi modelli di interazione, linee guida per la progettazione e problematiche specifiche.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: Tracciamento oculare, Realtà mista, Input, Sguardo fisso, Selezione oculare della destinazione, HoloLens 2, Selezione con gli occhi, Attesa, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, progettazione
ms.openlocfilehash: dfe74ee1fe304cc63bb0c547d01ebadeb0469b171caa806671887817c17f92ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201834"
---
# <a name="eye-gaze-and-dwell"></a>Sguardo fisso e attesa

Il modello di interazione _"sguardo fisso e attesa"_ è un caso speciale del modello di interazione [sguardo fisso e commit](gaze-and-commit.md):
1. Guardare una destinazione e 
2. Confermare l'intenzione di selezionare tale destinazione usando esplicitamente un input secondario: _continua semplicemente a guardare la destinazione che intendi selezionare_.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>Vantaggi del modello di interazione "sguardo fisso e attesa" 

Se le mani sono già occupate per eseguire un'attività o per maneggiare strumenti, potrebbe non essere possibile usarle per interagire con gli ologrammi.
Un'alternativa di interazione senza usare le mani per la selezione degli ologrammi è costituita dal modello _"sguardo fisso e attesa"_ . Con questo approccio anche gli utenti fortemente ostacolati nei movimenti, che potrebbero non essere in grado di ruotare completamente la testa o il corpo, possono interagire con gli ologrammi (ad esempio, in un ambiente di lavoro molto angusto).
L'utente fissa semplicemente lo sguardo sulla destinazione da selezionare e visualizza un feedback di attesa diverso per indicare il processo.

## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>Svantaggi del modello di interazione "sguardo fisso e attesa"

In generale, è consigliabile usare le attivazioni basate sull'attesa come ultima possibilità qualora non sia possibile usare l'input tramite voce o mani. La scelta del tempo di attesa infatti può essere complessa. Gli utenti inesperti sono a proprio agio con tempi di attesa più lunghi, mentre gli utenti esperti vogliono esplorare in modo rapido ed efficiente le proprie esperienze. Questa esigenza comporta la difficoltà di adattare il tempo di attesa in base alle esigenze specifiche di un utente.
Se il tempo di attesa è troppo breve, è possibile che l'utente sia sopraffatto dalla presenza continua di ologrammi che reagiscono al suo sguardo fisso. Se il tempo di attesa è troppo lungo, l'esperienza può risultare troppo lenta in quanto l'utente deve fissare lo sguardo sulle destinazioni per un lungo periodo di tempo interrompendo il flusso del lavoro.

## <a name="design-recommendations"></a>Suggerimenti per la progettazione

È consigliabile usare un approccio a due stati per il feedback dell'attesa:
1. *Ritardo iniziale*: quando l'utente inizia a guardare una destinazione, non dovrebbe prodursi alcuna azione per evitare un'esperienza utente spiacevole e schiacciante. Viene invece avviato un timer per rilevare se l'utente stia intenzionalmente fissando la destinazione o semplicemente guardandola.
Si consiglia un tempo di inizio di 150-250 ms in una determinata prossimità (differenza tra concentrare lo sguardo su una destinazione di grandi dimensioni e guardarsi intorno).  
2. *Inizio feedback attesa:* dopo aver verificato che l'utente stia intenzionalmente fissando la destinazione, si inizia a mostrare un feedback dell'attesa per informarlo che sta per essere avviata l'attivazione dell'attesa. 
3. *Feedback continuo:* mentre l'utente fissa lo sguardo sulla destinazione, visualizza un indicatore di avanzamento continuo che gli indica che non deve distogliere lo sguardo dalla destinazione. In particolare, per l'input con sguardo fisso è consigliabile _trattenere l'attenzione visiva dell'utente_ iniziando con un cerchio o una sfera più grande che si contrae in una versione più piccola. La visualizzazione di un indicatore per lo stato finale (cerchio piccolo) consente di comunicare all'utente quando termina l'attesa. Di seguito è riportata un'illustrazione di esempio. 
4. *Fine:* se l'utente ha continuato a fissare la destinazione (per altri 650-850 ms), completa l'attivazione dell'attesa e seleziona la destinazione fissata con lo sguardo.

![Stati dell'attesa](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>Vedere anche

* [Tracciamento oculare](eye-tracking.md)
* [Sguardo fisso e commit](gaze-and-commit-eyes.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Input vocale](../out-of-scope/voice-design.md)
