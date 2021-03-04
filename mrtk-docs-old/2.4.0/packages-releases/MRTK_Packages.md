---
title: MRTK_Pakages
description: Pakages in MRTK che supportano l'hardware e le piattaforme a realtà mista.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity pakage Manager,
ms.openlocfilehash: e55077df9f6415b50b0dd6b614696914c49e702e
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783134"
---
# <a name="mixed-reality-toolkit-packages"></a>Pacchetti Toolkit per realtà mista

Il Toolkit di realtà mista (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista multipiattaforma offrendo supporto per l'hardware e le piattaforme di realtà mista.

MRTK viene fornito tramite i seguenti pacchetti Unity:

- [Foundation](#foundation-package)
- [Estensioni](#extensions-package)
- [esempi](#examples-package)
- [Strumenti](#tools-package)

Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel ramo [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) su GitHub.

## <a name="foundation-package"></a>Pacchetto di base

Mixed Reality Toolkit Foundation è il set di codice che consente all'applicazione di sfruttare le funzionalità comuni nelle piattaforme di realtà mista.

<img src="../features//Images/Input/MRTK_Package_Foundation.png" width="350px" alt="Pakage Foundation" style="display:block;">  
<sup>Pacchetto di MRTK Foundation</sup>

MRTK Foundation è costituito da:

- **Pacchetto principale**

Il pacchetto principale contiene le definizioni per tutte le interfacce comuni, le classi e i tipi di dati utilizzati da tutti gli altri componenti. Si consiglia vivamente alle applicazioni di accedere ai componenti di MRTK esclusivamente tramite le interfacce definite per consentire il massimo livello di compatibilità tra le piattaforme.

- **Provider di piattaforma**

I pacchetti del provider della piattaforma MRTK sono i componenti che consentono al Toolkit di realtà misto di usare la funzionalità di piattaforma e hardware di realtà mista.

Le piattaforme supportate includono:

- Windows Mixed Reality
- OpenVR
- Windows Voice

- **Servizi di sistema**

I servizi di base forniscono le implementazioni predefinite per le interfacce del servizio di sistema, definite nel pacchetto principale.

MRTK Foundation include i servizi di sistema seguenti:

- [Sistema di limiti](../features/Boundary/BoundarySystemGettingStarted.md)
- [Sistema di diagnostica](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [Sistema di input](../features/Input/Overview.md)
- [Sistema di riconoscimento spaziale](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [Sistema Teleport](../features/TeleportSystem/Overview.md)

- **Asset funzionalità**

Gli asset di funzionalità sono raccolte di funzionalità correlate fornite come asset Unity e script, inclusi i controlli dell'interfaccia utente, gli asset standard e altro ancora.

## <a name="extensions-package"></a>Pacchetto di estensioni

Il pacchetto di estensioni contiene servizi e componenti aggiuntivi che estendono le funzionalità del pacchetto di base.

- [Servizio transizione scena](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md)

## <a name="examples-package"></a>Pacchetto di esempi

Il pacchetto degli esempi contiene demo, script di esempio e scene di esempio che esercitano le funzionalità del pacchetto di base. Questo pacchetto contiene la [scena HandInteractionExample](../features/README_HandInteractionExamples.md) (illustrata di seguito) che contiene oggetti di esempio che rispondono a diversi tipi di input della mano (articolati e non articolati).

![Scena HandInteractionExample](../features/Images/MRTK_Examples.png)

Questo pacchetto contiene anche le demo di rilevamento degli occhi, [documentate qui](../features/EyeTracking/EyeTracking_ExamplesOverview.md)

Più in generale, tutte le nuove funzionalità di MRTK devono contenere un esempio corrispondente nel pacchetto degli esempi, approssimativamente seguendo la stessa struttura di cartelle e la stessa posizione.

## <a name="tools-package"></a>Pacchetto strumenti

Il pacchetto Tools contiene strumenti utili per la creazione di esperienze di realtà miste il cui codice non verrà fornito come parte di un'applicazione.

- [Finestra dipendenze](../features/Tools/DependencyWindow.md)
- [Creazione guidata servizio di estensione](../features/Tools/ExtensionServiceCreationWizard.md)
- [Ottimizza finestra](../features/Tools/OptimizeWindow.md)
- [Utilità screenshot](../features/Tools/ScreenshotUtility.md)

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'architettura](../Architecture/Overview.md)
- [Sistemi, servizi di estensione e provider di dati](../Architecture/SystemsExtensionsProviders.md)
