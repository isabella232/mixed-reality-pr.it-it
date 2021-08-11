---
title: Introduzione al sistema della scena
description: Pagina di destinazione per il sistema della scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5b4f1c3b0f069d320feca8ccecacc6c66576b50339ea7b7733f34525005dd842
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191561"
---
# <a name="scene-system-getting-started"></a>Introduzione al sistema della scena

## <a name="when-to-use-the-scene-system"></a>Quando usare il sistema della scena

Se il progetto è costituito da una singola scena, è probabile che il sistema della scena non sia necessario. È particolarmente utile quando si verificano una o più delle condizioni seguenti:

- Il progetto ha più scene.
- L'utente è spesso usato per il caricamento di una singola scena, ma non è il modo in cui elimina l'istanza mixedRealityToolkit.
- Si vuole un modo semplice per caricare in modo additivo più scene per costruire l'esperienza.
- Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.
- Si vuole mantenere l'illuminazione coerente e prevedibile in tutte le scene.

## <a name="scene-system-resources"></a>Risorse di sistema della scena

Per impostazione predefinita, il sistema della scena usa una coppia di oggetti scena (DefaultManagerScene e DefaultLighting). Se non è possibile trovare una di queste scene, verrà visualizzato un messaggio nel controllo profilo scene system.

![Messaggio delle risorse predefinite](../images/scene-system/DefaultResourcesMessage.png)

>! [Nota] Se il progetto usa scene di illuminazione e gestione personalizzate, questo messaggio può essere tranquillamente ignorato.

Le sezioni seguenti descrivono ora come risolvere il messaggio, in base al metodo usato per importare l'Toolkit.

### <a name="unity-package-manager-upm"></a>Unity Gestione pacchetti (UPM)

In Realtà mista Toolkit pacchetti UPM, le risorse di sistema della scena vengono in pacchetto come esempio. Poiché i pacchetti UPM non sono modificabili, Unity non è in grado di aprire il file della scena necessario a meno che non vengano importati in modo esplicito nel progetto.

Per importare, seguire questa procedura:

- Selezionare **Finestra**  >  **Gestione pacchetti**
- Selezionare **Mixed Reality Toolkit Foundation**
- Individuare **le risorse di sistema della** scena nella **sezione** Esempi

  ![Importare le risorse di sistema della scena](../images/scene-system/UpmImportSceneSystemResources.png)

- Selezionare **Importa**

### <a name="asset-unitypackage-files"></a>File di asset (con estensione unitypackage)

Se la cartella SceneSystemResources è stata eliminata o è stata deselezionata durante l'importazione, è possibile recuperarla seguendo questa procedura:

- Selezionare **Assets** Import Package Custom Package  >  **(Importa pacchetto**  >  **personalizzato)**
- Aprire **Microsoft.MixedReality.Toolkit. Pacchetto Foundation**
- Assicurarsi che **services/SceneSystem/SceneSystemResources** e tutte le opzioni figlio siano selezionate

  ![Reimportare le risorse di sistema della scena](../images/scene-system/ReimportSceneSystemResources.png)

- Selezionare **Importa**

## <a name="how-to-use-the-scene-system"></a>Come usare il sistema della scena

- [Tipi di scena](scene-system-scene-types.md)
- [Caricamento della scena di contenuto](scene-system-content-loading.md)
- [Monitoraggio del caricamento del contenuto](scene-system-load-progress.md)
- [Caricamento della scena di illuminazione](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Impostazioni dell'editor

Per impostazione predefinita, scene system applica diversi comportamenti nell'editor di Unity. Se si trova uno di questi comportamenti con la  mano, questi possono essere disabilitati nella sezione Editor Impostazioni del profilo scene system.

- `Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto. Disabilitare questa opzione se si vuole il controllo totale sulle impostazioni di compilazione.

- `Editor Enforce Scene Order:` Se true, il servizio garantisce che la scena di gestione sia visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto. Disabilitare questa opzione se si vuole il controllo totale sulla gerarchia della scena.

- `Editor Manage Loaded Scenes:` Se true, il servizio garantisce che il gestore, il contenuto e le scene di illuminazione siano sempre caricati. Disabilitare se si vuole il controllo totale sulle scene caricate nell'editor.

- `Editor Enforce Lighting Scene Types:` Se true, il servizio garantisce che solo i componenti relativi all'illuminazione definiti in siano consentiti `PermittedLightingSceneComponentTypes` nelle scene di illuminazione. Disabilitare se si vuole il controllo totale sul contenuto delle scene di illuminazione.

![Impostazioni dell'editor del sistema della scena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
