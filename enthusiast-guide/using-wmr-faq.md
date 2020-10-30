---
title: Domande frequenti sull'uso di Windows Mixed Reality
description: Risposte alle domande comuni quando si lavora con la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: cf02ccfc92d80ee1d1a8f6ca3d4ab55650f4a62c
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044441"
---
# <a name="using-windows-mixed-reality-faq"></a>Domande frequenti sull'uso di Windows Mixed Reality

Per informazioni sull'uso dell'auricolare immersiva mista di Windows, vedere questi argomenti per informazioni generali e risoluzione dei problemi.

Serve ancora assistenza? Per la risoluzione avanzata dei problemi, vedere questo articolo.

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Viene visualizzato un messaggio che indica che il rilevamento è stato perso o che non è presente alcun limite per questo spazio.

Selezionare **avvia > portale per la realtà mista** sul desktop. Selezionare **menu** , quindi **Esegui il programma di installazione** per creare un nuovo limite. La realtà mista di Windows supporta più percorsi e identifica lo spazio all'avvio, purché la stanza non sia cambiata in modo significativo.  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>Non riesco a udire alcun suono o il suono proveniente dal mio computer invece che dall'auricolare

Se la cuffia a immersione non include cuffie predefinite, è necessario connettere le cuffie al jack audio dell'auricolare. Il Jack è spesso posizionato dietro la visiera o le lenti dell'auricolare; se si riscontrano problemi, rivolgersi al produttore dell'auricolare. 

Alcune cuffie audio dispongono di pulsanti fisici per controllare il volume. Se l'audio non funziona, verificare se il volume è disattivato o disattivato.

La realtà mista di Windows è progettata per riprodurre un suono attraverso l'auricolare immersiva quando lo si indossa e ci si connette alle cuffie. Quando si toglie la cuffia o si capovolge la visiera, l'audio passa al dispositivo Windows playback predefinito. È possibile modificare questa impostazione in **impostazioni > realtà mista > audio e sintesi vocale** .

> [!NOTE]
> * L'audio spaziale della realtà mista di Windows funziona meglio con le cuffie incorporate o connesse direttamente all'auricolare immersivo. Gli altoparlanti PC o le cuffie connesse al PC potrebbero non funzionare correttamente per l'audio spaziale.
> * La realtà mista di Windows non supporta le cuffie audio Bluetooth.

## <a name="speech-commands-arent-working"></a>Comandi vocali non funzionanti

