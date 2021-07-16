---
title: Uso di Vuforia con Unity
description: Usare Vuforia per compilare Windows Mixed Reality applicazioni in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcatori, coordinate, frame di riferimento, rilevamento, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, unity, HoloLens, rilevamento dei dispositivi, modalità prestazioni, Vuforia portale per sviluppatori
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232171"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motore Vuforia con Unity

Il motore Vuforia offre una funzionalità importante per HoloLens, la possibilità di connettere esperienze ar a immagini e oggetti specifici nell'ambiente. È possibile usare questa funzionalità per sovrapporre istruzioni dettagliate guidate ai macchinari per l'azienda industriale o aggiungere funzionalità ed esperienze digitali a un prodotto fisico o a un gioco.

Il motore Vuforia offre un'ampia gamma di funzionalità e destinazioni per rendere più flessibile il processo di sviluppo ar. Una delle funzionalità più recenti, Vuforia Model Targets, è una funzionalità chiave per usi commerciali e industriali. Le destinazioni del modello consentono alle applicazioni di riconoscere oggetti fisici come macchine, automobili o giocattoli e di tenerne traccia in base a un modello CAD o 3D digitale. Per gli usi industriali, questa funzionalità può fornire agli addetti all'assemblaggio e ai tecnici del servizio le istruzioni di lavoro e le indicazioni procedurali per l'ar mentre sono in fabbrica o fuori sul campo.

Le app del motore Vuforia esistenti create per telefoni e tablet possono essere facilmente configurate in Unity per l'esecuzione HoloLens. È anche possibile usare Vuforia Engine per portare la nuova app HoloLens in Windows 10 tablet, ad esempio Surface Pro e Surface Book.


## <a name="get-the-tools"></a>Get the tools

[Installare le versioni consigliate di](../install-the-tools.md) Visual Studio e Unity e quindi configurare Unity per l'Visual Studio e l'IDE e il compilatore preferiti. 

Quando si installa Unity, assicurarsi di installare il back-end di scripting "Windows Store IL2CPP Scripting".

