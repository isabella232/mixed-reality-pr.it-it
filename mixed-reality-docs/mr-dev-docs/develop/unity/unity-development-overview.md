---
title: Sviluppo di Unity per HoloLens
description: Introduzione alla creazione di app di realtà mista in Unity e HoloLens con il percorso di checkpoint dedicato.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realtà mista, sviluppo, guida introduttiva, nuovo progetto, porting, funzionalità, fotocamera, simulazione, emulazione, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, che cos'è la realtà virtuale, che cos'è la realtà aumentata, MRTK, mixed reality toolkit, mapping spaziale, input vocale, fotocamera individuabile, emulatore, Azure, esercitazioni
ms.openlocfilehash: 52c6fb57473255e440d9c2f795cc228cca44ea32
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982784"
---
# <a name="unity-development-for-hololens"></a>Sviluppo di Unity per HoloLens

![Logo banner di Unity](../images/unity_logo_banner.png)

La soluzione più veloce per creare un'[app di realtà mista](../../design/app-views.md) per HoloLens in [Unity](https://unity.com) è rappresentata da Mixed Reality Toolkit. Se si usa Unity per la prima volta, prima di continuare è consigliabile esplorare le [esercitazioni](https://unity3d.com/learn/tutorials) di livello principiante nella piattaforma Unity Learn. È opportuno anche visitare l'[Asset Store](https://assetstore.unity.com) completo e i [forum sulla realtà mista per Unity](https://forum.unity3d.com/forums/hololens.102/) per partecipare alla community online impegnata nella creazione di app di realtà mista. In questi ambienti si scoprono spesso risorse o soluzioni estremamente interessanti. Per iniziare a usare MRTK, passare ai checkpoint di sviluppo illustrati di seguito.

> [!IMPORTANT]
> Se si ha a disposizione un progetto Unity da trasferire in HoloLens 2, consultare le **[guide per il porting](../porting-apps/porting-overview.md)** . Sono disponibili guide per i progetti che usano HTK, MRTK V1 o SteamVR.

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista. Se non è stata ancora esplorata l'[applicazione di esempio Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), è consigliabile scaricarla e usarla per acquisire familiarità con i concetti di base dell'esperienza utente in realtà mista.

## <a name="1-getting-started"></a>1. Guida introduttiva

Il modo più semplice per sviluppare in Unity è quello di usare Mixed Reality Toolkit. MRTK consentirà di configurare automaticamente un progetto per la realtà mista e fornirà un set di funzionalità utili per accelerare il processo di sviluppo. Alla fine di questa sezione, si avrà una conoscenza di base su Mixed Reality Toolkit, un ambiente di sviluppo configurato correttamente per le app di realtà mista e un progetto MRTK funzionante in Unity creato dall'utente.

|  Checkpoint  |  Risultato  |
| --- | --- |
| [Che cos'è MRTK?](mrtk-getting-started.md) | Per iniziare, acquisire familiarità con Mixed Reality Toolkit e imparare a conoscere i vantaggi che offre |
| [Installare gli strumenti più recenti](../install-the-tools.md) | Scaricare e installare il pacchetto Unity più recente e configurare il progetto per la realtà mista |
| [Serie di esercitazioni su HoloLens 2](tutorials/mr-learning-base-01.md) | Seguire le esercitazioni su MRTK di livello principiante per l'hardware HoloLens 2 |
| Scaricare **facoltativamente** [lo strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md) | Un nuovo strumento di sviluppo per l'individuazione, l'aggiornamento e l'aggiunta di pacchetti di funzionalità di realtà mista ai progetti Unity |

> [!IMPORTANT]
> Se vuoi creare un nuovo progetto Unity senza importare Mixed Reality Toolkit, devi modificare manualmente un piccolo set di impostazioni di Unity per Windows Mixed Reality. Le impostazioni sono suddivise in due categorie: per progetto e per scena. Per la procedura dettagliata, vedere la [guida alla configurazione](configure-unity-project.md).

> [!NOTE]
> Dopo aver configurato MRTK V2 nel progetto, gli oggetti di gioco Unity standard, ad esempio la fotocamera, si illumineranno immediatamente per un'esperienza da seduti. Per istruzioni sulla modifica della scala di esperienza dell'applicazione, vedere la pagina relativa ai [sistemi di coordinate](coordinate-systems-in-unity.md).

## <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Tutti i componenti di base per le applicazioni di realtà mista sono esposti in modo coerente con altre API di Unity Questi blocchi predefiniti sono disponibili come funzionalità autonome e tramite il Mixed Reality Toolkit. Potrebbero non essere tutti necessari nell'immediato, ma è bene esaminarli nella fase iniziale. Dopo aver esaminato i blocchi predefiniti fondamentali indicati di seguito, si avrà a disposizione un insieme completo di funzionalità da integrare in un progetto di realtà mista autonomamente o tramite MRTK.

[!INCLUDE[](../includes/unity-building-blocks.md)]

## <a name="3-advanced-features"></a>3. Funzionalità avanzate

Altre funzionalità chiave per le applicazioni di realtà mista sono disponibili tramite le API di Unity senza la necessità di ulteriori pacchetti o configurazioni. Queste funzionalità possono essere aggiunte ai progetti Unity anche senza aver installato MRTK. Dopo aver esaminato le funzionalità più avanzate offerte da Unity, sarà possibile creare app di realtà mista più complesse.

|  Funzionalità  |  Capabilities  |
| --- | --- |
| [Esperienze condivise](shared-experiences-in-unity.md) | Visualizzare e interagire collettivamente con lo stesso ologramma in un punto fisso nello spazio usando la condivisione degli ancoraggi nello spazio |
| [Fotocamera individuabile](locatable-camera-in-unity.md) | Acquisire foto e contenuti video nell'applicazione di realtà mista |
| [Punto di interesse](focus-point-in-unity.md) | Suggerire a HoloLens il modo ottimale per eseguire la stabilizzazione degli ologrammi attualmente visualizzati |
| [Perdita del tracciamento](tracking-loss-in-unity.md) | Gestire gli scenari in cui il dispositivo non è in grado di individuare la propria posizione nello spazio globale dell'applicazione |
| [Input da tastiera](keyboard-input-in-unity.md) | Ottenere input nelle app da tastiere reali e di realtà mista |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. Distribuzione in un dispositivo o un emulatore

Non appena il progetto Unity olografico è pronto per il test, il passaggio successivo è quello di esportare e compilare una soluzione Unity di Visual Studio. Con questa soluzione di Visual Studio è possibile eseguire l'applicazione in uno dei tre modi seguenti, usando un dispositivo reale o simulato. Al termine di questa sezione, sarà possibile distribuire l'applicazione in qualsiasi dispositivo o emulatore in base alle esigenze di sviluppo.

* [Visore VR immersive di HoloLens o Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulatore di visore VR immersive di Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. Aggiunta di servizi

A questo punto del percorso di sviluppo, potrebbe essere necessario aggiungere servizi o ricevere supporto per una distribuzione commerciale. L'integrazione di [Servizi cloud di Azure](../mixed-reality-cloud-services.md) e funzionalità di Dynamics 365 può migliorare notevolmente i progetti. Sono stati definiti alcuni punti di partenza per consentire di esplorare e ampliare le conoscenze relative alla realtà mista.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

È anche disponibile un [elenco completo della documentazione di supporto per altri servizi di Azure](../mixed-reality-cloud-services.md#standalone-unity-services) che è possibile aggiungere ai progetti Unity in modo autonomo.

## <a name="whats-next"></a>Passaggi successivi

Il lavoro degli sviluppatori non finisce mai, soprattutto per quanto riguarda la conoscenza di nuovi strumenti o SDK. Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati. Questi argomenti e queste risorse non sono presentati in ordine sequenziale e possono quindi essere esplorati liberamente.

### <a name="porting"></a>Conversione

Se si hanno a disposizione app di cui si vuole eseguire la conversione, sarà utile consultare gli articoli elencati di seguito:

* [Da HoloToolkit/MRTK a MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [Guida alla conversione per le app Immersive](../porting-apps/porting-guides.md)
* [Guida al porting dell'input](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Esercitazioni

Se si cerca di aggiungere specifiche funzionalità di realtà mista alle applicazioni, sono disponibili diverse esercitazioni dedicate in grado di illustrare la procedura end-to-end. Di seguito sono elencati i contenuti più richiesti relativi a HoloLens 2 e HoloLens (prima generazione). È tuttavia possibile consultare l'intera raccolta visitando la pagina relativa alla panoramica delle esercitazioni.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Risorse aggiuntive

Prima di entrare nel mondo della realtà mista in totale autonomia, è consigliabile esaminare la documentazione relativa a MRTK riportata di seguito. Questi articoli costituiscono punti di partenza ottimali per comprendere il funzionamento di MRTK in modo più dettagliato e forniscono informazioni approfondite per migliorare le prestazioni dell'app.

|  Argomento  |  Descrizione  |
| --- | --- |
| [Panoramica dell'architettura MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/architecture/overview) | Acquisire una conoscenza più approfondita del funzionamento di MRTK SDK nei progetti |
| [Impostazioni e prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | Profilare l'app, aggiornare le impostazioni di Unity e ottenere le migliori prestazioni di stabilizzazione olografica disponibili |
| [Introduzione a MRTK + XR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Eseguire il trasferimento alla pipeline XR alternativa fornita da Unity |

### <a name="unity-resources"></a>Risorse di Unity

Oltre a questa documentazione disponibile in docs.microsoft.com, è disponibile la documentazione di Unity relativa alle funzionalità di Windows Mixed Reality, che viene installata insieme all'editor di Unity. La documentazione fornita da Unity include due sezioni distinte.

|  Risorsa  |  Descrizione  |
| --- | --- |
| [Informazioni di riferimento sullo scripting](https://docs.unity3d.com/ScriptReference/) | Questa sezione della documentazione contiene i dettagli dell'API di scripting fornita da Unity. È accessibile online dall'editor di Unity facendo clic su **Help > Scripting Reference** (Guida > Riferimento scripting) |
| [Manuale](https://docs.unity3d.com/Manual/index.html) | Questo manuale è stato progettato per facilitare l'utente nel processo di apprendimento di Unity, dalle tecniche di base a quelle più avanzate. È accessibile online oppure dall'editor di Unity facendo clic su **Help > Manual** (Guida > Manuale) |

> [!div class="nextstepaction"]
> [Esplora MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>Per inviare suggerimenti,

È possibile contattare gli sviluppatori Microsoft nei [forum Unity](https://aka.ms/unityforums) contrassegnando con un tag **Microsoft** e una combinazione dei tag seguenti per specificare a quale plug-in fa riferimento il feedback fornito:

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* XR legacy 

## <a name="see-also"></a>Vedere anche

* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Nozioni di base MR 100: Introduzione a Unity](tutorials/holograms-100.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modalità di gioco Unity](unity-play-mode.md)
* [Guide alla conversione](../porting-apps/porting-guides.md)