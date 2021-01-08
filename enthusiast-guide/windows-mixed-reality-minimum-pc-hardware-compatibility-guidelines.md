---
title: Linee guida sulla compatibilità con Windows Mixed Reality PC
description: Grafico di panoramica che illustra i requisiti minimi per il sistema PC per la compatibilità con la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, ultra, compatibile, compatibilità, requisiti di sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: ed53c388797cb57a7f2a53ed40b18923a23c8b74
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009121"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Linee guida per la compatibilità hardware con la realtà mista di Windows

## <a name="features-and-experiences"></a>Funzionalità ed esperienze

Windows 10 potenzia la realtà mista di Windows e la realtà mista di Windows. La versione che si verifica dipende dall'hardware del PC.

Con la realtà mista di Windows Ultra, si ottengono alcune funzionalità e funzionalità aggiuntive:

* Oggetti visivi più nitidi e una frequenza di aggiornamento superiore (90 fotogrammi al secondo).
* Altre app ed esperienze, inclusi i giochi a elevato utilizzo di grafica.
* Una finestra '' Mirror '' sul desktop che Mostra gli elementi visualizzati in realtà mista.
* Registra e Condividi video e foto delle esperienze di realtà miste.

## <a name="minimum-pc-hardware-guidelines"></a>Linee guida per l'hardware minimo

Per un'esperienza ottimale con la realtà mista di Windows, è possibile iniziare con un nuovo [PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) con supporto per la realtà mista di Windows o con un PC compatibile con la realtà mista di Windows in grado di offrire esperienze di realtà miste La realtà mista di Windows Ultra offre oggetti visivi più nitidi a frequenze di aggiornamento più elevate, più esperienze di app, tra cui la maggior parte dei giochi a elevato utilizzo di grafica, il mirroring dell'esperienza di realtà mista di Windows sul desktop e la possibilità di registrare e condividere (foto e video) esperienze con altri utenti. 

Vedere se il PC è in grado di eseguire la realtà mista di Windows esaminando le linee guida hardware seguenti ed eseguendo l'app del portale per la [realtà mista](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M).

Tenere presente che le prestazioni variano a seconda dell'impostazione esatta. Sarà anche necessario assicurarsi che il PC disponga delle [porte giuste](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) per la cuffia mista di Windows per la realtà mista che si sta usando.

>[!NOTE]
>Le linee guida per i PC di sviluppo sono superiori a quelle dei PC dei consumer che eseguono app di realtà mista. Se si è uno sviluppatore di realtà mista, [vedere le specifiche del PC di sviluppo consigliato](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).


## <a name="mixed-reality-portal-app"></a>App portale per realtà mista

Il portale per la realtà mista è il modo migliore per verificare che il PC sia pronto per l'esecuzione di realtà mista di Windows. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

Dopo aver eseguito l'app, si otterrà uno dei messaggi seguenti:
* **Si è pronti per iniziare.** Il PC ha il necessario per eseguire la realtà mista di Windows.
* **Supporta alcune funzionalità.** Questo computer può eseguire la realtà mista di Windows, ma alcune funzionalità potrebbero essere limitate.
* **Non è possibile eseguire la realtà mista.** Questo PC non soddisfa i requisiti minimi necessari per eseguire la realtà mista di Windows.

