---
title: FingertipVisualization
description: Panoramica sulla visualizzazione a portata di mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, a portata di mano
ms.openlocfilehash: 205c16f8868e659b87afd131047f7c91e765da37
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783067"
---
# <a name="fingertip-visualization"></a>Visualizzazione a mano

![Visualizzazione a mano principale](../images/fingertip/MRTK_FingertipVisualization_Main.png)

La convenienza per le dita consente all'utente di riconoscere la distanza dall'oggetto di destinazione. L'oggetto visivo della forma circolare regola le dimensioni in base alla distanza tra la punta e l'oggetto. La visualizzazione a forma di dito viene controllata principalmente da `FingerCursor` (assets/MRTK/SDK/features/UX/precasers/Cursors/FingerCursor. precasel) (e script) che viene generato come prefabbricato del cursore di *PokePointer*. Gli altri componenti della visualizzazione includono lo script *ProximityLight* e *MixedRealityStandard* shader.

## <a name="how-to-use-the-fingertip-visualization"></a>Come usare la visualizzazione a portata di mano

Per impostazione predefinita, la visualizzazione a dito funzionerà in qualsiasi scena Unity configurata per generare un FingerCursor. La generazione di FingerCursor si verifica nel *DefaultMixedRealityToolkitConfigurationProfile* in:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

A un livello elevato, la visualizzazione a portata di mano funziona usando una luce di prossimità per proiettare una sfumatura colorata in tutte le aree circostanti che accettano luci di prossimità. Il cursore del dito cerca quindi eventuali superfici interattive interattive, che sono determinate dall'elemento padre `IMixedRealityNearPointer(s)` , per allineare il dito anello con una superficie quando il dito si sposta verso una superficie. Quando un dito si avvicina a una superficie, l'anello viene anche animato dinamicamente usando le proprietà degli angoli arrotondati dello shader MixedRealityStandard.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di visualizzazione a forma di dito in quasi tutte le scene che funzionano con le mani articolate, ma è importante nella [scena HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Stati di visualizzazione a portata di mano](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Proprietà di Inspector

**FingerCursor** Molte delle proprietà del cursore dito vengono ereditate dalla classe del cursore di base. Le proprietà importanti includono i margini e le larghezze della superficie di distanza/prossimità che guidano l'animazione dell'anello dito nello shader MixedRealityStandard. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** Le impostazioni della luce di prossimità controllano il modo in cui la luce viene visualizzata quando si è vicini e lontani da una superficie. I colori centrale, centrale e esterno controllano l'aspetto sfumato della luce e possono essere personalizzati per la tavolozza dei colori dell'applicazione. Si noti che i colori sono HDR (intervallo dinamico elevato) per consentire agli utenti di schiarire la luce vicina ai valori sopra uno. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

**Shader MixedRealityStandard** Lo shader MixedRealityStandard viene usato per molti effetti in MRTK. Le due impostazioni importanti per la visualizzazione a portata di mano sono "near fade" e "prossimità Light". Near Fade consente agli oggetti di dissolversi in entrata o in uscita come fotocamera o luce vicina. Assicurarsi di selezionare "Light" (chiaro) per consentire le luci di prossimità per guidare la dissolvenza (anziché la fotocamera). È possibile invertire i valori di "Fade Begin" e "Fade Complete" per invertire una dissolvenza. Verificare "prossimità luce" per qualsiasi superficie a cui si desidera rendere più chiara la luce di prossimità. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
