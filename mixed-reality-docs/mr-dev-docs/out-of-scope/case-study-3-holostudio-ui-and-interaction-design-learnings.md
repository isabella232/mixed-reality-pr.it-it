---
title: "Case study : 3 app HoloStudio'interfaccia utente e di progettazione delle interazioni"
description: Lezioni apprese durante la progettazione dell'interfaccia utente e delle interazioni per HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195870"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Case study : 3 app HoloStudio'interfaccia utente e di progettazione delle interazioni

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) è stata una delle prime app Microsoft per HoloLens. Per questo è stato necessario creare nuove procedure consigliate per l'interfaccia utente 3D e la progettazione delle interazioni. A tale scopo, sono stati evasi molti test utente, prototipi, tentativi ed errori.

Si sa che non tutti hanno a disposizione le risorse necessarie per eseguire questo tipo di ricerca, quindi abbiamo condiviso tre cose apprese durante lo sviluppo di HoloStudio sull'interfaccia utente e sulla progettazione delle interazioni per le app HoloLens.

## <a name="watch-the-video"></a>Video

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema #1: Gli utenti non vogliono spostare le proprie creazioni

In origine il workbench in HoloStudio è stato progettato come un rettangolo, proprio come nel mondo reale. Il problema è che le persone hanno una durata di esperienza che indica loro di rimanere al loro posto quando siede a una cassa o lavorano davanti a un computer, quindi non si spostano nel workbench ed esplorano la creazione 3D da tutti i lati.

![La progettazione rettangolare del workbench in HoloStudio dissuaded users from moving around and seeing their creations from all sides (Gli utenti non si spostano e vedono le loro creazioni da tutti i lati).](images/rectangular-workbench-500px.jpg)

Abbiamo avuto le informazioni per completare il workbench, in modo che non ci fosse una posizione "anteriore" o chiara in cui ci si sarebbe trovati. Quando è stato testato, improvvisamente le persone hanno iniziato a spostarsi ed esplorare le proprie creazioni in modo personalizzato.

![La progettazione circolare di Workbench ha invoto gli utenti a spostarsi in tutte le loro creazioni.](images/circular-workbench-500px.jpg)

**Cosa abbiamo imparato**

È importante pensare sempre a ciò che è comodo per l'utente. Sfruttare il loro spazio fisico è una funzionalità interessante HoloLens e un'operazione che non è possibile eseguire con altri dispositivi.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: le finestre di dialogo modali a volte sono fuori dalla cornice olografica

In alcuni casi, l'utente potrebbe essere in una direzione diversa rispetto a un elemento che richiede attenzione nell'app. In un PC è sufficiente visualizzare una finestra di dialogo, ma se lo si fa in un ambiente 3D, è possibile che la finestra di dialogo si distorsi. Sono necessari per leggere il messaggio, ma l'istinto è tentare di allontanarsi da esso. Questa reazione è molto utile se si sta riproducendo un gioco, ma in uno strumento progettato per il lavoro è meno che ideale.

Dopo aver provato alcuni elementi diversi, è stato infine deciso di usare un sistema di "bolla di riflessione" per i dialoghe e sono stati aggiunti i tendenziali che gli utenti possono seguire fino a dove è necessaria l'attenzione nell'applicazione. Abbiamo anche effettuato l'pulsazione dei tendenziali, che implicava un senso di direzionalità in modo che gli utenti sapranno dove andare.

![Il sistema "Thought Bubble" includeva tendenti pulsazioni che hanno fornito un senso di direzione, guidando gli utenti verso il punto in cui era necessaria l'attenzione nell'app.](images/thought-bubble-500px.jpg)

**Cosa abbiamo imparato**

In 3D è molto più difficile avvisare gli utenti degli aspetti a cui devono prestare attenzione. L'uso di attenzione, ad esempio [l'audio](../design/spatial-sound.md)spaziale, i raggi di luce o le bolle di pensare, può portare gli utenti a dove devono essere.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problemi #3: a volte l'interfaccia utente può essere bloccata da altri ologrammi

In alcuni casi un utente vuole interagire con un ologramma e i controlli dell'interfaccia utente associati, ma viene bloccato dalla visualizzazione perché è davanti a essi un altro ologramma. Durante lo sviluppo di HoloStudio, abbiamo usato la versione di valutazione e l'errore per trovare una soluzione.

![Un controllo dell'interfaccia utente associato a un ologramma può diventare bloccato se è presente un altro ologramma tra di esso e l'utente HoloLens.](images/ui-blocked-500px.jpg)

Si è provato a spostare il controllo dell'interfaccia utente più vicino all'utente in modo che non fosse bloccato, ma si è scoperto che non era comodo per l'utente guardare un controllo vicino all'utente mentre guardava contemporaneamente un ologramma lontano. Se, tuttavia, il controllo è stato spostato davanti all'ologramma più vicino all'utente, sembra che sia stato scollegato dall'ologramma che avrebbe avuto effetto.

Infine, abbiamo finito per fantasmaare il controllo dell'interfaccia utente e metterlo alla stessa distanza dall'utente dell'ologramma a cui è associato, in modo che entrambi si senta connessi. In questo modo l'utente può interagire con il controllo anche se è stato nascosto.

![La soluzione: il controllo dell'interfaccia utente era fantasma, che consentiva l'interazione con il controllo e lo faceva in modo che fosse connesso all'ologramma su cui stava interessando.](images/ghosting-ui-500px.jpg)

**Cosa abbiamo imparato**

Gli utenti devono poter accedere facilmente ai controlli dell'interfaccia utente anche se sono stati bloccati, quindi è necessario individuare i metodi per garantire che gli utenti possano completare le attività indipendentemente dalla posizione in cui si trova l'ologramma nel mondo reale.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Sr. Holographic Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Interazioni istintive](../design/interaction-fundamentals.md)
