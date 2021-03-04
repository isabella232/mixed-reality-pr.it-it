---
title: DependencyWindow
description: Documentazione sull'utilizzo della finestra di dipendenza in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 59a06f5bf639be31f78302d432325ead23939600
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782223"
---
# <a name="dependency-window"></a>Finestra dipendenze

In Unity, spesso è difficile brillare quali asset vengono usati e quali sono i riferimenti. L'opzione "trova riferimenti in scena" è molto interessante quando si è interessati solo alla scena corrente, ma all'intero progetto Unity? Questo è il punto in cui la **finestra di dipendenza** (assets/MRTK/Tools/DependencyWindow) può essere utile.

Nella finestra dipendenza viene visualizzato il modo in cui gli asset fanno riferimento e dipendono tra loro. Le dipendenze vengono calcolate analizzando i GUID all'interno dei file YAML del progetto. Nota: le dipendenze di script per script non vengono considerate.

## <a name="usage"></a>Utilizzo

Per aprire la finestra, selezionare *mixed reality Toolkit->Utilities->finestra delle dipendenze* che apre la finestra e inizia automaticamente a compilare il grafico delle dipendenze del progetto. Una volta compilato il grafico delle dipendenze, è possibile selezionare Asset nella scheda progetto per esaminarne le dipendenze.

![Finestra dipendenze](../images/dependency-window/MRTK_Dependency_Window.png)

La finestra Visualizza un elenco di asset da cui dipende l'asset attualmente selezionato e un elenco gerarchico di asset che dipendono da esso. Se non dipende dall'asset attualmente selezionato, è possibile eliminarlo dal progetto (si noti che alcune risorse vengono caricate a livello di codice tramite API come shader. Find () e che potrebbero non essere rilevate dallo strumento di rilevamento delle dipendenze.

La finestra può anche visualizzare solo un elenco di tutti gli asset a cui non viene fatto riferimento da altri asset e che potrebbero essere presi in considerazione per l'eliminazione:

![Finestra di dipendenza che Mostra risorse senza riferimenti](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Se le risorse vengono modificate, aggiunte o rimosse mentre è in uso la finestra di dipendenza, è consigliabile aggiornare il grafico delle dipendenze per i risultati più aggiornati.
