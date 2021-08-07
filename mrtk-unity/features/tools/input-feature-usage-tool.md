---
title: Strumento di utilizzo delle funzionalità di input
description: Strumento InputFeatureUsage della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 9d5e80ee5f31086b12ec2b82ab2368361fb738e03ea7fe5cf02ba0b4bd22c0b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189436"
---
# <a name="input-feature-usage-tool"></a>Strumento di utilizzo delle funzionalità di input

Lo strumento InputFeatureUsage è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'input UnityFeatureUsages disponibile per un'origine di input rilevata (ad esempio controller di movimento o mano articolata).

> [!NOTE]
> Questa scena funziona solo in Unity 2019.3 o versione successiva.

Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware. Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.

![Strumento InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso dello strumento InputFeatureUsage

Per iniziare a usare lo strumento InputFeatureUsage, passare a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e aprire la **scena InputFeatureUsageTool.** Dopo aver caricato la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.

Per esaminare i mapping di Unity per un controller:

- Connessione controller
- Premere ogni pulsante e spostare ogni asse
- Si notino gli utilizzi delle funzionalità nella visualizzazione
- Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller

> [!NOTE]
> Lo strumento InputFeatureUsage non usa microsoft Mixed Reality Toolkit componenti. Comunica direttamente con Unity per determinare e visualizzare gli utilizzi delle funzionalità.

### <a name="panels"></a>Pannelli

I pannelli visualizzano lo stato corrente di tutte le inputFeatureUsages segnalate in tutte le origini di input unity rilevate.

Il pannello più piccolo nella parte superiore elenca i nomi di tutte le origini rilevate.

## <a name="see-also"></a>Vedi anche

- [Creazione di un provider di dati del sistema di input](../input/create-data-provider.md)
- [Strumento di mapping dei controller](controller-mapping-tool.md)
