---
title: Aggiornamento di progetti in Unreal
description: Informazioni sulle procedure di aggiornamento della versione, sulle modifiche alle API e sulle deprecazioni per i progetti Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR realtà mista, visore VR di windows mixed reality, visore VR per realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 88b3f12bf32c81e39e622a7766119ca4d1b087f80cfc774148853926b6446dbc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197237"
---
# <a name="upgrading-projects-in-unreal"></a>Aggiornamento di progetti in Unreal

Quando si esegue l'aggiornamento a una nuova versione di Unreal, le funzioni deprecate vengono visualizzate come avvisi durante la compilazione dei progetti o la creazione del pacchetto del progetto.  Le funzioni sono deprecate quando viene aggiunta una nuova funzione da usare in sostituzione. 

## <a name="426-upgrades"></a>Aggiornamenti alla versione 4.26
 
Nella versione 4.26 tutte le piattaforme AR e VR sono state sottoposte a refactoring per aggiungere interfacce comuni e rendere il codice dell'applicazione indipendente dalla piattaforma. È quindi possibile che vengano visualizzati più avvisi del solito.  È consigliabile eseguire l'aggiornamento alle nuove API, in modo che il progetto possa essere facilmente convertito per altre piattaforme.

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

## <a name="426-changes"></a>Modifiche della versione 4.26

La modifica più significativa apportata consiste nel fatto che l'opzione **Start in VR** (Avvia in VR) disponibile in **Edit > Project Settings > Project > Description > Settings** (Modifica > Impostazioni progetto > Progetto > Descrizione > Impostazioni) è obbligatoria per l'avvio del plug-in Windows Mixed Reality. Senza questo parametro, gli ologrammi non vengono visualizzati nel dispositivo.
