---
title: MixedRealityServices
description: Servizi correlati a MRTK in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 06b003e78387ba3ae6dc3c39eaba05c514f6c58cd474cc26a14ef12b561a2914
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187635"
---
# <a name="what-makes-a-mixed-reality-feature"></a>Che cosa rende una funzionalità di realtà mista

Per evitare il sovraccarico delle prestazioni della classe , tutti i servizi (sistemi, funzionalità o moduli che richiedono un'operazione indipendente in una soluzione di realtà mista, ad esempio input, limite, consapevolezza spaziale) devono essere `MonoBehaviour` classi c# discrete semplici che implementano e registrano con  `IMixedRealityService` `MixedRealityToolkit` .

Coordina quindi tutti i riferimenti tra i servizi e garantisce che ricevano tutti gli `MixedRealityToolkit` eventi appropriati ,ad esempio Durante l'inizializzazione, l'aggiornamento e l'eliminazione, nonché facilitando la ricerca di altri servizi quando necessario.

Inoltre, mantiene l'SDK VR/XR/AR attivo in uso nel progetto in esecuzione, per inizializzare il dispositivo attivo in base all'hardware collegato e `MixedRealityToolkit` istigare il corretto funzionamento.

## <a name="a-service"></a>Un servizio

Un singolo servizio può essere qualsiasi funzionalità che deve essere implementata nel progetto. Tradizionalmente alcuni progetti usano *singleton* che devono essere attivi nella scena, ma questo modello presenta vantaggi e svantaggi. Si è deciso di interrompere questo modello a favore di un approccio ibrido che offre diversi vantaggi rispetto alle implementazioni singleton tradizionali con `MonoBehaviours` , ad esempio:

* Prestazioni: senza il sovraccarico di un , gli aggiornamenti degli script sono circa `MonoBehaviour` [l'80% `GameObject` ](https://blogs.unity3d.com/2015/12/23/1k-update-calls/)più veloci e non richiedono un per la vita nella scena .
* Capacità di riferimento: i servizi possono essere individuati da molto più velocemente e `MixedRealityToolkit` più facilmente rispetto alla ricerca in una scena o `GameObjects` all'uso di `FindObjectsOfType<T>` .
* Nessuna dipendenza del tipo: anche se un metodo simile all'inserimento delle dipendenze, i servizi possono essere disaccoccodati dal tipo, ciò significa che l'implementazione concreta può essere scambiata in qualsiasi momento senza influire negativamente sul codice che la utilizza ,ad esempio sostituendo inputSystem predefinito con quello personalizzato, purché sia stata implementata completamente ogni interfaccia.
* Utilizzo di più scene: se un servizio deve conoscere una posizione in una scena, può semplicemente fare riferimento o creare un oggetto anziché essere un componente `transform` `GameObject` _a esso associato._ In questo modo è molto più semplice trovare e usare il servizio quando il progetto si estende su più scene.

## <a name="service-interfaces"></a>Interfacce di servizio

Il  contenitore del  servizio usa un tipo di interfaccia predefinito per l'archiviazione e il recupero di qualsiasi servizio, in modo che non siano presenti dipendenze rigide all'interno del Toolkit di realtà mista, in modo che ogni sottosistema possa essere facilmente scambiato con un altro (purché sia conforme all'interfaccia).

Le interfacce di sistema correnti fornite dal modello di Toolkit includono:

* [`IMixedRealityInputSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputSystem)
* [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)
* [`IMixedRealityTeleportSystem`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportSystem)

Quando si creano implementazioni proprie di questi sistemi, è necessario assicurarsi che ognuna sia conforme alle interfacce fornite dal Toolkit di realtà mista, ad esempio se si sostituisce InputSystem con un altro modello di progettazione personalizzato.

> [!NOTE]
> Tutti i servizi devono anche ereditare dalla classe o implementare , per implementare le funzioni richieste da in modo che i relativi cicli di vita siano [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) gestiti in modo `MixedRealityToolkit` appropriato. (Ad esempio, Initialize, Update, Destroy vengono chiamati correttamente.
