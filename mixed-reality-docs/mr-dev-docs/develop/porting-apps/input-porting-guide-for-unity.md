---
title: Guida alla conversione dell'input per Unity
description: Informazioni su come gestire l'input Windows Mixed Reality in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: input, unity, porting
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212079"
---
# <a name="input-porting-guide-for-unity"></a>Guida alla conversione dell'input per Unity

È possibile convertire la logica di input Windows Mixed Reality usando uno dei due approcci seguenti. Il primo è usare le API Input.GetButton/GetAxis generali di Unity che si estendono su più piattaforme. Il secondo è il Windows specifico del codice XR. Wsa. API di input, che offrono dati più specifici per i controller del movimento e HoloLens mani.

## <a name="general-inputgetbuttongetaxis-apis"></a>API Input.GetButton/GetAxis generali

Unity attualmente usa le API Input.GetButton/Input.GetAxis generali per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR SDK.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Se le app usano già queste API per l'input, le API Input.GetButton/Input.GetAxis sono i percorsi più semplici per supportare i controller del movimento in Windows Mixed Reality. Sarà necessario modificare solo il mapping di pulsanti e assi in Gestione input.

Per altre informazioni, vedere la tabella [di mapping di pulsanti/assi di Unity](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e la panoramica delle API comuni di [Unity.](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows specifico di XR. Wsa. API di input

Se l'app compila già la logica di input personalizzata per ogni piattaforma, è possibile usare le API di input spaziale specifiche di Windows nello spazio dei nomi **UnityEngine.XR.WSA.Input.** Da qui è possibile accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, consentendo di distogliere mani e controller HoloLens.

Per altre informazioni, vedere [la panoramica delle API UnityEngine.XR.WSA.Input.](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Posizione del mantenimento e posizione di puntamento

Windows Mixed Reality supporta i controller del movimento in fattori di forma diversi. La progettazione di ogni controller differisce nella relazione tra la posizione della mano dell'utente e la direzione "avanti" naturale che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, è possibile esaminare due tipi di posizioni per ogni origine di interazione:

* Posizione **del manopolo**, che rappresenta la posizione del palmo di una mano rilevata da un HoloLens o del palmo che contiene un controller del movimento.
    * Nei visori VR immersive, questa posizione è più adatta per eseguire il rendering della mano **dell'utente** o di un oggetto in mano **dell'utente,** ad esempio una mano o una mano.
    * Posizione **del riquadro:** centroide del palmo quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del riquadro.
    * Asse destro **dell'orientamento** del riquadro: quando si apre completamente la mano per formare una posizione piana a 5 dita, il raggio normale al palmo (in avanti dal palmo sinistro, all'indietro dal palmo destro)
    * Asse avanti **dell'orientamento** del controllo: quando si chiude parzialmente la mano, come se si tiene il controller, il raggio che punta "in avanti" attraverso il raggio formato dalle dita non del pollice.
    * Asse **su dell'orientamento del** riquadro: asse verso l'alto implicito dalle definizioni Right e Forward.
    * È possibile accedere alla posizione del pannello tramite l'API di input tra fornitori di Unity **[(XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o tramite l'API specifica Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** che richiede la posizione del controllo).
* Posizione **dell'indicatore** di misura, che rappresenta la punta del controller che punta in avanti.
    * Questa posizione è più adatta per il raycast quando **si punta all'interfaccia** utente quando si esegue il rendering del modello controller stesso.
    * Attualmente, la posizione del puntatore è disponibile solo tramite l'API specifica Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** che richiede la posizione del puntatore).

Queste coordinate di posizione sono tutte espresse in coordinate del mondo Unity.

## <a name="see-also"></a>Vedi anche
* [Controller del movimento]().. /.. /design/motion-controllers.md)
* [Controller del movimento in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide alla conversione](porting-guides.md)
