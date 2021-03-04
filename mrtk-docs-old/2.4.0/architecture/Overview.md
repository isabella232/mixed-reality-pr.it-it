---
title: Panoramica dell'architettura
description: Panoramica dell'architettura di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, architettura MRTK
ms.openlocfilehash: 569486924190de6e0310fff875fc6583053cfa74
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782043"
---
# <a name="architecture-overview"></a>Panoramica dell'architettura

Per un'introduzione generale al contenuto di MRTK, le informazioni sull'architettura contenute in questo documento consentiranno di comprendere quanto segue:

- Componenti di MRTK e modalità di connessione
- Concetti introdotti da MRTK che potrebbero non esistere in Vanilla Unity
- Come funzionano alcuni dei sistemi più grandi, ad esempio l'input.

Questa sezione non ha lo scopo di insegnare come eseguire le attività, ma piuttosto come strutturare tali attività e perché.

## <a name="many-audiences-one-toolkit"></a>Molti destinatari, un Toolkit

MRTK non dispone di un singolo gruppo di destinatari uniformi. È stato scritto per supportare casi di utilizzo compresi tra la prima volta gli hackathon, i singoli utenti che compilano esperienze condivise complesse per le aziende. È possibile che siano stati scritti codice e API che sono ottimizzati per uno più degli altri (ad esempio, alcune parti di MRTK sembrano più ottimizzate per "un solo clic su Configura"), ma è importante notare che alcune di queste sono più per motivi cronologici e di riapprovvigionamento. Man mano che MRTK si evolve, le funzionalità create devono essere progettate per la scalabilità in modo da supportare la gamma di casi d'uso.

MRTK dispone inoltre di requisiti per la scalabilità normale tra le esperienze VR e AR. Dovrebbe essere facile creare applicazioni che si riferiscono normalmente al comportamento quando vengono distribuite in un HoloLens 2 o HoloLens 1 e dovrebbe essere semplice compilare applicazioni destinate a OpenVR e WMR (e altre piattaforme). Sebbene a volte il team possa concentrare un'iterazione particolare su un sistema o una piattaforma specifica, l'obiettivo a lungo termine è creare un'ampia gamma di supporto per ogni persona che sviluppa esperienze di realtà miste.

## <a name="high-level-breakdown"></a>Suddivisione di alto livello

MRTK è una raccolta di strumenti che consentono di ottenere rapidamente un'esperienza di realtà mista (MR), nonché un Framework applicazione con opinioni sul proprio Runtime, su come deve essere esteso e su come deve essere configurato.

A un livello elevato, il MRTK può essere suddiviso nei modi seguenti:

![Diagramma della panoramica dell'architettura](../features/Images/Architecture/MRTK_Architecture.png)

Il MRTK contiene anche un altro set di utilità di recupero delle buste che non hanno dipendenze dal resto del MRTK (per elencarne alcune: strumenti di compilazione, risolutori, fattori di influenza audio, utilità di smussamento e renderer di riga)

Il resto della documentazione dell'architettura compilerà il massimo, a partire dal Framework e dal runtime, avanzando a sistemi più interessanti e complessi, ad esempio l'input. Per continuare con la panoramica dell'architettura, vedere il sommario.
