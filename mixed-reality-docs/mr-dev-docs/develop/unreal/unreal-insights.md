---
title: Profilatura con Unreal Insights
description: Informazioni su come usare Unreal Insights in HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, volgare, informazioni dettagliate irreali, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779387"
---
# <a name="profiling-with-unreal-insights"></a>Profilatura con Unreal Insights

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) è un sistema di profilatura che raccoglie, analizza e visualizza i dati da Unreal Engine. Il sistema di profilatura consente di trovare colli di bottiglia dell'ottimizzazione e le aree in cui le prestazioni delle app possono usare un aumento delle prestazioni. In genere, si abilita Unreal Insights dall'editor, ma per HoloLens 2 è necessario usare la riga di comando.

## <a name="setup"></a>Eseguire la configurazione

Unreal consente di creare e configurare un "profilo personalizzato" nell'utilità di avvio HoloLens con i parametri della riga di comando che abilitano Unreal Insights.

1. Trovare l'indirizzo IP del computer usando il **comando ipconfig** al prompt dei comandi. L'indirizzo IP è l'indirizzo IPv4 elencato da ipconfig. Tenere presente questo problema per un momento successivo quando si impostano i parametri della riga di comando.

> [!IMPORTANT]
> Se si è dietro una VPN, potrebbe invece essere necessario specificare l'indirizzo IP fornito tramite la VPN.

![Screenshot dei risultati della riga di comando per il comando ipconfig](images/unreal-insights-img-01.png)

2. Aprire **Project Impostazioni** dalla barra degli strumenti "Modifica" nella finestra principale dell'editor.

![Screenshot dell'elenco a discesa Modifica con Project Impostazioni evidenziato](images/unreal-insights-img-15.png)

3. Scorrere verso il basso il pannello sinistro fino a trovare **l'intestazione Platforms** (Piattaforme) **e selezionare HoloLens**.

![Screenshot della sezione Platforms (Piattaforme) nel pannello Project Impostazioni sinistra con HoloLens evidenziato](images/unreal-insights-img-15.png)

4. Verificare che nella **sezione Capabilities** (Funzionalità) sia selezionato "Internet Client", "Internet Client Server" (Server client Internet) e "Private Network Client Server" (Server client di rete privata).

![Screenshot delle opzioni funzionalità con client Internet, server client Internet e server client di rete privata selezionati](images/unreal-insights-img-14.png)

## <a name="launch"></a>Launch

1. Aprire **Project launcher** dal pannello UE4 sotto il pulsante Launch **(Avvia):**

![Screenshot delle opzioni di avvio con l'icona di avvio del progetto evidenziata](images/unreal-insights-img-07.png)

2. Selezionare il **+** pulsante per creare un profilo personalizzato in Profili di avvio **personalizzati.** Una volta creato, è sempre possibile modificare questo profilo in un secondo momento:

![Screenshot dell'utilità di avvio del progetto con i profili di avvio personalizzati evidenziati](images/unreal-insights-img-08.png)

3. Selezionare **il pulsante Modifica** profilo nel HoloLens di avvio personalizzato. Nella sezione **Build (Compilazione)** selezionare **Build UAT (Compila UAT)** e impostare **Additional Command Line Parameters (Parametri aggiuntivi della riga di comando).**
   - Per iniziare, provare a eseguire queste operazioni: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
   - È possibile trovare un elenco completo dei parametri di avvio disponibili nella documentazione di riferimento [di Unreal Insights di riferimento.](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)

> [!NOTE]
> "IP_OF_YOUR_PC" è l'indirizzo IP trovato nel passaggio 1. Questo è l'indirizzo IP del computer che esegue Unreal Insights, NON l'indirizzo IP del HoloLens.

> [!IMPORTANT]
> Le tracce possono raggiungere dimensioni molto grandi molto rapidamente. Abilitare solo i canali necessari per mantenere ridotte le dimensioni della traccia.

![Screenshot delle opzioni di compilazione nella configurazione del profilo](images/unreal-insights-img-17.png)

4. Selezionare **Cook** to **the Book (Prepara in base al libro)** per abilitare la copia nel dispositivo. Assicurarsi che le mappe siano selezionate in **Mappe**.

![Screenshot delle opzioni di cook nella configurazione del profilo con cook del libro e HoloLens evidenziate](images/unreal-insights-img-09.png)

5. Impostare **How would you like to package the build** (Come si vuole creare il pacchetto della **compilazione) su Package & store locally (Archivia pacchetto in locale).** Prendere nota del percorso del file scelto, che sarà necessario in seguito.

![Screenshot delle opzioni del pacchetto nella configurazione del profilo impostata per creare un pacchetto e archiviare in locale](images/unreal-insights-img-18.png)

6. Impostare **Come si desidera distribuire la compilazione?** su Non **distribuire**.

![Screenshot delle opzioni di distribuzione nella configurazione del profilo con la distribuzione impostata su Non distribuire](images/unreal-insights-img-19.png)

8. Selezionare **Indietro** per tornare alla radice della finestra di **Project di avvio**
9. Nell'editor fare clic **su Avvia** nel profilo di avvio personalizzato

![Screenshot dei profili di avvio personalizzati](images/unreal-insights-img-13.png)

10. Osservare come viene compilato il progetto e quindi distribuire appxbundle (nel percorso del pacchetto del passaggio 5) nel HoloLens tramite il portale per dispositivi

11. Avviare Unreal Insights. L'eseguibile Insights Unreal viene archiviato nella cartella del motore dei file binari, in genere come indicato di seguito: "C:\Programmi\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot dell'eseguibile di Unreal Insights in esecuzione](images/unreal-insights-img-12.png)

12. Avviare l'app nel HoloLens.

## <a name="profiling"></a>Profilatura

Tornare a Unreal Insights selezionare la **connessione** in tempo reale al dispositivo per avviare la profilatura

Il profilo personalizzato viene condiviso tra i progetti. Da qui in avanti è possibile usare il profilo personalizzato creato invece di dover eseguire questa operazione ogni volta. È necessario ricreare la connessione al dispositivo solo ogni volta che si avvia Unreal con i passaggi da 3 a 6 nella [sezione relativa alla configurazione](#setup).

## <a name="see-also"></a>Vedi anche

- [Documentazione di Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
