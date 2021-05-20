---
title: Domande frequenti sull'hardware immersive
description: Altri Windows Mixed Reality per la risoluzione dei problemi che vanno oltre la documentazione di supporto consumer standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Disinstallazione Windows Mixed Reality, Lingue supportate
appliesto:
- Windows 10
ms.openlocfilehash: ede2620ca6a47b085a3d7b54fd6df073bfaa528e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196596"
---
# <a name="other-questions"></a>Altre domande

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Il driver di grafica non è supportato (si verificano errori di errore del driver di grafica).

Cercare ed eseguire "dxdiag":

1.  Se il risultato è "Renderer di base", il driver di grafica non è installato. Per risolvere il problema:
    * Passare a **Gestione dispositivi e >'> ricerca di modifiche hardware.**
    * Usare Windows Update per aggiornare il driver.
    * Se il problema persiste, visitare il sito Web del produttore e installare l'aggiornamento più recente del driver. 
    * Se non è disponibile un aggiornamento per la GPU, WMR potrebbe non essere supportato nel dispositivo. Se si pensa che lo sia, contattare il [supporto tecnico](https://support.microsoft.com).
2.  Se si ottiene "WDDM 2.1" o una versione precedente, il driver di grafica è installato ma potrebbe non essere la versione più recente. Per ottenere la versione più recente:
    * Usare Windows Update per aggiornare il driver.
    * Se l'aggiornamento non risolve il problema, visitare il sito Web del produttore e installare l'aggiornamento più recente del driver. 
    * Se non è disponibile un aggiornamento per la GPU, WMR potrebbe non essere supportato nel dispositivo. Se si pensa che lo sia, contattare il [supporto tecnico](https://support.microsoft.com).

Se Windows Mixed Reality configurazione indica che la scheda grafica non soddisfa i requisiti e si pensa che lo sia, assicurarsi che il visore VR sia collegato alla scheda corretta.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>L'aggiornamento del firmware del visore VR Samsung Odyssey o Odyssey+ è bloccato.

Samsung possiede e pubblica gli aggiornamenti del firmware del visore VR tramite le app complementari per dispositivi "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey+Setup". Per altri dettagli e per informazioni sui problemi di aggiornamento del firmware Samsung, contattare il servizio clienti Samsung.

Se il processo di aggiornamento del firmware si blocca e non è stato fatto alcun avanzamento per più di cinque minuti:If the firmware update process is getting stuck, and there has been no progress for more than five minutes:

* Scollegare temporaneamente tutti gli altri dispositivi USB e ripetere l'aggiornamento del firmware.
* Connettere il visore Samsung a un'altra porta USB 3.0 nel PC.
* Disabilitare o disinstallare qualsiasi software installato che potrebbe interferire con gli aggiornamenti del firmware, ad esempio AORUS di Gigabyte App Center.
* Usare un PC diverso per aggiornare il firmware del visore Samsung.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Ricerca per categorie accedere al desktop del PC in realtà mista?
Avviare l'app Desktop nel visore da **Windows Button > Tutte le app** > Desktop per accedere al desktop del PC in realtà mista.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Come è possibile visualizzare più monitor in realtà mista

Per impostazione predefinita, l'app desktop passa automaticamente per visualizzare il monitoraggio con lo stato attivo. Per visualizzare tutti i monitoraggi in realtà mista:

* Selezionare l'icona del monitoraggio nell'angolo superiore sinistro dell'app.
* Disabilitare "Cambio automatico monitoraggio".
* Selezionare il monitoraggio che si vuole visualizzare.
* Avviare un'altra istanza dell'app Desktop.
* Selezionare il monitoraggio da visualizzare nell'istanza.
* Ripetere l'operazione per tutti i monitoraggi fisici.
Sarà necessario selezionare nuovamente il monitoraggio da visualizzare in ogni app desktop ogni volta che si riavvia la realtà mista.

## <a name="my-desktop-app-only-shows-a-black-screen"></a>L'app Desktop mostra solo una schermata nera

Se il PC ha una GPU ibrida Nvidia, il dispositivo Nvidia che esegue il runtimebroker.exe nella GPU discreta invece di quella integrata può essere il responsabile. Per risolvere questo problema, seguire queste istruzioni in "[Ricerca per categorie creare le impostazioni di Optimus per un nuovo programma?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" per aggiungere C:\windows\system32\runtimebroker.exe e forzare l'esecuzione nel processore "Grafica integrata". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa Windows Mixed Reality.

Se si usa una connessione Wi-Fi 2,4 GHz, i controller del movimento potrebbero rallentare il Wi-Fi:

* Passare a una connessione Wi-Fi 5 GHz, se disponibile. [Altre informazioni](https://support.microsoft.com/help/4000461)
* Usare un adattatore Bluetooth separato per connettere i controller del movimento al PC. Vedere [schede consigliate.](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Viene visualizzato un messaggio che indica di collegare e caricare il PC. Perché?

Se si usa un portatile, Windows Mixed Reality funziona meglio quando il PC è completamente caricato e collegato.

## <a name="what-is-the-experience-options-setting"></a>Che cos'è l'impostazione Opzioni esperienza?

**Le impostazioni > realtà mista > visore VR** > opzioni esperienza consentono di modificare le impostazioni Windows Mixed Reality prestazioni. In questo modo è possibile scegliere l'esperienza migliore per la configurazione hardware in un'ampia gamma di contenuti. Sono disponibili tre opzioni di esperienza tra cui scegliere:
* Automatico: Windows Mixed Reality determinerà l'esperienza migliore per la configurazione hardware. Per la maggior parte delle persone, questa è la scelta migliore per iniziare.
* 60 Hz: imposta la frequenza di aggiornamento su 60 Hz e disattiva determinate funzionalità, ad esempio l'acquisizione video e l'anteprima Portale realtà mista.
* 90 Hz: imposta la frequenza di aggiornamento su 90 Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Lingue supportate in Windows Mixed Reality

Windows Mixed Reality è disponibile nelle lingue seguenti:

* Cinese semplificato (Cina)
* Inglese (Australia)
* Inglese (Canada)
* Inglese (Gran Bretagna)
* Inglese (Stati Uniti)
* Francese (Canada)
* Francese (Francia)
* Tedesco (Germania)
* Italiano (Italia)
* Giapponese (Giappone)
* Spagnolo (Messico)
* Spagnolo (Spagna)

È possibile usare Windows Mixed Reality se il PC è impostato su una lingua diversa. Tuttavia, l'interfaccia verrà visualizzata in inglese (Stati Uniti) e i comandi vocali e la dettatura non saranno disponibili. La Windows Mixed Reality tastiera su schermo è solo inglese (Stati Uniti). Per immettere testo in un'altra lingua, usare una tastiera fisica connessa al PC. È anche possibile usare la dettatura in una delle lingue Windows Mixed Reality supportate elencate in precedenza: è sufficiente selezionare il microfono sulla tastiera su schermo.

Windows Mixed Reality è disponibile anche nelle lingue seguenti senza comandi vocali o funzionalità di dettatura:
* Cinese tradizionale (Taiwan e Hong Kong)
* Olandese (Paesi Bassi)
* Coreano (Corea)
* Russo (Russia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Ho domande sull'hardware del visore.

Per informazioni dettagliate sul visore, rivolgersi al produttore. Nella casella potrebbe essere presente una guida al prodotto oppure è possibile provare il sito Web del produttore.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Ricerca per categorie disinstallare Windows Mixed Reality?

1. Disconnettere il visore dal PC.
2. Chiudere Windows Mixed Reality portale.
2. Passare a  **Start > Settings > Mixed Reality** e selezionare "Uninstall".

Quando si è pronti per iniziare a usare di nuovo il visore, collegarlo e Windows Mixed Reality portale consente di eseguire la configurazione.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Viene visualizzato il messaggio "Non è stato possibile completare la Windows Mixed Reality".

Alcuni file, incluse le informazioni sull'ambiente, potrebbero essere ancora nel computer. Ciò può causare problemi se si decide di reinstallare Windows Mixed Reality in un secondo momento. È possibile rimuovere manualmente le informazioni Windows Mixed Reality dal PC modificando il Registro di sistema e usando Windows PowerShell per eseguire i comandi. _Se si modifica il Registro di sistema in modo non corretto, potrebbero verificarsi problemi gravi. Assicurarsi di seguire questi passaggi con attenzione. Per una maggiore protezione, eseguire il backup del Registro di sistema prima di modificarlo in modo da poterlo ripristinare in caso di problemi._ Per altre informazioni, vedere Come eseguire il backup e [il ripristino del Registro di sistema in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Per disinstallare La realtà mista di Windows usando questi comandi:
1. Riavvia il PC.
2. Nella casella **Cerca** digitare "regedit" e quindi selezionare "Sì".
3. Rimuovere questi valori del Registro di sistema:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, quindi eliminare "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, quindi eliminare "PreferDesktopSpeaker" e "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic,</b>quindi eliminare "DisableSpeechInput". Nota: gli elementi del Registro di HHKEY_CURRENT_USER devono essere eliminati per ogni account utente nel PC che ha usato Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, quindi eliminare "DeviceID" e "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, quindi eliminare "OnDeviceLearningCompleted".</li> 
   </ul>
4. Rimuovere le chiavi del Registro di sistema seguenti: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Chiudere l'editor del Registro di sistema.
6. Passare a **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** ed eliminare "RoomBounds.json". Ripetere questa operazione per ogni utente che ha usato Windows Mixed Reality.
7.Aprire il prompt dei comandi dell'amministratore e passare a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors.** Eliminare il contenuto della cartella "HeadTracking data" (ma non la cartella stessa).
8. Digitare "powershell" nella casella di ricerca, fare clic con il pulsante destro del mouse su "Windows PowerShell" e quindi scegliere "Esegui come amministratore".
9. In Windows PowerShell: <ul>
   <li>Al prompt dei comandi copiare e incollare <b>Dism /online /Get-Capabilities</b>, quindi premere INVIO.</b></li> 
   <li>Copiare l'identità della funzionalità che inizia con Analog.Holographic.Desktop. Se non è presente, l'elemento non è installato ed è possibile andare al passaggio 10.</li> 
   <li>Copiare e incollare il prompt dei comandi seguente, quindi premere INVIO: <b>Dism /online /Remove-Capability /CapabilityName: l'identità</b> della funzionalità copiata nell'ultimo passaggio</li>
   </ul>
10. Riavviare il PC.

