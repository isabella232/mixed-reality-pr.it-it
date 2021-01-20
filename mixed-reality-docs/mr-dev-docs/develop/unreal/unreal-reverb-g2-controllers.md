---
title: Controller di HP Reverb G2 in Unreal
description: Informazioni su come usare i nuovi controller di HP Reverb G2 in OpenXR e SteamVR per le applicazioni di realtà mista non reali.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, headset di realtà mista, auricolare della realtà virtuale
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582682"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controller di HP Reverb G2 in Unreal 

## <a name="getting-started"></a>Introduzione

> [!IMPORTANT]
> Unreal Engine 4,26 e OpenXR o SteamVR sono necessari per accedere al plug-in HP Motion controller, è necessario usare i controller di HP Reverb G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Porting di un'app OpenXR esistente 

Se nel gioco non sono presenti associazioni controller per il controller di realtà misto HP, il runtime di OpenXR tenterà di rimappare i binding esistenti al controller attivo.  In questo caso, il gioco ha binding Oculus touch e nessun binding del controller di realtà mista di HP.

![Modifica del mapping delle associazioni esistenti quando non esistono associazioni controller](images/reverb-g2-img-04.png)

Gli eventi verranno comunque attivati, ma se il gioco deve usare binding specifici del controller, ad esempio il pulsante di menu destro, è necessario usare il profilo di interazione con la realtà di HP mixed.  È possibile specificare più associazioni controller per azione per supportare al meglio dispositivi diversi.
   
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
* [Uso di SteamVR con la realtà mista di Windows](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Fotocamera Unreal Player](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)