---
title: Configurare il progetto senza MRTK
description: Istruzioni sulla configurazione di un progetto Unity per la realtà mista di Windows
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni
ms.openlocfilehash: 1337001e8cc5c280c5789acbc8f10f40bca9b763
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613390"
---
# <a name="configuring-your-project-without-mrtk"></a>Configurazione del progetto senza MRTK

La realtà mista di Windows (WMR) è una piattaforma Microsoft introdotta come parte del sistema operativo Windows 10. La piattaforma WMR consente di creare applicazioni che eseguono il rendering di contenuto digitale su dispositivi di visualizzazione olografici e VR.

Microsoft e la community hanno creato strumenti opensource come il Toolkit di [realtà mista (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurerà automaticamente l'ambiente WMR, molti sviluppatori desiderano creare le proprie esperienze da zero.  Nella documentazione seguente viene illustrato come configurare correttamente un progetto per lo sviluppo di realtà mista se si utilizza MRTK o no.  Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.

> [!NOTE]
> È sempre possibile importare MRTK in un secondo momento, quindi non è necessario prima di tutto procedere con la route manuale.

Se si sceglie l'installazione manuale di WMR, le impostazioni che è necessario modificare sono suddivise in due categorie: per progetto e per scena.

## <a name="per-project-settings"></a>Impostazioni per progetto

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

Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

### <a name="for-xrsdk"></a>Per XRSDK 

1. Nell'editor di Unity passare a **Edit > Settings Project** e selezionare **XR plugin Management**

2. Selezionare **Install XR plugin Management**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-5.png)

3. Selezionare **Inizializza XR all'avvio** e **realtà mista di Windows**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-7.png)

4. Espandere la sezione **Gestione plug-in XR** e selezionare **realtà mista di Windows**
5. Selezionare tutte le caselle e impostare la **modalità di invio profondità** su **profondità a 16 bit**

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione realtà mista di Windows evidenziata](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Per la versione precedente di XR 

> [!CAUTION]
> La versione precedente di XR è deprecata in Unity 2019 ed è stata rimossa in Unity 2020.

1. Apri **Impostazioni lettore...** dalle **impostazioni di compilazione... ed espandere il gruppo di** **impostazioni di XR**
2. Nella sezione **impostazioni di XR** selezionare **realtà virtuale supportata** per aggiungere l'elenco dispositivi della realtà virtuale
3. Imposta la profondità del **formato** a **16 bit** e Abilita la **condivisione del buffer di profondità**
4. Impostare la **modalità di rendering stereo** su **istanza Single Pass**
5. Selezionare la **comunicazione remota per WSA olografica supportata** se si vuole usare la comunicazione remota olografica 

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione delle impostazioni del lettore evidenziata](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Aggiornamento del manifesto

L'app ora può gestire il rendering olografico e l'input spaziale. Tuttavia, l'app deve dichiarare le funzionalità appropriate nel manifesto per sfruttare le funzionalità specifiche. È possibile trovare le funzionalità di progetto passando a **Impostazioni lettore > impostazioni per piattaforma UWP (Universal Windows Platform) > impostazioni di pubblicazione > funzionalità**. 

È consigliabile fare in modo che le dichiarazioni di manifesto in Unity vengano incluse in tutti i progetti futuri esportati. Le funzionalità applicabili per l'abilitazione di API Unity comunemente usate per la realtà mista sono:

|  Funzionalità  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accesso ai mesh di [mapping spaziale](../../design/spatial-mapping.md) in HoloLens) &mdash; *Nessuna funzionalità necessaria per il rilevamento spaziale generale dell'auricolare* | 
|  WebCam  |  Acquisizione e VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e per usare Unity Profiler) | 

### <a name="quality-settings"></a>Impostazioni qualità

HoloLens dispone di una GPU di classe mobile. Se l'app è destinata a HoloLens, è possibile ottimizzare le impostazioni di qualità nell'app per ottenere prestazioni più rapide per garantire la massima frequenza dei fotogrammi:

1. Selezionare **modifica > impostazioni progetto > qualità**
2. Selezionare l' **elenco a discesa** sotto il logo di **Windows Store** e selezionare **molto basso**. Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con **una riga molto bassa** è verde
3. Nella sezione **Shadows** selezionare **Disabilita ombreggiatura** .

![Screenshot della finestra delle impostazioni del progetto aperta nell'editor di Unity con la sezione delle impostazioni di qualità evidenziata](images/wmr-config-img-10.png)<br>
*Impostazioni qualità Unity*

## <a name="per-scene-settings"></a>Impostazioni per scena

### <a name="unity-camera-settings"></a>Impostazioni della fotocamera Unity

Con la **realtà virtuale supportata** selezionata, il componente della [fotocamera Unity](camera-in-unity.md) gestisce il [rilevamento Head e il rendering stereoscopico](../platform-capabilities-and-apis/rendering.md). Ciò significa che non è necessario sostituire l'oggetto fotocamera principale con una fotocamera personalizzata.

Se l'app è destinata a HoloLens in modo specifico, è necessario modificare alcune impostazioni per ottimizzare la visualizzazione trasparente del dispositivo. Queste impostazioni consentono di visualizzare il contenuto olografico nel mondo fisico:

1. Nella **gerarchia** selezionare la **fotocamera principale**
2. Nel pannello **Inspector** impostare la **posizione** di trasformazione su 0, 0 **, 0,** in modo che la posizione della testa dell'utente inizi in corrispondenza dell'origine mondiale di Unity.
3. Modificare i **flag cancellati** in **colore a tinta unita**.
4. Modificare il colore di **sfondo** in **RGBA 0**, 0, 0, 0. Il nero viene visualizzato come trasparente in HoloLens.
5. Modificare i **piani di ritaglio in prossimità** del [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (contatori).

![Screenshot della scheda di controllo aperta nell'editor di Unity](images/wmr-config-img-11.png)<br>
*Impostazioni della fotocamera Unity*

> [!IMPORTANT]
> Se si elimina e si crea una nuova fotocamera, assicurarsi che la nuova fotocamera sia contrassegnata come **MainCamera**.

## <a name="next-steps"></a>Passaggi successivi

Ora che il progetto è pronto, è possibile iniziare a sviluppare l'esperienza di realtà mista:

* Aggiungi [blocchi predefiniti principali](unity-development-overview.md#2-core-building-blocks)
* Scopri le [funzionalità della piattaforma disponibili e le API](unity-development-overview.md#3-platform-capabilities-and-apis)
* Informazioni su come [distribuire l'app](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)
* Usare il [simulatore di realtà mista](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)