---
title: Uso del plug-in Windows XR
description: Informazioni su come configurare i progetti Unity con e senza MRTK con il supporto di Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni, legacy, MRTK, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938121"
---
# <a name="using-windows-xr-plugin"></a>Uso del plug-in Windows XR

Per gli sviluppatori che hanno come destinazione Unity 2020, il plug-in Windows XR consente l'accesso a funzionalità di realtà mista in HoloLens 2 e Windows Mixed Reality Headset.  Questo plug-in è supportato anche in Unity 2019, sebbene ci siano alcune incompatibilità note con i Anchor spaziali di Azure quando si usa questo plug-in in questa versione.

Microsoft e la community hanno creato strumenti opensource come il Toolkit di [realtà mista (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurerà automaticamente l'ambiente WMR, molti sviluppatori desiderano creare le proprie esperienze da zero.  Nella documentazione seguente viene illustrato come configurare correttamente un progetto per lo sviluppo di realtà mista se si utilizza MRTK o no.  Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.

## <a name="setting-up-your-project-with-mrtk"></a>Impostazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Prova le nostre esercitazioni su MRTK](tutorials/mr-learning-base-01.md)

Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .

## <a name="manual-setup-without-mrtk"></a>Installazione manuale senza MRTK

Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Seleziona **File > impostazioni di compilazione...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )
3.  Impostare l' **architettura** su **ARM 64**
4.  Impostare il **dispositivo di destinazione** su **HoloLens**
5.  Imposta **tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK** sull' **ultima versione installata**
7.  Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) invece di una visualizzazione 2D quando viene esportata:

1. Nell'editor di Unity passare a **Edit > Settings Project** e selezionare **XR plugin Management**

2. Selezionare **Install XR plugin Management**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-5.png)

3. Selezionare **Inizializza XR all'avvio** e **realtà mista di Windows**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-7.png)

4. Espandere la sezione **Gestione plug-in XR** e selezionare la scheda **impostazioni della piattaforma Windows Univeral**
5. Se si usa Unity 2020 o versioni successive, verranno visualizzate le opzioni per controllare **OpenXR** o la **realtà mista di Windows**. 
    * È possibile scegliere Runtime.  Se si sta sviluppando in modo specifico per HoloLens 2 o HP Reverb G2 e si decide di provare il **OpenXR**, selezionare la casella OpenXR ed esaminare la Guida all' [uso del plug-in realtà mista OpenXR per Unity](openxr-getting-started.md) per configurarlo correttamente per questi dispositivi prima di tornare a questa esercitazione

> [!NOTE]
> A partire da Unity 2020 LTS, Microsoft abbraccia lo sviluppo con OpenXR.  Quando si esegue la migrazione a questo percorso, in Unity 2021,1 il plug-in Windows XR verrà deprecato e rimosso in 2021,2 rendendo OpenXR l'unico percorso supportato. Altre informazioni sono disponibili in [uso del plug-in OpenXR per la realtà mista](openxr-getting-started.md).

6. Se si decide di scegliere il plug-in per la **realtà mista di Windows** , selezionare tutte le caselle e impostare la **modalità di invio profondità** su **profondità a 16 bit**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione realtà mista di Windows evidenziata](images/wmr-config-img-8.png)
