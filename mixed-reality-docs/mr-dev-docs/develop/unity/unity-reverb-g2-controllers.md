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
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="f1d87-104">Controller di HP Reverb G2 in Unity</span><span class="sxs-lookup"><span data-stu-id="f1d87-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="f1d87-105">Introduzione</span><span class="sxs-lookup"><span data-stu-id="f1d87-105">Getting started</span></span>

<span data-ttu-id="f1d87-106">Non è necessaria alcuna configurazione aggiuntiva per usare il controller HP Reverb G2 se si sta sviluppando per SteamVR o si usa l'API di input della realtà mista di Windows (XR). WSA. Input).</span><span class="sxs-lookup"><span data-stu-id="f1d87-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="f1d87-107">Tuttavia, i pulsanti A, B, X, Y e il trigger squeeze non sono attualmente accessibili tramite Gestione input a meno che non si stia usando SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f1d87-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="f1d87-108">Il supporto per gli input G2 aggiuntivi del riverbero sarà disponibile a breve in futuro, quindi assicurarsi di controllarlo.</span><span class="sxs-lookup"><span data-stu-id="f1d87-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="f1d87-109">Porting di applicazioni esistenti</span><span class="sxs-lookup"><span data-stu-id="f1d87-109">Porting existing applications</span></span>

<span data-ttu-id="f1d87-110">Se si dispone già di un'app esistente che si sta sviluppando per auricolari immersivi di Windows, vedere la [Guida al porting](../porting-apps/porting-guides.md) e [le impostazioni di progetto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) per suggerimenti generali.</span><span class="sxs-lookup"><span data-stu-id="f1d87-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="f1d87-111">Input mapping</span><span class="sxs-lookup"><span data-stu-id="f1d87-111">Mapping input</span></span>

<span data-ttu-id="f1d87-112">Quando si è pronti per l'esecuzione del mapping di input per i nuovi controller, iniziare dalla sezione [mapping di input](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) della Guida per il porting immersivo.</span><span class="sxs-lookup"><span data-stu-id="f1d87-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="f1d87-113">Le istruzioni su come configurare gli input in Unity sono descritte in dettaglio in [movimenti e controller di movimento](gestures-and-motion-controllers-in-unity.md), insieme a un pulsante completo e a una [tabella di mapping dell'asse](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) per riferimento.</span><span class="sxs-lookup"><span data-stu-id="f1d87-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1d87-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1d87-114">See also</span></span>
* [<span data-ttu-id="f1d87-115">Aggiornamento per SteamVR</span><span class="sxs-lookup"><span data-stu-id="f1d87-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)