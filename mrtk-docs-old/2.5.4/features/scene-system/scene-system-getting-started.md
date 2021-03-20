---
title: SceneSystemGettingStarted
description: Pagina di destinazione per il sistema di scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e43bb401ea3c3175b5cb3805e7edf00d361eb4b6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685124"
---
# <a name="scene-system-overview"></a>Panoramica del sistema di scena

## <a name="when-to-use-the-scene-system"></a>Quando usare il sistema di scena

Se il progetto è costituito da un'unica scena, probabilmente il sistema della scena non è necessario. È particolarmente utile quando si verificano una o più delle condizioni seguenti:

- Il progetto include più scene.
- Si viene usati per il caricamento di una singola scena, ma non è come il modo in cui viene distrutta l'istanza di MixedRealityToolkit.
- Si vuole un modo semplice per caricare additivamente più scene per costruire la propria esperienza.
- Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.
- Si vuole rendere l'illuminazione coerente e prevedibile in tutte le scene.

## <a name="scene-system-resources"></a>Risorse di sistema della scena

Per impostazione predefinita, il sistema di scena usa una coppia di oggetti scene (scena DefaultManagerScene e DefaultLighting). Se una di queste scene non può essere individuata, verrà visualizzato un messaggio nella finestra di controllo profilo del sistema della scena.

![Messaggio risorse predefinite](../images/scene-system/DefaultResourcesMessage.png)

>! Si noti Se il progetto usa la gestione personalizzata e le scene di illuminazione, questo messaggio può essere ignorato.

Le sezioni seguenti descrivono ora per risolvere questo messaggio, in base al metodo usato per importare il Toolkit di realtà mista.

### <a name="unity-package-manager-upm"></a>Gestione pacchetti Unity (UPM)

Nei pacchetti UPM del Toolkit per realtà mista le risorse di sistema della scena sono assemblate come esempio. Dato che i pacchetti UPM non sono modificabili, Unity non è in grado di aprire il file della scena necessario, a meno che non vengano importati in modo esplicito nel progetto.

Per eseguire l'importazione, attenersi alla procedura seguente:

- Selezionare   >  **Gestione pacchetti** Windows
- Selezionare **mixed reality Toolkit Foundation**
- Individuare **le risorse di sistema della scena** nella sezione degli **esempi**

  ![Importa le risorse di sistema della scena](../images/scene-system/UpmImportSceneSystemResources.png)

- Selezionare **Importa**

### <a name="asset-unitypackage-files"></a>File di asset (con estensione file unitypackage Tools)

Se la cartella SceneSystemResources è stata eliminata o è stata deselezionata durante l'importazione, è possibile recuperarla attenendosi alla procedura seguente:

- Seleziona **Asset**  >  **Importa** pacchetto  >  **personalizzato** pacchetto
- Aprire il pacchetto **Microsoft. MixedReality. Toolkit. Foundation**
- Verificare che siano selezionate le opzioni **Services/SceneSystem/SceneSystemResources** e All Child

  ![Reimportare le risorse di sistema della scena](../images/scene-system/ReimportSceneSystemResources.png)

- Selezionare **Importa**

## <a name="how-to-use-the-scene-system"></a>Come usare il sistema di scena

- [Tipi di scena](scene-system-scene-types.md)
- [Caricamento della scena del contenuto](scene-system-content-loading.md)
- [Monitoraggio del caricamento del contenuto](scene-system-load-progress.md)
- [Caricamento della scena di illuminazione](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Impostazioni editor

Per impostazione predefinita, il sistema di scena impone diversi comportamenti nell'editor di Unity. Se uno di questi comportamenti è elevato, è possibile disabilitarli nella sezione **Impostazioni editor** del profilo di sistema della scena.

- `Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto. Disabilitare questa impostazione se si desidera il controllo totale sulle impostazioni di compilazione.

- `Editor Enforce Scene Order:` Se true, il servizio assicurerà che la scena del Manager venga visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto. Disabilitare questa proprietà se si desidera il controllo totale sulla gerarchia della scena.

- `Editor Manage Loaded Scenes:` Se true, il servizio assicurerà che il responsabile, il contenuto e le scene di illuminazione siano sempre caricati. Disabilitare se si desidera il controllo totale sulle scene caricate nell'editor.

- `Editor Enforce Lighting Scene Types:` Se true, il servizio garantirà che solo i componenti correlati all'illuminazione definiti in `PermittedLightingSceneComponentTypes` siano consentiti nelle scene di illuminazione. Disabilitare se si desidera il controllo totale sul contenuto delle scene di illuminazione.

![Impostazioni dell'editor di sistema della scena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
