---
title: Informazioni di riferimento sulle API di Portale di dispositivi
description: Rimanere aggiornati sull'API Windows Portale di dispositivi per HoloLens sviluppo.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, Windows Portale di dispositivi, API, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 6b41c569917150c303da933a75d354f574fb579ba676dac281e9cde2bfc59818
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207839"
---
# <a name="device-portal-api-reference"></a>Informazioni di riferimento sulle API di Portale di dispositivi

Tutti gli elementi [Windows Portale di dispositivi](using-the-windows-device-portal.md) si basano sulle API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.

## <a name="app-deloyment"></a>Deloyment delle app

**/api/app/packagemanager/package (DELETE)**

Disinstalla un'app

Parametri
* package: nome file del pacchetto da disinstallare.

**/api/app/packagemanager/package (POST)**

Installa un'app

Parametri
* package: nome file del pacchetto da installare.

Payload
* corpo HTTP conforme in più parti

**/api/app/packagemanager/packages (GET)**

Recupera l'elenco delle app installate nel sistema, con i dettagli

Restituisce i dati
* Elenco dei pacchetti installati con i dettagli

**/api/app/packagemanager/state (GET)**

Ottiene lo stato dell'installazione dell'app in corso

## <a name="dump-collection"></a>Raccolta dei dump

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Disabilita la raccolta di dump di arresto anomalo del sistema per un'app con sideloaded

Parametri
* packageFullname : nome pacchetto

**/api/debug/dump/usermode/crashcontrol (GET)**

Ottiene le impostazioni per la raccolta di dump di arresto anomalo delle app affiancate

Parametri
* packageFullname : nome pacchetto

**/api/debug/dump/usermode/crashcontrol (POST)**

Abilita e imposta le impostazioni del controllo dump per un'app con sideloaded

Parametri
* packageFullname : nome pacchetto

**/api/debug/dump/usermode/crashdump (DELETE)**

Elimina un dump di arresto anomalo del sistema per un'app con sideloaded

Parametri
* packageFullname : nome pacchetto
* fileName : nome file dump

**/api/debug/dump/usermode/crashdump (GET)**

Recupera un dump di arresto anomalo del sistema per un'app sideloaded

Parametri
* packageFullname : nome pacchetto
* fileName : nome file dump

Restituisce i dati
* File di dump. Ispezionare con WinDbg o Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Restituisce l'elenco di tutti i dump di arresto anomalo del sistema per le app con sideloaded

Restituisce i dati
* Elenco di dump di arresto anomalo del sistema per ogni app con caricamento laterale

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

Enumera i provider registrati

Restituisce i dati
* Elenco di provider, nome descrittivo e GUID

**/api/etw/session/realtime (GET/WebSocket)**

Crea una sessione ETW in tempo reale. gestito tramite un websocket.

Restituisce i dati
* Eventi ETW dai provider abilitati

## <a name="holographic-os"></a>Sistema operativo olografico

**/api/holographic/os/etw/customproviders (GET)**

Restituisce un elenco di HoloLens provider ETW specifici non registrati nel sistema

**/api/holographic/os/services (GET)**

Restituisce gli stati di tutti i servizi in esecuzione.

**/api/holographic/os/settings/ipd (GET)**

Ottiene l'IPD archiviato (distanza interpupillare) in millimetri

**/api/holographic/os/settings/ipd (POST)**

Imposta l'IPD

Parametri
* ipd: nuovo valore IPD da impostare in millimetri

**/api/holographic/os/webmanagement/settings/https (GET)**

Ottenere richieste HTTPS per Device Portal

**/api/holographic/os/webmanagement/settings/https (POST)**

Imposta i requisiti HTTPS per l'Portale di dispositivi

Parametri
* required : sì, no o default

## <a name="holographic-perception"></a>Percezione olografica

**/api/holographic/perception/client (GET/WebSocket)**

Accetta gli aggiornamenti websocket ed esegue un client perception che invia gli aggiornamenti a 30 fps.

Parametri
* clientmode: "active" forza la modalità di rilevamento visivo quando non può essere stabilita passivamente

## <a name="holographic-thermal"></a>Termica olografica

**/api/holographic/thermal/stage (GET)**

Ottenere la fase termica del dispositivo (0 normale, 1 caldo, 2 critico)

## <a name="map-manager"></a>Map Manager (Gestore mappe)

**/api/holographic/mapmanager/mapFiles (GET)**

Ottiene l'elenco dei file di mappa disponibili (con estensione mapx).

**/api/holographic/mapmanager/anchorFiles (GET)**

Ottiene l'elenco dei file di ancoraggio disponibili (con estensione ancx).

**/api/holographic/mapmanager/srdbFiles (GET)**

Ottiene l'elenco dei file di database di ricostruzione spaziale disponibili (con estensione srdb).

