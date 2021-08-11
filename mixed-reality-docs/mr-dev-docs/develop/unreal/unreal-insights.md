---
title: Profilatura con Unreal Insights
description: Informazioni su come usare Unreal Insights in HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, profling, approfondimenti irreali, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228636"
---
# <a name="profiling-with-unreal-insights"></a>Profilatura con Unreal Insights 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) è un sistema di profilatura che raccoglie, analizza e visualizza i dati dal motore Unreal. Il sistema di profilatura consente di trovare colli di bottiglia di ottimizzazione e aree in cui le prestazioni delle app potrebbero usare un boost. In genere, si abilita Unreal Insights direttamente dall'editor, ma per HoloLens 2 è necessario usare la riga di comando.  

## <a name="setup"></a>Eseguire la configurazione

Unreal consente di creare e configurare un "Profilo personalizzato" nell'utilità di avvio HoloLens con i parametri della riga di comando che abilitano Unreal Insights.

1.  Trovare l'indirizzo IP del computer usando il **comando ipconfig** al prompt dei comandi. L'indirizzo IP è l'indirizzo IPv4 elencato da ipconfig. Tenere presente questo problema per un secondo momento quando si impostano i parametri della riga di comando.

> [!IMPORTANT]
> Se si è dietro una VPN, potrebbe essere necessario fornire l'indirizzo IP fornito tramite la VPN.

![Screenshot dei risultati della riga di comando per il comando ipconfig](images/unreal-insights-img-01.png)

2.  Passare alla parte superiore del pannello Unreal Engine (Motore Unreal) e aprire **Gestione dispositivi** sotto il **pulsante Launch (Avvia):**

![Screenshot delle opzioni di avvio con Gestione dispositivi evidenziato](images/unreal-insights-img-02.png)

3.  In Gestione dispositivi selezionare **Aggiungi un dispositivo non in elenco:**

![Screenshot di Gestione dispositivi aperto nel motore Unreal](images/unreal-insights-img-03.png)

4. Fare **clic su Seleziona una piattaforma** e scegliere **HoloLens**:

![Screenshot dell'elenco a discesa Aggiungi dispositivo non in elenco HoloLens evidenziato](images/unreal-insights-img-04.png)

5.  Se si usa IPoverUSB, immettere 127.0.0.1:10080 come Identificatore di dispositivo. Immettere l HoloLens utente e la password nei rispettivi campi e **compilare Nome visualizzato** come si vuole.

> [!IMPORTANT]
> L'identificatore del dispositivo è l'indirizzo IP del HoloLens, NON del computer che esegue Unreal Insights trovato nel passaggio 1.

![Screenshot dei dettagli HoloLens dispositivo in Gestione dispositivi](images/unreal-insights-img-05.png)

6.  Selezionare **Aggiungi** e il HoloLens visualizzato nell'elenco dei dispositivi di Gestione dispositivi:

![Screenshot della HoloLens aggiunta all'elenco dei dispositivi](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. Aprire **Project launcher** dal pannello UE4 sotto il **pulsante** Avvia:

![Screenshot delle opzioni di avvio con l'icona di avvio del progetto evidenziata](images/unreal-insights-img-07.png)

2. Selezionare il **+** pulsante per creare un profilo personalizzato in Profili di avvio **personalizzati**. Una volta creato, è sempre possibile modificare questo profilo in un secondo momento:

![Screenshot dell'utilità di avvio del progetto con i profili di avvio personalizzati evidenziati](images/unreal-insights-img-08.png)

3. Selezionare **il pulsante Modifica** profilo nel HoloLens di avvio personalizzato e configurare:
    * Selezionare **Cook** to **By the Book per** abilitare la copia nel dispositivo
    * È possibile selezionare **Archivia?** nella sezione  Archivio per mantenere il file con estensione appxbundle generato anziché eliminarlo per risparmiare spazio su disco. Specificare un percorso per appxbundle e passare a una build di sviluppo se si vuole

![Screenshot delle opzioni cook nella configurazione del profilo con cook by the book e HoloLens evidenziata](images/unreal-insights-img-09.png)

4. Impostare **Come si vuole distribuire la compilazione?** **in** Copia nel dispositivo per attivare la **sezione Avvio** dell'interfaccia utente:

![Screenshot dell'utilità di avvio del progetto con le opzioni di distribuzione con l'opzione Copia nel dispositivo evidenziata](images/unreal-insights-img-10.png)

5. Impostare **Parametri aggiuntivi della riga di** comando nella **sezione** Avvio. I parametri verranno scritti in un file ue4commandline.txt, in pacchetto nel bundle e usati all'avvio. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Provare questi per i principianti: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame, CPU, GPU, LoadTime,File,Net**
    * È possibile trovare un elenco completo dei parametri di avvio disponibili nella documentazione [di riferimento di Unreal Insights di riferimento.](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)

> [!NOTE]
> "IP_OF_YOUR_PC" è l'indirizzo IP trovato nel passaggio 1. Questo è l'indirizzo IP del computer che esegue Unreal Insights, NON l'indirizzo IP del HoloLens.

> [!IMPORTANT]
> Le tracce possono avere dimensioni molto grandi molto rapidamente. Abilitare solo i canali necessari per mantenere le dimensioni della traccia ridotte.

![Screenshot delle opzioni di configurazione di avvio](images/unreal-insights-img-11.png)

6. Avviare Unreal Insights'avvio dell'app, in caso contrario Unreal Insights sarà in grado di inizializzare in modo appropriato prima dell'app:
    * L'eseguibile Insights Unreal viene archiviato nella cartella del motore dei file binari, in genere come segue: "C:\Programmi\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot dell'eseguibile di informazioni dettagliate irreali in esecuzione](images/unreal-insights-img-12.png)

6.  Selezionare **Indietro** per tornare alla radice della finestra di **Project launcher**
7.  Nell'editor fare clic **su Avvia** nel profilo di avvio personalizzato

![Screenshot dei profili di avvio personalizzati](images/unreal-insights-img-13.png)

8.  Osservare come il progetto viene in pacchetto, installato nel dispositivo e avviato

## <a name="profiling"></a>Profilatura

In Unreal Insights selezionare la **connessione** live al dispositivo per avviare la profilatura

Il profilo personalizzato viene condiviso tra progetti. Da qui in avanti, è possibile usare il profilo personalizzato creato anziché dover eseguire questa operazione ogni volta. È necessario ricreare la connessione al dispositivo solo ogni volta che si avvia Unreal con i passaggi da 3 a 6 nella sezione [di configurazione](#setup).

## <a name="see-also"></a>Vedi anche
* [Documentazione di Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

