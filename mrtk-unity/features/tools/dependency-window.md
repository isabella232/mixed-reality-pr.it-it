---
title: Finestra Dipendenze
description: Documentazione sull'utilizzo della finestra delle dipendenze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647028"
---
# <a name="dependency-window"></a>Finestra Dipendenze

In Unity è spesso difficile capire quali asset vengono usati e cosa vi fa riferimento. L'opzione "Trova riferimenti nella scena" è molto utile quando si è interessati solo alla scena corrente, ma per quanto riguarda l'intero progetto Unity? Qui può essere **utile la finestra Delle** dipendenze (Assets/MRTK/Tools/DependencyWindow).

Nella finestra Dipendenza viene visualizzato il modo in cui gli asset fanno riferimento e dipendono l'uno dall'altro. Le dipendenze vengono calcolate analizzando i GUID all'interno dei file YAML del progetto (si noti che le dipendenze da script a script non vengono considerate).

## <a name="usage"></a>Utilizzo

Per aprire la finestra, selezionare Mixed Reality Toolkit Utilities Dependency Window (Finestra dipendenza utilità **Mixed Reality** Toolkit) che aprirà la finestra e inizierà automaticamente a compilare il grafico delle  >    >    >   dipendenze del progetto. Dopo aver compilato il grafico delle dipendenze, è possibile selezionare gli asset nella scheda del progetto per esaminarne le dipendenze.

![Finestra Dipendenze](../images/dependency-window/MRTK_Dependency_Window.png)

Nella finestra viene visualizzato un elenco di asset da cui dipende l'asset attualmente selezionato e un elenco gerarchico di asset che dipendono da esso. Se non dipende dall'asset attualmente selezionato, è possibile eliminarlo dal progetto (si noti che alcuni asset vengono caricati a livello di codice tramite API come Shader.Find() e potrebbero non essere intercettate dallo tracker delle dipendenze).

La finestra può anche visualizzare solo un elenco di tutti gli asset a cui non fanno riferimento altri asset e che possono essere considerati per l'eliminazione:

![Finestra delle dipendenze con asset senza riferimenti](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Se gli asset vengono modificati, aggiunti o rimossi mentre la finestra delle dipendenze è in uso, è consigliabile aggiornare il grafico delle dipendenze per ottenere i risultati più "aggiornati".
