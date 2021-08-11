---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: 87b3ed98ebd5b16b62e8cf36364c350580ba38ac1c7dbb549858ed8bec2e1eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219783"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed distrutti automaticamente dai [**provider di input**](input-providers.md). Ogni tipo di controller ha un numero di *input* fisici definiti da un tipo di *asse,* indicando il tipo di dati del valore di input (Digital, Single Axis, Dual Axis, Six Dof, ...) e un tipo di *input* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) che descrive l'origine dell'input. Gli input fisici vengono mappati alle azioni di *input* tramite nel profilo di mapping dell'input del **controller,** sotto il profilo del sistema di *input* nel componente Toolkit realtà mista.

<img src="../images/input/ControllerInputMapping.png" style="max-width:100%;">
