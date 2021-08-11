---
title: Controller HP Reverb G2 in Unreal
description: Informazioni su come usare i nuovi controller HP Reverb G2 in OpenXR e SteamVR per applicazioni di realtà mista Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP Reverb G2, realtà mista, sviluppo, controller del movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204209"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controller HP Reverb G2 in Unreal 

## <a name="getting-started"></a>Guida introduttiva

> [!IMPORTANT]
> Unreal Engine 4.26 e OpenXR o MotionVR sono necessari per accedere al plug-in HP Motion Controller, che è necessario usare con i controller HP Reverb G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Porting di un'app OpenXR esistente 

Se non sono presenti binding del controller nel gioco per HP Mixed Reality Controller, il runtime OpenXR tenterà di modificare il mapping dei binding esistenti al controller attivo.  In questo caso, il gioco ha binding Oculus Touch e nessun binding del controller di realtà mista HP.

![Ridefinire il mapping delle associazioni esistenti quando non sono presenti associazioni del controller](images/reverb-g2-img-04.png)

Gli eventi verranno comunque generati, ma se il gioco deve usare binding specifici del controller, ad esempio il pulsante di menu a destra, è necessario usare il profilo di interazione di HP Mixed Reality.  È possibile specificare più associazioni del controller per azione per supportare meglio dispositivi diversi.
   
![Uso di più associazioni del controller](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Aggiunta di mapping delle azioni di input 

Definire una nuova azione ed eseguire il mapping a una delle combinazioni di tasti nella sezione HP Mixed Reality Controller.

![Definizione di nuove azioni e mapping](images/reverb-g2-img-02.png)

Il controller HP Reverb G2 ha anche un manopolo analogico, che può essere usato nei mapping degli assi con il binding "Asse di rotazione".  È disponibile un binding Disasato separato, che deve essere usato per i mapping delle azioni quando il pulsante di controllo viene premuto completamente. 

![Uso dei binding dell'asse Disassato](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Aggiunta di eventi di input

Fare clic con il pulsante destro del mouse su un progetto e cercare i nuovi nomi di azione dal sistema di input per aggiungere eventi per queste azioni.  In questo caso il progetto risponde agli eventi con una stringa di stampa che restituisce lo stato corrente del pulsante e dell'asse.

![Progetto che risponde agli eventi e restituisce lo stato corrente del pulsante e dell'asse](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Uso dell'input 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Vedi anche
* [Input DiVr a flusso](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Uso di SteamVR con Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player Camera](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)