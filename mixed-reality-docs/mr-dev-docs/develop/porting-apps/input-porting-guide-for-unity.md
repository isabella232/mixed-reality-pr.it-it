---
title: Guida alla conversione dell'input per Unity
description: Informazioni su come gestire l'input per la realtà mista di Windows in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: input, Unity, porting
ms.openlocfilehash: d6bef0f10cf1fc20d5067ac77a126bb793385f59
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192649"
---
# <a name="input-porting-guide-for-unity"></a>Guida alla conversione dell'input per Unity

È possibile trasferire la logica di input in una realtà mista di Windows usando uno dei due approcci. Il primo consiste nell'usare le API input. GetButton/getaxis di Unity che si estendono su più piattaforme. Il secondo è la specifica di Windows XR. WSA. API di input, che offrono dati più ricchi in modo specifico per i controller di movimento e le HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>Input generale. GetButton/API getaxis

Unity usa attualmente le API input. GetButton/input. getasse generale per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app usano già queste API per l'input, le API input. GetButton/input. getaxis sono i percorsi più semplici per supportare i controller di movimento in realtà mista di Windows. È necessario rimappare solo i pulsanti e gli assi nel gestore di input.

Per altre informazioni, vedere la [tabella di mapping degli assi e dei pulsanti di Unity](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e la [Panoramica delle API comuni di Unity](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR specifico di Windows. WSA. API di input

Se l'app crea già una logica di input personalizzata per ogni piattaforma, è possibile usare le API di input spaziali specifiche di Windows nello spazio dei nomi **UnityEngine. XR. WSA. input** . Da qui è possibile accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, in modo da informare le mani e i controller in HoloLens.

Per altre informazioni, vedere la [Panoramica delle API UnityEngine. XR. WSA. input](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma. La progettazione di ogni controller differisce dalla propria relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione:

* La posizione del **grip**, che rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.
    * Negli auricolari immersivi è consigliabile usare questa soluzione per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano**, ad esempio una spada o una pistola.
    * **Posizione del grip**: il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.
    * L' **asse destro dell'orientamento del grip**: quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)
    * **Asse di avanzamento dell'orientamento del grip**: quando si chiude parzialmente la mano, come se si tenesse il controller, il raggio che punta "avanza" attraverso il tubo formato dalle dita non Thumb.
    * **Asse verticale dell'orientamento del grip**: l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.
    * È possibile accedere al grip con l'API di input tra fornitori di Unity (**[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o tramite l'API specifica di Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, che richiede la richiesta della forma del grip).
* Il **puntatore** che rappresenta il suggerimento del controller che punta in poi.
    * Questa posizione è particolarmente utilizzata per Raycast quando si **punta all'interfaccia utente** quando si esegue il rendering del modello di controller.
    * Attualmente, la posa del puntatore è disponibile solo tramite l'API specifica di Windows (**sourceState. sourcePose. TryGetPosition/Rotation**, che richiede la posa del puntatore).

Queste coordinate di pose sono tutte espresse in coordinate internazionali di Unity.

## <a name="see-also"></a>Vedi anche
* [Controller di movimento]().. /.. /design/motion-controllers.md)
* [Controller di movimento in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide alla conversione](porting-guides.md)
