---
title: Tipi di scena del sistema di scena
description: Documentazione sui diversi tipi di scena in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144575"
---
# <a name="scene-types"></a>Tipi di scena

Le scene sono state suddivise in tre tipi e ogni tipo ha una funzione diversa.

![Sistema di scena nella gerarchia](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Scene di contenuto

Queste sono le scene con cui si è usati. Qualsiasi tipo di contenuto può essere archiviato in essi e può essere caricato o scaricato in qualsiasi combinazione.

Le scene di contenuto sono abilitate per impostazione predefinita. Tutte le scene incluse nella matrice del `Content Scenes` profilo possono essere caricate/scaricate dal servizio.

___

## <a name="manager-scenes"></a>Scene di gestione

Una singola scena con un'istanza MixedRealityToolkit richiesta. Questa scena verrà caricata per prima all'avvio e rimarrà caricata per tutta la durata dell'app. La scena di gestione può ospitare anche altri oggetti che non devono mai essere distrutti. Questa è l'alternativa preferita a DontDestroyOnLoad.

Per abilitare questa funzionalità, controllare `Use Manager Scene` il profilo e trascinare un oggetto scena nel `Manager Scene` campo .

___

## <a name="lighting-scenes"></a>Scene di illuminazione

Set di scene che archiviano informazioni sull'illuminazione e oggetti di illuminazione. Solo uno può essere caricato alla volta e le relative impostazioni possono essere combinate durante i carichi per transizioni di illuminazione fluide.

Le impostazioni di illuminazione di Unity, ad esempio luce ambientale, skybox e così via, possono essere complesse da gestire quando si usa il caricamento additivo perché sono collegate a singole scene e il comportamento di override non è semplice. In pratica questo può causare confusione quando gli asset vengono creati in condizioni di illuminazione che non si ottengono in fase di esecuzione.

![Impostazioni di illuminazione del sistema della scena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Il sistema scene usa scene di illuminazione per garantire che queste impostazioni rimangano coerenti indipendentemente dalle scene caricate o attive, sia in modalità di modifica che in modalità di riproduzione.

Per abilitare questa funzionalità, `Use Lighting Scene` archiviare il profilo e popolare la `Lighting Scenes` matrice.

### <a name="cached-lighting-settings"></a>Impostazioni di illuminazione memorizzate nella cache

Il profilo archivia copie memorizzate nella cache delle impostazioni di illuminazione mantenute nelle scene di illuminazione. Se queste impostazioni cambiano nelle scene di illuminazione, sarà necessario aggiornare la cache per assicurarsi che l'illuminazione venga visualizzata come previsto in modalità di riproduzione. Il profilo visualizza un avviso quando sospetta che le impostazioni memorizzate nella cache non siano aggiornate. Facendo `Update Cached Lighting Settings` clic su vengono caricate tutte le scene di illuminazione, ne vengono estratte le impostazioni e quindi archiviate nel profilo.

![Impostazioni di illuminazione memorizzate nella cache del sistema della scena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamento dell'editor

Uno dei vantaggi dell'uso delle scene di illuminazione è sapere che il contenuto viene acceso correttamente durante la modifica. A questo scopo, il servizio scene manterà sempre una scena di illuminazione caricata e copierà le impostazioni di illuminazione della scena nella scena attiva corrente.\*

È possibile modificare la scena di illuminazione caricata aprendo il controllo del servizio del [sistema della scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) In modalità di modifica è possibile eseguire immediatamente la transizione tra scene di illuminazione. In modalità di riproduzione è possibile visualizzare in anteprima le transizioni.

![Controllo sistema scena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Nota: in genere la scena attiva determina le impostazioni di illuminazione nell'editor. Tuttavia, si sceglie di non usare questa funzionalità per applicare le impostazioni di illuminazione, perché la scena attiva è anche la posizione degli oggetti appena creati per impostazione predefinita e le scene di illuminazione possono contenere solo componenti di illuminazione. Le impostazioni della scena di illuminazione corrente vengono invece copiate automaticamente nelle impostazioni della scena attiva. Tenere presente che ciò comporta la sovrascritta delle impostazioni di illuminazione della scena di contenuto.*