**/api/holographic/mapmanager/getanchors (GET)**

Ottiene l'elenco di ancoraggi persistenti per l'utente corrente. 

### <a name="downloaduploaddelete-files"></a>Scaricare/Upload/eliminare file
**/api/holographic/mapmanager/download (GET)**

Scarica un file di database mappa, ancoraggio o ricostruzione spaziale. Il file deve essere stato caricato o esportato in precedenza.

Parametri
* FileName: nome del file da scaricare.

Esempio: 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

Carica un file di database mappa, ancoraggio o spaziale. Una volta caricato, un file può essere importato in un secondo momento per essere usato dal sistema.

Parametri
* file: nome del file da caricare.

Esempio:
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

**/api/holographic/mapmanager/delete (POST)**

Elimina un file di database mappa, ancoraggio o spaziale. Il file deve essere stato caricato o esportato in precedenza.

Parametri
* FileName: nome del file da eliminare.

Esempio: 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>Esportazione

**/api/holographic/mapmanager/export (POST)**

Esporta la mappa attualmente in uso dal sistema. Una volta esportato, può essere scaricato. 

Esempio: 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

Esporta la mappa attualmente in uso dal sistema. Una volta esportato, può essere scaricato. Esempio: 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapandanchors (POST)**

Esporta la mappa e gli ancoraggi attualmente in uso dal sistema. Una volta esportati, possono essere scaricati. Esempio: 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

Esporta il database di mappa e di ricorsiva spaziale attualmente in uso dal sistema. Una volta esportati, possono essere scaricati. 

Esempio: 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>Importa

**/api/holographic/mapmanager/import (POST)**

Indica al sistema la mappa da usare attualmente. Può essere chiamato su file che sono stati esportati o caricati.

Parametri
* FileName: nome della mappa da usare. 

Esempio: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

Indica al sistema quali ancoraggi devono essere attualmente usati. Può essere chiamato su file che sono stati esportati o caricati.

Parametri
* FileName: nome degli ancoraggi da usare. 

Esempio: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importspatialmappingdb (POST)**

Indica al sistema quale database di ricorsiva spaziale deve essere attualmente utilizzato. Può essere chiamato su file che sono stati esportati o caricati.

Parametri
* FileName: nome del database di mapping spaziale da usare. 

Esempio: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>Altro

**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

Reimpostare il database della mappa, degli ancoraggi e dello spazio del sistema.

Esempio: 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (GET)**

Ottiene lo stato del sistema, incluse le mappe, gli ancoraggi e i file di database spaziali di cui è stata importata l'ultima volta. 


## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/api/holographic/mrc/file (GET)**

Scarica un file di realtà mista dal dispositivo. Usare il parametro di query op=stream per il flusso.

Parametri
* filename: nome, con codifica hex64, del file video da ottenere
* op : stream

**/api/holographic/mrc/file (DELETE)**

Elimina una registrazione di realtà mista dal dispositivo.

Parametri
* filename : nome, con codifica hex64, del file da eliminare

**/api/holographic/mrc/files (GET)**

Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo

**/api/holographic/mrc/photo (POST)**

Crea una foto di realtà mista e crea un file nel dispositivo

Parametri
* holo : capture ologrammi: true o false (il valore predefinito è false)
* pv: capture PV camera: true o false (il valore predefinito è false)
* RenderFromCamera: (solo HoloLens 2) eseguire il rendering dal punto di vista della fotocamera/videocamera: true o false (il valore predefinito è true)

**/api/holographic/mrc/settings (GET)**

Ottiene le impostazioni predefinite di acquisizione di realtà mista

**/api/holographic/mrc/settings (POST)**

Imposta le impostazioni predefinite di acquisizione di realtà mista.  Alcune di queste impostazioni vengono applicate all'acquisizione di foto e video MRC del sistema.

**/api/holographic/mrc/status (GET)**

Ottiene lo stato dell'acquisizione di realtà mista all'interno del Windows Portale di dispositivi.

***Response***.

La risposta contiene una proprietà JSON che indica se Windows Portale di dispositivi registra video o meno.

``` javascript
{"IsRecording" : boolean}
```

**/api/holographic/mrc/thumbnail (GET)**

Ottiene l'immagine di anteprima per il file specificato.

Parametri
* filename: nome, con codifica hex64, del file per cui viene richiesta l'anteprima

**/api/holographic/mrc/video/control/start (POST)**

Avvia una registrazione di realtà mista

Parametri
* holo : capture ologrammi: true o false (il valore predefinito è false)
* pv: capture PV camera: true o false (il valore predefinito è false)
* mic : acquisisci microfono: true o false (il valore predefinito è false)
* loopback: acquisisce l'audio dell'app: true o false (il valore predefinito è false)
* RenderFromCamera: (solo HoloLens 2) eseguire il rendering dal punto di vista della fotocamera/videocamera: true o false (il valore predefinito è true)
* vstab: (solo HoloLens 2) abilita la stabilizzazione video: true o false (il valore predefinito è true)
* vstabbuffer: (solo HoloLens 2) latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)

