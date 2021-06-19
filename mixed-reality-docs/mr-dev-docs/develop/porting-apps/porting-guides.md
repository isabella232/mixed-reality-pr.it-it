---
title: Conversione di app VR in Windows Mixed Reality
description: Procedura dettagliata che illustra come convertire un'applicazione immersiva esistente Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, unity, unreal, middleware, engine, UWP, Win32, porting, HoloLens di prima generazione, visore VR di realtà mista, visore VR windows mixed reality, migrazione, Windows 10, mapping di input,
ms.openlocfilehash: bb76325c0a2d10150cff6604e29c7ead8a97df8e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394465"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Conversione di app VR in Windows Mixed Reality

Windows 10 include il supporto per visori VR immersive e olografici. Se il contenuto è stato creato per altri dispositivi, ad esempio Oculus Rift o LASE Vive, questi hanno dipendenze dalle librerie esistenti sopra l'API della piattaforma del sistema operativo. Il resciso delle app Vr Win32 Unity esistenti Windows Mixed Reality comporta la ridestinazione dell'uso di SDK VR specifici del fornitore alle API VR tra fornitori di Unity.

## <a name="porting-requirements"></a>Requisiti di portabilità

A livello elevato, per la portabilità del contenuto esistente sono necessari i passaggi seguenti:
1. **Assicurarsi che il PC eserciti il Windows 10 Fall Creators Update (16299).** Non è più consigliabile ricevere build di anteprima dall'anello Insider Skip Ahead, perché non saranno le più stabili per lo sviluppo di realtà mista.
2. **Eseguire l'aggiornamento alla versione più recente del motore di grafica o di gioco.** I motori di gioco dovranno supportare Windows 10 SDK versione 10.0.15063.0 (rilasciata ad aprile 2017) o versione successiva.
3. **Aggiornare qualsiasi middleware, plug-in o componente.** Se l'app contiene componenti, è buona idea eseguire l'aggiornamento alla versione più recente.
4. **Rimuovere le dipendenze da SDK duplicati.** A seconda del dispositivo di destinazione del contenuto, dovrai rimuovere o compilare in modo condizionale l'SDK in modo da poter usare le API Windows come destinazione. Un esempio di questo scenario è SteamVR.
5. **Risolvere i problemi di compilazione.** A questo punto, l'esercizio di portabilità è specifico per l'app, il motore e le dipendenze dei componenti.

## <a name="common-porting-steps"></a>Passaggi comuni per la portabilità

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Assicurarsi di avere l'hardware di sviluppo giusto

La [pagina della guida per gli appassionati di](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) realtà virtuale elenca l'hardware di sviluppo consigliato.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Eseguire l'aggiornamento alla versione più recente Windows 10

La Windows Mixed Reality è ancora in fase di sviluppo attivo. È [consigliabile partecipare al Programma Windows Insider](https://insider.windows.com/) per accedere al volo "partecipante al Programma Windows Insider Fast".
1. Installare il [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Aggiungere](https://insider.windows.com/) il Programma Windows Insider.
3. Abilitare [la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development)
4. Passare alla sezione [Partecipante al Programma Windows Insider Fast Flights](/archive/blogs/uktechnet/joining-insider-preview) tramite Impostazioni **>'aggiornamento & sicurezza**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Eseguire l'aggiornamento alla build più recente di Visual Studio
* Se si usa un Visual Studio, eseguire l'aggiornamento alla build più recente
* Vedere [la pagina Installare gli](../install-the-tools.md#installation-checklist) strumenti in Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Scegliere l'adapter corretto
* Nei sistemi come i notebook con due GPU, scegliere [come destinazione la scheda corretta.](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications) Questo vale per le app Unity e DirectX native in cui viene creato un id3D11Device, in modo esplicito o implicito (Media Foundation), per la relativa funzionalità.

## <a name="unity-porting-guidance"></a>Linee guida per la portabilità di Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Linee guida per la portabilità di Unreal

> [!IMPORTANT]
> Se si usano controller HP Reverb G2, fare riferimento a questo articolo per [istruzioni](../unreal/unreal-reverb-g2-controllers.md) aggiuntive sul mapping dell'input.

## <a name="see-also"></a>Vedi anche
* [Windows Mixed Reality di compatibilità hardware minima del PC](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Informazioni sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Raccomandazioni sulle prestazioni per Unity](../unity/performance-recommendations-for-unity.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [Controller del movimento in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide alla conversione](porting-guides.md)