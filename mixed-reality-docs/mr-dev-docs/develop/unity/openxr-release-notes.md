---
title: Note sulla versione del plug-in OpenXR di Realtà mista
description: Rimanere aggiornati sulle note sulla versione più recenti e sugli aggiornamenti al plug-in OpenXR di Realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394647"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Note sulla versione del plug-in OpenXR di Realtà mista

## <a name="100---current-release"></a>1.0.0 - Versione corrente

* Correzione di un bug per cui un oggetto XRAnchorSubsystem viene sempre avviato all'avvio dell'app indipendentemente dalla versione di ARAnchorManager presente.
* Correzione di un bug per cui la modalità di nuovaproiezione non funzionava correttamente.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 - 2021-06-14

* Dipende dal plug-in OpenXR 1.2.2 di Unity.
* Modifica delle funzionalità di Holographic Remoting in in singoli gruppi di funzionalità.
* Correzione di un bug per cui "Applica HoloLens 2 impostazioni del progetto" modifica lo spazio colore del progetto. Questa operazione non è più necessaria dopo il plug-in Unity OpenXR 1.2.0.
* Correzione di un bug per cui un dispositivo di input viene connesso senza disconnessione dopo la sospensione e la ripresa dell'applicazione.
* Aggiunta del supporto per il rilevamento di plug-in e stati di rilevamento correnti tramite ARSession.
* Correzione di un bug per cui il prefab ARFoundation "AR Default Plane" non era visibile.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 - 2021-06-02

* Supporta le estensioni MSFT di comprensione della scena OpenXR anziché le estensioni di anteprima.
* Il rilevamento del piano HoloLens 2 non richiede più versioni di anteprima dei runtime OpenXR di Realtà mista.

## <a name="095---2021-05-21"></a>0.9.5 - 2021-05-21

* Dipende dal plug-in OpenXR 1.2.0 di Unity
* Adattato alla nuova interfaccia utente della funzionalità (in OpenXR Plugin 1.2.0) per la configurazione.
* Correzione di un bug per cui il provider di fotocamere localizzate non annullava correttamente la registrazione.
* Pulizia di alcuni utilizzi aggiuntivi di [Preserve].
* Aggiornare il nome "HP Reverb G2 Controller (OpenXR)" nell'interfaccia utente del sistema di input.

## <a name="094---2021-05-20"></a>0.9.4 - 2021-05-20

* Dipende dal plug-in OpenXR 1.2.0 di Unity.
* Aggiunta della nuova API C# per ottenere il modello glTF del controller del movimento.
* Aggiunta di una nuova API C# per ottenere le configurazioni di visualizzazione abilitate e impostare le impostazioni di nuova progetto.
* Aggiunta di una nuova API C# per impostare impostazioni aggiuntive per il calcolo delle mesh con XRMeshSubsystem.
* Aggiunta della nuova API C# per configurare e sottoscrivere gli eventi di riconoscimento dei movimenti.
* Aggiunta della finestra di dialogo >comunicazione remota di XR->Editor di Windows.
* Aggiunta del supporto ARM per le applicazioni UWP HoloLens.

## <a name="093---2021-04-29"></a>0.9.3 - 2021-04-29

* Correzione di un bug per cui la connessione remota holographic non è affidabile
* Correzione di un bug per cui le prestazioni di rendering vr sono sotto-ottimali dopo l'aggiornamento al plug-in OpenXR 1.1.1 di Unity.

## <a name="092---2021-04-21"></a>0.9.2 - 2021-04-21

* Il rilevamento del piano HoloLens 2 nella versione del plug-in 0.9.1 funzionerà con la versione 105 del runtime di anteprima di Mixed Reality OpenXR.
* Il rilevamento del piano HoloLens 2 nella versione del plug-in 0.9.2 funzionerà con la versione 106 del runtime di anteprima di Mixed Reality OpenXR.
* Sono stati rimossi alcuni callback inutilizzati da InputProvider per impedire che chiamate come XRInputSubsystem.* GetTrackingOriginMode (che non sono gestite dal sistema di input) restituiranno esito positivo con valori fuorvianti.
* Suddividere la versione deprecata di XRAnchorStore nel proprio file per evitare l'avviso della console unity.

## <a name="091---2021-04-20"></a>0.9.1 - 2021-04-20

* Dipende dal plug-in OpenXR 1.1.1 di Unity.
* Aggiunta del supporto per l'applicazione Holographic Remoting per la piattaforma UWP.
* Correzione di UnityException in cui XRAnchorStore tentava di ottenere un'istanza delle impostazioni all'esterno del thread principale.

## <a name="090---2021-03-29"></a>0.9.0 - 2021-03-29

* Aggiunta del supporto per il mapping spaziale tramite XRMeshSubsystem e ARMeshManager.
* Aggiunta di una nuova API C# per ottenere handle OpenXR per supportare altri pacchetti Unity che utilizzano estensioni OpenXR.
* Aggiunta di una nuova API C# per l'interoperabilità con le API Windows.Perception per supportare altri pacchetti Unity che utilizzano le API WinRT perception.
* Sono stati rimossi i profili di interazione dalle funzionalità Windows Mixed Reality set di funzionalità, in modo che gli sviluppatori possano scegliere i controller del movimento con cui hanno testato.
* Aggiunta del validator della funzionalità di comunicazione remota dell'editor Holographic per consentire agli utenti di configurare correttamente la comunicazione remota dell'editor.
* Correzione di un bug per cui l'editor di Unity si arresta in modo anomalo quando si esce dalla modalità remota dell'editor Holographic dopo un errore di connessione.
* Correzione di un bug per cui trame alfa non premoltimulate comportano prestazioni non ottimali in HoloLens 2.
* Correzione di un bug per cui il tracciamento delle mani non si trovava correttamente quando l'origine della scena era a livello del piano.
* Correzione di un bug per cui il tracciamento della mesh manuale scompare dopo l'uscita e il caricamento di una nuova scena.
* Correzione di un bug per cui il provider di fotocamere localizzate non ha eseguito correttamente la pulizia.
* Lo spazio dei nomi dell'API XRAnchorStore è stato modificato in Microsoft.MixedReality.OpenXR.