---
title: SceneSystemSceneTypes
description: Documentazione sui diversi tipi di scena in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 07ecb9fd4866fa5201a25ebe5c13ec39f8e46c737f808dd4050251f15e66a98d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210763"
---
# <a name="scene-types"></a>Tipi di scena

Le scene sono state suddivise in tre tipi e ogni tipo ha una funzione diversa.

![Sistema della scena nella gerarchia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Scene di contenuto

Queste sono le scene con cui si ha a che fare. Qualsiasi tipo di contenuto può essere archiviato in essi e può essere caricato o scaricato in qualsiasi combinazione.

Le scene di contenuto sono abilitate per impostazione predefinita. Tutte le scene incluse nella matrice del `Content Scenes` profilo possono essere caricate/scaricate dal servizio.

___

## <a name="manager-scenes"></a>Scene di gestione

Una singola scena con un'istanza obbligatoria di MixedRealityToolkit. Questa scena verrà caricata per prima all'avvio e rimarrà caricata per tutta la durata dell'app. La scena di gestione può ospitare anche altri oggetti che non devono mai essere distrutti. Questa è l'alternativa preferita a DontDestroyOnLoad.

Per abilitare questa funzionalità, `Use Manager Scene` controllare il profilo e trascinare un oggetto scena nel `Manager Scene` campo.

___

## <a name="lighting-scenes"></a>Scene di illuminazione

Set di scene in cui vengono archiviate le informazioni sull'illuminazione e gli oggetti di illuminazione. È possibile caricarne solo uno alla volta e le relative impostazioni possono essere combinate durante i carichi per transizioni di illuminazione uniformi.

Le impostazioni di illuminazione di Unity, ad esempio luce ambientale, skybox e così via, possono essere complesse da gestire quando si usa il caricamento additivo perché sono collegate a singole scene e il comportamento di override non è semplice. In pratica questo può causare confusione quando gli asset vengono creati in condizioni di illuminazione che non si ottengono in fase di esecuzione.

![Impostazioni di illuminazione del sistema della scena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Il sistema scene usa scene di illuminazione per garantire che queste impostazioni rimangano coerenti indipendentemente dalle scene caricate o attive, sia in modalità di modifica che in modalità di riproduzione.

Per abilitare questa funzionalità, `Use Lighting Scene` archiviare il profilo e popolare la `Lighting Scenes` matrice.

### <a name="cached-lighting-settings"></a>Impostazioni di illuminazione memorizzate nella cache

Il profilo archivia copie memorizzate nella cache delle impostazioni di illuminazione mantenute nelle scene di illuminazione. Se queste impostazioni cambiano nelle scene di illuminazione, sarà necessario aggiornare la cache per assicurarsi che l'illuminazione venga visualizzata come previsto in modalità di riproduzione. Il profilo visualizza un avviso quando sospetta che le impostazioni memorizzate nella cache non siano aggiornate. Facendo `Update Cached Lighting Settings` clic su vengono caricate tutte le scene di illuminazione, ne vengono estratte le impostazioni e quindi archiviate nel profilo.

![Impostazioni di illuminazione del sistema della scena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamento dell'editor

Uno dei vantaggi dell'uso delle scene di illuminazione è sapere che il contenuto viene acceso correttamente durante la modifica. A tale scopo, il servizio scene manterà sempre una scena di illuminazione caricata e copierà le impostazioni di illuminazione della scena nella scena attiva corrente.\*

È possibile modificare la scena di illuminazione caricata aprendo il controllo del servizio del sistema [della scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) In modalità di modifica è possibile passare immediatamente da una scena di illuminazione all'altro. In modalità di riproduzione è possibile visualizzare in anteprima le transizioni.

![Controllo sistema scena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Nota: in genere la scena attiva determina le impostazioni di illuminazione nell'editor. Tuttavia, si sceglie di non usare questa funzionalità per applicare le impostazioni di illuminazione, perché la scena attiva è anche la posizione predefinita degli oggetti appena creati e le scene di illuminazione possono contenere solo componenti di illuminazione. Al contrario, le impostazioni della scena di illuminazione corrente vengono copiate automaticamente nelle impostazioni della scena attiva. Tenere presente che in questo modo le impostazioni di illuminazione della scena di contenuto verranno sovrascritte.*
