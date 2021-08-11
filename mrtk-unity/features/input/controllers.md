---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224763"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed distrutti automaticamente dai [**provider di input**](input-providers.md). Ogni tipo di controller ha un numero di *input* fisici definiti da un tipo di asse *,* indicando il tipo di dati del valore di input (Digitale, Asse singolo, Asse doppio, Sei Dof, ...) e un tipo di *input* (Pressione del pulsante, Trigger, Levetta thumb, Puntatore spaziale, ...) che descrive l'origine dell'input. Gli input fisici vengono mappati alle azioni di *input* tramite nel profilo di mapping dell'input del **controller,** sotto *il* profilo del sistema di input nel componente Toolkit realtà mista.

![Mapping dell'input del controller](../images/input/ControllerInputMapping.png)
