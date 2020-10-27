---
title: Controller di HP Reverb G2 in Unreal
description: Istruzioni sull'uso dei controller HP Reverb G2 in OpenXR e SteamVR
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638721"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controller di HP Reverb G2 in Unreal 

## <a name="getting-started"></a>Introduzione

> [!IMPORTANT]
> Unreal Engine 4,26 e OpenXR o SteamVR sono necessari per accedere al plug-in HP Motion controller, è necessario usare i controller di HP Reverb G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Porting di un'app OpenXR esistente 

Se nel gioco non sono presenti associazioni controller per il controller di realtà misto HP, il runtime di OpenXR tenterà di rimappare i binding esistenti al controller attivo.  In questo caso, il gioco ha binding Oculus touch e nessun binding del controller di realtà mista di HP.

![Modifica del mapping delle associazioni esistenti quando non esistono associazioni controller](images/reverb-g2-img-04.png)

Gli eventi verranno comunque attivati, ma se il gioco deve usare binding specifici del controller, ad esempio il pulsante di menu destro, è necessario usare il profilo di interazione con la realtà mista di HP.  È possibile specificare più associazioni controller per azione per supportare al meglio dispositivi diversi.
   
![Uso di più associazioni controller](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Aggiunta di mapping di azioni di input 

Definire una nuova azione ed eseguire il mapping a una delle pressioni dei tasti nella sezione HP Mixed Reality controller.

![Definizione di nuove azioni e mapping](images/reverb-g2-img-02.png)

Il controller di HP Reverb G2 dispone anche di un grip analogico, che può essere usato nei mapping degli assi con il binding "Squeeze Axis".  È disponibile un'associazione di compressione separata, che deve essere usata per i mapping delle azioni quando il pulsante grip è premuto completamente. 

![Utilizzo delle associazioni dell'asse squeeze](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Aggiunta di eventi di input

Fare clic con il pulsante destro del mouse su un progetto e cercare i nuovi nomi di azione del sistema di input per aggiungere gli eventi per queste azioni.  Il progetto sta rispondendo agli eventi con una stringa di stampa che visualizza lo stato corrente del pulsante e dell'asse.

![Progetto che risponde agli eventi e output dello stato corrente del pulsante e dell'asse](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Uso dell'input 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Vedere anche
* [Input SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Uso di SteamVR con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Fotocamera Unreal Player](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)