---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: b41f73b5a7dd3026fded8711b2c2fc56f59e34eb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688521"
---
# <a name="controllers"></a>Controllers

I controller vengono creati ed eliminati automaticamente dai [**provider di input**](InputProviders.md). Ogni tipo di controller dispone di un numero di *input fisici* definito da un *tipo di asse*, indicando il tipo di dati del valore di input (digitale, asse singolo, asse doppio, sei DOF,...) e un *tipo di input* (premere pulsante, trigger, Thumb Stick, puntatore spaziale,...) che descrive l'origine dell'input. Per gli input fisici viene eseguito il mapping alle *azioni di input* tramite nel profilo di mapping di **input del controller**, sotto il profilo di *sistema di input* nel componente del Toolkit di realtà mista.

<img src="../images/input/ControllerInputMapping.png" style="max-width:100%;" alt="Input Maping Control">
