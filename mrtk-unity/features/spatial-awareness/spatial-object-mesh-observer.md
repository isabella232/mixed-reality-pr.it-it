---
title: Osservatore di mesh di oggetti spaziali
description: Documentazione su Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176689"
---
# <a name="spatial-object-mesh-observer"></a>Osservatore di mesh di oggetti spaziali

Un modo pratico per fornire i dati della mesh dell'ambiente nell'editor di Unity è usare la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe . *Spatial Object Mesh Observer è* un provider di dati solo editor per il sistema [di](spatial-awareness-getting-started.md) consapevolezza spaziale che consente di importare dati del modello 3D per rappresentare una mesh spaziale. Un uso comune di *Spatial Object Mesh Observer* è quello di importare i dati analizzati tramite un Microsoft HoloLens per testare come un'esperienza si adatta a ambienti diversi dall'interno di Unity.

## <a name="getting-started"></a>Guida introduttiva

In questa guida verrà illustrata la configurazione di *un osservatore spatial object mesh.* Per abilitare questa funzionalità, è necessario eseguire tre passaggi chiave.

1. Aggiungere un *osservatore di mesh di oggetti spaziali* al profilo di sistema di consapevolezza spaziale
1. Impostare l'oggetto Dati mesh dell'ambiente
1. [Configurare le altre proprietà del profilo di Mesh Observer](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configurare un profilo *osservatore mesh di oggetti spaziali*

1. Selezionare il profilo *di configurazione* Toolkit realtà mista o selezionare l'oggetto Toolkit *realtà* mista nella scena
1. Aprire o espandere la *scheda Sistema di consapevolezza* spaziale
1. Fare clic sul *pulsante "Aggiungi osservatore spaziale"*

    ![Aggiungere un osservatore spaziale](../images/spatial-awareness/AddObserver.png)

1. Selezionare il *tipo SpatialObjectMeshObserver*

    ![Selezionare l'osservatore mesh di oggetti spaziali](../images/spatial-awareness/SelectObjectObserver.png)

1. Selezionare *l'oggetto mesh spaziale desiderato.* Per impostazione predefinita, l'osservatore è configurato con un modello di esempio. Questo modello è stato creato usando un Microsoft HoloLens ma è possibile [creare un nuovo oggetto mesh di analisi.](#acquiring-environment-scans)
1. [Configurare le altre proprietà del profilo di Mesh Observer](configuring-spatial-awareness-mesh-observer.md)

    ![Selezionare l'oggetto mesh](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Note sul profilo dell'osservatore della mesh di oggetti spaziali

Poiché *Spatial Object Mesh Observer* carica i dati da un modello 3D, non rispetta alcune delle impostazioni dell'osservatore mesh standard descritte di seguito.

**Intervallo di aggiornamento**

Spatial  *Object Mesh Observer* invia tutte le mesh a un'applicazione quando viene caricato il modello. Non simula i differenziali di tempo tra gli aggiornamenti. Un'applicazione può ricevere nuovamente gli eventi mesh chiamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**Osservatore stazionario**

*Spatial Object Mesh Observer* considera tutti gli oggetti mesh 3D stazionari e ignora l'origine.

**Forma ed extent dell'osservatore**

Spatial  *Object Mesh Observer* invia l'intera mesh 3D all'applicazione. La forma e gli extent dell'osservatore non vengono considerati.

**Livello di dettaglio e triangoli/contatore cubo**

Observer non tenta di trovare i LOD del modello 3D durante l'invio delle mesh all'applicazione.

## <a name="acquiring-environment-scans"></a>Acquisizione di analisi dell'ambiente

In questa sezione vengono descritte informazioni aggiuntive per creare e raccogliere file *oggetto mesh* spaziale da usare con Spatial Object *Mesh Observer.*

### <a name="windows-device-portal"></a>Portale di dispositivi di Windows

Il [Windows Portale di dispositivi](/windows/mixed-reality/using-the-windows-device-portal) può essere usato per scaricare la mesh spaziale, come file obj, da un Microsoft HoloLens dispositivo.

1. Eseguire la scansione semplicemente a piedi e visualizzando l'ambiente desiderato con un HoloLens
1. Connessione al HoloLens usando il Windows Portale di dispositivi
1. Passare alla *pagina Visualizzazione 3D*
1. Fare clic *sul pulsante* Aggiorna nella *sezione Mapping* spaziale
1. Fare clic *sul pulsante* Salva nella *sezione Mapping* spaziale per salvare il file obj nel PC

> [!NOTE]
> **File con estensione room di HoloToolkit**
>
> Molti sviluppatori hanno usato in precedenza HoloToolkit per analizzare gli ambienti e creare file con estensione room. L'Toolkit realtà mista supporta ora l'importazione di questi file come GameObject in Unity e li usa come *oggetti mesh spaziali* nell'osservatore.

## <a name="see-also"></a>Vedere anche

- [Profili](../profiles/profiles.md)
- [Guida alla configurazione Toolkit profilo Toolkit realtà mista](../../configuration/mixed-reality-configuration-guide.md)
- [Introduzione alla consapevolezza spaziale](spatial-awareness-getting-started.md)
- [Configurazione degli osservatori mesh nel dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurazione degli osservatori mesh tramite codice](usage-guide.md)
- [Avviare il Portale di dispositivi di Windows](/windows/mixed-reality/using-the-windows-device-portal)
