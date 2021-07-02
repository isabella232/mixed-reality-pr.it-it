---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176921"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed distrutti automaticamente dai [**provider di input**](input-providers.md). Ogni tipo di controller ha un numero di *input* fisici definiti da un tipo di asse *,* indicando il tipo di dati del valore di input (Digitale, Asse singolo, Asse doppio, Sei Dof, ...) e un tipo di *input* (Pressione pulsante, Trigger, Levetta thumb, Puntatore spaziale, ...) che descrive l'origine dell'input. Gli input fisici vengono mappati alle azioni di *input* tramite nel profilo di mapping dell'input del **controller,** sotto *il* profilo del sistema di input nel componente Toolkit realtà mista.

![Mapping dell'input del controller](../images/input/ControllerInputMapping.png)
