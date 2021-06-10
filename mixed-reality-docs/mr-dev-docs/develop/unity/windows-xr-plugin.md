---
title: Uso del plug-in Windows XR
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto di Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, introduzione, nuovo progetto, Windows Mixed Reality, UWP, XR, prestazioni, legacy, mrtk, windows
ms.openlocfilehash: 44de6b418995b75d9e199f03922f89016b76c5cd
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743640"
---
# <a name="using-windows-xr-plugin"></a>Uso del plug-in XR di Windows

Per gli sviluppatori che hanno come destinazione Unity 2020, il plug-in Windows XR consente l'accesso alle funzionalità di realtà mista HoloLens 2 e Windows Mixed Reality visori.  Questo plug-in è supportato anche in Unity 2019, anche se esistono alcune incompatibilità note con Ancoraggi nello stato di Azure quando si usa questo plug-in in tale versione.

Mentre Microsoft e la community hanno creato strumenti opensource come [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurano automaticamente l'ambiente WMR, molti sviluppatori vogliono creare le proprie esperienze da zero.  La documentazione seguente illustra come configurare correttamente un progetto per lo sviluppo di realtà mista indipendentemente dal fatto che si utilizzi MRTK o meno.  Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Provare le esercitazioni su MRTK](./tutorials/mr-learning-base-02.md?tabs=winxr)

Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Se si usa desktop VR come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare alla piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architettura** su **ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK** su **Più recente installato**
7.  Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity informazioni per creare una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:

1. Nell'editor unity passare a **Modifica impostazioni > progetto** e selezionare Gestione **plug-in XR**

2. Selezionare **Installa gestione plug-in XR**

![Screenshot della finestra Impostazioni progetto aperta nell'editor unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-5.png)

3. Selezionare **Inizializza XR all'avvio** **e Windows Mixed Reality**

![Screenshot della finestra Impostazioni progetto aperta nell'editor unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-7.png)

4. Espandere la **sezione Gestione plug-in XR** e selezionare **la scheda Univeral Windows Platform Settings (Impostazioni piattaforma Windows univeral)**
5. Se si usa Unity 2020 o versioni successive, verranno visualizzati le opzioni per controllare **OpenXR** **o Windows Mixed Reality**. 
    * È possibile scegliere uno dei due runtime.  Se si sta sviluppando specificamente per il HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR,** selezionare la casella OpenXR ed esaminare la guida all'uso del plug-in [OpenXR](openxr-getting-started.md) di realtà mista per Unity per configurare correttamente questi dispositivi prima di tornare a questa esercitazione

> [!NOTE]
> A partire da Unity 2020 LTS, Microsoft sta abbracciando lo sviluppo con OpenXR.  Durante la migrazione a questo percorso, in Unity 2021.1 il plug-in Windows XR verrà deprecato e rimosso nel 2021.2 rendendo OpenXR l'unico percorso supportato. Per altre informazioni, vedere [Uso del plug-in OpenXR di realtà mista.](openxr-getting-started.md)

6. Se si decide di scegliere il **plug-Windows Mixed Reality,** selezionare tutte le caselle e impostare Modalità di invio **profondità** su **Profondità 16 Bit**

![Screenshot della finestra Impostazioni progetto aperta nell'editor unity con Windows Mixed Reality sezione evidenziata](images/wmr-config-img-8.png)