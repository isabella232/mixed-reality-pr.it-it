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
ms.locfileid: "115219762"
---
# <a name="input-overview"></a>Panoramica dell'input

Il sistema di input in MRTK consente di:

- Usare input da un'ampia gamma di origini di input, ad esempio 6 controller DOF, mani articolate o voce, tramite eventi di input.
- Definire azioni astratte, *ad esempio Seleziona* o *Menu,* e associarle a input diversi.
- Configurare i puntatori collegati ai controller per guidare i componenti dell'interfaccia utente tramite eventi di stato attivo e puntatore.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Panoramica del sistema di input MRTK</sup>

Gli input vengono prodotti dai [**provider di dati di input (Gestione dispositivi).**](input-providers.md) Ogni provider corrisponde a una particolare origine di input: Open VR, Windows Mixed Reality (WMR), Unity Joystick, Windows Speech e così via. I provider vengono aggiunti  al progetto tramite il profilo dei provider di servizi registrati nel componente *mixed reality Toolkit* e generano automaticamente eventi di [**input**](input-events.md) quando sono disponibili le origini di input corrispondenti, ad esempio quando viene rilevato un controller WMR o un gamepad connesso.

[**Le azioni di**](input-actions.md) input sono astrazioni su input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio,  definire un'azione Select e mapparla al pulsante sinistro del mouse, un pulsante in un gamepad e un trigger in un controller DOF 6. È quindi possibile fare in modo che la logica dell'applicazione sia in ascolto per selezionare gli eventi di azione di *input* invece di dover tenere presenti tutti i diversi input che possono generarli. Le azioni di input sono definite nel profilo azioni di **input,** disponibile all'interno del profilo di sistema di *input* nel componente *Toolkit* realtà mista.

[**I**](controllers.md) controller vengono creati *dai provider di input* quando i dispositivi di input vengono rilevati ed distrutti quando vengono persi o disconnessi. Il provider di input WMR, ad esempio, creerà controller *WMR* per 6 dispositivi DOF e controller mano *articolati WMR* per le mani articolate. È possibile eseguire il mapping degli input del controller alle azioni di input tramite **il profilo di mapping del controller**, all'interno del profilo di sistema di *input*. Gli eventi di input generati dai controller includeranno l'azione di input associata, se presente.

Ai controller possono [**essere associati puntatori**](pointers.md) che esercitino query sulla scena per determinare l'oggetto del gioco con lo stato attivo e generare eventi [**puntatore**](pointers.md#pointer-event-interfaces) su di esso. Ad esempio, il *puntatore di linea* esegue un raycast sulla scena usando la posizione del controller per calcolare l'origine e la direzione del raggio. I puntatori creati per ogni controller sono impostati in **Profilo** puntatore , in *Profilo di sistema di input*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Flusso di eventi.</sup>

Anche se è possibile gestire gli [eventi di input direttamente nei componenti](input-events.md)dell'interfaccia utente, è consigliabile usare gli eventi puntatore per mantenere l'implementazione indipendente dal dispositivo. [](pointers.md#pointer-event-interfaces)

MRTK offre anche diversi metodi pratici per eseguire query sullo stato di input direttamente in modo indipendente dal dispositivo. Per altre informazioni, vedere Accesso allo stato [di input in MRTK.](input-state.md)
