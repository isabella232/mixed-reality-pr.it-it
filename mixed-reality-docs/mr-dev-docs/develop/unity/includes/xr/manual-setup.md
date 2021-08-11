---
ms.openlocfilehash: c5276943bab0ddc961342f879c0cf4f8986aa7b4f67b16c9c8b5415ca6fc58fd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202717"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool. Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto **plug-in OpenXR di realtà** mista nella categoria **Supporto** piattaforma:

![Finestra pacchetti dello strumento di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>Impostazione della destinazione di compilazione

Se si usa desktop VR come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se si ha come destinazione HoloLens 2, è necessario passare alla piattaforma Windows universali:

1. Selezionare **File > build Impostazioni...**
2. Selezionare **Universal Windows Platform** nell'elenco Piattaforma e selezionare Cambia **piattaforma**
3. Impostare **Architecture** (Architettura) su **ARM64**
4. Impostare **Dispositivo di destinazione** su **HoloLens**
5. Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6. Impostare **Versione SDK di destinazione** su Versione più recente **installata**

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con Universal Windows Platform evidenziata](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>Configurazione di Gestione plug-in XR per OpenXR

Per impostare OpenXR come runtime in Unity:

1. Nell'editor di Unity passare a **Modifica > Project Impostazioni**
2. Nell'elenco di Impostazioni selezionare **Gestione plug-in XR** (dovrebbe essere già installato se è stato installato il plug-in OpenXR di realtà mista con MRFT)
3. Selezionare la **casella Inizializza XR all'avvio**
4. Se la destinazione è Desktop VR, rimanere nella scheda PC autonomo (monitor) e selezionare le caselle **OpenXR** **e Windows Mixed Reality set di funzionalità**
5. Se la destinazione HoloLens 2, passare alla scheda Universal Windows Platform (logo Windows) e selezionare le caselle **OpenXR** e **Microsoft HoloLens feature set**

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con la gestione dei plug-in XR evidenziata](../../images/openxr-img-05.png)

> [!IMPORTANT]
> Se viene visualizzata un'icona di avviso gialla accanto al **plug-in OpenXR,** fare clic sull'icona e selezionare **Correggi tutto** prima di continuare. Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

Se si sta sviluppando per HoloLens 2, selezionare la voce > Project > Applica impostazioni di progetto consigliate per HoloLens 2 **menu** per migliorare le prestazioni dell'app.

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.  Passare alla sezione successiva per informazioni su come usare gli esempi OpenXR.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Progetti di esempio Unity per OpenXR e HoloLens 2

Vedere il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti unity di esempio che illustrano come compilare applicazioni Unity per visori HoloLens 2 o realtà mista usando il plug-in OpenXR di realtà mista.

In caso contrario, se si è pronti per iniziare da un progetto vuoto, passare [all'articolo Configurazione della](../../camera-in-unity.md) fotocamera.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

> [!CAUTION]
> Il Windows plug-in XR è deprecato in Unity 2021.1 e verrà rimosso in Unity 2021.2.  Per lo sviluppo di Unity 2020, Microsoft consiglia invece il plug-in OpenXR.

Se si usa desktop VR come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se si ha come destinazione HoloLens 2, è necessario passare alla piattaforma Windows universali:

1.  Selezionare **File > build Impostazioni...**
2.  Selezionare **Universal Windows Platform** nell'elenco Piattaforma e selezionare Cambia **piattaforma**
3.  Impostare **Architecture** (Architettura) su **ARM64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6.  Impostare **Versione SDK di destinazione** su Versione più recente **installata**
7.  Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con Universal Windows Platform evidenziata](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity informazioni per creare una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:

1. Nell'editor unity passare a Modifica **impostazioni > Project e** selezionare Gestione **plug-in XR**

2. Selezionare Install XR Plugin Management (Installa **gestione plug-in XR)** se viene visualizzato

![Screenshot della finestra Project Impostazioni aperta nell'editor unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. Selezionare **Inizializza XR all'avvio** **e Windows Mixed Reality**

![Screenshot della finestra Project impostazioni aperte nell'editor unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. Selezionare la **sezione Gestione plug-in XR** Windows Mixed Reality, selezionare tutte le caselle e impostare Formato buffer di profondità su Buffer di profondità  >   a **16 bit** 

![Screenshot della finestra Project impostazioni aperte nell'editor unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

> [!CAUTION]
> Legacy XR è deprecato in Unity 2019 e rimosso in Unity 2020.

Se si usa desktop VR come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

Se si ha come destinazione HoloLens 2, è necessario passare alla piattaforma Windows universali:

1.  Selezionare **File > build Impostazioni...**
2.  Selezionare **Universal Windows Platform** nell'elenco Piattaforma e selezionare Cambia **piattaforma**
3.  Impostare **Architecture** (Architettura) su **ARM64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
6.  Impostare **Versione SDK di destinazione** su Versione più recente **installata**
7.  Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug

![Screenshot della finestra Build Impostazioni aperta nell'editor unity con Universal Windows Platform evidenziata](../../images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity informazioni per creare una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

1. Aprire **Player Impostazioni...** dal menu **Compila Impostazioni... finestra** ed espandere il **gruppo di Impostazioni XR**
2. Nella sezione **XR Impostazioni** selezionare **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)
3. Impostare **Formato profondità su** profondità a **16 bit** e selezionare Abilita condivisione buffer di **profondità**
4. Impostare **Stereo Rendering Mode** (Modalità di rendering stereo) su **Single Pass Instanced** (Istanze a singolo passaggio)
5. Selezionare **WSA Holographic Remoting Supported se** si desidera usare la comunicazione remota in modalità di riproduzione olografica

![Screenshot della finestra Project impostazioni aperte nell'editor unity con la sezione Impostazioni lettore evidenziata](../../images/wmr-config-img-9.png)