Aggiungere il pacchetto del motore Vuforia come descritto [qui.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Introduzione al motore Vuforia

Il punto di partenza migliore per imparare a conoscere Vuforia Engine e HoloLens è l'esempio di HoloLens [Vuforia Engine](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponibile in Unity Asset Store). L'esempio fornisce un progetto HoloLens completo che include scene preconfigurati che possono essere distribuite in un HoloLens.

Le scene mostrano come usare Vuforia Image Targets per riconoscere un'immagine e aumentarla con contenuto digitale in un'HoloLens virtuale. L'esempio di HoloLens motore Vuforia include anche una scena che mostra l'utilizzo di Destinazioni modello e VuMarks HoloLens. È possibile sostituire facilmente il proprio contenuto nelle scene per sperimentare la creazione di app HoloLens che usano il motore Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurazione di un'app Vuforia per HoloLens

Lo sviluppo di un'app Vuforia Engine HoloLens è fondamentalmente uguale allo sviluppo di app Vuforia Engine per altri dispositivi. È quindi possibile applicare le impostazioni di compilazione e le configurazioni descritte nella sezione seguente. Questo è tutto ciò che serve per consentire al motore Vuforia di funzionare con i HoloLens di rilevamento spaziale e posizionale.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilare ed eseguire l'esempio di motore Vuforia per HoloLens
1.  Scaricare [l'esempio di motore Vuforia per HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) da Unity Asset Store
2.  Applicare le [opzioni consigliate del motore unity per la potenza e le prestazioni](performance-recommendations-for-unity.md)
3.  Aggiungere le scene di esempio a **Scene** in **compilazione.**
4.  In **Build Impostazioni**(Piattaforma di compilazione) passare alla piattaforma **UWP** facendo clic **sul pulsante Add Open Scenes (Aggiungi scene** aperte).
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Selezionare il **pulsante Impostazioni** lettore.  
   * Selezionare **l'icona UWP** ed espandere la **sezione XR Impostazioni.**
   * Assicurarsi che **La realtà virtuale supportata sia** abilitata.    
   * In **SDK di realtà virtuale assicurarsi** che:
     * **Window Mixed Reality è** incluso nell'elenco e **l'opzione Abilita condivisione buffer** di profondità è abilitata. 
     * Il **formato della** profondità è impostato su profondità a **16 bit.** 
   * Assicurarsi che la **modalità di rendering stereo** sia impostata su Istanza a passaggio **singolo.**
6.  Espandere la **sezione Impostazioni** pubblicazione.
   * In **Funzionalità** assicurarsi che siano selezionate le opzioni **Client Internet, WebCam, Microfono** **e SpatialPerception.**
   * **NOTA: SpatialPerception** deve essere selezionato solo se si intende usare l'API Surface Observer.
   * In **Supported Device Families (Famiglie di dispositivi** supportate) assicurarsi che sia selezionato **Holographic.** 
7.  Espandere la **sezione Risoluzione e** presentazione.
   * Disabilitare **Esegui in background** in modo che il motore Vuforia si sospende quando l'app viene messa in background e può accedere di nuovo alla fotocamera quando l'app viene ripresa. 
   * **Nell'elenco a discesa Orientamento** predefinito verificare che sia selezionata **l'opzione Orizzontale** a sinistra.
8.  Tornare alla finestra **Compila Impostazioni** e selezionare **Compila** per generare un Visual Studio progetto.
9.  Compilare il file eseguibile Visual Studio e installarlo nel HoloLens.

## <a name="the-vuforia-developer-portal"></a>Vuforia portale per sviluppatori

Gli sviluppatori che desiderano creare esperienze di ar con Vuforia Engine e HoloLens devono iscriversi al portale per sviluppatori Vuforia [all'indirizzo developer.vuforia.com](https://developer.vuforia.com/). Nel portale gli sviluppatori hanno accesso ai [forum di Vuforia Engine](https://developer.vuforia.com/forum) in cui possono partecipare alle discussioni della community, una libreria con documentazione approfondita su tutte le funzionalità del motore Vuforia e [Vuforia Target Manager](https://developer.vuforia.com/target-manager) in cui gli utenti possono creare destinazioni personalizzate. [](https://library.vuforia.com/) Gli sviluppatori possono anche iscriversi per ottenere una licenza per sviluppatori gratuita usando [Vuforia License Manager.](https://developer.vuforia.com/license-manager)

## <a name="device-tracking-with-vuforia"></a>Rilevamento dei dispositivi con Vuforia

[Rilevamento dispositivi](https://library.vuforia.com/features/environments/device-tracker-overview.html) mantiene il rilevamento anche quando una destinazione non è più in visualizzazione. Viene abilitata automaticamente per tutte le destinazioni quando l'indicatore di dispositivo posizionale è abilitato. Per HoloLens applicazioni, Positional Device Tracker viene avviato automaticamente in Unity.

Il motore Vuforia unisce automaticamente le pose dal rilevamento della fotocamera e dal tracciamento spaziale di HoloLens per fornire posizioni di destinazione stabili indipendentemente dal fatto che la destinazione sia vista o meno dalla fotocamera.

Poiché il processo viene gestito automaticamente, non richiede alcuna programmazione da parte dello sviluppatore.


**Di seguito è riportata una descrizione di alto livello del processo:**
1. Il tracker di destinazione di Vuforia riconosce la destinazione
2. Il rilevamento di destinazione viene quindi inizializzato
3. La posizione e la rotazione della destinazione vengono analizzate per fornire una stima della posizione affidabile per il HoloLens
4. Il motore Vuforia trasforma la posizione della destinazione nello spazio delle coordinate di mapping HoloLens spaziale
5. HoloLens il rilevamento se la destinazione non è più in visualizzazione. Ogni volta che si osserva di nuovo la destinazione, Vuforia continuerà a tenere traccia delle immagini e degli oggetti in modo accurato.

Le destinazioni rilevate, ma non più visualizzate, vengono segnalate come EXTENDED_TRACKED. In questi casi, lo script DefaultTrackableEventHandler usato in tutte le destinazioni continua a eseguire il rendering del contenuto di aumento. Lo sviluppatore può controllare questo comportamento implementando uno script del gestore eventi rilevabile personalizzato.

## <a name="performance-mode-with-vuforia-engine"></a>Modalità prestazioni con il motore Vuforia 

È possibile tramite il motore Vuforia gestire le prestazioni sul HoloLens per l'estensione delle esperienze ar e ridurre il carico di lavoro nella CPU. Il motore Vuforia offre tre modalità che è possibile selezionare: predefinita, per ottimizzare la velocità e per ottimizzare la qualità. 

*   MODE_OPTIMIZE_SPEED consente di ridurre al minimo il carico di lavoro nel dispositivo HoloLens ed è ideale per l'estensione delle esperienze di ar. È consigliabile per le situazioni in cui l'app sta verificando oggetti/destinazioni statici.
*   MODE_DEFAULT è la modalità normale, che può essere usata nella maggior parte degli scenari.
*   MODE_OPTIMIZE_QUALITY è migliore per tenere traccia delle destinazioni mobili o delle destinazioni del modello che si prevede di essere prelevate.

**Impostazione della modalità**

Per modificare la modalità di prestazioni in Unity, passare a Vuforia Configuration (CTRL+MAIUSC+V/Cmd+Maiusc+V) che si trova come componente in ARCamera GameObject. 
*   Selezionare il menu a discesa per Modalità dispositivo fotocamera e selezionare una delle tre opzioni.


## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)
* [Sistemi di coordinate](../../design/coordinate-systems.md)
* [Mapping spaziale](../../design/spatial-mapping.md)
* [Fotocamera in Unity](camera-in-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentazione di Vuforia: Attività iniziali Vuforia Engine for Windows 10 Development](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Documentazione di Vuforia: Attività iniziali con Vuforia Engine in Unity](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Documentazione di Vuforia: Uso dell'esempio HoloLens in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Documentazione di Vuforia: Device Tracking in Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentazione di Vuforia: Framerate e Ottimizzazione delle prestazioni](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
