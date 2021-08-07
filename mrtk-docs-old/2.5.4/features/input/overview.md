---
title: Cenni preliminari sull'input
description: Panoramica del sistema di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214729"
---
# <a name="input-overview"></a>Panoramica dell'input

Il sistema di input in MRTK consente di:

- Utilizzare input da un'ampia gamma di origini di input, ad esempio 6 controller DOF, mani articolate o parlato, tramite eventi di input.
- Definire azioni astratte, *ad esempio Select* o *Menu,* e associarle a input diversi.
- Configurare i puntatori collegati ai controller per gestire i componenti dell'interfaccia utente tramite eventi di stato attivo e puntatore.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Panoramica del sistema di input MRTK</sup>

Gli input vengono prodotti dai [**provider di dati di input (Gestione dispositivi).**](input-providers.md) Ogni provider corrisponde a una particolare origine di input: Open VR, Windows Mixed Reality (WMR), Unity Unity UnityStick, Windows Speech e così via. I provider vengono aggiunti  al progetto tramite il profilo provider di servizi registrati nel componente *mixed reality Toolkit* e generano automaticamente eventi di [**input**](input-events.md) quando sono disponibili le origini di input corrispondenti, ad esempio quando viene rilevato un controller WMR o un game pad connesso.

[**Le azioni di**](input-actions.md) input sono astrazioni su input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio, definire un'azione *Select* e mapparla al pulsante sinistro del mouse, un pulsante in un game pad e un trigger in un controller DOF 6. È quindi possibile fare in modo che la logica dell'applicazione sia in ascolto degli eventi Di selezione dell'azione di *input* anziché essere a conoscenza di tutti i diversi input che possono generarli. Le azioni di input sono definite nel profilo azioni di **input,** disponibile nel profilo del sistema di *input* nel componente *Toolkit* realtà mista.

[**I**](controllers.md) controller vengono creati dai *provider di input* quando i dispositivi di input vengono rilevati ed distrutti quando vengono persi o disconnessi. Il provider di input WMR, ad esempio, creerà controller *WMR* per 6 dispositivi DOF e controller mano *articolati WMR* per le mani articolate. È possibile eseguire il mapping degli input del controller alle azioni di input tramite il profilo **di mapping del controller**, all'interno del profilo del sistema di *input.* Gli eventi di input generati dai controller includeranno l'azione di input associata, se presente.

Ai controller possono [**essere collegati puntatori**](pointers.md) che esercitino query sulla scena per determinare l'oggetto gioco con lo stato attivo e generare [**eventi puntatore**](pointers.md#pointer-event-interfaces) su di esso. Ad esempio, l'indicatore *di misura* della linea esegue un raycast sulla scena usando la posizione del controller per calcolare l'origine e la direzione del raggio. I puntatori creati per ogni controller sono impostati in **Profilo** puntatore , in *Profilo sistema di input*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Flusso di eventi.</sup>

Anche se è possibile gestire gli [eventi di input direttamente nei componenti dell'interfaccia](input-events.md)utente, è consigliabile usare gli eventi puntatore [per](pointers.md#pointer-event-interfaces) mantenere l'implementazione indipendente dal dispositivo.

MRTK offre anche diversi metodi pratici per eseguire query sullo stato di input direttamente in modo indipendente dal dispositivo. Per [altri dettagli, vedi Accesso allo stato di input in MRTK.](input-state.md)
