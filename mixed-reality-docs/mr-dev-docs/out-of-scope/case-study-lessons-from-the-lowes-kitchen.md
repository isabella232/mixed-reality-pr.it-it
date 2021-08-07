---
title: Case study - Lessons from the Lowe's kitchen (Case study - Lezioni dalla cucina di Lowe)
description: Il team HoloLens vuole condividere alcune delle procedure consigliate derivate dal progetto di HoloLens Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, cucina, case study
ms.openlocfilehash: f2428a23e07d62156d38f43dfd5d6ddda20d57340d17908cf326ca9f37d223b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210391"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Case study - Lessons from the Lowe's kitchen (Case study - Lezioni dalla cucina di Lowe)

Il team HoloLens vuole condividere alcune delle procedure consigliate derivate dal progetto di HoloLens Lowe. Di seguito è riportato un video dell'HoloLens lowe proiettato nel keynote di Satya 2016 Ignite.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Procedure consigliate HoloLens lowe

I due video trattano le procedure consigliate derivate dal progetto pilota di lowe HoloLens che si trova in due negozi lowe da aprile 2016. Gli argomenti principali sono:
* Ottimizzare le prestazioni per un dispositivo mobile
* Creare metodi UX con un frame olografico completo (seconda conversazione)
* Allineamento della precisione (seconda conversazione)
* Esperienze olografiche condivise (seconda conversazione)
* Interazione con i clienti (seconda conversazione)

## <a name="video-1"></a>Video 1

**Ottimizzare le prestazioni per un** dispositivo HoloLens è un dispositivo senza tethering con tutta l'elaborazione in corso nel dispositivo. Ciò richiede una piattaforma per dispositivi mobili e una mentalità simile alla creazione di applicazioni per dispositivi mobili. Microsoft consiglia all'applicazione HoloLens mantenere 60FPS per offrire agli utenti un'esperienza ottimale. La presenza di fps bassi può causare ologrammi instabili.

Alcuni degli aspetti più importanti da esaminare quando si sviluppano in HoloLens sono l'ottimizzazione/il contrasto degli asset, l'uso di shader personalizzati (disponibili gratuitamente nel [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)). Un'altra considerazione importante è misurare la frequenza dei fotogrammi dall'inizio del progetto. A seconda del progetto, anche l'ordine di visualizzazione degli asset può essere un grande collaboratore
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Video 2

**Creare metodi UX con un frame olografico completo** È importante comprendere la posizione degli ologrammi in un mondo fisico. Con Lowe si parla di diversi metodi di esperienza utente che consentono agli utenti di sperimentare da vicino gli ologrammi continuando a vedere l'ambiente più ampio degli ologrammi.

**Allineamento della precisione** Per lo scenario di Lowe, è fondamentale che l'esperienza abbia l'allineamento della precisione degli ologrammi alla cucina fisica. Vengono illustrate le tecniche che consentono di garantire un'esperienza che convinca gli utenti che l'ambiente fisico è cambiato.

**Esperienze olografiche condivise** Il modo principale in cui viene utilizzata l'esperienza di Lowe è l'inenza. Una persona può modificare il controsoffitto e l'altra persona potrà vedere le modifiche. Questa è stata definita "esperienze condivise".

**Interazione con i clienti** I progettisti di Lowe non usano un HoloLens, ma devono vedere cosa vedono i clienti. Viene illustrato come acquisire ciò che il cliente visualizza in un'applicazione UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