Si otterrà quindi un'analisi del PC con l'hardware, i driver e il sistema operativo necessari.
![Screenshot del controllo del PC con la realtà mista di Windows](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icona</th><th>Significato</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Il PC passa l'elemento richiesto.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Potrebbero verificarsi problemi con il PC per il requisito specificato. In caso di problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Il PC non soddisfa i requisiti per l'elemento specificato.</td>
</tr>
</table>

 [Ottenere assistenza con i risultati del portale di realtà mista](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>Linee guida sulla compatibilità

> [!IMPORTANT]
> Microsoft verrà aggiornato, apportando aggiunte a e potrebbe rivedere queste linee guida sulla compatibilità dei PC con Windows Mixed Reality. Per le linee guida e i requisiti più recenti, consultare regolarmente.

**Specifiche di HP Reverb compatible**<br>
A causa della risoluzione più elevata, i requisiti seguenti si applicano alle linee del prodotto HP reverbi G1 & G2 per garantire una risoluzione ottimale di 90 Hz, completa: 

<ul>
<li> Intel Core i5, i7, Intel Xenon E3-1240 V5, equivalente o superiore. AMD Ryzen 5 equivalente o superiore. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o superiore </li> 
<li> Memoria: 8 GB di RAM o superiore </li> 
<li> 1 porta di visualizzazione 1,3 </li> 
<li> 1x USB 3,0 Type-C con la distribuzione dell'alimentazione (o alimentatore incluso)</li>
<li> Windows 10 May 2019 Update o versione successiva </li>
</ul>

**Tutte le altre cuffie compatibili con WMR** <br>
Per tutti gli altri HMDs, fare riferimento ai requisiti seguenti: 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows reality Ultra PC</th>
    <th style="vertical-align: middle; text-align: center; width:30%">PC con realtà mista di Windows</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operativo</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) o versioni successive-Home, Pro, business, Education.<br/>    (<b>Nota</b>: non supportata nelle versioni N o Windows 10 Pro in modalità S)</td>
</tr><tr>
    <td style="vertical-align: middle">Processore</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (quarta generazione), quad core (o superiore) <br>AMD Ryzen 5 1400 3.4 GHz (desktop), quad core (o superiore)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200 (settima generazione di dispositivi mobili), dual core con tecnologia Intel Hyper-Threading abilitata (o superiore) <br>AMD Ryzen 5 1400 3.4 GHz (desktop), quad core (o superiore)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (o superiore)</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 Dual Channel (o superiore)</td>
</tr><tr>
    <td style="vertical-align: middle">Spazio libero su disco</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Almeno 10 GB</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Almeno 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Scheda grafica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>GPU discreta con supporto per DX12 NVIDIA GTX 1060 (o versione successiva)</li>
            <li>GPU discreta con supporto per DX12 AMD RX 470/570 (o versione successiva) </li>
            </ul>     
            <b>Nota:</b> La GPU deve essere ospitata in uno slot di collegamento PCIe 3,0 x4 + </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>GPU integrata Intel HD Graphics 620 (o versione successiva) integrata con supporto per DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(verificare se il modello è superiore)</a></li>
        <li>GPU di NVIDIA microfono MX150 (o versione successiva)</li>
        <li>GPU NVIDIA GeForce GTX 1050 discrete</li>
        <li>GPU di NVIDIA 965M discrete</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Nota:</b> Le GPU Intel precedenti, ad esempio HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx non sono supportate.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Driver grafica</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2,2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Porta di visualizzazione grafica</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2,0 o DisplayPort 1,2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1,4 o DisplayPort 1,2</td>
</tr><tr>
    <td style="vertical-align: middle">Schermo</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Visualizzazione connessione VGA (800x600) esterna o integrata (o superiore)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Connettività USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">Tipo USB 3,0-A </td>
</tr><tr>
    <td style="vertical-align: middle">Connettività Bluetooth (per i <a href="controllers-in-wmr.md">controller di movimento</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4,0</td>
</tr><tr>
    <td style="vertical-align: middle">Frequenza fotogrammi auricolare prevista</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Elettricità</td>
    <td style="vertical-align: middle; text-align: center;">Porte USB 3,0 (tipo A)</td>
    <td style="vertical-align: middle; text-align: center;">Porte USB 3,0 (tipo A)</td>
</tr>
</table>



**Altre informazioni:**
* I portatili più grandi con schermate di almeno 15 "migliorano.
* Per un'esperienza ottimale, è consigliabile un ottavo processore Intel® Core™ o settime gen Intel® Core™ i5.
* Le configurazioni grafiche ibride sono compatibili solo con la realtà mista di Windows Ultra. La scheda grafica discreta in una configurazione ibrida deve soddisfare tutti i requisiti elencati nelle linee guida per la realtà mista di Windows per adattatori grafici discreti.
* Se si dispone di una scheda grafica discreta che deve eseguire la realtà di Windows misto Ultra, ma il valore predefinito è una frequenza di aggiornamento di 60 Hz (60 frame al secondo), utilizzare un adattatore DisplayPort per HDMI 2,0 per collegare la cuffia e abilitare una frequenza di aggiornamento di 90 Hz.
* Auricolari diversi possono richiedere porte hardware diverse, quindi assicurarsi che il PC disponga delle porte corrette o degli [adattatori necessari](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) per la connessione all'auricolare.

>[!NOTE]
>L'hardware grafico discreto e integrato che non soddisfano le specifiche minime confermate non è stato testato, confermato o ottimizzato per la realtà mista di Windows e potrebbe non funzionare correttamente.

## <a name="windows-mixed-reality-and-surface"></a>Realtà e superficie mista di Windows

Per la migliore esperienza di realtà mista di Windows in un dispositivo Surface, è consigliabile usare SurfaceBook 2 (15 ") configurato con NVIDIA GeForce GTX 1060 GB e 16 GB di RAM.  Questa configurazione supporta tutte le funzionalità della realtà mista di Windows @ 90 Hz ed è stata testata e dotata di badge per la realtà mista di Windows.  Il libro Surface 2 (13 "), Surface Studio, Surface laptop e Surface Pro (2017) supporta tutte le funzionalità della realtà mista di Windows se configurate con una CPU Intel Core i5 (o superiore) e almeno 8 GB di RAM.

**Requisiti:**
* I prodotti Surface richiedono che gli aggiornamenti dei driver siano compatibili con la realtà mista di Windows. Per installare questi driver, passare a **impostazioni > aggiornamento e sicurezza > verificare la disponibilità di aggiornamenti**.
* I prodotti Surface richiedono un [Adapter](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) dalla porta video (Mini DisplayPort o USB-C, a seconda del PC Surface) a HDMI 2,0 per le cuffie di realtà miste di Windows. La versione più recente della superficie Mini-DisplayPort alla scheda HDMI AV è compatibile con HDMI 2,0 (la versione precedente non è). Analogamente, la <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">superficie USB-C alla scheda HDMI</a> è compatibile anche con HDMI 2,0.

>[!WARNING]
>Non tutti i mini DisplayPort o USB-C per gli adapter HDMI sono compatibili con HDMI 2,0. Provare a verificare la compatibilità "HDMI 2,0" o la compatibilità "4K" esplicita su qualsiasi adapter.

Altre informazioni sulla compatibilità della superficie con la realtà mista di Windows sono disponibili nella tabella seguente:

<table>
    <tr>
        <th> Dispositivo Surface </th><th> Supporto per la funzionalità di realtà mista di Windows </th><th> Configurazione consigliata </th><th> Note</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (originale)/Surface Pro 2 </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
(con Windows 10 Pro installato) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface book con base prestazioni </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> Nessuno </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Surface Book 2 (15 &quot; ) </td><td style="vertical-align: middle"> Full </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16GB di RAM </td>
        <td>
            <ul>
                <li><b>Consigliato</b>: per la migliore esperienza di realtà mista di Windows in un dispositivo Surface, è consigliabile usare il SurfaceBook 2 15 "configurato con NVIDIA GeForce GTX 1060 GB e 16 GB di RAM.  Questa configurazione viene testata e sottoposta a badge come la realtà mista di Windows, in modo che supporti tutte le funzionalità di realtà mista di Windows e consentirà di usufruire della più ampia gamma di app e giochi compatibili.</li>
                <li>NVIDIA GeForce GTX 1060 discrete GPU offrirà un'esperienza di Windows per la realtà mista ultra @ 90-Hz</li><br/>                <li>Per ottenere prestazioni ottimali, usare i driver NVIDIA graphics rilasciati per Surface Book 2. I driver più recenti possono essere disponibili nel sito web nvidia&#39;s, ma non sono stati testati.</li><br/>                <li>Richiede la <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">superficie USB-C alla scheda HDMI</a> (altri adapter possono funzionare, ma non sono testati)</li>
                <li><b>Nota su Surface Dock</b>: l'uso di Surface Dock con Surface Book 2 non è ufficialmente supportato con la realtà mista di Windows, a causa delle limitazioni dell'alimentazione di Surface Dock.</li><br/>                <li><b>Nota su Windows 10 versione 1803</b>: se si&#39;la versione 1803 di Windows 10, assicurarsi di&#39;re sulla build del sistema operativo 17134,137 o versione successiva (installata da KB4284848) per assicurarsi di disporre delle correzioni delle prestazioni più recenti. Per ulteriori informazioni, vedere le note sulla versione di <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13,5 &quot; ) </td><td style="vertical-align: middle"> Parziale </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16GB di RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: la superficie del libro 2 (13 ") non è un badge per la realtà mista di Windows, ma supporta alcune funzionalità di realtà mista di Windows che consentono di usare un numero limitato di app e giochi compatibili.  Le prestazioni dipendono dalla configurazione.</li>
                <li>Le configurazioni con una GPU integrata Intel Core i5/Intel HD 620 offrono un'esperienza di realtà mista di Windows a 60 Hz</li>
                <li>Le configurazioni con una GPU di Intel Core i7/NVIDIA GeForce GTX 1050 offriranno un'esperienza di realtà mista di Windows a 90 Hz</li>                       <li>Per ottenere prestazioni ottimali, usare i driver NVIDIA graphics rilasciati per Surface Book 2. I driver più recenti possono essere disponibili nel sito web nvidia&#39;s, ma non sono stati testati.</li>
                <li>Richiede la <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">superficie USB-C alla scheda HDMI</a> (altri adapter possono funzionare, ma non sono testati)</li>
                <li><b>Nota su Surface Dock</b>: l'uso di Surface Dock con Surface Book 2 non è ufficialmente supportato con la realtà mista di Windows, a causa delle limitazioni dell'alimentazione di Surface Dock.</li>
                <li><b>Nota su Windows 10 versione 1803</b>: se si&#39;la versione 1803 di Windows 10, assicurarsi di&#39;re sulla build del sistema operativo 17134,137 o versione successiva (installata da KB4284848) per assicurarsi di disporre delle correzioni delle prestazioni più recenti. Per ulteriori informazioni, vedere le note sulla versione di <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Parziale </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16GB di RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: Surface Studio non è un badge per la realtà mista di Windows, ma supporta alcune funzionalità della realtà mista di Windows che consentono di usare un numero limitato di giochi e app compatibili.  Le prestazioni dipendono dalla configurazione.</li>
                <li>Le configurazioni con NVIDIA GeForce GTX 965 m offriranno un'esperienza di Windows mista per la realtà a 60 Hz.</li>
                <li>Le configurazioni con NVIDIA GeForce GTX 980 m offriranno un'esperienza di Windows mista per la realtà a 90 Hz.</li>
                <li>Scheda da Mini DisplayPort a HDMI 2,0 (altri adapter possono funzionare, ma non sono testati)</li>
                <li>L'auricolare di realtà mista di Windows deve essere connesso alla porta USB con il simbolo "+"</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> Parziale </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iris™ Plus graphics 640/16GB di RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: la superficie Pro (2017) non è dotata di badge per la realtà mista di Windows, ma supporta alcune funzionalità di realtà mista di Windows che consentono di usare un numero limitato di app e giochi compatibili.  Le prestazioni dipendono dalla configurazione.</li>
                <li>Le configurazioni con una GPU integrata Intel Core M3/Intel HD Graphics 615 <b>non sono supportate</b></li>
                <li>Le configurazioni con una GPU integrata Intel Core i5/Intel HD 620 offrono un'esperienza di realtà mista di Windows a 60 Hz</li>
                <li>Le configurazioni con Intel Core i7/Intel® Iris™ Plus graphics 640 Integrated GPU offriranno un'esperienza di realtà mista di Windows @ 60-Hz</li><br/><li>Richiede la superficie Mini DisplayPort alla scheda HDMI 2,0 (altri adapter possono funzionare, ma non sono testati)</li>
                <li>Richiede un <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">dispositivo di scorrimento delle prestazioni</a> impostato su "prestazioni ottimali" durante l'utilizzo</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Parziale </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iris™ Plus graphics 640/16GB di RAM </td>
        <td>
            <ul>
                <li><b>Nota</b>: la superficie portatile non è una notifica per la realtà mista di Windows, ma supporta alcune funzionalità della realtà mista di Windows che consentono di usare un numero limitato di giochi e app compatibili.  Le prestazioni dipendono dalla configurazione.</li>
                <li>Le configurazioni con una GPU integrata Intel Core M3/Intel HD Graphics 615 <b>non sono supportate</b></li>
                <li>Le configurazioni con una GPU integrata Intel Core i5/Intel HD 620 offrono un'esperienza di realtà mista di Windows a 60 Hz</li>
                <li>Le configurazioni con Intel Core i7/Intel® Iris™ Plus graphics 640 Integrated GPU offriranno un'esperienza di realtà mista di Windows @ 60-Hz</li><br/><li>Richiede la superficie Mini DisplayPort alla scheda HDMI 2,0 (altri adapter possono funzionare, ma non sono testati)</li>
                <li>Richiede un <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">dispositivo di scorrimento delle prestazioni</a> impostato su "prestazioni ottimali" durante l'utilizzo</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>Vedere anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Adattatori consigliati per PC con supporto per la realtà mista di Windows](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
