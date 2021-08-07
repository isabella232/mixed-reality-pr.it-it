---
title: Configurare il progetto senza MRTK
description: Informazioni su come configurare un nuovo progetto Unity per Windows Mixed Reality senza l'Toolkit.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realtà mista, sviluppo, introduzione, nuovo progetto, Windows Mixed Reality, UWP, XR, prestazioni
ms.openlocfilehash: 85f8dee3208ce2c2a3bd328641544cbba0525cabdd1bf99404065572aeb354cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210984"
---
# <a name="configuring-your-project-without-mrtk"></a>Configurazione del progetto senza MRTK

Windows Mixed Reality (WMR) è una piattaforma Microsoft introdotta come parte del Windows 10 operativo. La piattaforma WMR consente di creare applicazioni che eseguono il rendering di contenuto digitale su dispositivi di visualizzazione olografici e VR.

Anche se Microsoft e la community hanno creato strumenti di open source come [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) che configurano automaticamente l'ambiente WMR, molti sviluppatori vogliono creare le proprie esperienze da zero.  La documentazione seguente illustra come configurare correttamente un progetto per lo sviluppo di realtà mista indipendentemente dal fatto che si utilizzi o meno MRTK.  Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.

> [!NOTE]
> È sempre possibile importare MRTK in un secondo momento, in modo da non intasare prima la route manuale.

Se si sceglie la configurazione manuale di WMR, le impostazioni che è necessario modificare sono suddivise in due categorie: per progetto e per scena.

## <a name="per-project-settings"></a>Impostazioni per progetto

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra build Impostazioni aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare alla piattaforma Windows universali:

1.  Selezionare **File > Compilazione Impostazioni...**
2.  Selezionare **Universal Windows Platform nell'elenco** Platform (Piattaforma) e selezionare Switch Platform **(Cambia piattaforma)**
3.  Impostare **Architettura** su **ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**
7.  Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug

![Screenshot della finestra Build Impostazioni aperta nell'editor di Unity con universal Windows Platform evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

### <a name="for-xrsdk"></a>Per XRSDK 

1. Nell'editor di Unity passare a **Edit > Project settings (> Project impostazioni)** e selezionare **XR Plugin Management (Gestione plug-in XR).**

2. Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)**

![Screenshot della finestra Project Impostazioni aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-5.png)

3. Selezionare **Initialize XR on Startup (Inizializza XR all'avvio)** **Windows Mixed Reality**

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-7.png)

4. Espandere la **sezione XR Plug-in Management (Gestione plug-in XR)** e selezionare **univeral Windows Platform Impostazioni** scheda
5. Se si usa Unity 2020 o versione successiva, verranno visualizzati i controlli **OpenXR** **o Windows Mixed Reality**. 
    * È possibile scegliere uno dei due runtime.  Se si sviluppa specificamente per il HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR,** selezionare la casella OpenXR ed esaminare la guida Using [the Mixed Reality OpenXR Plugin for Unity](./xr-project-setup.md) (Uso del plug-in OpenXR di Realtà mista per Unity) per configurare correttamente questi dispositivi prima di tornare a questa esercitazione

> [!NOTE]
> A partire da Unity 2020 LTS, Microsoft sta iniziando lo sviluppo con OpenXR.  Durante la migrazione a questo percorso, in Unity 2021.1 il plug-in Windows XR verrà deprecato e rimosso nella versione 2021.2 rendendo OpenXR l'unico percorso supportato. Per altre informazioni, vedere [Using the Mixed Reality OpenXR plugin (Uso del plug-in OpenXR di Realtà mista).](./xr-project-setup.md)

6. Se si decide di scegliere il **plug-Windows Mixed Reality,** selezionare tutte le caselle e impostare Modalità di invio **profondità** **su Depth 16 Bit (Profondità 16 bit)**

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Per XR legacy 

> [!CAUTION]
> XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.

