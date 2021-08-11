---
title: Procedure consigliate generali
description: Rimanere aggiornati su tutte le procedure consigliate per lo sviluppo di applicazioni di realtà mista nel motore Unreal.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, estensioni dell'editor, editor Unreal, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 822e64d873952bdb4bb1fb91da4c85f956a1eb513c92d4afee7bfebb18a824eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203268"
---
# <a name="general-best-practices"></a>Procedure consigliate generali

Di seguito sono riportate alcune procedure consigliate generali che è consigliabile seguire per tutti gli sviluppatori durante la creazione di un progetto Unreal Engine per la realtà mista.

## <a name="constructors"></a>Costruttori

Se è necessario l'equivalente di un "costruttore" nei progetti, usare lo [script](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)di costruzione di Unreals. Il vantaggio principale rispetto all'uso degli eventi "BeginPlay" è l'esecuzione dello script del costruttore anche nell'"editor". Nella maggior parte dei casi i valori possono essere memorizzati nella cache all'inizio o anche in fase di compilazione.

> [!NOTE]
> Altre informazioni di supporto per gli script di costruzione sono disponibili nella panoramica delle [estensioni dell'editor.](unreal-editor-extensions.md#construction-scripts)

## <a name="3d-buttons-and-textures"></a>Pulsanti e trame 3D

È naturale pensare alle prestazioni durante la creazione o la pianificazione dell'uso di pulsanti 3D nelle applicazioni di realtà mista. Tuttavia, non tutto deve essere creato dalle mesh per essere percepito come 3D. È possibile usare Paper2D con trame appositamente predisposte per ottenere questo aspetto 3D. Questa operazione funziona molto bene per i pulsanti che "sembrano" 3D, ma sono solo immagini incorporate su un quad. Una versione fancy di questi elementi è denominata [sprite.](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)

## <a name="variants"></a>Varianti

Usare [varianti Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) negli scenari in cui si crea una scena con più configurazioni di oggetti in fase di esecuzione. Le variazioni possono includere materiali o mesh mutevoli. 

## <a name="animation"></a>Animazione

Sfruttare i vantaggi del componente [Spline](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (non del componente spline "Mesh") e dei nodi [sequenza](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) temporale se si creano molte "animazioni con interazione". 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Comunicazioni

Usare un [progetto di livello](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) se si verificano problemi durante la ricerca dinamica di oggetti o se si usa una larghezza di banda troppo elevata per comunicare tra più attori e progetti. Tenere presente che Unreal Engine 4 non è come Unity, non tutti gli elementi devono essere all'interno di un componente. I progetti a livello sono un modo perfettamente valido e consigliato per semplificare la comunicazione tra più attori. I riferimenti agli oggetti possono anche essere "memorizzati nella cache" all'avvio in OnBeginPlay del progetto Level.

## <a name="global-state"></a>Stato globale

Spesso è necessario archiviare lo stato specifico del livello, ad esempio punteggio, dati di livello, informazioni specifiche del giocatore o qualsiasi altro elemento che non appartenga a un determinato oggetto. Non tralasciare [GameMode.](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html) La maggior parte delle persone dimentica che esiste, ma gameMode può essere creato per ogni livello e contenere dati specifici per ogni livello.

## <a name="optimizing-blueprints"></a>Ottimizzazione dei progetti

Se i progetti sono troppo lenti, lasciare che Unreal "nativizza" i progetti prima di ricorrere alla riscrittura del codice in c++. Provare a usare la [nativizzazione automatica](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) prima di creare una soluzione personalizzata.

![Impostazione dei progetti con il metodo di nativizzazione del progetto con l'opzione inclusiva evidenziata](images/unreal-general-practices-img-01.jpg)