Per usare i comandi vocali, le impostazioni relative alla lingua e al riconoscimento vocale del PC devono essere impostate su una [lingua e un'area di realtà mista di Windows supportata](wmr-setup-faq.md#what-languages-are-supported-in-windows-mixed-reality). Per verificare l'area geografica e la lingua di Windows, selezionare **impostazioni > ora & lingua > regione & lingua** . Per controllare la lingua vocale, selezionare **impostazioni > ora & lingua > voce** .

Se la cuffia non ha un microfono incorporato, alleghi le cuffie con un microfono alla cuffia o al PC. Per fare in modo che l'input Mic venga attivato automaticamente all'auricolare quando le cuffie sono direttamente connesse, selezionare **impostazioni > realtà mista > audio e sintesi vocale** e assicurarsi che **, quando si indossa la cuffia, passare alla cuffia microfonica** è accesa.

Alcune cuffie audio hanno un pulsante fisico per disattivare e disattivare il microfono. Se i comandi di sintesi vocale non funzionano, controllare se il MIC è disattivato.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Il limite è sempre visibile. Come è possibile fare in modo che vada via?

Quando si è vicini al limite, viene visualizzato. Se il limite include le sezioni con una forma stretta o irregolare, è possibile che ci si avvicini e che la causa appaia, più spesso di quanto si desideri. Per risolvere il problema, provare a creare di nuovo il limite, usando una forma più grande e più regolare. Selezionare **avvia > portale per la realtà mista** sul desktop, quindi selezionare **Esegui installazione** . 

È anche possibile disattivare temporaneamente il limite dal portale per la realtà mista: selezionare **menu** , quindi usare l'interruttore per disattivare il limite. Quando il limite è disattivato, è necessario rimanere in un'unica posizione per evitare gli ostacoli.

## <a name="im-having-trouble-with-my-motion-controllers"></a>Si verificano problemi con i controller di movimento

Se i controller di movimento non funzionano correttamente, non si connettono o se non viene visualizzata un'immagine dei controller quando si indossa la cuffia, provare a eseguire le operazioni seguenti:

* Verificare che i controller siano accesi. Per attivarli, tenere premuto il pulsante **Windows** per 2 secondi.
* Selezionare **avvia > portale per la realtà mista** nel PC e quindi selezionare **menu** per visualizzare i controller di movimento elencati insieme a un messaggio di stato:
    * Pronto: tutti i controller sono impostati.
    * Rilevamento perso: il portale per la realtà mista non riesce a trovare i controller. Tenerli davanti all'auricolare e riavviarli premendo il pulsante **Windows** per 4 secondi, quindi di nuovo per 2 secondi.
    * Batteria insufficiente: sostituire le batterie del controller.
* Se si usa il Wi-Fi, provare a connettere il PC a una rete Wi-Fi 5GHz per ridurre l'interferenza senza fili. 
* Per i nuovi auricolari associati direttamente ai controller, selezionare **"..."** pulsante nel **portale per la realtà mista** e scegliere **Configura controller** . Verrà visualizzata l'app per la cuffia per associare i controller alla cuffia.  
* Per gli auricolari meno recenti che non dispongono di Bluetooth integrato per l'associazione diretta dei controller:  
    * Selezionare impostazioni > dispositivi > Bluetooth & altri dispositivi nel PC e assicurarsi che i controller siano elencati come abbinati.In caso contrario, è necessario associarli. 
    * Se si dispone di altri dispositivi Bluetooth associati al PC, ad esempio cuffie o gamepad, provare a rimuoverne alcuni. Selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC, selezionare i dispositivi e quindi selezionare **Rimuovi dispositivo** .
    * Rimuovere cuffie e altoparlanti Bluetooth in **impostazioni > dispositivi > Bluetooth & altri dispositivi** e spegnere i dispositivi. 
    * Se si usa una scheda Bluetooth USB, assicurarsi che sia collegata a una porta USB 2,0 nera e che sia collegata al più lontano possibile da qualsiasi altro trasmettitore wireless o unità flash USB, incluso il connettore USB per l'auricolare. 
    * Se il PC dispone di Bluetooth integrato e si verificano problemi di connessione, provare a usare una scheda Bluetooth USB. A tale scopo, è necessario disattivare anche la radio Bluetooth incorporata in [Device Manager](https://support.microsoft.com/help/4026149), quindi abbinare gli altri dispositivi Bluetooth con la nuova scheda.
* Se l'app impostazioni è aperta nella pagina Bluetooth & altri dispositivi, chiuderla.

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Si è verificato un fastidio quando si usa l'auricolare

Per informazioni generali sulla comodità nella realtà mista di Windows, vedere la pagina relativa all' [integrità, alla sicurezza e alla comodità dell'auricolare misto](wmr-health-safety-comfort.md)di Windows. Per informazioni dettagliate sull'auricolare specifico, rivolgersi al produttore dell'auricolare.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Gli oggetti visivi sono irregolari, vengono caricati lentamente o non sembrano corretti

Se gli oggetti visivi della realtà mista non hanno un aspetto ottimale, provare a eseguire le operazioni seguenti.

* Assicurarsi che l'auricolare sia collegato alla scheda grafica corretta nel PC. Alcuni PC hanno schede grafiche sia integrate che discrete. La scheda discreta offre in genere le prestazioni migliori. [Altre informazioni sull'hardware del PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Chiudere le app non usate sul desktop.
* Regolare l'adattamento dell'auricolare: spostarlo in basso e in alto o a sinistra e a destra e assicurarsi che si adatti perfettamente.
* Modificare le impostazioni visive dell'auricolare ( **impostazioni > realtà mista > visualizzazione dell'auricolare** ). Quando la **qualità visiva** è impostata su **automatica** , scegliere la migliore esperienza di realtà mista per il PC. Per un'esperienza con un maggior numero di dettagli visivi, impostare **qualità visiva** su **alta** . Se gli oggetti visivi sono increspati, potrebbe essere necessario selezionare un'impostazione inferiore.
* Provare a regolare la calibrazione dell'auricolare. Le lenti devono essere modificate in modo che corrispondano alla distanza interpupillare (dpi), alla distanza tra gli alunni. Se non si conosce il valore di dpi, un optometrista dovrebbe essere in grado di misurarlo. Sono inoltre disponibili siti Web progettati per misurare i dpi. Quando si conosce il dpi, usare la manopola di calibrazione dell'auricolare per apportare modifiche. Se la cuffia non ha una manopola di calibrazione, selezionare **impostazioni > realtà mista > visualizzare l'auricolare** e modificare il controllo di calibrazione.

