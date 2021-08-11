---
title: Visualizzazione punta delle dita
description: Panoramica sulla visualizzazione fingertip in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, punta delle dita
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193308"
---
# <a name="fingertip-visualization"></a>Visualizzazione punta delle dita

![Visualizzazione punta delle dita Principale](../images/fingertip/MRTK_FingertipVisualization_Main.png)

La punta delle dita consente all'utente di riconoscere la distanza dall'oggetto di destinazione. L'oggetto visivo della forma ad anello regola le dimensioni in base alla distanza dalla punta delle dita all'oggetto. La visualizzazione della punta del dito è controllata principalmente da `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (e dallo script ) che viene generato come prefab del cursore *di PokePointer*. Altri componenti della visualizzazione includono lo script *ProximityLight* e lo shader *MixedRealityStandard.*

## <a name="how-to-use-the-fingertip-visualization"></a>Come usare la visualizzazione della punta delle dita

Per impostazione predefinita, la visualizzazione della punta delle dita funzionerà in qualsiasi scena di Unity configurata per generare un FingerCursor. La generazione di FingerCursor si verifica in *DefaultMixedRealityToolkitConfigurationProfile* in:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

A livello elevato, la visualizzazione a punta delle dita funziona usando una luce di prossimità per proiettare una sfumatura colorata su qualsiasi superficie vicina che accetta luci di prossimità. Il cursore del dito cerca quindi eventuali superfici interagiscibili nelle vicinanze, determinate dall'elemento padre, per allineare l'anello del dito a una superficie mentre il dito si sposta `IMixedRealityNearPointer(s)` verso una superficie. Quando un dito si avvicina a una superficie, l'anello del dito viene animato dinamicamente usando le proprietà degli angoli arrotondati dello shader MixedRealityStandard.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di visualizzazione della punta delle dita in quasi tutte le scene che funzionano con le mani articolate, ma è importante nella scena [HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Stati di visualizzazione della punta delle dita](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Proprietà del controllo

**FingerCursor** Molte delle proprietà del cursore del dito vengono ereditate dalla classe di cursore di base. Le proprietà importanti includono i margini e la larghezza della superficie vicini che guidano l'animazione dell'anello delle dita nello shader MixedRealityStandard. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** Le impostazioni della luce di prossimità controllano l'aspetto della luce quando è vicina e lontana da una superficie. I colori centrale, centrale ed esterno controllano l'aspetto sfumato della luce e possono essere personalizzati per la tavolozza dei colori dell'applicazione. Si noti che i colori sono HDR (High Dynamic Range) per consentire agli utenti di illuminare la luce di prossimità ai valori superiori a uno. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

**Shader MixedRealityStandard** Lo shader MixedRealityStandard viene usato per molti effetti in MRTK. Le due impostazioni importanti per la visualizzazione della punta delle dita sono "Near Fade" e "Proximity Light". Near Fade consente agli oggetti di dissolvenza in entrata/in uscita quando una fotocamera o una luce li avvicina. Assicurarsi di selezionare "Luce" per consentire alle luci di prossimità di guidare la dissolvenza (anziché la fotocamera). È possibile invertire i valori di "Fade Begin" e "Fade Complete" per invertire una dissolvenza. Selezionare "Luce di prossimità" per qualsiasi superficie in cui si vuole che la luce di prossimità si accarezza. Per altre proprietà, passare il mouse sulle descrizioni comandi del controllo.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
