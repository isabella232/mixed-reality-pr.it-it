---
title: Procedure consigliate generali
description: È possibile rimanere sempre aggiornati su tutte le procedure consigliate per lo sviluppo di applicazioni con realtà mista in Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, estensioni dell'editor, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584903"
---
# <a name="general-best-practices"></a>Procedure consigliate generali

Di seguito sono riportate alcune procedure consigliate generali che tutti gli sviluppatori seguono quando si crea un progetto di motore Unreal per la realtà mista.

## <a name="constructors"></a>Costruttori

Se è necessario l'equivalente di un "costruttore" nei progetti, usare [lo script di costruzione](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)"Unreal". Il vantaggio principale dell'utilizzo degli eventi "BeginPlay" è lo script del costruttore eseguito anche nell'"Editor". Nella maggior parte dei casi i valori possono essere memorizzati nella cache direttamente all'inizio o anche in fase di compilazione.

> [!NOTE]
> Per ulteriori informazioni di supporto per gli script di costruzione, vedere [Cenni preliminari sulle estensioni dell'editor](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>pulsanti e trame 3D

Quando si crea o si pianifica l'uso di pulsanti 3D in applicazioni di realtà miste, è naturale considerare le prestazioni. Tuttavia, non è necessario che tutte le mesh siano percepite come 3D. È possibile scegliere di usare Paper2D con trame appositamente create per ottenere l'aspetto 3D. Questa funzione è molto valida per i pulsanti che "sembrano" 3D, ma sono solo immagini con acquisti in un quad. Una versione sofisticata è detta [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).

## <a name="variants"></a>Varianti

Usare [varianti irreali](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) negli scenari in cui si sta creando una scena con più configurazioni di oggetti in fase di esecuzione. Le variazioni possono includere la modifica di materiali o mesh. 

## <a name="animation"></a>Animazione

Usare il [componente spline](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (non il componente "mesh" della spline) e i [nodi della sequenza temporale](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) se si creano molte "animazioni interagibili". 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Comunicazioni

Usare un [progetto di livello](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) se si verificano problemi nella ricerca dinamica degli oggetti o nell'uso di una larghezza di banda eccessiva per comunicare tra più attori e progetti. Si ricordi che Unreal Engine 4 non è come Unity, ma non tutti gli elementi devono trovarsi all'interno di un componente. I progetti di livello sono un metodo perfettamente valido e consigliato per semplificare la comunicazione tra più attori. I riferimenti agli oggetti possono anche essere "memorizzati nella cache" all'avvio nel OnBeginPlay del progetto di livello.

## <a name="global-state"></a>Stato globale

Spesso è necessario archiviare lo stato specifico del livello, ad esempio Punteggio, dati di livello, informazioni specifiche del giocatore o qualsiasi altro elemento che non appartenga a un oggetto specifico. Non trascurare [gamemode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html). La maggior parte degli utenti dimentica di esistere, ma è possibile creare GameMode per ogni livello e contenere dati specifici per ogni livello.

## <a name="optimizing-blueprints"></a>Ottimizzazione di progetti

Se la ricerca dei progetti è troppo lenta, è necessario innativizere i progetti prima di ricorrere alla riscrittura del codice in c++. Provare a usare la [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) automatica prima di creare una soluzione personalizzata.

![Impostazione dei progetti con il metodo nativization del progetto con evidenziato inclusivo](images/unreal-general-practices-img-01.jpg)