## <a name="i-have-questions-about-my-headset-hardware"></a>Domande sull'hardware della cuffia

Per informazioni dettagliate sull'auricolare, rivolgersi al produttore. È possibile che sia presente una guida del prodotto nella casella oppure provare il sito Web del produttore.

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>Il piano in realtà mista sembra trovarsi nella posizione sbagliata

Se il piano non viene visualizzato, ad esempio se si è certi di essere mobile, selezionare **avvia > regolazione della stanza** mentre si indossa l'auricolare per apportare modifiche.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ho ricevuto un messaggio che dice di inserire e addebitare il mio PC. Perché?

Se si usa un computer portatile, la realtà mista di Windows funziona meglio quando il PC è completamente addebitato e collegato.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Ricerca per categorie disinstallare la realtà mista di Windows?

Selezionare **avvia > impostazioni > realtà mista** , quindi selezionare **Disinstalla** . Assicurarsi di disconnettere l'auricolare dal PC e chiudere il portale di realtà mista prima di disinstallare.

Quando si è pronti per iniziare a usare nuovamente l'auricolare, collegarlo e il portale per la realtà mista consente di eseguire l'installazione.

> [!NOTE]
> Se viene visualizzato un messaggio indicante che non è stato possibile completare la rimozione della realtà mista di Windows, significa che alcuni file, incluse le informazioni sull'ambiente, potrebbero essere ancora presenti nel computer. Questo può causare problemi se si decide di reinstallare la realtà mista di Windows in un secondo momento.
> 
> Per informazioni su come rimuovere manualmente le informazioni sulla realtà mista di Windows rimanenti dal PC, vedere **[questo articolo](installation_errors.md)** .

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa la realtà mista di Windows

Se si usa una connessione Wi-Fi a 2,4 GHz, i controller di movimento potrebbero rallentare la connessione Wi-Fi. Provare una delle operazioni seguenti:

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* Passare a una connessione Wi-Fi 5GHz, se disponibile. [Scopri di più](https://support.microsoft.com/help/4000461)
* Usare una scheda Bluetooth separata per connettere i controller di movimento al PC. [Vedere gli adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>Che cos'è l'impostazione opzioni esperienza?

L'impostazione opzioni esperienza ( **impostazioni > realtà mista > visualizzazione > opzioni esperienza** ) consente di modificare le impostazioni delle prestazioni della realtà mista di Windows. Questo consente di scegliere la migliore esperienza possibile per la configurazione hardware in un intervallo di contenuti. L'esperienza 90Hz è disponibile per tutti i sistemi, ma potrebbe essere necessario provare prima l'impostazione automatica per visualizzare l'impostazione preferita.

Ecco le opzioni seguenti:

* Automatico o lasciare che Windows decida: la realtà mista di Windows determina la migliore esperienza per la configurazione hardware. Per la maggior parte delle persone, questa è la scelta migliore per iniziare.
* 60Hz: imposta la frequenza di aggiornamento su 60Hz e disattiva determinate funzionalità, ad esempio acquisizione video e anteprima nel portale di realtà mista.
* 90Hz: imposta la frequenza di aggiornamento su 90Hz se l'auricolare può essere eseguito alla velocità. Se i problemi del cavo impediscono l'esecuzione dell'auricolare in 90Hz, potrebbe essere visualizzato un errore all'avvio con questa modalità selezionata. 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Viene visualizzato un messaggio che indica "put on the headset" anche se l'auricolare è acceso

Quando si usa l'auricolare, la realtà mista di Windows richiede un po' di tempo per ricaricare lo spazio. Questa operazione potrebbe richiedere alcuni secondi. Se il messaggio non viene rimosso, assicurarsi che l'adesivo protettivo sia stato rimosso dal sensore di prossimità, che si trova all'interno dell'auricolare, tra le lenti. Se l'adesivo è stato rimosso e si verificano ancora problemi, contattare il produttore dell'auricolare. Quando si preme **Win + Y** sulla tastiera, l'auricolare viene attivato manualmente per l'esecuzione se il sensore di prossimità non viene attivato automaticamente. 

Serve ancora assistenza? Per la risoluzione avanzata dei problemi, vedere [questo articolo](troubleshooting-windows-mixed-reality.md).

## <a name="see-also"></a>Vedi anche
* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)