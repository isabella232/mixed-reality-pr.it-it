---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535933"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool. Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Platform Support **(Supporto** piattaforma):

![Finestra dei pacchetti degli strumenti di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Impostazione della destinazione di compilazione

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1. Selezionare **Impostazioni > file...**
2. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3. Impostare **Architecture** (Architettura) su **ARM64**
4. Impostare **Dispositivo di destinazione** su **HoloLens**
5. Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6. Impostare **Versione SDK di destinazione** su Più recente **installato**

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurazione della gestione dei plug-in XR per OpenXR

Per impostare OpenXR come runtime in Unity:

1. Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**
2. Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**
3. Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)** se viene visualizzata ![ la schermata della finestra Project Settings (Impostazioni progetto) aperta nell'editor unity con XR Plugin management (Gestione plug-in XR) evidenziato](../../images/wmr-config-img-5.png)
4. Selezionare la **casella Initialize XR on Startup (Inizializza XR all'avvio)**
5. Se la destinazione è Desktop VR, rimanere nella scheda PC autonomo (monitor) e selezionare le caselle **OpenXR** e **Windows Mixed Reality set di funzionalità**
6. Se la destinazione HoloLens 2, passare alla scheda piattaforma UWP (Universal Windows Platform) (logo Windows) e selezionare le caselle **OpenXR** e **Microsoft HoloLens set di funzionalità**

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Se viene visualizzata un'icona di avviso gialla accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare. Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Se stai sviluppando per HoloLens 2, seleziona la voce di menu **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori dell'app).

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.  Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Progetti di esempio Unity per OpenXR e HoloLens 2

Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.

In caso contrario, se si è pronti per iniziare da un progetto vuoto, passare all'articolo [Configurazione della fotocamera.](../../camera-in-unity.md)

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> Il plug-in Windows XR è deprecato in Unity 2021.1 e verrà rimosso in Unity 2021.2.  Per lo sviluppo di Unity 2020, Microsoft consiglia invece il plug-in OpenXR.

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architecture** (Architettura) su **ARM64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6.  Impostare **Versione SDK di destinazione** su Più recente **installato**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:

1. Nell'editor di Unity passare a **Edit > Project settings (Modifica impostazioni progetto)** e selezionare **XR Plugin Management (Gestione plug-in XR)**

2. Selezionare **Install XR Plugin Management (Installa gestione plug-in XR),** se visualizzato

![Screenshot della finestra Project Settings (Impostazioni progetto) aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. Selezionare Initialize XR on Startup (Inizializza **XR all'avvio)** **Windows Mixed Reality**

![Screenshot della finestra Delle impostazioni del progetto aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. Selezionare la **sezione Gestione plug-in XR Windows Mixed Reality,** selezionare tutte le caselle e impostare Depth Buffer Format (Formato buffer profondità) su  >   Depth Buffer **16 Bit (Buffer profondità a 16 bit)** 

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

> [!CAUTION]
> XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Selezionare **Impostazioni > file...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**
3.  Impostare **Architecture** (Architettura) su **ARM64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6.  Impostare **Versione SDK di destinazione** su Più recente **installato**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

1. Aprire **Player Settings (Impostazioni lettore)** da Build Settings **(Impostazioni compilazione) ed** espandere il **gruppo XR Settings (Impostazioni XR)**
2. Nella sezione **XR Settings (Impostazioni XR)** selezionare **Virtual Reality Supported (Realtà virtuale supportata)** per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)
3. Impostare **Depth Format (Formato profondità)** su **16 bit depth (Profondità 16 bit)** e **selezionare Enable Depth Buffer Sharing (Abilita condivisione buffer di profondità)**
4. Impostare **Stereo Rendering Mode** (Modalità di rendering stereo) su **Single Pass Instanced** (Istanze a singolo passaggio)
5. Selezionare **WSA Holographic Remoting Supported se** si desidera usare la comunicazione remota in modalità di riproduzione olografica

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con la sezione Player settings (Impostazioni lettore) evidenziata](../../images/wmr-config-img-9.png)
