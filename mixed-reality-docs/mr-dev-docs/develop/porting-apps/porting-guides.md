---
title: Conversione di app VR in Windows Mixed Reality
description: Procedura dettagliata che spiega come trasferire un'applicazione immersiva esistente a una realtà mista di Windows.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: porta, Unity, Unreal, middleware, motore, UWP, Win32, porting, HoloLens 1st Gen, auricolare realtà mista, cuffia a realtà mista di Windows, migrazione, Windows 10, mapping di input,
ms.openlocfilehash: 4137ff4dcc9f72dd66b9078b0d86c2d06f01f2bc
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613225"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Conversione di app VR in Windows Mixed Reality

Windows 10 include il supporto per auricolari immersivi e olografici. Se è stato creato contenuto per altri dispositivi, ad esempio Oculus Rift o HTC vive, questi hanno dipendenze da librerie esistenti sopra l'API della piattaforma del sistema operativo. Il riutilizzo delle app VR Unity di Win32 per la realtà mista di Windows prevede il reindirizzamento dell'utilizzo di SDK VR specifici del fornitore alle API VR tra fornitori di Unity.

## <a name="porting-requirements"></a>Requisiti di porting

A livello generale, sono necessari i passaggi seguenti per trasferire il contenuto esistente:
1. **Verificare che il PC esegua Windows 10 Fall Creators Update (16299).** Non è più consigliabile ricevere le build di anteprima dall'anello Insider Skip Ahead, perché tali Build non saranno le più stabili per lo sviluppo di realtà miste.
2. **Eseguire l'aggiornamento alla versione più recente della grafica o del motore di gioco.** I motori di gioco dovranno supportare Windows 10 SDK versione 10.0.15063.0 (rilasciato ad aprile 2017) o versione successiva.
3. **Aggiornare tutti i middleware, i plug-in o i componenti.** Se l'app contiene componenti, è consigliabile eseguire l'aggiornamento alla versione più recente.
4. **Rimuovere le dipendenze da SDK duplicati**. A seconda del dispositivo a cui è destinato il contenuto, è necessario rimuovere o compilarlo in modo condizionale per poter usare le API di Windows. Un esempio di questo scenario è SteamVR.
5. **Risolvere i problemi di compilazione.** A questo punto, l'esercizio di porting è specifico per l'app, il motore e le dipendenze dei componenti.

## <a name="common-porting-steps"></a>Passaggi comuni di porting

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Assicurarsi di disporre dell'hardware di sviluppo appropriato

Nella pagina [installa strumenti](../install-the-tools.md#immersive-vr-headset-requirements) è elencato l'hardware di sviluppo consigliato.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. eseguire l'aggiornamento all'ultimo volo di Windows 10

La piattaforma di realtà mista Windows è ancora in fase di sviluppo attivo. È consigliabile [partecipare al programma Windows Insider](https://insider.windows.com/) per accedere al volo "Windows Insider Fast".
1. Installare [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Partecipa](https://insider.windows.com/) al programma Windows Insider.
3. Abilita [modalità sviluppatore](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Passa alla sezione relativa ai [voli rapidi di Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) tramite **le impostazioni > sezione aggiornamento & sicurezza**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. eseguire l'aggiornamento alla build più recente di Visual Studio
* Se si usa Visual Studio, eseguire l'aggiornamento alla build più recente
* Vedere [Install the Tools](../install-the-tools.md#installation-checklist) page in Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. scegliere la scheda corretta
* Nei sistemi come notebook con due GPU, fare [riferimento alla scheda corretta](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Questo vale per Unity e per le app DirectX native in cui viene creato un ID3D11Device, in modo esplicito o implicito (Media Foundation), per la funzionalità.

## <a name="unity-porting-guidance"></a>Guida al porting di Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Guida al porting non reale

> [!IMPORTANT]
> Se si usano i controller di HP Reverb G2, fare riferimento a [questo articolo](../unreal/unreal-reverb-g2-controllers.md) per istruzioni aggiuntive sul mapping degli input.

## <a name="see-also"></a>Vedere anche
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Informazioni sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Suggerimenti sulle prestazioni per Unity](../unity/performance-recommendations-for-unity.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [Movimenti e controller del movimento in Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide alla conversione](porting-guides.md)