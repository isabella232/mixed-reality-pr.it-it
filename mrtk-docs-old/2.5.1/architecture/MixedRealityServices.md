---
title: MixedRealityServices
description: Servizi correlati a MRTK in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c23c16e7dac54ff209beca24bd8b8b857967f697
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104680804"
---
# <a name="what-makes-a-mixed-reality-feature"></a>Cosa rende una funzionalità di realtà mista

Per evitare sovraccarichi delle prestazioni della `MonoBehaviour` classe, tutti i *Servizi* (sistemi, funzionalità o moduli che richiedono operazioni indipendenti in una soluzione di realtà mista, ad esempio input, limite, conoscenza spaziale), devono essere semplici classi c# discrete che implementano `IMixedRealityService` e per la registrazione in `MixedRealityToolkit` .

`MixedRealityToolkit`Quindi coordina tutti i riferimenti tra i servizi e garantisce che ricevano tutti gli eventi appropriati, ad esempio È possibile riattivare/inizializzare, aggiornare, eliminare definitivamente e facilitare la ricerca di altri servizi, quando necessario.

Inoltre, `MixedRealityToolkit` gestisce anche l'SDK attivo VR/XR/AR in uso nel progetto in esecuzione, per inizializzare il dispositivo attivo in base all'hardware collegato e istigare il corretto funzionamento.

## <a name="a-service"></a>Un servizio

Un singolo servizio può essere qualsiasi funzionalità che deve essere implementata nel progetto. Tradizionalmente alcuni progetti usano i *singleton* che devono essere attivi nella scena, ma questo modello presenta vantaggi e svantaggi. Abbiamo deciso di abbandonare questo modello a favore di un approccio ibrido che offre diversi vantaggi rispetto alle implementazioni singleton tradizionali con `MonoBehaviours` , ovvero:

* Prestazioni: senza l'overhead di un `MonoBehaviour` , [gli aggiornamenti degli script sono più veloci circa il 80% e non richiedono un `GameObject` per vivere nella scena](https://blogs.unity3d.com/2015/12/23/1k-update-calls/).
* Reference-Capacity: i servizi possono essere individuati dalla `MixedRealityToolkit` molto più veloce e più semplice rispetto alla ricerca `GameObjects` in una scena o all'uso di `FindObjectsOfType<T>` .
* Nessuna dipendenza di tipo: Sebbene un metodo simile all'inserimento delle dipendenze, i servizi possano essere separati dal tipo, ciò significa che l'implementazione concreta può essere scambiata in qualsiasi momento senza influire negativamente sul codice che lo utilizza, ad esempio sostituendo il InputSystem predefinito con quello personalizzato, purché sia stata implementata completamente ogni interfaccia.
* Utilizzo multiscena: se un servizio deve essere a conoscenza di una `transform` posizione in una scena, può semplicemente fare riferimento o creare, `GameObject` _anziché essere un componente associato_. Questo rende molto più semplice trovare e usare il servizio quando il progetto si estende su più scene.

## <a name="service-interfaces"></a>Interfacce del servizio

Il contenitore di *Servizi* utilizza un tipo di *interfaccia* predefinito per l'archiviazione e il recupero di qualsiasi servizio, in modo da garantire che non esistano dipendenze rigide nel Toolkit di realtà mista, in modo che ogni sottosistema possa essere facilmente scambiato con un altro (purché sia conforme all'interfaccia).

Le interfacce di sistema correnti fornite dal Toolkit per la realtà mista includono:

* [`IMixedRealityInputSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputSystem)
* [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)
* [`IMixedRealityTeleportSystem`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportSystem)

Quando si creano implementazioni personalizzate di questi sistemi, è necessario assicurarsi che ogni sia conforme alle interfacce fornite dal Toolkit di realtà mista (ad esempio, se si sostituisce InputSystem con un'altra progettazione).

> [!NOTE]
> Tutti i servizi devono anche ereditare dalla [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe o implementare [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , per implementare le funzioni richieste da, in `MixedRealityToolkit` modo che i cicli di vita vengano gestiti in modo appropriato. es. Initialize, Update e Destroy vengono chiamati correttamente.
