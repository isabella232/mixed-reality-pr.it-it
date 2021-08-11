---
title: Estensioni dell'editor in Unreal
description: Informazioni su come estendere l'editor del motore Unreal con script personalizzati, azioni con script e widget di utilità.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, estensioni dell'editor, editor Unreal, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 91d9a84e4e19cb7f0f2bf54060b45da1767b8d50cdfeb5655f5e58a29d45a702
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226623"
---
# <a name="editor-extensions-in-unreal"></a>Estensioni dell'editor in Unreal

Unreal offre un set completo di funzionalità che consentono di personalizzare il motore in base alle esigenze. Le funzionalità vanno da semplici ma limitate, a molto potenti ma complesse. I passaggi seguenti sono elencati in ordine di complessità crescente. In generale, prima di passare a un'opzione più complessa, è consigliabile cercare soluzioni più semplici al problema e esaurirne le opzioni. Ad esempio, si è scoperto che lo script di costruzione di base può essere usato al posto dei plug-in nella maggior parte dei casi. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Script di costruzione

È possibile usare script di costruzione per eseguire azioni di inizializzazione, che vengono eseguite quando viene creata l'istanza del progetto.

* [Script di Costruzione utente](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Esempio di progetto](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Esercitazione video](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Azioni con script

Le azioni con script sono progetti di utilità editor. È possibile avviarli nell'editor unreal:
* Fare clic con il **pulsante destro del mouse** su Asset nel visualizzatore contenuto
* Oppure facendo clic con il pulsante destro del mouse su **Actors** (Attori) nel riquadro di visualizzazione level (Livello) o in World Outliner (Struttura globale)

Le azioni con script sono particolarmente adatte per i casi in cui è necessario che la logica del progetto abbia consapevolezza contestuale sui set di asset o attori. In genere, un'azione con script ottiene un elenco di asset o attori selezionati durante l'esecuzione dell'azione, quindi li modifica o li considera nel grafico.

* [Azioni con script](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Esecuzione di azioni con script all'avvio del progetto](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Widget di utilità dell'editor

È possibile usare [i widget dell'utilità Editor](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) ogni volta che si vogliono aggiungere nuovi elementi dell'interfaccia utente per modificare il Interfaccia utente dell'editor di Unreal. I widget di utilità dell'editor sono basati su Unreal Motion Graphics (UMG), quindi è possibile configurare i widget in un progetto come per qualsiasi altro progetto di widget UMG.

Questi widget sono specifici per l'interfaccia utente dell'editor ed è possibile usarli per creare schede personalizzate dell'editor. È quindi possibile selezionare queste schede personalizzate dal menu Windows, come si selezionano le schede dell'editor esistenti.

## <a name="plugins"></a>Plug-in

Unreal consente di sviluppare e gestire plug-in [personalizzati](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) da usare con gli strumenti e il runtime UE4. È possibile abilitare o disabilitare i plug-in in qualsiasi momento nell'editor di Unreal. I plug-in possono aggiungere funzionalità di gioco di runtime, modificare le funzionalità del motore incorporate, creare nuovi tipi di file ed estendere le funzionalità dell'editor.

<!-- ## Engine modifications -->

