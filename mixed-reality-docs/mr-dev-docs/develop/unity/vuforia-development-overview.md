---
title: Uso di Vuforia con Unity
description: Usare Vuforia per creare applicazioni di realtà miste Windows in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, marcatori, coordinate, frame di riferimento, rilevamento, cuffia a realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, Unity, HoloLens, rilevamento dei dispositivi, modalità prestazioni, portale per sviluppatori Vuforia
ms.openlocfilehash: ecacf4036bfab38eb90782a194c445a83ca623ba
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010562"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motore Vuforia con Unity

Il motore Vuforia offre una funzionalità importante per HoloLens: la potenza di connettere le esperienze AR a immagini e oggetti specifici nell'ambiente. È possibile usare questa funzionalità per sovrapporre istruzioni dettagliate guidate sui macchinari per l'azienda industriale o aggiungere funzionalità e esperienze digitali a un prodotto o gioco fisico.

Il motore Vuforia offre un'ampia gamma di funzionalità e destinazioni per rendere più flessibile il processo di sviluppo AR. Una delle funzionalità più recenti, Vuforia Model targets, è una funzionalità chiave per usi sia commerciali che industriali. Le destinazioni dei modelli consentono alle applicazioni di riconoscere oggetti fisici, ad esempio computer, automobili o giocattoli, e di tenerne traccia in base a un modello CAD o digitale 3D. Per gli usi industriali, questa funzionalità può fornire agli addetti agli assembly e ai tecnici del servizio le istruzioni di lavoro AR e le linee guida procedurali in fabbrica o nel campo.

Le app esistenti del motore Vuforia compilate per telefoni e tablet possono essere facilmente configurate in Unity per l'esecuzione in HoloLens. È anche possibile usare il motore Vuforia per portare la nuova app HoloLens a Tablet Windows 10, ad esempio Surface Pro e Surface book.


## <a name="get-the-tools"></a>Get the tools

[Installare le versioni consigliate](../install-the-tools.md) di Visual Studio e Unity, quindi configurare Unity per l'uso di Visual Studio e dell'IDE e del compilatore preferiti. 

Quando si installa Unity, assicurarsi di installare il "back-end di scripting di Windows Store IL2CPP".

