---
title: Invio di un'app a Microsoft Store
description: Esplora il processo di creazione di pacchetti, test e invio delle app di realtà mista al Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, visori immersivi, app, uwp, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, wack, certificazione, pacchetto, appx, visore per la realtà mista, visore per realtà mista windows, visore per realtà virtuale
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197722"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Invio di un'app a Microsoft Store

> [!IMPORTANT]
> Se si invia un'applicazione Unreal, assicurarsi di seguire le istruzioni di **[pubblicazione](../develop/unreal/unreal-publishing-to-store.md)** prima di continuare.

## <a name="prerequisites"></a>Prerequisiti

Sia [HoloLens](/hololens/hololens1-hardware) che il PC Windows 10 il visore [immersivo](../discover/immersive-headset-hardware-details.md) eseguono app universal Windows Platform. Indipendentemente dal fatto che si invii un'app che supporta HoloLens, PC o entrambi, l'invio dell'app viene [Partner Center](https://partner.microsoft.com/dashboard).

Se non si ha già un account Partner Center [](https://developer.microsoft.com/store/register) sviluppatore, iscriversi per un account prima di procedere. Altre informazioni sulle linee guida per l'invio e sugli elenchi di controllo sono disponibili in questo [articolo sugli invii di app.](/windows/uwp/publish/app-submissions)

> [!IMPORTANT]
> Non sarà possibile inviare le applicazioni al Microsoft Store se l'account Partner Center sviluppatore non supera il controllo di verifica dell'impiego. Per altri dettagli, contattare Partner Center [team](https://developer.microsoft.com/windows/support) di supporto tecnico.

## <a name="packaging-a-mixed-reality-app"></a>Creazione del pacchetto di un'app di realtà mista

Esistono diversi passaggi per creare un pacchetto di un'applicazione di realtà mista, tra cui:

* Preparazione corretta di tutti gli asset di immagine
* Scelta dell'immagine del riquadro visualizzata nel HoloLens menu Start
* Impostazione della versione minima e di Windows di destinazione per l'app
* Impostazione delle famiglie di dispositivi di destinazione nelle dipendenze dell'app
* Aggiunta di metadati per associare l'app al Microsoft Store
* Creazione di un pacchetto di caricamento

Ognuna di queste fasi di invio è illustrata nella sezione seguente. È consigliabile passarle in sequenza e non lasciarle al primo tentativo di invio.

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparare gli asset immagine inclusi in appx

Gli asset immagine seguenti sono necessari per gli strumenti di compilazione appx per compilare l'applicazione in un pacchetto appx, che è necessario per l'invio al Microsoft Store. Per altre informazioni sulle linee [guida per gli asset di riquadri e icone,](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) vedere MSDN.

| Asset obbligatorio | Scalabilità consigliata | Formato immagine | Dove viene visualizzato l'asset? | 
|----------|----------|----------|------------------|
| Logo quadrato 71x71 | Qualsiasi |  PNG | N/D | 
| Logo quadrato 150x150 | 150x150 (scala 100%) o 225x225 (scala 150%) | PNG | Pin di avvio e tutte le app (se non viene specificato 310x310), Suggerimenti per la ricerca dello Store, pagina di inserzione dello Store, Esplorazione dello Store, Ricerca store | 
|  Wide 310x150 Logo |  Qualsiasi  |  PNG  |  N/D | 
|  Logo Store |  75x75 (scala 150%)  |  PNG  |  Partner Center, App report, Scrivi una recensione, Libreria | 
|  Schermata iniziale |  930x450 (scala 150%)  |  PNG  |  Icona di avvio delle app 2D (slate) | 

Se si sta sviluppando per HoloLens, sono disponibili altri asset consigliati di cui è possibile sfruttare i vantaggi seguenti:

| Asset consigliati | Scalabilità consigliata | Dove viene visualizzato l'asset? | 
|----------|----------|----------|
|  Logo quadrato 310x310 |  310x310 (scala 150%) |  Pin di avvio e tutte le app | 

### <a name="live-tile-requirements"></a>Riquadro animato requisiti

Il menu Start in HoloLens per impostazione predefinita userà l'immagine del riquadro quadrato incluso più grande. Le app pubblicate da Microsoft hanno un'utilità di avvio 3D facoltativa, che è possibile aggiungere all'app seguendo le istruzioni di implementazione dell'icona di [avvio delle app 3D.](implementing-3d-app-launchers.md)

### <a name="specifying-target-and-minimum-version-of-windows"></a>Specifica della versione minima e di destinazione Windows

Se l'app Di realtà mista include funzionalità specifiche di una versione Windows, è importante specificare le versioni di piattaforma di destinazione e minime supportate.

**Prestare particolare attenzione per le app Windows Mixed Reality [visori immersive,](../discover/immersive-headset-hardware-details.md)che richiedono almeno il Windows 10 Fall Creators Update (10.0; Build 16299) per funzionare correttamente.**

Verrà richiesto di impostare la versione di destinazione e minima di Windows quando si crea un nuovo Windows Project universale in Visual Studio. Per i progetti esistenti, è possibile modificare questa impostazione nel menu **Project** selezionando il<Proprietà> del nome **dell'app** nella parte inferiore del menu a discesa.

![Impostazione delle versioni minime e della piattaforma di destinazione in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Impostazione delle versioni minime e della piattaforma di destinazione in Visual Studio*

### <a name="specifying-target-device-families"></a>Specifica delle famiglie di dispositivi di destinazione

Windows Mixed Reality applicazioni (per visori HoloLens e [immersive)](../discover/immersive-headset-hardware-details.md)fanno parte della piattaforma Universal Windows, quindi qualsiasi pacchetto di app con un [](/hololens/hololens1-hardware) **Windows. La famiglia** [di dispositivi di](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) destinazione universale può essere eseguita HoloLens o Windows 10 PC con visori immersivi. Se non si specifica una famiglia di dispositivi di destinazione nel manifesto dell'app, è possibile aprire inavvertitamente l'app fino a dispositivi Windows 10 non intenzionali. Seguire la procedura seguente per specificare la famiglia di dispositivi Windows 10 prevista, quindi verificare di aver impostato le famiglie di dispositivi corrette quando si carica il pacchetto [dell'app in Partner Center per Microsoft Store'invio.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Per impostare questo campo in Visual Studio, fare clic con il pulsante destro del mouse su **Package.appxmanifest** e scegliere **Visualizza** codice, quindi trovare il campo **TargetDeviceFamily Name** (Nome dispositivo di destinazione). Per impostazione predefinita, dovrebbe essere simile alla voce seguente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se si crea un'app **HoloLens,** è possibile assicurarsi che sia installata solo in HoloLens impostando la famiglia di dispositivi di destinazione **su Windows. Olografico:** 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se l'app richiede una funzionalità HoloLens 2, ad esempio il tracciamento oculare o manuale, è possibile assicurarsi che sia destinata Windows versioni 18362 o successive impostando la famiglia di dispositivi di destinazione su  **Windows. Olografico** con **MinVersion** 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Se l'app viene creata Windows Mixed Reality visori **immersive,** è possibile assicurarsi che sia installata solo nei PC Windows 10 con Windows 10 Fall Creators Update (necessario per Windows Mixed Reality) impostando la famiglia di dispositivi di destinazione su **Windows. Desktop** con **MinVersion** 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Infine, se l'app è progettata per l'esecuzione in visori immersivi **HoloLens** e **Windows Mixed Reality,** è possibile assicurarsi che l'app sia disponibile solo per queste due famiglie di dispositivi e contemporaneamente assicurarsi che ogni destinazione abbia la versione minima Windows corretta includendo una riga per ogni famiglia di dispositivi di destinazione con la rispettiva versione MinVersion:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Per altre informazioni sulla destinazione delle famiglie di dispositivi, vedere la documentazione [della piattaforma UWP TargetDeviceFamily](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associare l'app a Store

Quando si associa l'app al Microsoft Store, i valori seguenti vengono scaricati nel file manifesto dell'app locale dei progetti correnti:

* Nome visualizzato del pacchetto
* Nome pacchetto
* Publisher ID (ID editore)
* Nome visualizzato editore
* Versione

Se si esegue l'override del file package.appxmanifest predefinito con il proprio file .xml personalizzato, non è possibile associare l'app al Microsoft Store. L'associazione di un file manifesto personalizzato all'archivio restituirà un messaggio di errore.

È anche possibile testare gli scenari di acquisto e notifica andando alla soluzione Visual Studio e selezionando **Project > Store > Associa app a Store**.

### <a name="creating-an-upload-package"></a>Creazione di un pacchetto di caricamento

Seguire le linee guida in Creazione di pacchetti di app [universali Windows per Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

Il passaggio finale della creazione di un pacchetto di caricamento consiste nella convalida del pacchetto usando Windows Kit di certificazione [app.](#windows-app-certification-kit)

Se si aggiunge un pacchetto specifico HoloLens a un prodotto esistente disponibile in altre famiglie di dispositivi Windows 10, prestare attenzione a: 

* [Impatto dei numeri di versione sui pacchetti recapitati a clienti specifici](/windows/uwp/publish/package-version-numbering)
* [Modalità di distribuzione dei pacchetti in sistemi operativi diversi](/windows/uwp/publish/guidance-for-app-package-management)

Le indicazioni generali sono che il pacchetto con il numero di versione più alto per un dispositivo è quello distribuito dallo Store.

In uno scenario in cui è presente un **Windows. Pacchetto** universale e **Windows. Pacchetto olografico** e Windows. Il pacchetto universale ha un numero di versione più alto, HoloLens un utente scarica il numero di versione più alto Windows. Pacchetto universale anziché Windows. Pacchetto olografico. 

Nei casi in cui lo scenario precedente non è il risultato che si sta cercando, sono disponibili diverse soluzioni:

* Assicurarsi che i pacchetti specifici della piattaforma, ad esempio Windows. Holographic, avere sempre un numero di versione superiore rispetto ai pacchetti indipendenti dalla piattaforma, ad esempio Windows. Universale
* Non creare un pacchetto delle app come Windows. Universale se si hanno anche pacchetti specifici della piattaforma, ma creare il pacchetto Windows. Pacchetto universale per le piattaforme specifiche in cui si vuole che sia disponibile
* Creare una singola Windows. Pacchetto universale che funziona in tutte le piattaforme. Il supporto per questa opzione non è ideale al momento, quindi sono consigliate le soluzioni precedenti.

>[!NOTE]
> Per supportare l'app HoloLens (prima generazione) e HoloLen 2, è necessario caricare due pacchetti di app. una contenente x86 per HoloLens (prima generazione) e una contenente ARM o ARM64 per HoloLens 2. 
> 
> Se si includono sia ARM che ARM64 nel pacchetto, la versione ARM64 sarà quella usata in HoloLens 2. 

>[!NOTE]
> È possibile dichiarare un singolo pacchetto applicabile a più famiglie di dispositivi di destinazione

## <a name="testing-your-app"></a>Testare l'app

### <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Quando si creano pacchetti dell'app da inviare a Partner Center tramite Visual Studio, la procedura guidata Crea pacchetti dell'app richiede di eseguire il kit di certificazione app Windows per i pacchetti creati. Per un processo di invio senza problemi a Store, è necessario verificare che la copia locale dell'app superi i test del kit di certificazione app [Windows](/previous-versions/windows/apps/jj657973(v=win.10)) prima di inviarli a Store. L'esecuzione Windows Kit di certificazione app in un HoloLens remoto non è attualmente supportata.

### <a name="run-on-all-targeted-device-families"></a>Esecuzione in tutte le famiglie di dispositivi di destinazione

La Windows Universal Platform consente di creare una singola applicazione che viene eseguita in tutte le famiglie Windows 10 dispositivi. Tuttavia, non garantisce che le app universali Windows funzionino solo in tutte le famiglie di dispositivi. È importante testare [l'app](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) in ognuna delle famiglie di dispositivi scelte per garantire un'esperienza ottimale.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Invio dell'app di realtà mista a Store

Se si invia un'app di realtà mista basata su un progetto Unity, vedere prima [questo video.](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)

In generale, l'invio di un'app Windows Mixed Reality che funziona su HoloLens o visori VR immersive è come inviare qualsiasi app UWP al Microsoft Store. Dopo aver creato [l'app riservando il](/windows/uwp/publish/create-your-app-by-reserving-a-name)nome , seguire l'elenco di controllo per l'invio [della UWP.](/windows/uwp/publish/app-submissions)

Una delle prime operazioni da eseguire è selezionare una categoria e una [sottocategoria](/windows/uwp/publish/category-and-subcategory-table) per l'esperienza di realtà mista. È importante scegliere la categoria più accurata **per l'app.** Le categorie consentono di aiutare l'applicazione nelle categorie dello Store più a destra e di assicurarsi che sia visualizzata usando query di ricerca pertinenti. **L'inserimento** del titolo vr come gioco non comporta una migliore esposizione per l'app e può impedire che venga visualizzato in categorie più adattate e meno affette.

Esistono tuttavia quattro aree chiave nel processo di invio in cui è necessario effettuare selezioni specifiche della realtà mista:
1. Nella sezione **[Dichiarazioni di prodotto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** in [Proprietà](/windows/uwp/publish/enter-app-properties).
2. Nella sezione **[Requisiti di sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** in [Proprietà](/windows/uwp/publish/enter-app-properties).
3. Nella sezione **[Disponibilità della famiglia di dispositivi](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** in [Pacchetti](/windows/uwp/publish/upload-app-packages).
4. In molti dei campi **[presentazione nello Store pagina.](submitting-an-app-to-the-microsoft-store.md#store-listing-page)**

### <a name="mixed-reality-product-declarations"></a>Dichiarazioni di prodotti di realtà mista

Nella pagina **[Proprietà](/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella **[sezione Dichiarazioni del](/windows/uwp/publish/app-declarations)** prodotto.

![Dichiarazioni di prodotti di realtà mista](images/product-declarations-900px.png)<br>
Dichiarazioni di prodotti di realtà mista

In primo luogo, devi identificare i tipi di dispositivi per cui l'app offre un'esperienza di realtà mista. L'identificazione dei tipi di dispositivo garantisce che l'app sia inclusa Windows Mixed Reality raccolte nello Store.

Accanto a "Questa esperienza è progettata per Windows Mixed Reality su:"
* Seleziona la **casella PC** se l'app offre un'esperienza di realtà virtuale quando un visore VR immersive è connesso al PC dell'utente. È consigliabile selezionare questa casella se l'app è impostata per l'esecuzione esclusivamente su un visore VR immersive o se si tratta di un gioco o un'app per PC standard che offre una modalità di realtà mista o contenuti bonus quando un visore VR è connesso.
* Selezionare la **HoloLens** solo se l'app offre un'esperienza olografica quando viene eseguita in HoloLens.
* Selezionare **entrambe le** caselle se l'app offre un'esperienza di realtà mista in entrambi i tipi di dispositivi.

Se hai selezionato "PC" sopra, dovrai impostare la "Configurazione di Realtà mista" (livello di attività). Questo vale solo per le esperienze di realtà mista eseguite su PC connessi a visori VR immersive, perché le app di realtà mista in HoloLens sono su scala globale e l'utente non definisce un limite durante la configurazione.
* Scegliere **Seated + standing se** l'app è stata progettata in modo che l'utente rimanga in una posizione. Ad esempio, in un gioco in cui si ha il controllo di un pannello di controllo dell'aereo.
* Scegliere **Tutte le esperienze** se l'app è progettata con l'intenzione che l'utente passi all'interno di un limite definito durante l'installazione. Ad esempio, potrebbe essere un gioco in cui si è affiancati e si evitano attacchi.

### <a name="mixed-reality-system-requirements"></a>Requisiti di sistema di Realtà mista

Nella pagina **[Proprietà](/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella **[sezione Requisiti di](/windows/uwp/publish/enter-app-properties#system-requirements)** sistema.

![Requisiti di sistema](images/system-reqs-800px.png)<br>
Requisiti di sistema

In questa sezione si identificheranno l'hardware minimo (obbligatorio) e l'hardware consigliato (facoltativo) per l'app di realtà mista.

**Hardware di input:**

Usare le caselle di controllo per  indicare ai potenziali clienti se l'app supporta il microfono per [l'input](../design/voice-input.md)vocale, il controller Xbox o **[il game pad](../discover/hardware-accessories.md#bluetooth-gamepads)** o Windows Mixed Reality controller del **[movimento.](../design/motion-controllers.md)** Queste informazioni verranno visualizzate nella pagina dei dettagli del prodotto dell'app nello Store e saranno utili per includere l'app nelle raccolte di app/giochi appropriate. Ad esempio, può esistere una raccolta per tutti i giochi che supportano controller del movimento.

È consigliabile selezionare le caselle di controllo per "hardware minimo" o "hardware consigliato" per i tipi di input. 

Ad esempio: 
* Se il gioco richiede controller del movimento, ma accetta l'input vocale tramite microfono, selezionare la casella di controllo "Hardware minimo" accanto a "Controller del movimento Windows Mixed Reality", ma la casella di controllo "Hardware consigliato" accanto a "Microfono". 
* Se il gioco può essere riprodotto con un controller Xbox, un game pad o un controller del movimento, è possibile selezionare la casella di controllo "hardware minimo" accanto a "Controller Xbox o game pad" e selezionare la casella di controllo "Hardware consigliato" accanto a "Controller del movimento Windows Mixed Reality" poiché i controller del movimento offriranno probabilmente un'esperienza di passaggio dal game pad.

**Windows Mixed Reality visore VR immersive:**

Indicare se è necessario un visore VR immersive per usare l'app o è facoltativo, è fondamentale per la soddisfazione e l'istruzione dei clienti.

Se l'app può *essere usata* solo tramite un visore VR immersive, selezionare la casella di controllo "Hardware minimo" accanto a "Windows Mixed Reality visore VR immersive". Questo verrà visualizzato nella pagina dei dettagli del prodotto dell'app nello Store sotto forma di avviso sopra il pulsante di acquisto, in modo che i clienti non pensino di acquistare un'app che funzionerà nel PC come un'app desktop tradizionale.

Se l'app viene eseguita sul desktop come un'app per PC tradizionale, ma offre un'esperienza di realtà virtuale quando è connesso un visore VR immersive (indipendentemente dal fatto che il contenuto completo dell'app sia disponibile o solo una parte), selezionare la casella di controllo "Hardware consigliato" accanto a "visore VR immersive Windows Mixed Reality". Non verrà visualizzato alcun avviso sopra il pulsante di acquisto nella pagina dei dettagli del prodotto dell'app se l'app funziona come un'app desktop tradizionale senza visore VR immersive connesso.

**Specifiche del PC:**

Se si vuole che l'app raggiunga il maggior numero possibile di Windows Mixed Reality visori VR [immersive,](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) scegliere come destinazione le specifiche del PC per i PC Windows Mixed Reality con [grafica integrata.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

Indipendentemente dal fatto che l'app di realtà mista sia destinata ai requisiti minimi del PC Windows Mixed Reality o che debba una configurazione pc specifica, ad esempio la GPU dedicata di un [PC Windows Mixed Reality Ultra](), è necessario aggiungere le specifiche del PC pertinenti nella colonna https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines "hardware minimo".

Se l'app realtà mista è progettata per migliorare le prestazioni o offre grafica a risoluzione più elevata in una particolare configurazione pc o scheda grafica, è necessario includere le specifiche del PC pertinenti nella colonna "hardware consigliato".

Questo vale solo se l'app realtà mista usa un visore VR immersive connesso a un PC. Se l'app realtà mista viene eseguita solo HoloLens, non sarà necessario indicare le specifiche del PC perché HoloLens ha una sola configurazione hardware.

### <a name="device-family-availability"></a>Disponibilità famiglia di dispositivi

Se [l'app è stata](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in pacchetto correttamente in Visual Studio, caricarla nella pagina Pacchetti dovrebbe produrre una tabella con le famiglie di dispositivi disponibili.

![Tabella di disponibilità della famiglia di dispositivi](images/device-family-table-900px.png)<br>
Tabella di disponibilità della famiglia di dispositivi

Se l'app realtà mista funziona con visori VR immersive, nella tabella deve essere selezionato almeno "Windows 10 Desktop". Se l'app realtà mista funziona HoloLens, è necessario selezionare almeno "Windows 10 Holographic". Se l'app viene eseguita in Windows Mixed Reality visori VR, devono essere selezionati sia "Windows 10 Desktop" che "Windows 10 Holographic".

>[!TIP]
>Molti sviluppatori si verificano errori durante il caricamento del pacchetto dell'app correlato a mancata corrispondenza tra il manifesto del pacchetto e le informazioni sull'account dell'app o dell'editore in Partner Center. Questi errori spesso possono essere evitati accedendo a Visual Studio con lo stesso account associato all'account per sviluppatore di Windows (quello usato per accedere Partner Center). Se si usa lo stesso account, sarà possibile associare l'app alla relativa identità nel Microsoft Store prima di creare il pacchetto.

![Associare l'app al Microsoft Store](images/associate-your-app-700px.png)<br>
Associare l'app al Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>presentazione nello Store pagina

Nella pagina [presentazione nello Store](/windows/uwp/publish/create-app-store-listings) del processo di invio dell'app è possibile aggiungere informazioni utili sull'app di realtà mista in diversi punti.

>[!IMPORTANT]
>Per assicurarsi che l'app sia categorizzata correttamente dallo Store e resa individuabile ai clienti di Windows Mixed Reality, è necessario aggiungere **"Windows Mixed Reality"** come uno dei termini di ricerca per l'app (è possibile trovare i termini di ricerca espandendo la sezione "Campi condivisi").

![Aggiungere Windows Mixed Reality ai termini di ricerca](images/search-terms-800px.png)<br>
Aggiungere "Windows Mixed Reality" ai termini di ricerca

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Offerta di una versione di valutazione gratuita per il gioco o l'app

In molti casi, i consumer non avranno alcuna esperienza con la realtà virtuale prima di acquistare un visore VR Windows Mixed Reality immersive. Potrebbe non sapere cosa aspettarsi da giochi intensi o avere familiarità con la propria soglia di comfort nelle esperienze immersive. Molti clienti possono anche provare un visore VR immersive Windows Mixed Reality su PC senza badge [Windows Mixed Reality.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) Per queste considerazioni, è consigliabile offrire una versione di valutazione [gratuita](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) per l'app o il gioco di realtà mista a pagamento.

## <a name="see-also"></a>Vedi anche
* [Che cos'è la realtà mista?](../discover/mixed-reality.md)
* [Cenni preliminari sullo sviluppo](../develop/development.md)
* [Visualizzazioni delle app](../design/app-views.md)
* [Informazioni sulle prestazioni per la realtà mista](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Prestazioni Consigli per Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Test dell'app in HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality linee guida minime per la compatibilità hardware del PC](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)