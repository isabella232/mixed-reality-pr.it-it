---
title: Panoramica dell'architettura
description: Panoramica dell'architettura di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, architettura MRTK,
ms.openlocfilehash: ccd53805d4b0c13ef97123d7be9af863ac1299518d2b018bc5801279a9b4f369
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187608"
---
# <a name="architecture-overview"></a>Panoramica dell'architettura

Per un'introduzione generale al contenuto di MRTK, le informazioni sull'architettura contenute in questo documento consentono di comprendere quanto segue:

- Grandi parti di MRTK e come si connettono
- Concetti introdotti da MRTK che potrebbero non esistere in Vanilla Unity
- Funzionamento di alcuni dei sistemi più grandi (ad esempio Input)

Questa sezione non ha lo scopo di illustrare come eseguire le attività, ma piuttosto come tali attività sono strutturate e perché.

## <a name="many-audiences-one-toolkit"></a>Molti destinatari, un toolkit

MRTK non ha un singolo pubblico uniforme. È stato scritto per supportare casi d'uso che vanno dagli hackathon per la prima volta ai singoli utenti che compilano esperienze complesse e condivise per l'azienda. È possibile che sia stato scritto codice e API ottimizzati per uno più dell'altro (ad esempio, alcune parti di MRTK sembrano più ottimizzate per la "configurazione con un clic"), ma è importante notare che alcune di queste sono più per motivi cronologici e di risorse. Con l'evolversi di MRTK, le funzionalità create devono essere progettate per la scalabilità per supportare la gamma di casi d'uso.

MRTK ha anche requisiti per ridimensionare correttamente le esperienze vr e AR. Dovrebbe essere facile compilare applicazioni che normalmente fallback nel comportamento quando vengono distribuite in un HoloLens 2 O un HoloLens 1 e dovrebbe essere semplice compilare applicazioni che hanno come destinazione OpenVR e WMR (e altre piattaforme). Anche se a volte il team può concentrarsi su un'iterazione specifica su un sistema o una piattaforma specifica, l'obiettivo a lungo termine è quello di creare un'ampia gamma di supporto per ogni luogo in cui le persone stanno creando esperienze di realtà mista.

## <a name="high-level-breakdown"></a>Suddivisione di alto livello

MRTK è sia una raccolta di strumenti per ottenere rapidamente esperienze di realtà mista (MR), sia un framework di applicazioni con opinioni sul proprio runtime, su come deve essere esteso e su come deve essere configurato.

A livello elevato, il codice MRTK può essere suddiviso nei modi seguenti:

![Diagramma di panoramica dell'architettura](../features/images/architecture/MRTK_Architecture.png)

MrTK contiene anche un altro set di utilità grab-bag che hanno dipendenze da poco o nessuna sul resto di MRTK (per elencarne alcune: strumenti di compilazione, risolutori, fattori di influenza audio, utilità di smoothing e renderer di linea)

Il resto della documentazione dell'architettura verrà compilato in basso, a partire dal framework e dal runtime, procedendo verso sistemi più interessanti e complessi, ad esempio l'input. Per continuare con la panoramica dell'architettura, vedere il sommario.
