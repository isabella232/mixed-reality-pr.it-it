---
title: SceneSystemSceneTypes
description: Documentazione su diversi tipi di scena in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 627510d1961b48a64d3b5914f06543cf9037af32
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693478"
---
# <a name="scene-types"></a>Tipi di scena

Le scene sono state divise in tre tipi e ogni tipo ha una funzione diversa.

![Sistema di scena nella gerarchia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Scene di contenuto

Queste sono le scene che vengono usate per gestire. Tutti i tipi di contenuto possono essere archiviati in essi e possono essere caricati o scaricati in qualsiasi combinazione.

Le scene di contenuto sono abilitate per impostazione predefinita. Tutte le scene incluse nell'array del profilo `Content Scenes` possono essere caricate o scaricate dal servizio.

___

## <a name="manager-scenes"></a>Scene di gestione

Una singola scena con un'istanza di MixedRealityToolkit obbligatoria. Questa scena verrà caricata prima all'avvio e rimarrà caricata per la durata dell'app. La scena del responsabile può inoltre ospitare altri oggetti che non devono mai essere eliminati definitivamente. Si tratta dell'alternativa preferita a DontDestroyOnLoad.

Per abilitare questa funzionalità, archiviare il `Use Manager Scene` profilo e trascinare un oggetto scena nel `Manager Scene` campo.

___

## <a name="lighting-scenes"></a>Scene di illuminazione

Set di scene che archivia le informazioni sull'illuminazione e gli oggetti di illuminazione. È possibile caricare solo un oggetto alla volta e le relative impostazioni possono essere combinate durante i caricamenti per le transizioni con illuminazione uniforme.

Le impostazioni di illuminazione di Unity, luce ambientale, Skybox e così via, possono essere difficili da gestire quando si usa il caricamento di additivi perché sono legate a singole scene e il comportamento di sostituzione non è semplice. In pratica questo può causare confusione quando le risorse vengono create in condizioni di illuminazione che non vengono ottenute in fase di esecuzione.

![Impostazioni di illuminazione del sistema di scena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Il sistema di scena USA scene di illuminazione per assicurarsi che queste impostazioni rimangano coerenti indipendentemente dalle scene caricate o attive, sia in modalità di modifica che in modalità di riproduzione.

Per abilitare questa funzionalità, archiviare il `Use Lighting Scene` profilo e popolare la `Lighting Scenes` matrice.

### <a name="cached-lighting-settings"></a>Impostazioni di illuminazione memorizzate nella cache

Il profilo archivia le copie memorizzate nella cache delle impostazioni di illuminazione mantenute nelle scene di illuminazione. Se queste impostazioni cambiano nelle scene di illuminazione, sarà necessario aggiornare la cache per assicurarsi che l'illuminazione venga visualizzata come previsto in modalità di riproduzione. Nel profilo verrà visualizzato un avviso quando si sospetta che le impostazioni memorizzate nella cache non siano aggiornate. Se si fa clic su `Update Cached Lighting Settings` , si caricherà ogni scena di illuminazione, si estraggono le impostazioni e quindi le si archivia nel profilo.

![Impostazioni di illuminazione del sistema di scena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamento dell'editor

Un vantaggio dell'uso di scene di illuminazione è la consapevolezza che i contenuti sono illuminati correttamente durante la modifica. A questo scopo, il servizio di scena manterrà una scena di illuminazione sempre caricata e copierà le impostazioni di illuminazione della scena nella scena attiva corrente.\*

È possibile modificare la scena di illuminazione che viene caricata aprendo il [controllo del servizio](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) del sistema di scena. In modalità di modifica è possibile eseguire istantaneamente la transizione tra le scene di illuminazione. In modalità di riproduzione è possibile visualizzare in anteprima le transizioni.

![Controllo di sistema della scena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Nota: in genere la scena attiva determina le impostazioni di illuminazione nell'editor. Tuttavia, si sceglie di non usare questa funzionalità per applicare le impostazioni di illuminazione, perché la scena attiva è anche la posizione in cui vengono inseriti gli oggetti appena creati per impostazione predefinita e gli scenari di illuminazione possono contenere solo componenti di illuminazione. Al contrario, le impostazioni correnti della scena di illuminazione vengono automaticamente copiate nelle impostazioni della scena attiva. Tenere presente che questa operazione comporterà la sovrascrittura delle impostazioni di illuminazione della scena del contenuto.*
