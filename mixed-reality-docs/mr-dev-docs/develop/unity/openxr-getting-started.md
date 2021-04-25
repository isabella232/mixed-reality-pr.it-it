---
title: Uso del plug-in OpenXR di realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR di Realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: 4c220deeca13c6807857375b71640207823b94ed
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944662"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Uso del plug-in OpenXR di realtà mista per Unity

A partire da Unity versione 2020.2, il pacchetto di plug-in OpenXR di Realtà mista di Microsoft è disponibile tramite mixed [reality feature tool.](welcome-to-mr-feature-tool.md)

## <a name="prerequisites"></a>Prerequisiti

* Unity 2020.3 LTS o versione successiva
* Plug-in Unity OpenXR 1.1.1 o versione successiva
* Visual Studio 2019 o versione successiva
* Installare il supporto della piattaforma **UWP** in Unity per HoloLens 2 app

> [!NOTE]
> Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario. Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Configurare il progetto con MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool. Seguire le [istruzioni di installazione e utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:

![Finestra dei pacchetti dello strumento di funzionalità di realtà mista con il plug-in xr aperto evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Impostazione della destinazione di compilazione

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architecture (Architettura)** **su ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

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
> Se viene visualizzata un'icona di avviso rossa accanto al **plug-in OpenXR,** fare clic sull'icona e selezionare **Correggi tutto** prima di continuare. Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.  Passare alla sezione successiva per informazioni su come usare gli esempi OpenXR.

## <a name="try-out-the-unity-sample-scenes"></a>Provare le scene di esempio di Unity

### <a name="hololens-2-samples"></a>HoloLens 2 esempi

1. Nell'editor di Unity passare a **Finestra > Gestione pacchetti**
2. Nell'elenco dei pacchetti selezionare **Mixed Reality OpenXR Plugin**
3. Individuare l'esempio **nell'elenco Esempi** e selezionare **Importa**

![Screenshot di Unity Gestione pacchetti aperto nell'editor unity con il plug-in OpenXR di realtà mista selezionato e il pulsante di importazione degli esempi evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Quando un pacchetto viene aggiornato, Unity offre la possibilità di aggiornare gli esempi importati.  L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e agli asset associati.

## <a name="using-mrtk-with-openxr-support"></a>Uso di MRTK con il supporto OpenXR

MRTK-Unity supporta il plug-in OpenXR di realtà mista a partire dalla versione 2.5.3.

1. Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto. Il supporto openXR è nel **pacchetto Foundation.**
2. Passare allo script del componente MixedReality Toolkit in Inspector e passare al **profilo DefaultOpenXRConfigurationProfile:**

    ![Screenshot del cambio della configurazione MRTK nel componente Mixed Reality Toolkit nel controllo](images/openxr-img-11.png)

    1. Per informazioni più dettagliate sulla [migrazione a OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK.

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
