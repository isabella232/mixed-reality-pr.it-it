---
title: Panoramica del software e cronologia delle versioni
description: Panoramica dei componenti software principali per l'Windows Mixed Reality, i visori VR immersive e la relativa cronologia delle versioni.
author: qianw211
ms.author: v-qianwen
ms.date: 10/5/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, componenti software, cronologia delle versioni, note sulla versione, cronologia delle versioni
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: b27006790d48107bdb19c7afa59e9c8adbda45b1
ms.sourcegitcommit: 289cefbe479d6e0f4451a618bf926e4b08b50260
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129593379"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Panoramica e cronologia delle versioni del software Realtà mista

## <a name="introduction-to-mixed-reality-software"></a>Introduzione al software di realtà mista

Windows Mixed Reality è costituito dai componenti software principali seguenti:

1. **Portale realtà mista**, che fornisce l'esperienza Windows Mixed Reality principale
    * Nelle Windows 10 1709 e 1803, Portale realtà mista è un componente chiave del sistema operativo Windows 10 aggiornato tramite Windows Update.
    * Nella Windows 10 1809 e versioni più Portale realtà mista viene aggiornata tramite l'app Microsoft Store.
    * Nella Windows 11 versione 21H2, la Portale realtà mista viene aggiornata tramite l Microsoft Store app.
