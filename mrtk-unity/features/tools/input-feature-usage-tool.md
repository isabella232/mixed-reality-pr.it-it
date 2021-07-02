---
title: Strumento di utilizzo delle funzionalità di input
description: Strumento InputFeatureUsage della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176124"
---
# <a name="input-feature-usage-tool"></a>Strumento di utilizzo delle funzionalità di input

Lo strumento InputFeatureUsage è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'inputFeatureUsages unity disponibile per un'origine di input rilevata (ad esempio, controller del movimento o mano articolata).

> [!NOTE]
> Questa scena funziona solo in Unity 2019.3 o versione successiva.

Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware. Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.

![Strumento InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso dello strumento InputFeatureUsage

Per iniziare a usare lo strumento InputFeatureUsage, passare a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e aprire la **scena InputFeatureUsageTool.** Dopo che la scena è stata caricata, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connessione il controller
- Premere ogni pulsante e spostare ogni asse
- Si notino gli utilizzi delle funzionalità nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento InputFeatureUsage non usa Microsoft Mixed Reality Toolkit componenti. Comunica direttamente con Unity per determinare e visualizzare gli utilizzi delle funzionalità.

### <a name="panels"></a>Pannelli

I pannelli visualizzano lo stato corrente di tutte le proprietà InputFeatureUsages segnalate in tutte le origini di input Unity rilevate.

Il pannello più piccolo nella parte superiore elenca i nomi di tutte le origini rilevate.

## <a name="see-also"></a>Vedere anche

- [Creazione di un provider di dati del sistema di input](../input/create-data-provider.md)
- [Strumento di mapping del controller](controller-mapping-tool.md)
