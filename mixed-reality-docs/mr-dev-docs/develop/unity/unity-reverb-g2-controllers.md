---
title: Controller di HP Reverb G2 in Unity
description: Istruzioni sull'uso dei controller HP Reverb G2 in SteamVR e in realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638388"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controller di HP Reverb G2 in Unity

## <a name="getting-started"></a>Introduzione

Non è necessaria alcuna configurazione aggiuntiva per usare il controller HP Reverb G2 se si sta sviluppando per SteamVR o si usa l'API di input della realtà mista di Windows (XR). WSA. Input). Tuttavia, i pulsanti A, B, X, Y e il trigger squeeze non sono attualmente accessibili tramite Gestione input a meno che non si stia usando SteamVR. Il supporto per gli input G2 aggiuntivi del riverbero sarà disponibile a breve in futuro, quindi assicurarsi di controllarlo.

## <a name="porting-existing-applications"></a>Porting di applicazioni esistenti

Se si dispone già di un'app esistente che si sta sviluppando per auricolari immersivi di Windows, vedere la [Guida al porting](../porting-apps/porting-guides.md) e [le impostazioni di progetto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) per suggerimenti generali.

## <a name="mapping-input"></a>Input mapping

Quando si è pronti per l'esecuzione del mapping di input per i nuovi controller, iniziare dalla sezione [mapping di input](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) della Guida per il porting immersivo. Le istruzioni su come configurare gli input in Unity sono descritte in dettaglio in [movimenti e controller di movimento](gestures-and-motion-controllers-in-unity.md), insieme a un pulsante completo e a una [tabella di mapping dell'asse](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) per riferimento.

## <a name="see-also"></a>Vedere anche
* [Aggiornamento per SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)