2. Il **pacchetto di funzionalità su richiesta** di realtà mista, scaricato e installato automaticamente durante la Portale realtà mista della prima esecuzione. Altre informazioni sul pacchetto SUD sono disponibili [qui](/windows/application-management/manage-windows-mixed-reality)
3. Il **visore VR** di realtà mista e il driver del controller del movimento, noto anche come driver HoloLens Sensors, è il pacchetto di driver chiave che consente ai visori VR di Windows Mixed Reality di funzionare con Windows Mixed Reality. Questo viene scaricato e installato automaticamente tramite Windows Aggiorna la prima volta che il visore VR realtà mista viene collegato e aggiornato regolarmente tramite Windows Update
4. I driver del modello di controller del movimento di realtà mista contengono i modelli 3D dei controller del movimento di realtà mista e sono necessari per esperienze di realtà mista di terze parti. Questo viene scaricato e installato automaticamente tramite Windows Aggiorna la prima volta che i controller del movimento di realtà mista vengono associati al PC e vengono aggiornati tramite Windows Update
5. **Windows 10 versione 1709 (Fall Creator's Update)** o versioni più recenti contiene tecnologie e componenti chiave del sistema operativo che consentono di Windows Mixed Reality

L Windows Mixed Reality in SteamVR richiede il software seguente:

6. **SteamVR,** sviluppato e gestito da Valve Corporation che consente app e giochi di realtà virtuale in Steam. Altre informazioni sono disponibili [qui](https://go.microsoft.com/fwlink/?linkid=862788)
7. Il **Windows Mixed Reality per il componente SteamVR,** che consente di creare un bridge per Larrevr con Windows Mixed Reality. Altre informazioni su questo componente sono disponibili nella [pagina Windows Mixed Reality per SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gestione del visore VR Windows Mixed Reality:

8. **L'app Device Companion,** sviluppata e gestita da ogni produttore di visori VR, offre una rapida introduzione al visore WINDOWS MIXED REALITY visore VR. Nei visori VR con funzionalità di Bluetooth predefinita, l'app Device Companion consente di ripristinare i controller del movimento nella propria Bluetooth dispositivi. Alcuni visori VR (ad esempio Samsung Odyssey e Samsung Odyssey+) usano anche l'app Device Companion per distribuire gli aggiornamenti del firmware del visore VR dal produttore del visore VR. Questa app viene scaricata automaticamente la prima volta che il visore VR viene collegato e si trova nel menu Start Windows.

## <a name="windows-11-release-notes---october-2021"></a>Windows 11 - Ottobre 2021

### <a name="infinite-expanse"></a>Infinite Expanse

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* Nuovo ambiente domestico virtuale per Windows Mixed Reality con una riduzione significativa dell'ambito e delle dimensioni, semplificato in una fase singolare invece che nella più ricca di funzionalità Diote. 
* Progettato per le prestazioni, Infinite Expanse è stato progettato per far fronte alle richieste dei clienti di lunga data per un ambiente domestico virtuale a elevato utilizzo di risorse che consente ai clienti di ottenere prestazioni ottimali dai giochi e dalle esperienze. 
* Questo nuovo ambiente domestico virtuale è disponibile nel pannello **Pin nel** menu **Luoghi.** 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>Avvio di SteamVR con Portale realtà mista avvio

* Nuova impostazione disponibile per avviare automaticamente SteamVR all'avvio di WMR, consentendo di ignorare lo spazio iniziale wmr e passare direttamente a WmRVR.
   * Questa nuova impostazione è disponibile nell'app **Impostazioni** in Mixed Reality > Startup and **Desktop > Automatic Startup**.
    
### <a name="new-startup-experience-settings"></a>Nuove impostazioni dell'esperienza di avvio

* Nuove impostazioni disponibili per configurare meglio l'esperienza di avvio ideale aumentando il livello di controllo sul momento Portale realtà mista avvio.
* È ora possibile controllare se un Portale realtà mista viene avviato quando un dispositivo è connesso o quando viene attivato il sensore di presenza, nonché controllare la modalità di apertura dell'app desktop virtuale.
* Queste nuove impostazioni sono disponibili nell'app **Impostazioni** in Realtà mista **> avvio e desktop**
    * Attivare/disattivare per avviare MRP nel plug-in HMD.
    * Attivare o disattivare l'avvio di MRP quando viene rilevata la presenza.
    * Attivare o disattivare Apri app desktop sullo stato attivo dell'app desktop.

### <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - Maggio 2020](release-notes-may-2020.md)
* [Note sulla versione - Maggio 2019](release-notes-may-2019.md)
* [Note sulla versione - ottobre 2018](release-notes-october-2018.md)
* [Note sulla versione - Aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Cronologia delle versioni del visore VR di realtà mista e del driver del controller del movimento ###

Questo driver viene scaricato e installato automaticamente tramite Windows Update, ma i collegamenti di download sono disponibili inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 versione 2004 (aggiornamento di maggio 2020) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 marzo 2021  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Aggiornare l'ordine di vento della mesh dell'area nascosta in modo che HP Reverb G2 sia coerente con altri visori VR.</li><li>Miglioramenti della qualità degli oggetti visivi per i visori VR HP Reverb G2.</li><li>Windows Mixed Reality dell'affidabilità e della piattaforma visore VR.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 dicembre 2020  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Nuovo firmware del controller per il controller HP per risolvere un problema a causa del quale alcuni controller hanno trigger non funzionanti.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 ottobre 2020  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Supporto ufficiale per HP Reverb G2, HP Omnicept e il nuovo controller HP.</li><li>Correzioni dello schermo secondarie per i visori VR HP Reverb e Samsung Odyssey+. (richiede la build del sistema [operativo 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) o successiva o le build del sistema operativo [18362.1110 e 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) o successive).</li><li>Miglioramenti alla transizione dello stato di alimentazione del computer dalla sospensione per ridurre gli errori SWW 1-4.</li><li>Windows Mixed Reality miglioramenti di affidabilità e correzioni secondarie della piattaforma visore VR.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 maggio 2020      | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Windows Mixed Reality miglioramenti di affidabilità e correzioni secondarie della piattaforma visore VR.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versione 1903 (aggiornamento di maggio 2019) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 ottobre 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Windows Mixed Reality correzioni secondarie della piattaforma visore VR.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 giugno 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Windows Mixed Reality dell'affidabilità e della piattaforma visore VR per i computer in sospensione e le transizioni dello stato di alimentazione.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1° maggio 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Contiene l'aggiornamento del firmware per I visori VR di Acer, Asus, Dell, Fujitsu, HP, Lenovo e Medion Windows Mixed Reality 2017. Questo aggiornamento del firmware migliora la compatibilità e l'affidabilità dei visori VR con determinati adattatori grafici o driver di grafica.</li><li>Windows Mixed Reality dell'affidabilità e della piattaforma per visori VR</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 gennaio 2019      | Compatibile con Windows 10, versione 1803 e versioni più recente.<br/><ul><li>Correzioni di instabilità e stutter per il rilevamento del visore VR</li><li>Correzioni per l'affidabilità della modalità torcia</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809.<br/>Compatibile con Windows 10, versione 1803 e versioni più recente.<br/><ul><li>Abilita nuove Windows Mixed Reality, ad esempio la modalità torcia, in Windows 10, versione 1809</li><li>Miglioramenti per il rilevamento e l'affidabilità dei visori VR</li><li>Miglioramenti delle prestazioni e del rilevamento del controller del movimento</li><li>Prestazioni e miglioramenti di USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 aprile 2018      | Versione pubblica iniziale del driver per Windows 10 versione 1803<br/> <ul><li>Miglioramenti per il rilevamento e l'affidabilità dei visori VR</li><li>Miglioramenti delle prestazioni e del rilevamento del controller del movimento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 febbraio 2018    | <ul><li>Supporto ufficiale per 3 visori VR Blubur S2 Mixed Reality per 3glass</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 dicembre 2017   | <ul><li>Risolve il problema di HID che causa *un* problema con codice di errore 2181038087-7 in alcuni PC</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 dicembre 2017    | <ul><li>Monitoraggio del visore VR migliorato</li><li>Miglioramenti della velocità di risposta del touchpad del controller del movimento</li><li>Risolve il problema a causa del quale l'installazione del driver potrebbe talvolta non riuscire</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 novembre 2017   | <ul><li>Risolve un problema che causava la visualizzazione di visori VR a volte in nero durante l'uso</li><li>Risolve un problema che talvolta causava la scomparsa dei controller del movimento</li><li>Miglioramenti delle prestazioni del sensore di presenza per il visore VR Dell Visor</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | 10.0.16299.1036  | 7 novembre 2017    | <ul><li>Miglioramenti del meccanismo di lancio del controller del movimento:<ul><li>La velocità verrà ora segnalata correttamente quando l'accuratezza della posizione è approssimativa, quindi è ora possibile lanciarsi dietro la testa.</li><li>Il codice di esempio per la generazione di eccezioni è disponibile nel pacchetto Unity "ThrowingStarter" [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Aprire la scena di lancio per iniziare</li></ul></li><li>Report della batteria del controller del movimento migliorato</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | 10.0.16299.1012  | 17 ottobre 2017    | Versione pubblica iniziale del driver                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Cronologia delle versioni del driver del modello di controller del movimento di realtà mista ###

Questo driver viene scaricato e installato automaticamente anche tramite Windows Update, ma i collegamenti di download sono disponibili inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 versione 2004 (aggiornamento di maggio 2020)

| Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 settembre 2020      | Versione pubblica iniziale del driver per i nuovi controller del movimento HP. Compatibile con Windows 10, versione 1903 e versioni più recente. Questo driver è compatibile solo con i nuovi controller del movimento HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809. Compatibile con Windows 10, versione 1803 e versioni più recente.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 aprile 2018      | Versione pubblica iniziale del driver per Windows 10 versione 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 ottobre 2017    | Versione pubblica iniziale del driver                          |

### <a name="mixed-reality-portal-release-history"></a>Portale realtà mista delle versioni ###

In Windows 10, versione 1809 e versioni più Portale realtà mista [viene](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) aggiornato tramite l'app Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versione 1809 e più recente ####

   | Versione            | Data di rilascio          | Modifiche principali                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 giugno 2021          | <ul><li>Aggiunge collegamenti per la risoluzione dei problemi all'app Richiesta supporto errori comuni del visore VR.</li><li>Risolve un problema a causa del quale l'app complementare del dispositivo visore VR potrebbe essere ignorata durante la configurazione iniziale.</li><li>Aggiorna la pagina dei requisiti di sistema con informazioni aggiuntive per i visori VR ad alta risoluzione.</li><li>Aggiorna la schermata iniziale e la pagina di destinazione con nuovi oggetti visivi.</li></ul>  |
   | 2000.21041.1051.0  | 26 aprile 2021        | <ul><li>Aggiorna l'icona dell'app per Portale realtà mista.</li></ul>  |
   | 2000.20111.1381.0  | 10 dicembre 2020     | <ul><li>Aggiorna la pagina di destinazione di Portale realtà mista.</li><li>Riduce gli errori di connettività del visore VR durante gli aggiornamenti del firmware. </li></ul>  |
   | 2000.20071.1133.0  | 5 agosto 2020        | <ul><li>Supporto per [OpenXR per](/windows/mixed-reality/openxr) sospendere la finestra di anteprima.</li></ul>  | 
   | 2000.20041.1212.0  | 11 maggio 2020          | <ul><li>Risolve un problema di temporizzazione che ha generato un errore 15-5 incoerente.</li><li>Supporto migliorato per l'Windows Mixed Reality senza connessione Internet.</li><li>Supporto migliorato per l'associazione dei controller del movimento tramite **i controller di installazione**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 aprile 2020        | <ul><li>Supporto per l'iscriversi per ottenere informazioni, suggerimenti e offerte su Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 febbraio 2020     | <ul><li>Supporto migliorato per le applicazioni che [usano OpenXR](/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li><li>Risoluzione dei problemi di accessibilità e dello stato attivo della tastiera</li></ul>  | 
   | 2000.19101.1211.0  | 11 novembre 2019     | <ul><li>Risolve un problema che impedisce l'aggregazione di oggetti visivi limite della stanza.</li><li>Risolve un problema che impedisce di centrare un visore VR durante la configurazione dei limiti della stanza.</li></ul>  | 
   | 2000.19081.1301.0  | 23 settembre 2019    | <ul><li>Risolve un problema a causa del quale nei visori VR con problemi hardware viene visualizzato un messaggio di errore non corretto. Gli utenti che hanno ricevuto un codice di errore 1-4 nelle versioni precedenti possono ora ricevere un codice di errore più specifico per lo stato del dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 agosto 2019     | <ul><li>Supporto per le applicazioni che [usano OpenXR](/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 luglio 2019         | <ul><li>Supporto per le opzioni di configurazione JSON per personalizzare il comportamento dell'app. Per altre informazioni, [vedere Configurare l'intrattenimento basato sulla posizione con Windows Mixed Reality](/windows/mixed-reality/location-based-experiences#setup).</li></ul>  | 

### <a name="steamvr-release-history"></a>Cronologia delle versioni di SteamVR ###

Le note sulla versione di Valve per SteamVR sono disponibili qui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality per la cronologia delle versioni di SteamVR ###

Le note sulla versione per Windows Mixed Reality per il componente SteamVR sono disponibili qui:[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
