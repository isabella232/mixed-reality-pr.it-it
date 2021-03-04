---
title: Cenni preliminari sull'input
description: Panoramica del sistema di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ec8ebced1f7faea04e88068612cd642e15fb165f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782051"
---
# <a name="input-overview"></a>Cenni preliminari sull'input

Il sistema di input in MRTK consente di:

- Utilizzare gli input da un'ampia gamma di origini di input, ad esempio 6 controller DOF, articolati o vocali, tramite gli eventi di input.
- Definire azioni astratte, ad esempio *Select* o *menu*, e associarle a input diversi.
- Configurare i puntatori collegati ai controller per guidare i componenti dell'interfaccia utente tramite eventi di stato attivo e puntatore.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Panoramica del sistema di input MRTK</sup>

Gli input vengono prodotti da [**provider di dati di input (gestione dispositivi)**](input-providers.md). Ogni provider corrisponde a una determinata origine di input: Open VR, Windows Mixed Reality (WMR), Unity joystick, Windows Speech e così via. I provider vengono aggiunti al progetto tramite il **profilo dei provider di servizi registrati** nel componente del *Toolkit di realtà mista* e produrranno automaticamente [**gli eventi di input**](input-events.md) quando sono disponibili le origini di input corrispondenti, ad esempio quando viene rilevato un controller WMR o un gamepad connesso.

Le [**azioni di input**](input-actions.md) sono astrazioni rispetto a input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio, definire un'azione *Select* ed eseguirne il mapping con il pulsante sinistro del mouse, un pulsante in un gamepad e un trigger in un controller 6 DOF. È quindi possibile fare in modo che la logica dell'applicazione attenda gli eventi di azione *Select* input anziché tenere presente tutti i diversi input in grado di produrli. Le azioni di input sono definite nel **profilo azioni di input**, disponibile all'interno del *profilo del sistema di input* nel componente del *Toolkit di realtà mista* .

I [**controller**](controllers.md) vengono creati dai *provider di input* quando i dispositivi di input vengono rilevati ed eliminati definitivamente quando vengono persi o disconnessi. Il provider di input WMR, ad esempio, creerà *controller WMR* per 6 dispositivi DOF e *controller mano WMR articolati* per le mani articolate. È possibile eseguire il mapping degli input del controller alle azioni di input tramite il **profilo di mapping del controller**, all'interno del profilo di sistema di *input*. Gli eventi di input generati dai controller includeranno l'azione di input associata, se disponibile.

Ai controller possono essere associati [**puntatori**](pointers.md) che eseguono query sulla scena per determinare l'oggetto gioco con lo stato attivo e generare [**eventi puntatore**](pointers.md#pointer-event-interfaces) su di esso. Ad esempio, il *puntatore di linea* esegue un Raycast sulla scena usando la post del controller per calcolare l'origine e la direzione del raggio. I puntatori creati per ogni controller sono configurati nel **profilo del puntatore**, sotto il *profilo di sistema di input*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Flusso eventi.</sup>

Sebbene sia possibile gestire [gli eventi di input direttamente nei componenti dell'interfaccia utente](input-events.md), è consigliabile usare [gli eventi puntatore](pointers.md#pointer-event-interfaces) per impedire che l'implementazione sia indipendente dal dispositivo.

MRTK fornisce anche diversi metodi pratici per eseguire query sullo stato di input direttamente in modo indipendente dal dispositivo. Per ulteriori informazioni, vedere [accesso allo stato di input in MRTK](input-state.md) .