**/api/holographic/mrc/video/control/stop (POST)**

Arresta la registrazione corrente di realtà mista

## <a name="mixed-reality-streaming"></a>Streaming di realtà mista

> [!CAUTION]
> A causa dell'isolamento del loopback, non è possibile connettersi a Mixed Reality Streaming dall'interno di un'app in un dispositivo.

HoloLens supporta l'anteprima live della realtà mista tramite il download in blocchi di un mp4 frammentato.

I flussi di realtà mista condividono lo stesso set di parametri per controllare ciò che viene acquisito:
* holo: acquisizione di ologrammi: true o false
* pv: acquisizione della fotocamera PV: true o false
* mic : capture microphone: true o false
* loopback: acquisizione dell'audio dell'app: true o false

Se non viene specificato nessuno di questi elementi: ologrammi, foto/videocamera e audio dell'app verranno acquisiti<br>
Se vengono specificati parametri non specificati, il valore predefinito è false

Parametri facoltativi (HoloLens 2 facoltativi)
* RenderFromCamera: rendering dal punto di vista della foto/videocamera: true o false (il valore predefinito è true)
* vstab: abilita la stabilizzazione video: true o false (il valore predefinito è false)
* vstabbuffer: latenza del buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)

**/api/holographic/stream/live.mp4 (GET)**

Flusso 1280x720p 30fps 5Mbit.

**/api/holographic/stream/live_high.mp4 (GET)**

Flusso 1280x720p 30fps 5Mbit.

**/api/holographic/stream/live_med.mp4 (GET)**

Flusso 854x480p 30fps 2.5Mbit.

**/api/holographic/stream/live_low.mp4 (GET)**

Flusso 428x240p 15fps 0,6Mbit.

## <a name="networking"></a>Rete

**/api/networking/ipconfig (GET)**

Ottiene la configurazione IP corrente

## <a name="os-information"></a>Informazioni sul sistema operativo

**/api/os/info (GET)**

Ottiene le informazioni sul sistema operativo

**/api/os/machinename (GET)**

Ottiene il nome del computer

**/api/os/machinename (POST)**

Imposta il nome del computer

Parametri
* name: nuovo nome del computer con codifica hex64, su cui impostare

## <a name="perception-simulation-control"></a>Controllo simulazione percezione

**/api/holographic/simulation/control/mode (GET)**

Ottenere la modalità di simulazione

**/api/holographic/simulation/control/mode (POST)**

Impostare la modalità di simulazione

Parametri
* mode : modalità di simulazione: predefinita, simulazione, remota, legacy

**/api/holographic/simulation/control/stream (DELETE)**

Eliminare un flusso di controllo.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Aprire una connessione Web Socket per un flusso di controllo.

**/api/holographic/simulation/control/stream (POST)**

Creare un flusso di controllo (la priorità è obbligatoria) o pubblicare i dati in un flusso creato (streamId obbligatorio). È previsto che i dati inseriti siano di tipo 'application/octet-stream'.

**/api/holographic/simulation/display/stream (GET/WebSocket)**

Richiedere un flusso video di simulazione contenente il contenuto sottoposto a rendering nella visualizzazione del sistema in modalità "Simulazione".  Inizialmente verrà inviata un'intestazione del descrittore di formato semplice, seguita da trame con codifica H.264, ognuna preceduta da un'intestazione che indica l'indice degli occhi e le dimensioni della trama.

## <a name="perception-simulation-playback"></a>Riproduzione simulazione percezione

**/api/holographic/simulation/playback/file (DELETE)**

Eliminare una registrazione.

Parametri
* recording : nome della registrazione da eliminare.

**/api/holographic/simulation/playback/file (POST)**

Upload una registrazione.

**/api/holographic/simulation/playback/files (GET)**

Ottenere tutte le registrazioni.

**/api/holographic/simulation/playback/session (GET)**

Ottiene lo stato di riproduzione corrente di una registrazione.

Parametri
* recording : nome della registrazione.

**/api/holographic/simulation/playback/session/file (DELETE)**

Scaricare una registrazione.

Parametri
* recording : nome della registrazione da scaricare.

**/api/holographic/simulation/playback/session/file (POST)**

Caricare una registrazione.

Parametri
* recording : nome della registrazione da caricare.

**/api/holographic/simulation/playback/session/files (GET)**

Ottenere tutte le registrazioni caricate.

**/api/holographic/simulation/playback/session/pause (POST)**

Sospendere una registrazione.

Parametri
* recording : nome della registrazione.

**/api/holographic/simulation/playback/session/play (POST)**

Riprodurre una registrazione.

