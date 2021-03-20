---
title: SpatialObjectMeshObserver
description: Documentazione sull'osservatore mesh spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0ac419313c474f4dfe5d1a9da4dea1dea1ee755f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692478"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>Configurazione degli osservatori mesh per l'editor

Un modo pratico per fornire i dati di rete dell'ambiente nell'editor di Unity consiste nell'usare la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe. L' *osservatore mesh di oggetti spaziali* è un provider di dati solo editor per il [sistema di riconoscimento spaziale](SpatialAwarenessGettingStarted.md) che consente di importare i dati del modello 3D per rappresentare una mesh spaziale. Un uso comune dell' *osservatore mesh di oggetti spaziali* consiste nell'importare i dati analizzati tramite un HoloLens Microsoft per testare il modo in cui un'esperienza si adatta a diversi ambienti da Unity.

## <a name="getting-started"></a>Introduzione

In questa guida viene illustrata la configurazione di un *Observer mesh di oggetti spaziali*. Per abilitare questa funzionalità, è necessario eseguire tre passaggi principali.

1. Aggiungere un *Observer mesh di oggetti spaziali* al profilo del sistema di riconoscimento spaziale
1. Impostare l'oggetto dati mesh ambiente
1. [Configurare il resto delle proprietà del profilo osservatore mesh](ConfiguringSpatialAwarenessMeshObserver.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configurare un profilo *osservatore mesh oggetto spaziale*

1. Selezionare il profilo di configurazione del *Toolkit di realtà mista* desiderato o selezionare l'oggetto del *Toolkit di realtà mista* in scena
1. Aprire o espandere la scheda *sistema di riconoscimento spaziale*
1. Fai clic sul pulsante *"Aggiungi osservatore spaziale"*

    ![Aggiungi osservatore spaziale](../Images/SpatialAwareness/AddObserver.png)

1. Selezionare il tipo di *SpatialObjectMeshObserver*

    ![Seleziona osservatore mesh oggetto spaziale](../Images/SpatialAwareness/SelectObjectObserver.png)

1. Selezionare l' *oggetto mesh spaziale* desiderato. Per impostazione predefinita, l'Observer viene configurato con un modello di esempio. Questo modello è stato creato usando un HoloLens Microsoft, ma è possibile [creare un nuovo oggetto mesh di analisi](#acquiring-environment-scans).
1. [Configurare il resto delle proprietà del profilo osservatore mesh](ConfiguringSpatialAwarenessMeshObserver.md)

    ![Selezionare l'oggetto mesh](../Images/SpatialAwareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Note del profilo osservatore mesh oggetto spaziale

Poiché l' *osservatore mesh di oggetti spaziali* carica i dati da un modello 3D, non rispetta alcune delle impostazioni standard dell'Observer mesh descritte di seguito.

**Intervallo di aggiornamento**

L'  *osservatore mesh di oggetti spaziali* Invia tutte le mesh a un'applicazione quando il modello viene caricato. Non simula i Delta temporali tra gli aggiornamenti. Un'applicazione può ricevere nuovamente gli eventi mesh chiamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**Osservatore stazionario**

L' *osservatore mesh oggetto spaziale* considera tutti gli oggetti mesh 3D come stazionari e non considera l'origine.

**Forma ed extent dell'Observer**

L'  *osservatore mesh di oggetti spaziali* invia l'intera mesh 3D all'applicazione. Gli extent e la forma Observer non vengono considerati.

**Livello di dettaglio e triangoli/misuratore cubico**

L'Observer non tenta di trovare il modello 3D LODs quando invia le mesh all'applicazione.

## <a name="acquiring-environment-scans"></a>Acquisizione di analisi dell'ambiente

In questa sezione vengono descritte informazioni aggiuntive per la creazione e la raccolta di file di *oggetti mesh spaziali* da utilizzare con l' *osservatore mesh di oggetti spaziali*.

### <a name="windows-device-portal"></a>Portale di dispositivi di Windows

Il [portale per dispositivi Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) può essere usato per scaricare la mesh spaziale, come file con estensione obj, da un dispositivo HoloLens Microsoft.

1. Eseguire un'analisi semplicemente e visualizzare l'ambiente desiderato con un HoloLens
1. Connettersi a HoloLens tramite il portale del dispositivo Windows
1. Passa alla pagina della *visualizzazione 3D*
1. Fare clic sul pulsante *Aggiorna* in sezione *mapping spaziale*
1. Fare clic sul pulsante *Salva* nella sezione *mapping spaziale* per salvare il file obj sul PC

> [!NOTE]
> **File HoloToolkit. room**
>
> Molti sviluppatori utilizzeranno in precedenza HoloToolkit per analizzare gli ambienti e creare file con estensione room. Il Toolkit di realtà mista supporta ora l'importazione di questi file come GameObject in Unity e li usa come *oggetti mesh spaziali* nell'Observer.

## <a name="see-also"></a>Vedi anche

- [Profili](../Profiles/Profiles.md)
- [Guida alla configurazione del profilo del Toolkit di realtà mista](../../out-of-scope/MixedRealityConfigurationGuide.md)
- [Introduzione a consapevolezza spaziale](SpatialAwarenessGettingStarted.md)
- [Configurazione degli osservatori mesh nel dispositivo](ConfiguringSpatialAwarenessMeshObserver.md)
- [Configurazione di osservatori mesh tramite codice](UsageGuide.md)
- [Avviare il Portale di dispositivi di Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)
