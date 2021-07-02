---
title: Rilevamento dei controller in MRTK
description: Documentazione sull'uso di vari controller con MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller, HP Reverb, Oculus, HTC Vive, Mani
ms.openlocfilehash: 2bb749f4e2f6294c4feb74f97af55ecb857d5f76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175590"
---
# <a name="detecting-controllers-in-mrtk"></a>Rilevamento dei controller in MRTK

MRTK supporta molti controller diversi. Molti controller, ad esempio i wands DI VIVE e i wands DI VIVE, funzioneranno in modo nativo dopo l'avvio di un'applicazione compilata con MRTK nel dispositivo compatibile. Altri controller, ad esempio le mani articolate su Oculus Quest e i controller HP Reverb G2, richiedono pacchetti aggiuntivi prima che siano riconosciuti da MRTK.

Questo documento descrive gli scenari comuni in cui è necessario installare pacchetti aggiuntivi. Per istruzioni su come eseguire la distribuzione nel dispositivo, vedere le pagine di [**distribuzione di Hololens/WMR**](./wmr-mrtk.md) o [**Oculus Quest.**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) Per altre informazioni sui controller, visitare la [**pagina delle funzionalità**](../features/input/controllers.md). Per eseguire il debug dei problemi con i controller, vedere lo [ **strumento di mapping dei controller**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Controller HP Reverb G2

Per rilevare e visualizzare i controller HP Reverb G2 quando si usa MRTK, seguire questa procedura per installare il pacchetto [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) Dopo l'installazione di questo pacchetto, non è necessario apportare altre modifiche ai profili predefiniti per visualizzare i controller in HP Reverb. 

Per visualizzare i controller nell'editor, è necessario assicurarsi di usare il plug-in [**OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).

## <a name="oculus-controllers"></a>Controller Oculus 

Per visualizzare i modelli di controller Oculus, seguire le istruzioni per la distribuzione di Oculus Quest. Se si desidera visualizzare le mani virtuali quando si usano i controller, assicurarsi che l'opzione **Render Avatar Hands Instead Of Controllers** sia selezionata in XR SDK Oculus Device Manager. In caso contrario, deselezionare questa opzione.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
