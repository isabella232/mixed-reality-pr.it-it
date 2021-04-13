---
title: Esercitazioni introduttive - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questa esercitazione illustra come configurare i profili di Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, consapevolezza spaziale
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300456"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configurazione dei profili di Mixed Reality Toolkit

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.

I <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">profili di MRTK</a> sono profili annidati in una struttura ad albero che costituiscono le informazioni di configurazione per la modalità di inizializzazione dei sistemi e delle funzionalità di MRTK. Il profilo di primo livello, quello di configurazione, contiene profili annidati per ognuno dei sistemi core principali. Ogni profilo annidato è progettato per la configurazione del comportamento del sistema corrispondente.

Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale. Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.

Come rilevato quando è stato distribuito il progetto in HoloLens 2 nell'[esercitazione precedente](mr-learning-base-02.md#congratulations), la mesh <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> è una raccolta di mesh che rappresentano la geometria dell'ambiente. Si tratta di una visualizzazione utile nella fase iniziale, ma che in genere è disabilitata per evitare distrazioni a livello visivo e l'impatto aggiuntivo che produrrebbe sulle prestazioni.

## <a name="objectives"></a>Obiettivi

* Imparare a personalizzare e configurare i profili di MRTK
* Nascondere il mesh di consapevolezza spaziale

## <a name="changing-the-spatial-awareness-display-option"></a>Modifica delle opzioni di visualizzazione di consapevolezza spaziale

Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:

1. Clonare il profilo di configurazione predefinito
2. Abilitare il sistema di consapevolezza spaziale
3. Clonare il profilo predefinito del sistema di consapevolezza spaziale
4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale
5. Modificare la visibilità della mesh di consapevolezza spaziale

> [!NOTE]
> per impostazione predefinita, i profili di MRTK non sono modificabili. Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati. Sono disponibili diversi livelli annidati di profili. È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Posizionamento degli oggetti nella scena](mr-learning-base-04.md)