---
title: Altre domande
description: Ulteriori suggerimenti sulla risoluzione dei problemi di Windows Mixed Reality che vanno oltre la documentazione del supporto clienti standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto, disinstallazione di realtà mista di Windows, lingue supportate
appliesto:
- Windows 10
ms.openlocfilehash: aa61148a115ae295c1dc64b575a2fae7b0111470
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044463"
---
# <a name="other-questions"></a>Altre domande

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Il driver della grafica non è supportato (si verificano errori nel driver di grafica).

Cercare ed eseguire "dxdiag":

1.  Se il risultato è "renderer di base", il driver di grafica non è installato. Per risolvere il problema:
    * Passare a **Device Manager > azione > analizzare le modifiche apportate all'hardware** .
    * Utilizzare Windows Update per aggiornare il driver.
    * Se il problema persiste, accedere al sito Web del produttore e installare l'aggiornamento del driver più recente. 
    * Se un aggiornamento non è disponibile per la GPU, è possibile che WMR non sia supportato nel dispositivo. Se lo si ritiene necessario, contattare il [supporto tecnico](https://support.microsoft.com).
2.  Se si ottiene una versione "WDDM 2,1" o una versione precedente, il driver di grafica viene installato, ma potrebbe non essere la versione più recente. Per ottenere la versione più recente:
    * Utilizzare Windows Update per aggiornare il driver.
    * Se tale aggiornamento non risolve il problema, passare al sito Web del produttore e installare l'aggiornamento del driver più recente. 
    * Se un aggiornamento non è disponibile per la GPU, è possibile che WMR non sia supportato nel dispositivo. Se lo si ritiene necessario, contattare il [supporto tecnico](https://support.microsoft.com).
    
Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>L'aggiornamento del firmware di Samsung Odyssey o Odyssey + Headset è bloccato.

Samsung è proprietario e pubblica gli aggiornamenti del firmware dell'auricolare forniti tramite le app complementari per dispositivi "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey + Setup". Per altri dettagli e per informazioni sui problemi di aggiornamento del firmware Samsung, contattare il servizio clienti Samsung.

Se il processo di aggiornamento del firmware si blocca e non è stato trovato alcun progresso per più di cinque minuti:
* Scollegare temporaneamente tutti gli altri dispositivi USB e riprovare a eseguire l'aggiornamento del firmware.
* Connettere la cuffia Samsung a una porta USB 3,0 diversa nel PC.
* Disabilitare e/o disinstallare tutti i software installati che potrebbero interferire con gli aggiornamenti del firmware, ad esempio AORUS App Center di gigabyte.
* Usare un PC diverso per eseguire l'aggiornamento del firmware per la cuffia Samsung.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Ricerca per categorie accedere al desktop del PC in realtà mista?
Avviare l'app desktop nel pulsante cuffia da **Windows > tutte le app > desktop** per accedere al desktop del PC in realtà mista.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Come è possibile visualizzare più monitor in realtà mista?
Per impostazione predefinita, l'app desktop passa automaticamente a visualizzare il monitoraggio con lo stato attivo. Se si desidera visualizzare tutti i monitoraggi in realtà mista: 
* Fare clic sull'icona di monitoraggio nell'angolo superiore sinistro dell'app.
* Disabilitare "cambia automaticamente il monitoraggio".
* Selezionare il monitoraggio che si desidera visualizzare.
* Avviare un'altra istanza dell'app desktop.
* Selezionare il monitoraggio che si desidera visualizzare su tale istanza.
* Ripetere la ripetizione per tutti i monitoraggi fisici.
Si noti che sarà necessario selezionare nuovamente il monitoraggio da visualizzare in ogni app desktop ogni volta che si riavvia la realtà mista. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>My Desktop App Mostra solo una schermata nera.
Se il PC ha una GPU NVIDIA ibrida, il problema potrebbe essere causato dal dispositivo Nvidia che esegue il runtimebroker.exe sulla GPU discreta invece che su quello integrato. Per risolvere il problema, seguire queste istruzioni in "[ricerca per categorie creare le impostazioni Optimus per un nuovo programma?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" per aggiungere C:\windows\system32\runtimebroker.exe e forzarlo per l'esecuzione nel processore "Integrated graphics". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa la realtà mista di Windows.

Se si usa una connessione Wi-Fi a 2,4 GHz, i controller di movimento potrebbero rallentare la connessione Wi-Fi. Provare una delle operazioni seguenti:
* Passare a una connessione Wi-Fi 5GHz, se disponibile. [Altre informazioni](https://support.microsoft.com/en-us/help/4000461)
* Usare una scheda Bluetooth separata per connettere i controller di movimento al PC. Vedere [Adapter consigliati](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ho ricevuto un messaggio che dice di inserire e addebitare il mio PC. Perché?

Se si usa un computer portatile, la realtà mista di Windows funziona meglio quando il PC è completamente addebitato e collegato. 

## <a name="what-is-the-experience-options-setting"></a>Che cos'è l'impostazione opzioni esperienza?

Questa impostazione ( **impostazioni > realtà mista > visualizzare > opzioni di esperienza** ) consente di modificare le impostazioni delle prestazioni della realtà mista di Windows. Questo consente di scegliere l'esperienza ottimale per la configurazione hardware in un intervallo di contenuti. Sono disponibili le opzioni seguenti:
* Automatico: la realtà mista di Windows determina la migliore esperienza per la configurazione hardware. Per la maggior parte delle persone, questa è la scelta migliore per iniziare.
* 60Hz: imposta la frequenza di aggiornamento su 60Hz e disattiva determinate funzionalità, ad esempio acquisizione video e anteprima nel portale di realtà mista.
* 90Hz: imposta la frequenza di aggiornamento su 90Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quali lingue sono supportate in realtà mista di Windows?

La realtà mista di Windows è disponibile nelle seguenti lingue:
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

È possibile usare la realtà mista di Windows se il PC è impostato su una lingua diversa, ma l'interfaccia verrà visualizzata in inglese (Stati Uniti) e i comandi vocali e la dettatura non saranno disponibili. La tastiera di Windows per la realtà mista è solo l'inglese (Stati Uniti). Per immettere testo in un'altra lingua, usare una tastiera fisica connessa al PC. È anche possibile usare la dettatura in uno dei linguaggi di realtà mista supportati di Windows elencati in precedenza. è sufficiente selezionare microfono sulla tastiera sullo schermo.

La realtà mista di Windows è disponibile anche nelle seguenti lingue senza comandi vocali o funzionalità di dettatura:
* Cinese tradizionale (Taiwan e Hong Kong)
* Olandese (Paesi Bassi)
* Coreano (Corea)
* Russo (Russia)

## <a name="i-have-questions-about-my-headset-hardware"></a>Ho domande sull'hardware dell'auricolare.

Per informazioni dettagliate sull'auricolare, rivolgersi al produttore. È possibile che sia presente una guida del prodotto nella casella oppure provare il sito Web del produttore.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Ricerca per categorie disinstallare la realtà mista di Windows?

1. Disconnettere l'auricolare dal PC.
2. Chiudere il portale di realtà mista di Windows.
2. Passare a  **avvia > impostazioni > realtà mista** e selezionare "Disinstalla".

Quando si è pronti per iniziare a usare nuovamente l'auricolare, collegarlo e il portale di realtà mista di Windows consentirà di eseguire l'installazione.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Ho un messaggio "non è stato possibile completare la disinstallazione della realtà mista di Windows".

Alcuni file, incluse le informazioni sull'ambiente, potrebbero essere ancora presenti nel computer. Questo può causare problemi se si decide di reinstallare la realtà mista di Windows in un secondo momento. È possibile rimuovere manualmente le altre informazioni sulla realtà mista di Windows dal PC modificando il registro di sistema e usando Windows PowerShell per eseguire i comandi. _Se si modifica il registro di sistema in modo non corretto, potrebbero verificarsi gravi problemi. Assicurarsi di seguire attentamente questi passaggi. Per una maggiore protezione, eseguire il backup del registro di sistema prima di modificarlo in modo che sia possibile ripristinarlo se si verifica un problema._ Per ulteriori informazioni, vedere [How to backup and restory the Registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Per disinstallare la realtà mista di Windows usando i comandi seguenti:
1. Riavvia il PC.
2. Nella casella di **ricerca** Digitare "regedit" e quindi selezionare "Sì".
3. Rimuovere i valori del registro di sistema seguenti:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, quindi eliminare "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, quindi eliminare "PreferDesktopSpeaker" e "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, quindi eliminare "DisableSpeechInput". Nota: gli elementi del registro di sistema in HHKEY_CURRENT_USER devono essere eliminati per ogni account utente nel computer che ha utilizzato la realtà mista di Windows.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, quindi eliminare "DeviceID" e "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, quindi eliminare "OnDeviceLearningCompleted".</li> 
   </ul>
4. Rimuovere le chiavi del registro di sistema seguenti: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Chiudere l'editor del registro di sistema.
6. Passare a **C:\Utenti\nome name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** ed eliminare "RoomBounds.json". Ripetere questa operazione per ogni utente che ha utilizzato la realtà mista di Windows.
7. Aprire il prompt dei comandi di amministrazione e passare a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Eliminare il contenuto della cartella "HeadTracking data", ma non la cartella stessa.
8. Digitare "PowerShell" nella casella di ricerca, fare clic con il pulsante destro del mouse su "Windows PowerShell" e selezionare "Esegui come amministratore".
9. In Windows PowerShell: <ul>
   <li>Al prompt dei comandi, copiare e incollare <b>DISM/online/Get-capabilities</b>, quindi premere INVIO.</b></li> 
   <li>Copiare l'identità della funzionalità che inizia con Analog. Olografic. desktop (se non è presente, questo significa che questo elemento non è installato. In tal caso, andare al passaggio 10.</li> 
   <li>Copiare e incollare il prompt dei comandi seguente, quindi premere INVIO: <b>DISM/online/Remove-Capability/CapabilityName: identità funzionalità copiata nell'ultimo passaggio</b></li>
   </ul>
10. Riavviare il PC.

