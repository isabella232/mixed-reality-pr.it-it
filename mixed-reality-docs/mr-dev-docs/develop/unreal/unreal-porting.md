---
title: Aggiornamento di progetti in Unreal
description: Panoramica delle procedure di aggiornamento della versione e delle API deprecate nei progetti Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR realtà mista, visore VR di windows mixed reality, visore VR per realtà virtuale, porting, aggiornamento
ms.openlocfilehash: efad783ee199ed42c7355917a180855b3ec4f11b
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355706"
---
# <a name="upgrading-projects-in-unreal"></a>Aggiornamento di progetti in Unreal

Quando si esegue l'aggiornamento a una nuova versione di Unreal, le funzioni deprecate vengono visualizzate come avvisi durante la compilazione del progetto o la creazione del pacchetto del progetto.  Le funzioni sono deprecate quando viene aggiunta una nuova funzione da usare in sostituzione. 

## <a name="426-upgrades"></a>Aggiornamenti alla versione 4.26
 
Nella versione 4.26 tutte le piattaforme AR e VR sono state sottoposte a refactoring per aggiungere interfacce comuni e rendere il codice dell'applicazione indipendente dalla piattaforma.  A causa del refactoring, i progetti HoloLens aggiornati alla versione 4.26 possono visualizzare un numero di avvisi superiore al normale.  È consigliabile eseguire l'aggiornamento alle nuove API, in modo che il progetto possa essere facilmente convertito per altre piattaforme.

Nei messaggi di avviso verrà visualizzata la funzione deprecata e verrà indicata la funzione da usare in sostituzione.  Tutte le funzioni deprecate continueranno a funzionare per questa versione, ma potrebbero non funzionare nelle versioni future.  Le funzioni deprecate non verranno nemmeno più elencate durante la ricerca di funzioni in un progetto.

![Progetto della funzione Create Named ARPin](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Funzioni deprecate della versione 4.25

| Funzione deprecata | Nuova funzione |
| --- | --- |
| CreateNamedARPin | ![Progetto della funzione Pin Component](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Progetto della funzione Load ARPins from Local Store](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Progetto della funzione Save ARPin to Local Store](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Progetto della funzione Remove ARPin from Local Store](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Progetto della funzione Set Enabled XRCamera](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Progetto della funzione Resize XRCamera](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Progetto della funzione Toggle ARCapture per l'avvio dell'acquisizione della fotocamera](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Progetto della funzione Toggle ARCapture per l'arresto dell'acquisizione della fotocamera](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Progetto della funzione Toggle ARCapture per l'avvio dell'acquisizione del codice a matrice](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Progetto della funzione Toggle ARCapture per l'arresto dell'acquisizione del codice a matrice](images/unreal-porting-img-11.png) |
| Il mapping spaziale viene avviato automaticamente nella versione 4.25, mentre nella versione 4.26 deve essere attivato. | ![Progetto della funzione Toggle ARCapture per l'attivazione del mapping spaziale](images/unreal-porting-img-12.png) |
| ShowKeyboard | Rimossa nella versione 4.26 poiché la tastiera viene visualizzata automaticamente quando si attiva lo stato di un widget di testo. |
| HideKeyboard | Rimossa nella versione 4.26 poiché la tastiera viene nascosta automaticamente quando lo stato di un widget di testo non è più attivo. |
| SupportsHandTracking | ![Progetto della proprietà Supports Hand Tracking](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Progetto della proprietà IsDisplayOpaque](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Progetto della funzione Get Motion Controller Data](images/unreal-porting-img-15.png) |
| GetVersionString | ![Progetto della funzione Get Version String](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Progetto della proprietà IsTrackingAvailable](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Usare il sistema di azione di input di Unreal. |
| SetFocusPointForFrame | Rimossa nella versione 4.26.  In precedenza questa funzione veniva usata per la riproiezione durante la comunicazione remota, ora supportata dalla riproiezione avanzata. |