Parametri
* recording : nome della registrazione.

**/api/holographic/simulation/playback/session/stop (POST)**

Arrestare una registrazione.

Parametri
* recording : nome della registrazione.

**/api/holographic/simulation/playback/session/types (GET)**

Ottenere i tipi di dati in una registrazione caricata.

Parametri
* recording : nome della registrazione.

## <a name="perception-simulation-recording"></a>Registrazione simulazione percezione

**/api/holographic/simulation/recording/start (POST)**

Avviare una registrazione. Solo una singola registrazione può essere attiva contemporaneamente. È necessario impostare una delle proprietà head, hands, spatialMapping o environment.

Parametri
* head: impostare su 1 per registrare i dati head.
* hands: impostare su 1 per registrare i dati della mano.
* spatialMapping: impostare su 1 per registrare il mapping spaziale.
* environment: impostare su 1 per registrare i dati dell'ambiente.
* name: nome della registrazione.
* singleSpatialMappingFrame: impostare su 1 per registrare un solo frame di mapping spaziale.

**/api/holographic/simulation/recording/status (GET)**

Ottiene lo stato della registrazione.

**/api/holographic/simulation/recording/stop (GET)**

Arrestare la registrazione corrente. La registrazione verrà restituita come file.

## <a name="performance-data"></a>Dati sulle prestazioni

**/api/resourcemanager/processes (GET)**

Restituisce l'elenco dei processi in esecuzione con i dettagli

Restituisce i dati
* JSON con elenco di processi e dettagli per ogni processo

**/api/resourcemanager/systemperf (GET)**

Restituisce statistiche sulle prestazioni di sistema (lettura/scrittura di I/O, statistiche di memoria e così via)

Restituisce i dati
* JSON con informazioni di sistema: CPU, GPU, memoria, rete, I/O

## <a name="power"></a>Elettricità

**/api/power/battery (GET)**

Ottiene lo stato corrente della batteria

**/api/power/state (GET)**

Verifica se il sistema è in stato di alimentazione insufficiente

## <a name="remote-control"></a>Controllo remoto

**/api/control/restart (POST)**

Riavvia il dispositivo di destinazione

**/api/control/shutdown (POST)**

Arresta il dispositivo di destinazione

## <a name="task-manager"></a>Gestione attività

**/api/taskmanager/app (DELETE)**

Arresta un'app moderna

Parametri
* package: nome completo del pacchetto dell'app con codifica hex64
* forcestop: forza l'arresto di tutti i processi (=yes)

**/api/taskmanager/app (POST)**

Avvia un'app moderna

Parametri
* appid: PRAID dell'app da avviare, con codifica hex64
* package: nome completo del pacchetto dell'app con codifica hex64

## <a name="wifi-management"></a>Gestione Wi-Fi

**/api/wifi/interfaces (GET)**

Enumera le interfacce di rete wireless

Restituisce i dati
* Elenco di interfacce wireless con dettagli (GUID, descrizione e così via)

**/api/wifi/network (DELETE)**

Elimina un profilo associato a una rete in un'interfaccia specificata

Parametri
* interface: guid interfaccia di rete
* profile: nome del profilo

**/api/wifi/networks (GET)**

Enumera le reti wireless nell'interfaccia di rete specificata

Parametri
* interface: guid interfaccia di rete

Restituisce i dati
* Elenco delle reti wireless trovate nell'interfaccia di rete con i dettagli

**/api/wifi/network (POST)**

Si connette o si disconnette a una rete nell'interfaccia specificata

Parametri
* interface: guid interfaccia di rete
* ssid: ssid, con codifica hex64, a cui connettersi
* op: connettersi o disconnettersi
* createprofile: sì o no
* key: chiave condivisa, con codifica hex64

## <a name="windows-performance-recorder"></a>Windows Registratore prestazioni

**/api/wpr/customtrace (POST)**

Carica un profilo WPR e avvia la traccia usando il profilo caricato.

Payload
* corpo HTTP conforme in più parti

Restituisce i dati
* Restituisce lo stato della sessione WPR.

**/api/wpr/status (GET)**

Recupera lo stato della sessione WPR

Restituisce i dati
* Stato della sessione WPR.

**/api/wpr/trace (GET)**

Arresta una sessione di traccia WPR (performance)

Restituisce i dati
* Restituisce il file ETL di traccia

**/api/wpr/trace (POST)**

Avvia sessioni di traccia WPR (prestazioni)

Parametri
* profile: nome del profilo. I profili disponibili vengono archiviati in perfprofiles/profiles.jsin

Restituisce i dati
* All'avvio, restituisce lo stato della sessione WPR.

## <a name="see-also"></a>Vedi anche
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
* [Portale di dispositivi informazioni di riferimento sulle API principali (UWP)](/windows/uwp/debug-test-perf/device-portal-api-core)