Aggiungere il pacchetto del motore Vuforia come descritto [qui.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Introduzione al motore Vuforia

Il punto di partenza migliore per conoscere il motore Vuforia e HoloLens è l' [esempio HoloLens Engine Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponibile in Unity Asset Store). L'esempio fornisce un progetto HoloLens completo che include scene preconfigurate che possono essere distribuite in un HoloLens.

Le scene illustrano come usare le destinazioni delle immagini Vuforia per riconoscere un'immagine e aumentarla con contenuto digitale in un'esperienza HoloLens. L'esempio HoloLens del motore Vuforia include anche una scena che mostra l'utilizzo delle destinazioni dei modelli e di VuMarks in HoloLens. È possibile sostituire facilmente il proprio contenuto nelle scene per sperimentare la creazione di app HoloLens che usano il motore Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurazione di un'app Vuforia per HoloLens

Lo sviluppo di un'app del motore Vuforia per HoloLens è fondamentalmente lo stesso dello sviluppo di app del motore Vuforia per altri dispositivi. È quindi possibile applicare le impostazioni e le configurazioni di compilazione descritte nella sezione seguente. Questo è tutto ciò che serve per consentire al motore Vuforia di funzionare con il mapping spaziale HoloLens e i sistemi di rilevamento posizionale.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilare ed eseguire l'esempio di motore Vuforia per HoloLens
1.  Scaricare l' [esempio di motore Vuforia per HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) da Unity Asset Store
2.  Applicare le [Opzioni consigliate del motore Unity per l'alimentazione e le prestazioni](performance-recommendations-for-unity.md)
3.  Aggiungere le scene di esempio alle **scene** nella **compilazione.**
4.  In **impostazioni di compilazione** cambiare piattaforma di compilazione in **UWP** facendo clic sul pulsante **Aggiungi scene aperte** .
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Selezionare il pulsante **Impostazioni lettore** .  
   * Selezionare l'icona **UWP** ed espandere la sezione **impostazioni di XR** .
   * Verificare che la **realtà virtuale supportata** sia abilitata.    
   * In **Virtual Reality SDK** verificare che:
     * La **realtà mista della finestra** è inclusa nell'elenco e l' **Abilitazione** della condivisione del buffer di profondità è abilitata. 
     * Il **formato di profondità** è impostato sulla **profondità a 16 bit.** 
   * Verificare che la **modalità di rendering stereo** sia impostata su **Single Pass instanced.**
6.  Espandere la sezione **impostazioni di pubblicazione** .
   * In **funzionalità** verificare che siano selezionati **client Internet, webcam, microfoni** e **SpatialPerception** .
   * **Nota:** è consigliabile selezionare SpatialPerception solo se si intende usare l'API Observer di Surface.
   * In **gruppi di dispositivi supportati** verificare che sia selezionato **olografico** . 
7.  Espandere la sezione **risoluzione e presentazione** .
   * Disabilitare l' **esecuzione in background in** modo che il motore Vuforia si sospenda quando l'app viene messa in background e può accedere nuovamente alla fotocamera quando l'app viene ripresa. 
   * Nell'elenco a discesa **orientamento predefinito** assicurarsi che sia selezionato **Landscape Left** .
8.  Tornare alla finestra **impostazioni di compilazione** e selezionare **Compila** per generare un progetto di Visual Studio.
9.  Compilare il file eseguibile da Visual Studio e installarlo nella HoloLens.

## <a name="the-vuforia-developer-portal"></a>Portale per sviluppatori Vuforia

Gli sviluppatori che desiderano creare le proprie esperienze AR con il motore Vuforia e HoloLens devono iscriversi nel portale per sviluppatori Vuforia in [Developer.Vuforia.com](https://developer.vuforia.com/). Nel portale gli sviluppatori hanno accesso ai forum del [motore Vuforia](https://developer.vuforia.com/forum) , in cui possono partecipare a discussioni della community, una [libreria](https://library.vuforia.com/) con una documentazione dettagliata su tutte le funzionalità del motore Vuforia e la [gestione di destinazione Vuforia](https://developer.vuforia.com/target-manager) in cui gli utenti possono creare le proprie destinazioni personalizzate. Gli sviluppatori possono inoltre iscriversi per ottenere una licenza gratuita per sviluppatori utilizzando il [gestore delle licenze Vuforia](https://developer.vuforia.com/license-manager).

## <a name="device-tracking-with-vuforia"></a>Rilevamento del dispositivo con Vuforia

Il rilevamento del [dispositivo](https://library.vuforia.com/features/environments/device-tracker-overview.html) mantiene il rilevamento anche quando una destinazione non è più in visualizzazione. Viene abilitata automaticamente per tutte le destinazioni quando è abilitato il rilevamento del dispositivo posizionale. Per le applicazioni HoloLens, lo strumento di rilevamento del dispositivo posizionale viene avviato automaticamente in Unity.

Il motore Vuforia unisce automaticamente le pose dal rilevamento della fotocamera e dal rilevamento spaziale di HoloLens per fornire una destinazione stabile, indipendentemente dal fatto che la destinazione sia visibile o meno dalla fotocamera.

Poiché il processo viene gestito automaticamente, non richiede alcuna programmazione da parte dello sviluppatore.


**Di seguito è riportata una descrizione di alto livello del processo:**
1. Il Tracker di destinazione di Vuforia riconosce la destinazione
2. Il rilevamento della destinazione viene quindi inizializzato
3. La posizione e la rotazione della destinazione vengono analizzate per fornire una stima di posa affidabile per HoloLens
4. Il motore Vuforia trasforma il posto della destinazione nello spazio delle coordinate del mapping spaziale HoloLens
5. HoloLens acquisisce il controllo se la destinazione non è più in visualizzazione. Ogni volta che si cerca di nuovo nella destinazione, Vuforia continuerà a tenere traccia delle immagini e degli oggetti in modo accurato.

Le destinazioni rilevate, ma non più visualizzate, vengono segnalate come EXTENDED_TRACKED. In questi casi, lo script DefaultTrackableEventHandler usato in tutte le destinazioni continua a eseguire il rendering del contenuto di aumento. Lo sviluppatore può controllare questo comportamento implementando uno script personalizzato del gestore eventi rilevabili.

## <a name="performance-mode-with-vuforia-engine"></a>Modalità prestazioni con il motore Vuforia 

È possibile usare il motore Vuforia per gestire le prestazioni in HoloLens per l'estensione delle esperienze AR e ridurre il carico di lavoro sulla CPU. Il motore Vuforia offre tre modalità che è possibile selezionare: predefinita, per ottimizzare la velocità e ottimizzare la qualità. 

*   MODE_OPTIMIZE_SPEED consente di ridurre al minimo il carico di lavoro nel dispositivo HoloLens ed è ideale per estendere le esperienze AR. È consigliabile per le situazioni in cui l'app tiene traccia degli oggetti/destinazioni statici.
*   MODE_DEFAULT è la modalità normale, che può essere usata nella maggior parte degli scenari.
*   MODE_OPTIMIZE_QUALITY è migliore per tenere traccia degli obiettivi mobili o degli obiettivi del modello che si prevede di prelevare.

**Impostazione della modalità**

Per modificare la modalità di prestazioni in Unity, passare a configurazione di Vuforia (CTRL + MAIUSC + V/Cmd + Maiusc + V) che si trova come componente in ARCamera GameObject. 
*   Selezionare il menu a discesa per la modalità dispositivo fotocamera e selezionare una delle tre opzioni.


## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)
* [Sistemi di coordinate](../../design/coordinate-systems.md)
* [Mapping spaziale](../../design/spatial-mapping.md)
* [Fotocamera in Unity](camera-in-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentazione di Vuforia: sviluppo per Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentazione di Vuforia: come installare l'estensione di Unity Vuforia](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentazione di Vuforia: uso dell'esempio HoloLens in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentazione di Vuforia: rilevamento dei dispositivi in Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Documentazione di Vuforia: ottimizzazione delle prestazioni e del framerate](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
