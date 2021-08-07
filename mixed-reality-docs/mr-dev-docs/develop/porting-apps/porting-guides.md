---
title: Conversione di app VR in Windows Mixed Reality
description: Procedura dettagliata che illustra come convertire un'applicazione immersiva esistente Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, unity, unreal, middleware, engine, UWP, Win32, porting, HoloLens 1st gen, mixed reality headset, windows mixed reality headset, migration, Windows 10, input mapping,
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213515"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Conversione di app VR in Windows Mixed Reality

Windows 10 include il supporto per visori immersive e olografici. Se sono stati creati contenuti per altri dispositivi, ad esempio Oculus Rift o l'opzione DISAUS Vive, questi hanno dipendenze dalle librerie esistenti sopra l'API della piattaforma del sistema operativo. Il retargeting delle app VR Win32 Unity esistenti Windows Mixed Reality comporta il retargeting dell'utilizzo di SDK VR specifici del fornitore alle API VR tra fornitori di Unity.

## <a name="porting-requirements"></a>Requisiti di porting

A livello di alto livello, i passaggi seguenti sono necessari per il porting del contenuto esistente:
1. **Assicurarsi che il PC eserciti il Windows 10 Fall Creators Update (16299).** Non è più consigliabile ricevere build di anteprima dall'anello Insider Skip Ahead, perché non saranno le più stabili per lo sviluppo di realtà mista.
2. **Eseguire l'aggiornamento alla versione più recente del motore di grafica o di gioco.** I motori di gioco dovranno supportare Windows 10 SDK versione 10.0.15063.0 (rilasciata ad aprile 2017) o successiva.
3. **Aggiornare qualsiasi middleware, plug-in o componente.** Se l'app contiene componenti, è buona idea eseguire l'aggiornamento alla versione più recente.
4. **Rimuovere le dipendenze da SDK duplicati.** A seconda del dispositivo di destinazione del contenuto, è necessario rimuovere o compilare in modo condizionale l'SDK in modo da poter usare le API Windows destinazione. Un esempio di questo scenario è SteamVR.
5. **Risolvere i problemi di compilazione.** A questo punto, l'esercizio di porting è specifico per l'app, il motore e le dipendenze dei componenti.

## <a name="common-porting-steps"></a>Passaggi comuni di porting

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Assicurarsi di avere l'hardware di sviluppo giusto

La [pagina della guida per gli appassionati di VR](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) elenca l'hardware di sviluppo consigliato.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Eseguire l'aggiornamento al volo più recente di Windows 10

La Windows Mixed Reality è ancora in fase di sviluppo attivo. È [consigliabile partecipare al Windows Programma Insider](https://insider.windows.com/) per accedere al volo "Windows Circuito Insider veloce".
1. Installare il [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Aggiungere](https://insider.windows.com/) il Windows Programma Insider.
3. Abilitare [la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development)
4. Passare ai voli [Windows Circuito Insider veloce tramite](/archive/blogs/uktechnet/joining-insider-preview) Impostazioni > update **& Security**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Eseguire l'aggiornamento alla build più recente di Visual Studio
* Se si usa Visual Studio, eseguire l'aggiornamento alla build più recente
* Vedere [La pagina Installa gli](../install-the-tools.md#installation-checklist) strumenti in Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Scegliere l'adapter corretto
* In sistemi come notebook con due GPU, [scegliere come destinazione la scheda corretta.](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications) Questo vale per Unity e per le app DirectX native in cui viene creato un dispositivo ID3D11, in modo esplicito o implicito (Media Foundation), per la relativa funzionalità.

## <a name="unity-porting-guidance"></a>Linee guida per il porting di Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Linee guida per la portabilità unreal

> [!IMPORTANT]
> Se si usano controller HP Reverb G2, fare riferimento a [questo articolo](../unreal/unreal-reverb-g2-controllers.md) per istruzioni aggiuntive sul mapping dell'input.

## <a name="see-also"></a>Vedi anche
* [Windows Mixed Reality linee guida minime sulla compatibilità hardware del PC](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Informazioni sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Prestazioni Consigli per Unity](../unity/performance-recommendations-for-unity.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [Controller di movimento in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide alla conversione](porting-guides.md)