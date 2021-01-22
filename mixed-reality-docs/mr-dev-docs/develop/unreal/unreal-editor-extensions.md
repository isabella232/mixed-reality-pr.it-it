---
title: Estensioni dell'editor in Unreal
description: Informazioni su come estendere l'editor Unreal Engine con script personalizzati, azioni con script e widget di utilità.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, estensioni dell'editor, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584922"
---
# <a name="editor-extensions-in-unreal"></a>Estensioni dell'editor in Unreal

Unreal fornisce un set completo di funzionalità che consentono di personalizzare il motore in base alle esigenze. Le funzionalità variano da semplice ma limitato a molto potente ma complesso. La procedura seguente è elencata in ordine di complessità crescente. In generale, è consigliabile raggiungere soluzioni più semplici al problema e esaurirne le opzioni, prima di procedere con un'opzione più complessa. Ad esempio, è stato rilevato che lo script di costruzione di base può essere utilizzato in sostituzione dei plug-in nella maggior parte dei casi. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Script di costruzione

È possibile usare gli script di costruzione per eseguire azioni di inizializzazione, che vengono eseguite quando si crea un'istanza del progetto.

* [Script per costruzioni utente](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Esempio di progetto](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Esercitazione video](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Azioni con script

Le azioni con script sono progetti di utilità dell'editor. È possibile avviarli nell'editor di Unreal:
* Fare clic con il pulsante destro del mouse su **Asset** nel browser contenuto
* In alternativa, fare clic con il pulsante destro del mouse su **Actors** nel viewport livello o nel mondo

Le azioni con script sono particolarmente adatte per i momenti in cui è necessaria la logica del progetto per la consapevolezza contestuale di set di asset o attori. In genere, un'azione con script ottiene un elenco di asset o attori selezionati durante l'esecuzione dell'azione, quindi modifica tali oggetti o li considera nel grafico.

* [Azioni con script](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Esecuzione di azioni con script all'avvio del progetto](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Widget dell'utilità Editor

È possibile utilizzare i [widget dell'utilità di editor](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) ogni volta che si desidera aggiungere nuovi elementi dell'interfaccia utente per modificare l'interfaccia utente dell'editor non reale. I widget dell'utilità di editor sono basati su UMG (Unreal Motion Graphics), quindi è possibile configurare i widget in un progetto come per qualsiasi altro progetto di widget di UMG.

Questi widget sono specifici dell'interfaccia utente dell'editor ed è possibile usarli per creare schede dell'editor personalizzate. È quindi possibile selezionare queste schede personalizzate dal menu Windows, come si selezionano le schede dell'editor esistente.

## <a name="plugins"></a>Plug-in

Unreal consente di sviluppare e gestire i [plug](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) -in personalizzati da usare con gli strumenti e il runtime UE4. È possibile abilitare o disabilitare i plug-in in qualsiasi momento nell'editor non reale. I plug-in possono aggiungere funzionalità di gioco in fase di esecuzione, modificare le funzionalità predefinite del motore, creare nuovi tipi di file ed estendere le funzionalità dell'editor.

<!-- ## Engine modifications -->

