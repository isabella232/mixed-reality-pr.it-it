---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: 7acfffb0bba852b7ac63a5b22349a11c73e223e0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783344"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed eliminati automaticamente dai [**provider di input**](InputProviders.md). Ogni tipo di controller dispone di un numero di *input fisici* definito da un *tipo di asse*, indicando il tipo di dati del valore di input (digitale, asse singolo, asse doppio, sei DOF,...) e un *tipo di input* (premere pulsante, trigger, Thumb Stick, puntatore spaziale,...) che descrive l'origine dell'input. Per gli input fisici viene eseguito il mapping alle *azioni di input* tramite nel profilo di mapping di **input del controller**, sotto il profilo di *sistema di input* nel componente del Toolkit di realtà mista.

<img src="../Images/Input/ControllerInputMapping.png" style="max-width:100%;" alt="Controller input maping">