1. Aprire **Player Impostazioni...** dalla finestra **di Impostazioni... ed** espandere il **gruppo di Impostazioni XR**
2. Nella sezione **XR Impostazioni** selezionare **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)
3. Impostare **Depth Format (Formato profondità)** su **Depth (Profondità) a 16 bit** e abilitare Depth Buffer Sharing **(Condivisione buffer di profondità)**
4. Impostare **La modalità di rendering stereo** su Istanza a passaggio **singolo**
5. Selezionare **WSA Holographic Remoting Supported** se si desidera usare holographic remoting 

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con la sezione Player settings evidenziata](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Aggiornamento del manifesto

L'app può ora gestire il rendering olografico e l'input spaziale. Tuttavia, l'app deve dichiarare le funzionalità appropriate nel manifesto per sfruttare determinate funzionalità. Per trovare le funzionalità dei progetti, vedere Player Impostazioni > Impostazioni for Universal Windows Platform > Publishing Impostazioni > Capabilities (Player Impostazioni > Impostazioni per universal Windows Platform > Publishing Impostazioni > Capabilities (Funzionalità di pubblicazione **Impostazioni >).** 

È consigliabile creare le dichiarazioni del manifesto in Unity per includerle in tutti i progetti futuri esportati. Le funzionalità applicabili per abilitare le API Unity di uso comune per la realtà mista sono:

|  Funzionalità  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accesso alle mesh [di mapping](../../design/spatial-mapping.md) spaziale in HoloLens) Non è necessaria alcuna funzionalità per il rilevamento spaziale generale &mdash; *del visore VR* | 
|  Webcam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione di audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e per usare il profiler Unity) | 

### <a name="quality-settings"></a>Impostazioni di qualità

HoloLens ha una GPU di classe mobile. Se l'app è HoloLens, è necessario iniziare con le impostazioni di qualità nell'app ottimizzate per ottenere prestazioni più veloci per garantire la massima frequenza dei fotogrammi.  Dopo aver seguito ulteriormente lo sviluppo, è possibile valutare la possibilità di migliorare le impostazioni di qualità per trovare il giusto equilibrio tra qualità e prestazioni: 

1. Selezionare **Modifica > Project Impostazioni > qualità** 
2. Selezionare **l'elenco** a  **discesa sotto il** logo Windows Store e selezionare Molto    **basso.** Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e la riga Very Low (Molto bassa) è verde 
3. Nella sezione **Shadows**   (Ombreggiature) selezionare **Disable Shadows (Disabilita ombreggiature)** 

![Screenshot della finestra Project impostazioni aperte nell'editor di Unity con la sezione delle impostazioni di qualità evidenziata](images/wmr-config-img-10.png)<br>
*Impostazioni di qualità di Unity*

## <a name="per-scene-settings"></a>Impostazioni per scena

### <a name="unity-camera-settings"></a>Impostazioni della fotocamera Unity

Con **l'opzione Virtual Reality Supported** (Realtà virtuale supportata) selezionata, il componente Unity [Camera](camera-in-unity.md) gestisce il rilevamento della testa e il [rendering stereoscopico.](../platform-capabilities-and-apis/rendering.md) Ciò significa che non è necessario sostituire l'oggetto Main Camera con una fotocamera personalizzata.

Se l'app è HoloLens, è necessario modificare alcune impostazioni per ottimizzare gli schermi trasparenti del dispositivo. Queste impostazioni consentono la visualizzazione del contenuto olografico nel mondo fisico:

1. Nella **gerarchia** selezionare la **fotocamera principale**
2. Nel pannello **Inspector** (Controllo) imposta la posizione della trasformazione su  **0, 0, 0** in modo che la posizione della testa dell'utente inizi dall'origine del mondo Unity.
3. Impostare **Clear Flags (Cancella flag)** **su Solid Color (Colore a tinta unita).**
4. Modificare il **colore di** sfondo **in RGBA 0,0,0,0**. Il nero viene visualizzato come trasparente in HoloLens.
5. Modificare **i piani di ritaglio: vicino** alla HoloLens 0,85 (metri) consigliati. [](camera-in-unity.md#using-clipping-planes)

![Screenshot della scheda inspector aperta nell'editor di Unity](images/wmr-config-img-11.png)<br>
*Impostazioni della fotocamera unity*

> [!IMPORTANT]
> Se si elimina e si crea una nuova fotocamera, assicurarsi che la nuova fotocamera sia contrassegnata come **MainCamera.**

## <a name="next-steps"></a>Passaggi successivi

Ora che il progetto è pronto, è possibile iniziare a sviluppare l'esperienza di realtà mista:

* Aggiungere [blocchi predefiniti principali](unity-development-overview.md#2-core-building-blocks)
* Vedere le API [e le funzionalità della piattaforma disponibili](unity-development-overview.md#3-advanced-features)
* Informazioni su come [distribuire l'app](../platform-capabilities-and-apis/using-visual-studio.md#)
* Usare il [simulatore di realtà mista](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)