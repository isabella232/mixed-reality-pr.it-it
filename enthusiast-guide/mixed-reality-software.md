---
title: Panoramica del software e cronologia delle versioni
description: Panoramica dei componenti software principali per Windows Mixed Reality, visori immersivi e cronologia delle versioni.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, componenti software, cronologia delle versioni, note sulla versione, cronologia delle versioni
appliesto:
- Windows 10
ms.openlocfilehash: 51c13326d2ad8aebe164e64d0bfc380923a91d1be02cea840cec4addd062533f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219727"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Panoramica e cronologia delle versioni del software Realtà mista

## <a name="introduction-to-mixed-reality-software"></a>Introduzione al software di realtà mista

Windows Mixed Reality è costituito dai componenti software principali seguenti:

1. **Portale realtà mista**, che offre l'esperienza Windows Mixed Reality principale
    * Nelle Windows 10 1709 e 1803, Portale realtà mista è un componente chiave del sistema operativo Windows 10 aggiornato tramite Windows Update.
    * In Windows 10 1809 e versioni più Portale realtà mista aggiornamento tramite l'app Microsoft Store.
2. Il **pacchetto fod (Feature On Demand Package)** di realtà mista, scaricato e installato automaticamente durante Portale realtà mista prima esecuzione. Altre informazioni sul pacchetto FOD sono disponibili [qui](/windows/application-management/manage-windows-mixed-reality)
3. Il driver visore visore e controller di movimento di Realtà mista, noto anche come driver HoloLens Sensors, è il pacchetto driver chiave che consente ai visori Windows Mixed Reality di funzionare con Windows Mixed Reality. Questo viene scaricato e installato automaticamente tramite Windows la prima volta che il visore di realtà mista è collegato e viene aggiornato regolarmente tramite Windows Update
4. I driver del modello di controller di movimento **Realtà mista contengono i modelli 3D dei controller di movimento di realtà mista e sono necessari per esperienze di realtà mista di terze parti. Questo viene scaricato e installato automaticamente tramite Windows Aggiorna la prima volta che i controller di movimento di realtà mista vengono associati al PC e vengono aggiornati tramite Windows Update
5. **Windows 10 versione 1709 (Fall Creator's Update)** o versione successiva contiene componenti e tecnologie chiave del sistema operativo che Windows Mixed Reality

L Windows Mixed Reality in SteamVR richiede il software seguente:

6. **SteamVR,** sviluppato e gestito da Valve Corporation che consente app e giochi di realtà virtuale su Steam. Altre informazioni sono disponibili [qui](https://go.microsoft.com/fwlink/?linkid=862788)
7. Il **Windows Mixed Reality per il componente SteamVR,** che consente il bridge di SteamVR con Windows Mixed Reality. Altre informazioni su questo componente sono disponibili nella [pagina Windows Mixed Reality per SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gestione del visore Windows Mixed Reality visore:

8. **L'app Device Companion,** sviluppata e gestita da ognuno dei produttori di visori, offre una rapida introduzione al visore Windows Mixed Reality visore. Nei visori con funzionalità di Bluetooth integrata, l'app Device Companion consente di ripristinare i controller di movimento nella propria Bluetooth di dispositivi. Alcuni visori (ad esempio Samsung Odyssey e Samsung Odyssey+) usano anche l'app Device Companion per distribuire gli aggiornamenti del firmware del visore dal produttore del visore. Questa app viene scaricata automaticamente la prima volta che il visore è collegato ed è disponibile nel menu Start Windows di avvio.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 note sulla versione - Maggio 2020

L'aggiornamento Windows 10 maggio **2020 (v2004)** include nuove funzionalità per i visori Windows Mixed Reality (VR), ad esempio la possibilità di avviare applicazioni Win32 nel ambiente iniziale. HoloLens (prima generazione) si trova in Long Term Servicing (LTS), con aggiornamenti di manutenzione che verranno rilasciati mensilmente.

Aggiornamento alla versione più recente del PC Windows Mixed Reality visori vr immersive, aprire Impostazioni > **Update & Security** (Verifica disponibilità **aggiornamenti).** In un PC Windows 10, è anche possibile installare manualmente l'aggiornamento **Windows 10 maggio 2020** usando lo strumento Windows [di creazione di supporti.](https://www.microsoft.com/software-download/windows10)

**Versione più recente per desktop:** Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Aggiornamenti per Windows Mixed Reality visori immersive

#### <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge

Come [annunciato in](/windows/mixed-reality/new-microsoft-edge)precedenza, sono stati apportati aggiornamenti per un supporto migliore usando il nuovo browser Microsoft Edge in Windows Mixed Reality. Il nuovo Microsoft Edge adotta il Chromium open source per creare una migliore compatibilità Web per i clienti e una minore frammentazione del Web per tutti gli sviluppatori Web. Supporta anche WebXR, il nuovo standard per la creazione di esperienze Web immersive per visori VR, al posto di WebVR.

#### <a name="improved-settings-for-wmr"></a>Miglioramento Impostazioni per WMR

Grazie ai commenti e suggerimenti, sono state aggiunte e chiarite le impostazioni nella pagina di visualizzazione visore:

* **Qualità visiva della casa:** la modifica di queste impostazioni influisce solo sull'ambiente ambiente iniziale (Casa sulla scogliera e Skyloft):

* **Regolare il livello di dettaglio e la** qualità degli effetti nel ambiente iniziale: questa modifica modifica parte del rendering influisce sull'uso nella home page. In particolare, la qualità visiva dei diversi materiali (wood, concrete e così via) verrà ridimensionata quando si modifica questa impostazione da bassa a alta.

* **Modificare la risoluzione della finestra** dell'app: per impostazione predefinita, la maggior parte delle finestre 2D avviate nella home viene avviata con una risoluzione di 720 p. Anche se è possibile ridimensionarle manualmente & verticalmente, è anche possibile scegliere di avviarle tutte a 1080p. In precedenza questa opzione era disponibile come opzione Molto alta (beta) in Qualità visiva. È stata suddivisa in modo appropriato come impostazione separata.

* **Opzioni di esperienza:** queste opzioni modificano l'esperienza di realtà mista per ridurre il carico sui sistemi in cui l'hardware potrebbe fare fatica a tenere il passo con un numero illimitato di 90 fps. È possibile abilitare o disabilitare in modo esplicito queste impostazioni aggiuntive oppure scegliere Consenti Windows decidere e lasciare che l'euristica continui a decidere quando attivare e disattivare queste impostazioni.

* **Risoluzione:** se si dispone di un visore ad alta risoluzione come HP Reverb, è possibile eseguire il dispositivo alla risoluzione nativa o a una risoluzione ridotta per motivi di prestazioni. I visori precedenti, ad esempio Samsung Odyssey e Odyssey+, supportano solo una singola risoluzione, quindi non è possibile modificare questa impostazione su tali visori.

* **Frequenza fotogrammi:** è ora possibile impostare manualmente la frequenza dei fotogrammi dello schermo del visore o continuare Windows usare l'euristica per determinare se 60 Hz o 90 Hz è più appropriato.

* **Calibrazione:** come in precedenza, è possibile regolare l'IPD (distanza interpupillare) se supportato dal visore.

* **Cambio di input:** attiva/disattiva il comportamento del cambio dello stato attivo di input (Win+Y) in modo che sia automatico (in base al feedback del sensore di presenza) o manuale.

#### <a name="new-cortana-app"></a>Nuova Cortana app

Questo aggiornamento a Windows include la versione più recente dell'app Cortana, che attualmente è solo inglese negli Stati Uniti e non supporta più determinati comandi specifici della realtà mista, ad esempio "Scatta una foto" e "Scatta un video". È possibile usare il nuovo Cortana per avviare le app e supporta anche nuovi comandi incentrati sulla produttività, ad esempio "When's my next meeting?" o "Send an email to <name> that I'm running late".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Aggiornamenti aggiuntivi disponibili in 19041.546 (data di rilascio ottobre 2020)

Questo aggiornamento di manutenzione mensile desktop include le modifiche seguenti per Windows Mixed Reality dispositivi: 
* Riduce le distorsioni e le aberrazioni Windows Mixed Reality display montati sulla testa (HMD). 
* Aggiunge il supporto per i controller di movimento Windows Mixed Reality HP. 
* Modifica il comportamento dell'impostazione della frequenza di aggiornamento a 90 Hz in Windows Mixed Reality per non tornare più automaticamente a 60 Hz in determinati casi quando non è possibile ottenere 90 Hz. 

#### <a name="help-us-improve"></a>Aiutaci a migliorare.

Microsoft cerca continuamente di migliorare la compatibilità.  Se l'applicazione Win32 classica preferita non funziona correttamente mentre Windows Mixed Reality, inviare commenti e suggerimenti tramite il Hub di Feedback [.](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

### <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - Maggio 2019](release-notes-may-2019.md)
* [Note sulla versione - ottobre 2018](release-notes-october-2018.md)
* [Note sulla versione - Aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Cronologia delle versioni del driver di visore di realtà mista e del driver del controller di movimento ###

Questo driver viene scaricato e installato automaticamente tramite Windows Update, ma i collegamenti di download vengono forniti inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 versione 2004 (aggiornamento di maggio 2020) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 marzo 2021  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Aggiornare l'ordine di avvolgimento della mesh dell'area nascosta perché HP Reverb G2 sia coerente con altri visori.</li><li>Miglioramenti della qualità degli oggetti visivi per i visori HP Reverb G2.</li><li>Windows Mixed Reality alla piattaforma visore e all'affidabilità.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 dicembre 2020  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Nuovo firmware del controller per hp Controller per risolvere un problema a causa del quale alcuni controller dispongono di trigger non funzionanti.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 ottobre 2020  | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Supporto ufficiale per HP Reverb G2, HP Omnicept e il nuovo controller HP.</li><li>Correzioni dello schermo secondarie per i visori HP Reverb e Samsung Odyssey+. (Richiede la build del sistema operativo [19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) o versione successiva o build del sistema operativo [18362.1110 e 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) o versioni successive).</li><li>Miglioramenti alla transizione dello stato di alimentazione del computer dalla sospensione per ridurre gli errori SWW 1-4.</li><li>Windows Mixed Reality correzioni secondarie della piattaforma visore e miglioramenti all'affidabilità.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 maggio 2020      | Compatibile con Windows 10, versione 1903 e versioni più recente.<br/><ul><li>Windows Mixed Reality correzioni secondarie della piattaforma visore e miglioramenti all'affidabilità.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10 versione 1903 (aggiornamento di maggio 2019) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 ottobre 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Windows Mixed Reality correzioni secondarie della piattaforma visore.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 giugno 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Windows Mixed Reality alla piattaforma visore e all'affidabilità per i computer in sospensione e le transizioni dello stato di alimentazione.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1° maggio 2019      | Compatibile con Windows 10, versione 1809 e versioni più nuove.<br/><ul><li>Contiene l'aggiornamento del firmware per acer, Asus, Dell, Fujitsu, HP, Lenovo e Medion Windows Mixed Reality visori. Questo aggiornamento del firmware migliora la compatibilità e l'affidabilità dello schermo del visore con determinati adattatori grafici o driver di grafica.</li><li>Windows Mixed Reality Windows Mixed Reality della piattaforma visore e dell'affidabilità</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10 versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 gennaio 2019      | Compatibile con Windows 10, versione 1803 e versioni più nuove.<br/><ul><li>Correzioni di jitter e stutter di rilevamento delle cuffia</li><li>Correzioni di affidabilità della modalità torcia</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1° ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809.<br/>Compatibile con Windows 10, versione 1803 e versioni più nuove.<br/><ul><li>Abilita nuove Windows Mixed Reality, ad esempio la modalità torcia elettrica, in Windows 10, versione 1809</li><li>Miglioramenti del rilevamento e dell'affidabilità delle cuffia</li><li>Miglioramenti del rilevamento e delle prestazioni del controller di movimento</li><li>Prestazioni e miglioramenti usb</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 aprile 2018      | Versione pubblica iniziale del driver per Windows 10 versione 1803<br/> <ul><li>Miglioramenti del rilevamento e dell'affidabilità delle cuffia</li><li>Miglioramenti del rilevamento e delle prestazioni del controller di movimento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 febbraio 2018    | <ul><li>Supporto ufficiale per il visore 3Glasses Blubur S2 Mixed Reality</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 dicembre 2017   | <ul><li>Risolve il problema HID che *causava* un errore del codice di errore 2181038087-7 in alcuni PC</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 dicembre 2017    | <ul><li>Rilevamento visore migliorato</li><li>Miglioramenti della velocità di risposta del touchpad del controller di movimento</li><li>Risolve il problema a causa del quale l'installazione del driver potrebbe talvolta non riuscire</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 novembre 2017   | <ul><li>Risolve un problema che causava la visualizzazione di visori a volte in nero durante l'uso</li><li>Risolve un problema che talvolta causava la scomparsa dei controller di movimento</li><li>Miglioramenti delle prestazioni del sensore di presenza per il visore Dell Visor</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | 10.0.16299.1036  | 7 novembre 2017    | <ul><li>Miglioramenti del meccanismo di generazione del controller di movimento:<ul><li>La velocità verrà ora segnalata correttamente quando l'accuratezza della posizione è approssimativa, quindi è ora possibile gettare dietro la testa.</li><li>Il codice di esempio per la generazione è disponibile nel pacchetto unity "ThrowingStarter" [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Aprire la scena di lancio per iniziare</li></ul></li><li>Segnalazione migliorata della batteria del controller di movimento</li><li>Varie correzioni di stabilità e affidabilità</li></ul> |
   | 10.0.16299.1012  | 17 ottobre 2017    | Versione pubblica iniziale del driver                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Cronologia di rilascio del driver del modello di controller di movimento di realtà mista ###

Questo driver viene scaricato e installato automaticamente anche tramite Windows Update, ma i collegamenti di download vengono forniti inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 versione 2004 (aggiornamento di maggio 2020)

| Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 settembre 2020      | Versione pubblica iniziale del driver per i nuovi controller di movimento HP. Compatibile con Windows 10, versione 1903 e versioni più recente. Questo driver è compatibile solo con i nuovi controller HP Motion.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10 versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1° ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809. Compatibile con Windows 10, versione 1803 e versioni più nuove.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 aprile 2018      | Versione pubblica iniziale del driver per Windows 10 versione 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 ottobre 2017    | Versione pubblica iniziale del driver                          |

### <a name="mixed-reality-portal-release-history"></a>Portale realtà mista delle versioni ###

In Windows 10, versione 1809 e versioni più Portale realtà mista [viene](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) aggiornato tramite l'app Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versione 1809 e più recente ####

   | Versione            | Data di rilascio          | Modifiche principali                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 giugno 2021          | <ul><li>Aggiunge collegamenti per la risoluzione dei problemi all'app Richiesta supporto per gli errori comuni del visore VR.</li><li>Risolve un problema a causa del quale l'app complementare del dispositivo visore VR potrebbe essere ignorata durante la configurazione iniziale.</li><li>Aggiorna la pagina dei requisiti di sistema con informazioni aggiuntive per i visori VR ad alta risoluzione.</li><li>Aggiorna la schermata iniziale e la pagina di destinazione con nuovi oggetti visivi.</li></ul>  |
   | 2000.21041.1051.0  | 26 aprile 2021        | <ul><li>Aggiorna l'icona dell'app per Portale realtà mista.</li></ul>  |
   | 2000.20111.1381.0  | 10 dicembre 2020     | <ul><li>Aggiorna la pagina di destinazione di Portale realtà mista.</li><li>Riduce gli errori di connettività del visore VR durante gli aggiornamenti del firmware. </li></ul>  |
   | 2000.20071.1133.0  | 5 agosto 2020        | <ul><li>Supporto per [OpenXR per](/windows/mixed-reality/openxr) sospendere la finestra di anteprima.</li></ul>  | 
   | 2000.20041.1212.0  | 11 maggio 2020          | <ul><li>Risolve un problema di temporizzazione che ha generato un errore 15-5 incoerente.</li><li>Supporto migliorato per l'Windows Mixed Reality senza connessione Internet.</li><li>Supporto migliorato per l'associazione dei controller del movimento tramite **i controller di installazione**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 aprile 2020        | <ul><li>Supporto per l'iscriversi per ottenere informazioni, suggerimenti e offerte Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 febbraio 2020     | <ul><li>Supporto migliorato per le applicazioni che [usano OpenXR](/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li><li>Risoluzione dei problemi di accessibilità e dello stato attivo della tastiera</li></ul>  | 
   | 2000.19101.1211.0  | 11 novembre 2019     | <ul><li>Risolve un problema che impedisce l'aggregazione di oggetti visivi limite della stanza.</li><li>Risolve un problema che impedisce di centrare un visore VR durante la configurazione dei limiti della stanza.</li></ul>  | 
   | 2000.19081.1301.0  | 23 settembre 2019    | <ul><li>Risolve un problema a causa del quale nei visori VR con problemi hardware viene visualizzato un messaggio di errore non corretto. Gli utenti che hanno ricevuto un codice di errore 1-4 nelle versioni precedenti possono ora ricevere un codice di errore più specifico per lo stato del dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 agosto 2019     | <ul><li>Supporto per le applicazioni che [usano OpenXR](/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 luglio 2019         | <ul><li>Supporto per le opzioni di configurazione JSON per personalizzare il comportamento dell'app. Per altre informazioni, vedere https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Cronologia delle versioni di SteamVR ###

Le note sulla versione di Valve per SteamVR sono disponibili qui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality per la cronologia delle versioni di SteamVR ###

Le note sulla versione per Windows Mixed Reality per il componente SteamVR sono disponibili qui:[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
