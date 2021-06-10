---
title: Controller in MRTK
description: Documentazione sull'uso di vari controller con MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller, riverbero HP, Oculus, PIÙ Vive, mani
ms.openlocfilehash: 111ebf2b1eb26bbef8cde16832f780acfa758595
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743579"
---
# <a name="controllers-in-mrtk"></a>Controller in MRTK

MRTK supporta molti controller diversi. Molti controller, ad esempio ILVA ViveUckles e ILVA Vive Wands, funzioneranno in modo nativo dopo l'avvio di un'applicazione compilata con MRTK nel dispositivo compatibile. Altri controller, ad esempio le mani articolate su Oculus Quest e i controller HP Reverb G2, richiedono pacchetti aggiuntivi prima che siano riconosciuti da MRTK.

Questo documento descrive gli scenari comuni in cui è necessario installare pacchetti aggiuntivi. Per istruzioni su come eseguire la distribuzione nel dispositivo, vedere le pagine di [**distribuzione di Hololens/WMR**](./wmr-mrtk.md) o [**Oculus Quest.**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) Per altre informazioni sui controller, visitare la [**pagina delle funzionalità**](../features/input/controllers.md). Per eseguire il debug dei problemi con i controller, vedere lo [ **strumento di mapping dei controller**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Controller HP Reverb G2

Per rilevare e visualizzare i controller HP Reverb G2 quando si usa MRTK, seguire questa procedura per installare il [**pacchetto Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) Dopo aver installato questo pacchetto, non è necessario apportare altre modifiche ai profili predefiniti per visualizzare i controller nel riverbero HP. 

Per visualizzare i controller nell'editor, è necessario assicurarsi di usare usando il [**plug-in OpenXR.**](/windows/mixed-reality/develop/unity/openxr-getting-started)

## <a name="oculus-controllers"></a>Controller Oculus 

Per visualizzare i modelli di controller Oculus, seguire le istruzioni per la distribuzione di Oculus Quest. Se si vogliono visualizzare le mani virtuali quando si usano i controller, assicurarsi che l'opzione Render **Avatar Hands Instead Of Controllers** (Rendering delle mani avatar anziché dei controller) sia selezionata in XR SDK Oculus Device Manager. In caso contrario, deselezionare questa opzione.

![OculusDeviceManagerSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)