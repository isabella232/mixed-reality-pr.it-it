---
title: Invio di un'app a Microsoft Store
description: Esplora il processo di creazione di pacchetti, test e invio di app per realtà mista al Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, cuffie immersive, app, UWP, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, predato, certificazione, pacchetto, appx, merchandising, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: b5d25817afeb2d8d970d329c802b7eaabcdf7f35
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703117"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Invio di un'app a Microsoft Store

Sia [HoloLens](../hololens-hardware-details.md) che il PC Windows 10 che alimentano le [cuffie immersive](../discover/immersive-headset-hardware-details.md) eseguono piattaforma UWP (Universal Windows Platform) app. Se si sta inviando un'app che supporta HoloLens, PC o entrambi, l'invio dell'app passa attraverso il centro per i [partner](https://partner.microsoft.com/dashboard).

Se non si dispone già di un account per sviluppatore del centro per i partner, [iscriversi](https://developer.microsoft.com/store/register) a uno prima di procedere.

## <a name="packaging-a-mixed-reality-app"></a>Creazione del pacchetto di un'app per realtà mista

Sono disponibili diversi passaggi per la creazione di pacchetti di un'applicazione di realtà mista, tra cui:

* Preparazione corretta di tutti gli asset immagine
* Scelta dell'immagine del riquadro visualizzata nel menu di avvio di HoloLens
* Impostazione della versione di destinazione e della versione minima di Windows per l'app
* Impostazione delle famiglie di dispositivi di destinazione nelle dipendenze dell'app
* Aggiunta di metadati per associare l'app al Microsoft Store
* Creazione di un pacchetto di caricamento

Ognuna di queste fasi di invio è illustrata nella sezione seguente: si consiglia di esaminarle in modo sequenziale. non è possibile uscire dal primo tentativo di invio.

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparare le risorse dell'immagine incluse nel appx

Gli asset immagine seguenti sono necessari per gli strumenti di compilazione appx per compilare l'applicazione in un pacchetto appx, che è necessario per l'invio al Microsoft Store. Sono disponibili altre informazioni sulle [linee guida per le risorse di Tile e icone](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) in MSDN.

| Asset obbligatorio | Scala consigliata | Formato immagine | Dove viene visualizzato l'asset? | 
|----------|----------|----------|------------------|
| Logo quadrato 71x71 | Qualsiasi |  PNG | N/D | 
| Logo quadrato 150x150 | 150x150 (100% scala) o 225x225 (150% scala) | PNG | Start pin e tutte le app (se non è specificato 310x310), archiviare i suggerimenti di ricerca, la pagina di presentazione del negozio, l'esplorazione del negozio, la ricerca nel negozio | 
|  Logo 310x150 Wide |  Qualsiasi  |  PNG  |  N/D | 
|  Logo Store |  75x75 (150% di scalabilità)  |  PNG  |  Centro per i partner, app report, Scrivi una recensione, raccolta personale | 
|  Schermata iniziale |  930x450 (150% di scalabilità)  |  PNG  |  utilità di avvio app 2D (Slate) | 

Se si sta sviluppando per HoloLens, sono disponibili altre risorse consigliate che è possibile sfruttare:

| Asset consigliati | Scala consigliata | Dove viene visualizzato l'asset? | 
|----------|----------|----------|
|  Logo quadrato 310x310 |  310x310 (150% di scalabilità) |  Avvia pin e tutte le app | 

### <a name="live-tile-requirements"></a>Requisiti dei riquadri animati

Per impostazione predefinita, il menu Start in HoloLens utilizzerà l'immagine del riquadro quadrato più grande inclusa. Le app pubblicate da Microsoft hanno un utilità di avvio 3D opzionale, che è possibile aggiungere all'app seguendo le istruzioni di [implementazione dell'utilità di avvio delle app 3D](implementing-3d-app-launchers.md) .

### <a name="specifying-target-and-minimum-version-of-windows"></a>Specifica della destinazione e della versione minima di Windows

Se l'app per la realtà mista include funzionalità specifiche di una versione di Windows, è importante specificare la destinazione supportata e le versioni minime della piattaforma.

**Prestare particolare attenzione alle app destinate a [auricolari immersivi di Windows per realtà mista](../discover/immersive-headset-hardware-details.md), che richiedono almeno Windows 10 Fall Creators Update (10,0; Compilazione 16299) per il corretto funzionamento.**

Quando si crea un nuovo progetto di Windows universale in Visual Studio, verrà richiesto di impostare la versione di destinazione e la versione minima di Windows. Per i progetti esistenti, è possibile modificare questa impostazione nel menu **progetto** selezionando il **<le proprietà del> del nome dell'app** nella parte inferiore del menu a discesa.

![Impostazione delle versioni minime e della piattaforma di destinazione in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Impostazione delle versioni minime e della piattaforma di destinazione in Visual Studio*

### <a name="specifying-target-device-families"></a>Specifica delle famiglie di dispositivi di destinazione

Le applicazioni di realtà mista di Windows (sia per [HoloLens](../hololens-hardware-details.md) che per [auricolari immersivi](../discover/immersive-headset-hardware-details.md)) fanno parte del piattaforma UWP (Universal Windows Platform), quindi qualsiasi pacchetto dell'app con una [famiglia di dispositivi di destinazione](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) **Windows. universale** può essere eseguito su PC HoloLens o Windows 10 con auricolari immersivi. Se non si specifica una famiglia di dispositivi di destinazione nel manifesto dell'applicazione, è possibile aprire inavvertitamente l'app fino a dispositivi Windows 10 non intenzionali. Attenersi alla procedura seguente per specificare la famiglia di dispositivi Windows 10 desiderata, quindi [verificare che le famiglie di dispositivi corrette siano impostate quando si carica il pacchetto dell'app nel centro partner per Microsoft Store l'invio.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Per impostare questo campo in Visual Studio, fare clic con il pulsante destro del mouse su **Package. appxmanifest** e selezionare **Visualizza codice**, quindi trovare il campo **nome TargetDeviceFamily** . Per impostazione predefinita, l'aspetto dovrebbe essere simile al seguente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se si sta creando un'app **HoloLens** , è possibile assicurarsi che sia installata solo in HoloLens impostando il gruppo di dispositivi di destinazione su **Windows. olografico**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Se l'app richiede la funzionalità **HoloLens 2** , ad esempio Eye o hand-Tracking, è possibile assicurarsi che sia destinata a windows versione 18362 o successiva impostando il gruppo di dispositivi di destinazione su **Windows. olografico** con **MinVersion** di 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Se l'app viene creata per **auricolari immersivi di Windows**, è possibile assicurarsi che sia installata solo nei PC Windows 10 con Windows 10 Fall Creators Update (necessario per la realtà mista di Windows) impostando la famiglia di dispositivi di destinazione su **Windows. desktop** con **MinVersion** di 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Infine, se l'app è progettata per l'esecuzione sia in **HoloLens** che in modalità **mista di Windows**, è possibile verificare che l'app sia disponibile solo per queste due famiglie di dispositivi e che ogni destinazione disponga della versione minima di Windows corretta includendo una riga per ogni famiglia di dispositivi di destinazione con la rispettiva MinVersion:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Per altre informazioni sulla destinazione delle famiglie di dispositivi, vedere la [documentazione di TARGETDEVICEFAMILY UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associare l'app allo Store

Quando si associa l'app alla Microsoft Store, i valori seguenti vengono scaricati nel file manifesto dell'app locale del progetto corrente:

* Nome visualizzato del pacchetto
* Nome pacchetto
* Publisher ID (ID editore)
* Nome visualizzato editore
* Versione

Se si sta eseguendo l'override del file Package. appxmanifest predefinito con un file con estensione XML personalizzato, non è possibile associare l'app al Microsoft Store. L'associazione di un file manifesto personalizzato con l'archivio comporterà un messaggio di errore.

Per testare gli scenari di acquisto e di notifica, è anche possibile passare alla soluzione Visual Studio e selezionare **Project > store > associare l'app allo Store**.

### <a name="creating-an-upload-package"></a>Creazione di un pacchetto di caricamento

Seguire le linee guida per la creazione [di pacchetti di app di Windows universale per Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

Il passaggio finale della creazione di un pacchetto di caricamento consiste nel convalidare il pacchetto con il [Kit di certificazione applicazioni Windows](#windows-app-certification-kit).

Se si aggiunge un pacchetto specifico di HoloLens a un prodotto esistente disponibile in altre famiglie di dispositivi Windows 10, prestare attenzione a: 

* [In che modo i numeri di versione possono avere un effetto sui pacchetti distribuiti a clienti specifici](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)
* [Modalità di distribuzione dei pacchetti a diversi sistemi operativi](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)

Il materiale sussidiario generale è che il pacchetto con il numero di versione più alto per un dispositivo è quello distribuito dallo Store.

In uno scenario in cui è presente un pacchetto **Windows. Universal** e un pacchetto **Windows. olografico** e il pacchetto Windows. Universal ha un numero di versione superiore, un utente di HoloLens scaricherà il numero di versione superiore del pacchetto Windows. Universal anziché il pacchetto Windows. olografico. 

Nei casi in cui lo scenario precedente non è il risultato che si sta cercando, esistono diverse soluzioni disponibili:

* Assicurarsi che i pacchetti specifici della piattaforma, ad esempio Windows. olografica, abbiano sempre un numero di versione superiore rispetto a quello dei pacchetti indipendenti dalla piattaforma come Windows. Universal
* Non creare pacchetti di app come Windows. universali se sono presenti anche pacchetti specifici della piattaforma, ma creare un pacchetto del pacchetto Windows. Universal per le piattaforme specifiche in cui si vuole che sia disponibile
* Creare un singolo pacchetto Windows. Universal che funziona in tutte le piattaforme. Il supporto per questa opzione non è attualmente eccezionale, quindi sono consigliate le soluzioni precedenti.

>[!NOTE]
> Per supportare l'app in HoloLens (1st Gen) e HoloLen 2, è necessario caricare due pacchetti dell'app; una contenente x86 per HoloLens (1a generazione) e una contenente ARM o ARM64 per HoloLens 2. 
> 
> Se nel pacchetto si includono sia ARM che ARM64, la versione di ARM64 sarà quella usata in HoloLens 2. 

>[!NOTE]
> È possibile dichiarare un singolo pacchetto da applicare a più famiglie di dispositivi di destinazione

## <a name="testing-your-app"></a>Testare l'app

### <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Quando si creano pacchetti di app da inviare al centro per i partner tramite Visual Studio, la procedura guidata crea pacchetti dell'applicazione richiede di eseguire il kit di certificazione app Windows in base ai pacchetti che vengono creati. Per avere un processo di invio uniforme allo Store, è consigliabile verificare che la copia locale dell'app superi i test del [Kit di certificazione applicazioni Windows](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) prima di inviarli allo Store. L'esecuzione del kit di certificazione app Windows in un HoloLens remoto non è attualmente supportata.

### <a name="run-on-all-targeted-device-families"></a>Esegui in tutte le famiglie di dispositivi di destinazione

La piattaforma universale di Windows consente di creare una singola applicazione che può essere eseguita in tutte le famiglie di dispositivi Windows 10. Tuttavia, non garantisce che le app di Windows universale funzioneranno solo su tutte le famiglie di dispositivi. È importante [testare l'app](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) in ognuna delle famiglie di dispositivi selezionate per garantire un'esperienza ottimale.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Invio dell'app per la realtà mista allo Store

Se si sta inviando un'app realtà mista basata su un progetto Unity, vedere prima questo [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) .

In generale, l'invio di un'app di realtà mista Windows che funziona su HoloLens e/o cuffie immersive è proprio come l'invio di qualsiasi app UWP al Microsoft Store. Dopo aver [creato l'app riservando il nome](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), seguire l'elenco di [controllo](https://docs.microsoft.com/windows/uwp/publish/app-submissions)per l'invio di UWP.

Una delle prime operazioni da eseguire è [selezionare una categoria e una sottocategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) per l'esperienza di realtà mista. È importante **scegliere la categoria più accurata per l'app**. Le categorie consentono di commercializzare l'applicazione nelle categorie dei negozi appropriati e di assicurarsi che venga visualizzata usando le query di ricerca pertinenti. **Elencare il titolo di VR come gioco non comporta una migliore esposizione per l'app** e può impedire che venga visualizzato in categorie più adatte e meno affollate.

Tuttavia, nel processo di invio sono presenti quattro aree principali in cui si desidera effettuare selezioni specifiche per la realtà mista:
1. Nella sezione delle **[dichiarazioni di prodotto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** in [Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Nella sezione **[requisiti di sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** in [Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. Nella sezione relativa alla **[disponibilità della famiglia di dispositivi](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** in [pacchetti](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. In diversi campi della **[pagina di elenco dei negozi](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Dichiarazioni di prodotti di realtà mista

Nella pagina delle **[Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella sezione relativa alle **[dichiarazioni di prodotti](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** .

![Dichiarazioni di prodotti di realtà mista](images/product-declarations-900px.png)<br>
Dichiarazioni di prodotti di realtà mista

In primo luogo, è necessario identificare i tipi di dispositivi per i quali l'app offre un'esperienza di realtà mista. L'identificazione dei tipi di dispositivo garantisce che l'app sia inclusa nelle raccolte di realtà miste di Windows nell'archivio.

Accanto a "questa esperienza è progettata per la realtà mista di Windows in:"
* Controllare la casella **PC** se l'app offre un'esperienza VR quando un headset immersivo è connesso al PC dell'utente. Si consiglia di selezionare questa casella di controllo se l'app è impostata per l'esecuzione esclusivamente su un dispositivo headset immersivo o se si tratta di un'app o di un gioco per PC standard che offre una modalità di realtà mista e/o un contenuto bonus quando si connette una cuffia.
* Controllare la casella **HoloLens** solo se l'app offre un'esperienza olografica quando viene eseguita in HoloLens.
* Controllare **entrambe** le caselle se l'app offre un'esperienza di realtà mista in entrambi i tipi di dispositivo.

Se è stato selezionato "PC" in precedenza, è necessario impostare la "configurazione della realtà mista" (livello di attività). Questo vale solo per le esperienze di realtà miste eseguite su PC connessi a auricolari immersivi, in quanto le app di realtà mista in HoloLens sono a livello globale e l'utente non definisce un limite durante l'installazione.
* Se l'app è stata progettata per fare in modo che l'utente resti in un'unica posizione, scegliere **seduto + in piedi** . Ad esempio, in un gioco in cui è possibile controllare il pozzetto di un aeromobile.
* Scegliere **tutte le esperienze** se l'app è progettata con l'intenzione di aggirare l'utente all'interno di un limite impostato definito durante l'installazione. Ad esempio, potrebbe trattarsi di un gioco in cui si esegue il passaggio e l'anatra per schivare gli attacchi.

### <a name="mixed-reality-system-requirements"></a>Requisiti di sistema per la realtà mista

Nella pagina delle **[Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella sezione **[requisiti di sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisiti di sistema](images/system-reqs-800px.png)<br>
Requisiti di sistema

In questa sezione si identificherà l'hardware minimo (obbligatorio) e l'hardware consigliato (facoltativo) per l'app realtà mista.

**Hardware di input:**

Usare le caselle di controllo per indicare ai potenziali clienti se l'app supporta il **microfono** per l' [input vocale](../design/voice-input.md)), il **[controller Xbox o gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)** e/o i **[controller di movimento della realtà mista di Windows](../design/motion-controllers.md)**. Queste informazioni verranno riportate nella pagina dei dettagli del prodotto dell'app nello Store e aiuteranno l'app a essere inclusa nelle raccolte di giochi/app appropriate. È ad esempio possibile che esista una raccolta per tutti i giochi che supportano i controller di movimento.

Si consiglia di selezionare le caselle di controllo per "hardware minimo" o "hardware consigliato" per i tipi di input. 

Ad esempio: 
* Se il gioco richiede controller di movimento, ma accetta l'input vocale tramite microfono, selezionare la casella di controllo "hardware minimo" accanto a "controller di movimento per la realtà mista di Windows", ma la casella di controllo "hardware consigliato" accanto a "microfono". 
* Se è possibile riprodurre il gioco con un controller Xbox, un gamepad o un controller di movimento, è possibile selezionare la casella di controllo "hardware minimo" accanto a "controller Xbox o gamepad" e selezionare la casella di controllo "hardware consigliato" accanto a "controller di movimento per la realtà mista di Windows". i controller di movimento offriranno probabilmente un passo avanti nell'esperienza del gamepad.

**Cuffia mista a realtà mista di Windows:**

Che indica se è necessaria una cuffia immersiva per usare l'app o è facoltativa, è essenziale per la soddisfazione e la formazione dei clienti.

Se l'app può essere usata *solo* tramite un auricolare immersivo, selezionare la casella di controllo "hardware minimo" accanto a "Windows Mixed Reality Full-headset". Questa operazione verrà rilevata nella pagina dei dettagli del prodotto dell'app in Store come un avviso sopra il pulsante Purchase, in modo che i clienti non stiano acquistando un'app che funzionerà nel PC come un'app desktop tradizionale.

Se l'app viene eseguita sul desktop come un'app per PC tradizionale, ma offre un'esperienza di VR quando è connesso un headset immersivo (se il contenuto completo dell'app è disponibile o solo una parte), selezionare la casella di controllo "hardware consigliato" accanto a "Windows Mixed Reality Full-headset". Non verrà visualizzato alcun avviso sopra il pulsante Acquista nella pagina dei dettagli del prodotto dell'app se l'app funziona come un'app desktop tradizionale senza una cuffia a immersione connessa.

**Specifiche del PC:**

Se si vuole che l'app raggiunga il maggior numero possibile di utenti con cuffie immersive di Windows miste, definire come [destinazione](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) le specifiche del PC per i [PC con la realtà mista di Windows con grafica integrata](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Se l'app per la realtà mista è destinata ai requisiti minimi del PC Windows Mixed Reality o richiede una configurazione specifica del PC, ad esempio la GPU dedicata di un [Windows realtà Ultra PC] ( https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines , è necessario aggiungere le specifiche del PC rilevanti nella colonna "hardware minimo".

Se l'app per la realtà mista è progettata per migliorare le prestazioni o offre grafica a risoluzione superiore in una particolare configurazione PC o scheda grafica, è necessario includere le specifiche del PC rilevanti nella colonna "hardware consigliato".

Questa opzione si applica solo se l'app per la realtà mista Usa un headset immersivo connesso a un PC. Se l'app per la realtà mista viene eseguita solo su HoloLens, non è necessario indicare le specifiche del PC perché HoloLens ha una sola configurazione hardware.

### <a name="device-family-availability"></a>Disponibilità famiglia di dispositivi

Se [l'app è stata assemblata correttamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio, è necessario caricarla nella pagina pacchetti per produrre una tabella con le famiglie di dispositivi disponibili.

![Tabella di disponibilità della famiglia di dispositivi](images/device-family-table-900px.png)<br>
Tabella di disponibilità della famiglia di dispositivi

Se l'app per la realtà mista funziona con auricolari immersivi, è necessario selezionare almeno "Windows 10 desktop" nella tabella. Se l'app per la realtà mista funziona in HoloLens, è necessario selezionare almeno "Windows 10 olografico". Se l'app è in esecuzione in entrambi i tipi di cuffie di realtà mista di Windows, è necessario selezionare sia "Windows 10 desktop" sia "Windows 10 olografico".

>[!TIP]
>Molti sviluppatori si verificano errori durante il caricamento del pacchetto dell'app correlato a mancate corrispondenze tra il manifesto del pacchetto e le informazioni sull'account dell'editore o dell'app nel centro per i partner. Questi errori possono spesso essere evitati accedendo a Visual Studio con lo stesso account associato all'account per sviluppatore di Windows (quello usato per accedere al centro per i partner). Se si usa lo stesso account, sarà possibile associare l'app alla relativa identità nella Microsoft Store prima di eseguirne il pacchetto.

![Associare l'app al Microsoft Store](images/associate-your-app-700px.png)<br>
Associare l'app al Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Pagina di inserzione dello Store

Nella pagina di presentazione dello [Store](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) del processo di invio dell'app è possibile aggiungere informazioni utili sull'app per realtà mista.

>[!IMPORTANT]
>Per assicurarsi che l'app sia categorizzata correttamente dallo Store e resa individuabile per i clienti con realtà mista di Windows, è necessario aggiungere **"realtà mista di Windows"** come uno dei "termini di ricerca" per l'app (è possibile trovare i termini di ricerca espandendo la sezione "campi condivisi").

![Aggiungere la realtà mista di Windows ai termini di ricerca](images/search-terms-800px.png)<br>
Aggiungere "realtà mista di Windows" ai termini di ricerca

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Offerta di una versione di valutazione gratuita per il gioco o l'app

In molti casi, gli utenti non avranno alcuna esperienza con la realtà virtuale prima di acquistare una cuffia mista a realtà mista di Windows. Potrebbero non sapere cosa aspettarsi da giochi intensi o avere familiarità con la loro soglia di comfort in esperienze immersive. Molti clienti possono anche provare a usare un auricolare immersivo a realtà mista di Windows nei PC che non sono associati ai PC con la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). A causa di queste considerazioni, è consigliabile valutare la possibilità di offrire una [versione di valutazione gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) per l'app o il gioco in realtà mista a pagamento.

## <a name="see-also"></a>Vedere anche
* [Che cos'è Realtà mista?](../discover/mixed-reality.md)
* [Cenni preliminari sullo sviluppo](../develop/development.md)
* [Visualizzazioni delle app](../design/app-views.md)
* [Informazioni sulle prestazioni per la realtà mista](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Suggerimenti sulle prestazioni per Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Test dell'app in HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
