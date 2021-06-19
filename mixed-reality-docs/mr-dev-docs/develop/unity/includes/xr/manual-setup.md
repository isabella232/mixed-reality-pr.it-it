---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394585"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool. Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:

![Finestra dei pacchetti dello strumento di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Impostazione della destinazione di compilazione

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1. Selezionare **Impostazioni > file...**
2. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3. Impostare **Architettura** su **ARM 64**
4. Impostare **Dispositivo di destinazione** su **HoloLens**
5. Impostare **Tipo di compilazione** su **D3D**
6. Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurazione della gestione dei plug-in XR per OpenXR

Per impostare OpenXR come runtime in Unity:

1. Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**
2. Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**
3. Selezionare le **caselle Inizializza XR all'avvio** **e OpenXR**
4. Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens **set di funzionalità**

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

Se stai sviluppando per HoloLens 2, passa a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori per le app).

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

> [!IMPORTANT]
> Se viene visualizzata un'icona di avviso gialla accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare. Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.  Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Progetti di esempio Unity per OpenXR e HoloLens 2

Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architettura** su **ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:

1. Nell'editor di Unity passare a **Edit > Project settings (Modifica impostazioni progetto)** e selezionare **XR Plugin Management (Gestione plug-in XR)**

2. Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)**

![Screenshot della finestra Project Settings (Impostazioni progetto) aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. Selezionare Initialize XR on Startup (Inizializza **XR all'avvio)** **Windows Mixed Reality**

![Screenshot della finestra Delle impostazioni del progetto aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. Espandere la **sezione XR Plug-in Management (Gestione plug-in XR)** e selezionare **la scheda Univeral Windows Platform Settings (Impostazioni piattaforma Windows univeral)**
5. Se si usa Unity 2020 o versione successiva, verranno visualizzati i controlli **OpenXR** **o Windows Mixed Reality**. 
    * È possibile scegliere uno dei due runtime.  Se si sviluppa specificamente per il HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR,** selezionare la casella OpenXR ed esaminare la guida Uso del plug-in [OpenXR](../../openxr-getting-started.md) di Realtà mista per Unity per configurare correttamente questi dispositivi prima di tornare a questa esercitazione

> [!NOTE]
> A partire da Unity 2020 LTS, Microsoft sta iniziando lo sviluppo con OpenXR.  Durante la migrazione a questo percorso, in Unity 2021.1 il plug-in Windows XR verrà deprecato e rimosso nella versione 2021.2 rendendo OpenXR l'unico percorso supportato. Per altre informazioni, vedere [Using the Mixed Reality OpenXR plugin (Uso del plug-in OpenXR di Realtà mista).](../../openxr-getting-started.md)

6. Se si decide di scegliere il **plug-Windows Mixed Reality,** selezionare tutte le caselle e impostare Modalità di invio **profondità** **su Depth 16 Bit (Profondità 16 bit)**

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architettura** su **ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

> [!CAUTION]
> XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.

1. Aprire **Player Settings (Impostazioni lettore)** da Build Settings **(Impostazioni di compilazione) ed** espandere il **gruppo XR Settings (Impostazioni XR)**
2. Nella sezione **XR Settings (Impostazioni XR)** selezionare **Virtual Reality Supported (Realtà virtuale supportata)** per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)
3. Impostare **Depth Format (Formato profondità)** su **Depth (Profondità) a 16 bit** e abilitare Depth Buffer Sharing **(Condivisione buffer di profondità)**
4. Impostare **La modalità di rendering stereo** su Istanza a passaggio **singolo**
5. Selezionare **WSA Holographic Remoting Supported** se si desidera usare holographic remoting 

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con la sezione Player settings (Impostazioni lettore) evidenziata](../../images/wmr-config-img-9.png)