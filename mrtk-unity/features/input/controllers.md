---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850337"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed distrutti automaticamente dai [**provider di input**](input-providers.md). Ogni tipo di controller ha un numero di *input* fisici definiti da un tipo di asse *,* indicando il tipo di dati del valore di input (Digitale, Asse singolo, Asse doppio, Sei Dof, ...) e un tipo di *input* (Pressione pulsante, Trigger, Levetta thumb, Puntatore spaziale, ...) che descrive l'origine dell'input. Gli input fisici vengono mappati alle azioni di *input* tramite nel profilo di mapping dell'input del **controller,** nel profilo del sistema di *input* nel componente Mixed Reality Toolkit.

MRTK rileverà automaticamente i controller WMR e li visualizza quando viene installato il pacchetto [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) I modelli controller verranno visualizzati nell'editor solo quando si usa la pipeline OpenXR. Per visualizzare i modelli di controller Oculus, seguire le istruzioni [per la distribuzione di Oculus Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![Mapping dell'input del controller](../images/input/ControllerInputMapping.png)