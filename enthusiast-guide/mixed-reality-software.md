---
title: Panoramica e cronologia delle versioni del software Realtà mista
description: Panoramica dei principali componenti software per la realtà mista di Windows e della relativa cronologia di rilascio
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, componenti software, cronologia delle versioni, note sulla versione, cronologia delle versioni
appliesto:
- Windows 10
ms.openlocfilehash: 0dd2ef30252189d006bfaf5702c47dce72f2798d
ms.sourcegitcommit: d8db38647cf45f05b9445ceaf057d4cd01721ee6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97091305"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Panoramica e cronologia delle versioni del software Realtà mista

## <a name="introduction-to-mixed-reality-software"></a>Introduzione al software per realtà mista

La realtà mista di Windows è costituita dai componenti software principali seguenti:

1. **Portale per la realtà mista**, che fornisce la principale esperienza della realtà mista di Windows
    * In Windows 10, versioni 1709 e 1803, il portale di realtà mista è un componente chiave del sistema operativo Windows 10 e viene aggiornato tramite Windows Update.
    * In Windows 10, versione 1809 e successive, il portale di realtà mista viene aggiornato tramite l'app Microsoft Store.
2. Il **pacchetto di funzionalità per la realtà mista** (Dom), scaricato e installato automaticamente durante la prima esecuzione del portale di realtà mista. Altre informazioni sul pacchetto Dom sono disponibili [qui](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)
3. Il **driver** per la realtà mista e il driver del controller di movimento, noto anche come driver HoloLens Sensors, è il pacchetto di driver chiave che consente di usare le cuffie di realtà miste di Windows con la realtà mista di Windows. Questa operazione viene scaricata e installata automaticamente tramite Windows Update la prima volta che si collega la cuffia a realtà mista e viene regolarmente aggiornata tramite Windows Update
4. I **driver del modello a realtà mista Motion controller** contengono i modelli 3D dei controller di movimento della realtà mista e sono necessari per esperienze di realtà miste di terze parti. Questa operazione viene scaricata e installata automaticamente tramite Windows Update la prima volta che i controller di movimento della realtà mista vengono associati al PC e vengono aggiornati tramite Windows Update
5. **Windows 10, versione 1709 (l'aggiornamento di Fall Creator) o più recente** contiene componenti chiave del sistema operativo e tecnologie che consentono la realtà mista di Windows

Inoltre, l'uso della realtà mista di Windows in SteamVR richiede il seguente software:

6. **SteamVR**, sviluppato e gestito da Valve Corporation che consente app e giochi per la realtà virtuale su Steam. Altre informazioni sono disponibili [qui](https://go.microsoft.com/fwlink/?linkid=862788)
7. **Realtà mista di Windows per** il componente SteamVR, che colma SteamVR con la realtà mista di Windows. Altre informazioni su questo componente sono disponibili [nella pagina realtà mista di Windows per SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gestione dell'auricolare della realtà mista di Windows:

8. L' **app complementare per dispositivi**, sviluppata e gestita da ciascuno dei produttori di auricolari, fornisce una rapida introduzione all'auricolare della realtà mista di Windows. Con le cuffie con funzionalità Bluetooth integrate, l'app per dispositivi complementari consente di ripristinare i controller di movimento nell'associazione Bluetooth di fabbrica. Alcuni auricolari, ad esempio Samsung Odyssey e Samsung Odyssey +, usano anche l'app Device Companion per distribuire gli aggiornamenti del firmware dell'auricolare dal produttore dell'auricolare. Questa app viene scaricata automaticamente la prima volta che l'auricolare è collegato e si trova nel menu Start di Windows.

## <a name="windows-10-release-notes---may-2020"></a>Note sulla versione di Windows 10-maggio 2020

**Windows 10 May 2020 Update (v2004)** include nuove funzionalità per le cuffie per la realtà mista di Windows (VR), ad esempio la possibilità di avviare applicazioni Win32 nella Home realtà mista. HoloLens (1a generazione) è in manutenzione a lungo termine, con aggiornamenti di manutenzione da rilasciare mensilmente.

Per eseguire l'aggiornamento alla versione più recente sul PC per gli auricolari per la realtà mista di Windows (VR), aprire l'app **Impostazioni** , passare a **Aggiorna & sicurezza**, quindi selezionare il pulsante **Verifica aggiornamenti** . In un PC Windows 10, è anche possibile installare manualmente l' **aggiornamento di Windows 10 May 2020** usando lo [strumento di creazione di Windows Media](https://www.microsoft.com/software-download/windows10).

**Versione più recente per desktop**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Aggiornamenti per gli auricolari immersivi a realtà mista di Windows

#### <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge
Come [annunciato in precedenza](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), sono stati apportati aggiornamenti per un supporto migliore con il nuovo browser Microsoft Edge in realtà mista di Windows. Il nuovo Microsoft Edge adotta il progetto Chromium open source per creare una migliore compatibilità Web per i clienti e meno frammentazione del Web per tutti gli sviluppatori Web. Supporta anche WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR, al posto di WebVR.

#### <a name="improved-settings-for-wmr"></a>Impostazioni migliorate per WMR
Grazie ai commenti e suggerimenti, abbiamo aggiunto e chiarito le impostazioni nella pagina di visualizzazione dell'auricolare:

* **Qualità visiva della Home** : la modifica di queste impostazioni influiscono solo sull'ambiente di casa realtà mista (Cliff House e Skyloft):

* **Modificare il livello di dettaglio e la qualità degli effetti nella Home realtà mista** : in questo modo vengono modificati alcuni effetti sul rendering usati nella Home page. In particolare, la qualità visiva dei diversi materiali (legno, calcestruzzo e così via) verrà ridimensionata quando si modifica questa impostazione da bassa ad alta.

* **Modificare la risoluzione della finestra dell'app** : per impostazione predefinita, la maggior parte delle finestre 2D avviate nella Home page viene avviata con una risoluzione 720p. Sebbene sia possibile ridimensionarli manualmente orizzontalmente & verticalmente, è anche possibile scegliere di avviarli tutti a 1080p. In precedenza questa opzione era disponibile come opzione molto alta (beta) in qualità visiva. È stato suddiviso in modo appropriato come impostazione separata.

* **Opzioni di esperienza** : queste opzioni consentono di modificare l'esperienza di realtà mista per ridurre il carico sui sistemi in cui l'hardware potrebbe avere difficoltà a tenere il passo con un 90 fps senza restrizioni. È possibile scegliere di abilitare o disabilitare in modo esplicito queste impostazioni aggiuntive oppure scegliere Consenti a Windows di decidere e lasciare che l'euristica continui a decidere quando attivare e disattivare queste impostazioni.

* **Risoluzione** : se si dispone di una cuffia ad alta risoluzione come il reverbio di HP, è supportata l'esecuzione con la risoluzione nativa oppure con una risoluzione ridotta per motivi di prestazioni. Gli auricolari precedenti, come Samsung Odyssey ed Odyssey +, supportano solo una singola risoluzione, in modo da non poter modificare questa impostazione in tali auricolari.

* **Frequenza dei fotogrammi** : è ora possibile impostare manualmente la frequenza dei fotogrammi dello schermo della cuffia oppure continuare a consentire a Windows di usare l'euristica per determinare se 60 hz o 90 Hz sono più appropriati.

* **Taratura** : come prima, è possibile regolare il dpi (interpupillare distance) se supportato dall'auricolare.

* **Commutazione di input** : attivare o disattivare il comportamento di commutazione dello stato attivo (Win + Y) automatico (in base ai commenti del sensore di presenza) o manuale.

#### <a name="new-cortana-app"></a>Nuova app Cortana
Questo aggiornamento a Windows include la versione più recente dell'app Cortana, che attualmente è solo in lingua inglese (Stati Uniti) e non supporta più alcuni comandi specifici della realtà mista, ad esempio "scattare un'immagine" e "scattare un video". Sarà comunque possibile usare la nuova Cortana per avviare le app e supportare anche nuovi comandi mirati per la produttività, ad esempio, "quando il prossimo incontro?" oppure "Invia un messaggio di posta elettronica a <name> che sto eseguendo tardi".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Aggiornamenti aggiuntivi disponibili nel 19041,546 (rilasciato ottobre 2020)
Questo aggiornamento di manutenzione mensile del desktop include le modifiche seguenti per i dispositivi di realtà mista di Windows: 
* Consente di ridurre le distorsioni e le aberrazioni nelle visualizzazioni montate in realtà mista di Windows (HMD). 
* Aggiunge il supporto per i controller di movimento della realtà mista di HP Windows imminenti. 
* Modifica il comportamento dell'impostazione della frequenza di aggiornamento 90Hz in realtà mista di Windows in modo che non venga più riattivato automaticamente a 60Hz in alcuni casi quando non è possibile ottenere 90Hz. 

#### <a name="please-help-us-improve"></a>Aiutaci a migliorare!
Si cerca continuamente di migliorare la compatibilità.  Se le applicazioni Win32 classiche preferite non si comportano correttamente durante la realtà mista di Windows, inviare commenti e suggerimenti tramite l'hub per i [Commenti](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione-2019 maggio](release-notes-may-2019.md)
* [Note sulla versione - ottobre 2018](release-notes-october-2018.md)
* [Note sulla versione-2018 aprile](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Cronologia delle versioni dell'auricolare e del controller di movimento per la realtà mista ###

Questo driver viene scaricato e installato automaticamente tramite Windows Update, ma i collegamenti al download vengono forniti inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versione 2004 (aggiornamento di maggio 2020) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | Decimo dicembre 2020  | Compatibile con Windows 10, versione 1903 e versioni successive.<br/><ul><li>Nuovo firmware del controller per il controller HP per risolvere un problema per cui alcuni controller hanno trigger non funzionanti.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 ottobre 2020  | Compatibile con Windows 10, versione 1903 e versioni successive.<br/><ul><li>Supporto ufficiale per HP reverbi G2, HP Omnicept e il nuovo controller HP.</li><li>Correzioni di visualizzazione secondarie per gli auricolari HP Reverb e Samsung Odyssey +. (Richiede la [Build del sistema operativo 19041,546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) o versioni successive oppure [Build del sistema operativo 18362,1110 e 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) o versione successiva).</li><li>Miglioramenti delle transizioni dello stato di alimentazione del computer dalla sospensione per ridurre gli errori di SWW 1-4.</li><li>Correzioni e miglioramenti dell'affidabilità della piattaforma per l'auricolare della realtà mista di Windows.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 maggio, 2020      | Compatibile con Windows 10, versione 1903 e versioni successive.<br/><ul><li>Correzioni e miglioramenti dell'affidabilità della piattaforma per l'auricolare della realtà mista di Windows.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versione 1903 (aggiornamento di maggio 2019) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 ottobre 2019      | Compatibile con Windows 10, versione 1809 e versioni successive.<br/><ul><li>Correzioni minime della piattaforma per l'auricolare della realtà Windows mista.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 giugno, 2019      | Compatibile con Windows 10, versione 1809 e versioni successive.<br/><ul><li>Funzionalità di Windows Mixed Reality Headset e miglioramenti dell'affidabilità per i computer in sospensione e le transizioni di stato dell'alimentazione.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1° maggio 2019      | Compatibile con Windows 10, versione 1809 e versioni successive.<br/><ul><li>Contiene l'aggiornamento del firmware per 2017 Acer, ASUS, Dell, Fujitsu, HP, Lenovo e Medion Windows Mixed Reality Headset. Questo aggiornamento del firmware migliora la compatibilità e l'affidabilità di visualizzazione dell'auricolare con determinati adattatori grafici e/o driver di grafica.</li><li>Miglioramenti all'affidabilità e alla piattaforma per l'auricolare della realtà mista Windows</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 gennaio 2019      | Compatibile con Windows 10, versione 1803 e versioni successive.<br/><ul><li>Correzioni di jitter e balbetta Tracking per le cuffie</li><li>Correzioni di affidabilità in modalità torcia</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 ° ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809.<br/>Compatibile con Windows 10, versione 1803 e versioni successive.<br/><ul><li>Abilita nuove funzionalità della realtà mista di Windows, ad esempio la modalità torcia, in Windows 10 versione 1809</li><li>Miglioramenti dell'affidabilità e del rilevamento delle cuffie</li><li>Miglioramento delle prestazioni e del rilevamento del controller di movimento</li><li>Miglioramenti e prestazioni USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 aprile 2018      | Versione pubblica iniziale del driver per Windows 10 versione 1803<br/> <ul><li>Miglioramenti dell'affidabilità e del rilevamento delle cuffie</li><li>Miglioramento delle prestazioni e del rilevamento del controller di movimento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 febbraio, 2018    | <ul><li>Supporto ufficiale per l'auricolare della realtà mista 3Glasses Blubur S2</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 dicembre, 2017   | <ul><li>Risolve il problema nascosto. si *è verificato un* errore nel codice di errore 2181038087-7 in alcuni computer</li><li>Diverse correzioni per la stabilità e l'affidabilità</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 dicembre 2017    | <ul><li>Rilevamento delle cuffie migliorato</li><li>Miglioramenti della velocità di risposta touchpad del controller di movimento</li><li>Risolve un problema a causa del quale l'installazione del driver potrebbe non riuscire</li><li>Diverse correzioni per la stabilità e l'affidabilità</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 novembre, 2017   | <ul><li>Risolve un problema che ha causato la visualizzazione dell'auricolare a volte in nero durante l'uso</li><li>Risolve un problema che talvolta ha causato la scomparsa dei controller di movimento</li><li>Miglioramenti delle prestazioni del sensore di presenza per l'auricolare dell visiera</li><li>Diverse correzioni per la stabilità e l'affidabilità</li></ul> |
   | 10.0.16299.1036  | 7 novembre, 2017    | <ul><li>Motion controller che genera miglioramenti meccanici:<ul><li>La velocità verrà ora segnalata correttamente quando l'accuratezza della posizione è approssimativa, quindi è ora possibile generare un'operazione dietro la testa.</li><li>Il codice di esempio per la generazione di è reperibile [nel pacchetto](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)Unity "ThrowingStarter". Apri la scena di lancio per iniziare</li></ul></li><li>Segnalazione migliorata della batteria del controller di movimento</li><li>Diverse correzioni per la stabilità e l'affidabilità</li></ul> |
   | 10.0.16299.1012  | 17 ottobre 2017    | Versione pubblica iniziale del driver                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Cronologia delle versioni del driver del modello di reality Motion controller ###

Questo driver viene scaricato e installato automaticamente anche tramite Windows Update, ma i collegamenti al download vengono forniti inline:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versione 2004 (aggiornamento di maggio 2020)

| Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 settembre, 2020      | Versione pubblica iniziale del driver per i nuovi controller di movimento di HP. Compatibile con Windows 10, versione 1903 e versioni successive. Questo driver è compatibile solo con i nuovi controller di movimento di HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versione 1803 (aggiornamento di aprile 2018) e versione 1809 (aggiornamento di ottobre 2018) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 ° ottobre 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1809. Compatibile con Windows 10, versione 1803 e versioni successive.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 aprile 2018      | Versione pubblica iniziale del driver per Windows 10, versione 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versione 1709 (Fall Creators Update) ####

   | Versione          | Data di rilascio          | Modifiche principali                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 ottobre 2017    | Versione pubblica iniziale del driver                          |

### <a name="mixed-reality-portal-release-history"></a>Cronologia delle versioni del portale per la realtà mista ###

In Windows 10, versione 1809 e successive, il [portale di realtà mista](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) viene aggiornato tramite l'app Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versione 1809 e successive ####

   | Versione            | Data di rilascio          | Modifiche principali                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 5 agosto 2020        | <ul><li>Supporto per [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) per sospendere la finestra di anteprima.</li></ul>  | 
   | 2000.20041.1212.0  | 11 maggio 2020          | <ul><li>Risolve un problema di temporizzazione che ha provocato un errore 15-5 incoerente.</li><li>Supporto migliorato per l'esecuzione di realtà mista di Windows senza connessione a Internet.</li><li>Supporto migliorato per l'associazione di controller di movimento tramite i **controller di configurazione**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 aprile 2020        | <ul><li>Supporto per l'iscrizione a informazioni, suggerimenti e offerte per la realtà mista di Windows.</li></ul>  | 
   | 2000.20011.1312.0  | 11 febbraio 2020     | <ul><li>Supporto migliorato per le applicazioni che usano [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li><li>Risolve i problemi di accessibilità e lo stato attivo della tastiera</li></ul>  | 
   | 2000.19101.1211.0  | 11 novembre 2019     | <ul><li>Risolve un problema che impedisce l'attivazione di oggetti visivi limite spazio.</li><li>Risolve un problema che impedisce di centrare un auricolare durante la configurazione dei limiti della stanza.</li></ul>  | 
   | 2000.19081.1301.0  | 23 settembre 2019    | <ul><li>Risolve un problema per cui gli auricolari che riscontrano problemi hardware hanno visualizzato un messaggio di errore non corretto. Gli utenti che hanno ricevuto un codice di errore 1-4 nelle versioni precedenti potrebbero ora ricevere un codice di errore più specifico per lo stato del dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 agosto, 2019     | <ul><li>Supporto per le applicazioni che usano [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) nei dispositivi con l'aggiornamento di maggio 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 luglio 2019         | <ul><li>Supporto per le opzioni di configurazione JSON per personalizzare il comportamento dell'app. Per altre informazioni https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup , vedere.</li></ul>  | 

### <a name="steamvr-release-history"></a>Cronologia delle versioni di SteamVR ###

Le note sulla versione di Valve per SteamVR sono disponibili qui: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Realtà mista di Windows per la cronologia delle versioni di SteamVR ###

Le note sulla versione per il componente realtà mista di Windows per SteamVR sono disponibili qui: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
