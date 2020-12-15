---
title: Profilatura con informazioni dettagliate non reali
description: Informazioni su come usare Unreal Insights in HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, profling, Unreal Insights, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486379"
---
# <a name="profiling-with-unreal-insights"></a>Profilatura con informazioni dettagliate non reali 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) è un sistema di profilatura che raccoglie, analizza e Visualizza i dati da Unreal Engine. Il sistema di profilatura consente di individuare i colli di bottiglia e le aree di ottimizzazione in cui le prestazioni delle app possono usare un Boost. In genere, si abilitano le informazioni dettagliate non reali direttamente dall'editor, ma per HoloLens 2 è necessario usare la riga di comando.  

## <a name="setup"></a>Configurazione

Unreal consente di creare e configurare un "profilo personalizzato" nell'utilità di avvio HoloLens con i parametri della riga di comando che abilitano le informazioni non reali.

1.  Individuare l'indirizzo IP del computer utilizzando il comando **ipconfig** al prompt dei comandi. L'indirizzo IP è l'indirizzo IPv4 elencato da ipconfig. Tenere presente questo aspetto per un momento successivo quando si impostano i parametri della riga di comando.

> [!IMPORTANT]
> Se si è protetti da una VPN, potrebbe essere necessario specificare l'indirizzo IP fornito tramite la VPN.

![Screenshot dei risultati della riga di comando per il comando ipconfig](images/unreal-insights-img-01.png)

2.  Passare alla parte superiore del pannello Unreal Engine e aprire **Device Manager** sotto il pulsante **Launch (avvia** ):

![Screenshot delle opzioni di avvio con gestione dispositivi evidenziato](images/unreal-insights-img-02.png)

3.  Nella Device Manager selezionare **Aggiungi un dispositivo** non in elenco:

![Screenshot di gestione dispositivi aperto in Unreal Engine](images/unreal-insights-img-03.png)

4. Fare clic su **selezionare una piattaforma** e scegliere **HoloLens**:

![Screenshot dell'elenco a discesa Aggiungi dispositivo non in elenco con HoloLens evidenziato](images/unreal-insights-img-04.png)

5.  Se si usa IPoverUSB, immettere 127.0.0.1:10080 come identificatore del dispositivo. Immettere l'utente e la password di HoloLens nei rispettivi campi e compilare il **nome visualizzato** come desiderato.

> [!IMPORTANT]
> L'identificatore del dispositivo è l'indirizzo IP del HoloLens, non del computer che esegue informazioni dettagliate non reali trovate nel passaggio 1.

![Schermata dei dettagli del dispositivo HoloLens in gestione dispositivi](images/unreal-insights-img-05.png)

6.  Selezionare **Aggiungi** per visualizzare il HoloLens nell'elenco dei dispositivi di gestione dispositivi:

![Screenshot di HoloLens aggiunto all'elenco dei dispositivi](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. Aprire **avvio progetto** dal pannello UE4 sotto il pulsante **Launch (avvia** ):

![Screenshot delle opzioni di avvio con avvio del progetto evidenziato](images/unreal-insights-img-07.png)

2. Selezionare il **+** pulsante per creare un profilo personalizzato in **profili di avvio personalizzati**. Una volta creato, è sempre possibile modificare il profilo in un secondo momento:

![Screenshot dell'utilità di avvio del progetto con profili di avvio personalizzati evidenziati](images/unreal-insights-img-08.png)

3. Selezionare il pulsante **modifica profilo** nel profilo di avvio personalizzato di HoloLens e configurare:
    * Selezionare **Cook** to **by the book** per abilitare la copia nel dispositivo
    * È possibile scegliere di archiviare l'archivio **?** nella sezione **Archivio** per mantenere il. appxbundle generato anziché eliminare per risparmiare spazio su disco. Specificare un percorso per il appxbundle e passare a una build di sviluppo, se si desidera

![Screenshot delle opzioni di Cook nella configurazione del profilo con Cook by the book e HoloLens evidenziato](images/unreal-insights-img-09.png)

4. Impostare la **modalità di distribuzione della compilazione** per la **copia nel dispositivo** per attivare la sezione **Launch** dell'interfaccia utente:

![Screenshot dell'utilità di avvio del progetto con opzioni di distribuzione con copia nel dispositivo evidenziato](images/unreal-insights-img-10.png)

5. Impostare **parametri della riga di comando aggiuntivi** nella sezione **Launch** . I parametri verranno scritti in un file di ue4commandline.txt, inclusi nel bundle e usati all'avvio. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Provare a eseguire queste operazioni per i principianti: **-tracehost = IP_OF_YOUR_PC-trace = log, Bookmark, frame, CPU, GPU, LoadTime, file, NET**
    * È possibile trovare un elenco completo dei parametri di avvio disponibili nella [documentazione di riferimento di Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" è l'indirizzo IP trovato nel passaggio 1. Si tratta dell'indirizzo IP del computer che esegue Unreal Insights, non dell'indirizzo IP del HoloLens.

> [!IMPORTANT]
> Il numero di tracce può essere molto rapido. Abilitare solo i canali necessari per ridurre le dimensioni della traccia.

![Screenshot delle opzioni di configurazione di avvio](images/unreal-insights-img-11.png)

6. Avviare informazioni dettagliate non reali prima dell'avvio dell'app. in caso contrario, le informazioni dettagliate non saranno in grado di inizializzare in modo appropriato prima dell'app:
    * Il file eseguibile di Unreal Insights viene archiviato nella cartella del motore dei binari, in genere come segue: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot del file eseguibile di Unreal Insights in esecuzione](images/unreal-insights-img-12.png)

6.  Selezionare **indietro** per tornare alla radice della finestra di dialogo di **avvio del progetto**
7.  Nell'editor fare clic su **Launch (avvia** ) nel profilo di avvio personalizzato

![Screenshot dei profili di avvio personalizzati](images/unreal-insights-img-13.png)

8.  È possibile osservare il pacchetto del progetto, installarlo nel dispositivo e avviare

## <a name="profiling"></a>Profilatura

Per avviare la profilatura, selezionare la connessione in **tempo** reale al dispositivo per avviare la profilatura.

Il profilo personalizzato è condiviso tra i progetti. Da questo punto in poi, è possibile usare il profilo personalizzato creato anziché eseguire questa operazione ogni volta. È necessario ricreare la connessione al dispositivo ogni volta che si avvia Unreal con i passaggi da 3 a 6 nella [sezione relativa all'installazione](#setup).

## <a name="see-also"></a>Vedere anche
* [Documentazione di Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

