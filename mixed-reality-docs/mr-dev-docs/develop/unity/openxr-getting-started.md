---
title: Uso del plug-in Mixed Reality OpenXR
description: Informazioni su come abilitare il plug-in OpenXR di Realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547039"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>Uso del plug-in Mixed Reality OpenXR

Per gli sviluppatori che hanno come destinazione Unity 2020 la creazione di applicazioni HoloLens 2 o realtà mista, è possibile usare il plug-in OpenXR invece del plug-in WindowsXR per una migliore compatibilità multipiattaforma.  Il plug-in OpenXR di Realtà mista funziona bene anche con la versione più recente di [Mixed Reality Toolkit 2.7.](/windows/mixed-reality/mrtk-unity)

## <a name="prerequisites"></a>Prerequisiti

* Versione più recente di Unity 2020.3 LTS (è consigliabile usare 2020.3.8f1 o versione superiore)
* Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)
* Strumenti [più recenti per HoloLens 2 sviluppo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* MrTK più recente (facoltativo), (è consigliabile la versione 2.7 o successiva)
* Plug-in OpenXR di realtà mista più recente (è consigliabile usare la versione 1.0.0-preview.1 o successiva)

![Screenshot dell'esempio di base xr unity aperto in esecuzione in holoLens](images/openxr-example.png)

> [!NOTE]
> Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario. Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Configurare il progetto con MRTK](./tutorials/mr-learning-base-02.md?tabs=openxr)

Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool. Seguire le [istruzioni di installazione e utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:

![Finestra dei pacchetti degli strumenti di funzionalità di realtà mista con il plug-in xr aperto evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Impostazione della destinazione di compilazione

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1. Selezionare **Impostazioni > file...**
2. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3. Impostare **Architecture (Architettura)** **su ARM 64**
4. Impostare **Dispositivo di destinazione** su **HoloLens**
5. Impostare **Tipo di compilazione** su **D3D**
6. Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configurazione della gestione dei plug-in XR per OpenXR

Per impostare OpenXR come runtime in Unity:

1. Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**
2. Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**
3. Selezionare le **caselle Inizializza XR all'avvio** **e OpenXR**
4. Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens **set di funzionalità**

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Se stai sviluppando per HoloLens 2, passa a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori per le app).

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

> [!IMPORTANT]
> Se viene visualizzata un'icona di avviso rossa accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare. Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.  Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Progetti di esempio Unity per OpenXR e HoloLens 2

Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.

## <a name="using-mrtk-with-openxr-support"></a>Uso di MRTK con il supporto di OpenXR

MRTK per Unity versione 2.7 ora supporta ufficialmente il plug-in OpenXR di Realtà mista.

Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto. Il supporto di OpenXR è in pacchetto **Foundation.**

![Finestra delle funzionalità di individuazione delle funzionalità di realtà mista con gli asset standard evidenziati](images/mrft-install-openxr.png)

> [!NOTE]
> Quando si esegue l'aggiornamento da una versione precedente di MRTK, assicurarsi che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.

## <a name="next-steps"></a>Passaggi successivi

Ora che il progetto è configurato per OpenXR e [](openxr-supported-features.md) si ha accesso agli esempi, vedere quali funzionalità sono attualmente supportate nel plug-in OpenXR.

## <a name="have-feedback"></a>Commenti e suggerimenti?

OpenXR è ancora sperimentale, quindi i commenti e i suggerimenti che è possibile inviare sono utili per migliorarlo. È possibile trovare microsoft nei [forum unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e HoloLens 2 o **Windows Mixed Reality**. 

## <a name="see-also"></a>Vedi anche

* [Configurazione del progetto senza MRTK](configure-unity-project.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
