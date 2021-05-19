---
title: Windows Mixed Reality di compatibilità dei PC
description: Grafico di panoramica che delinea i requisiti minimi di sistema dei PC per la compatibilità con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Ultra, compatibile, compatibilità, requisiti di sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: e73b00dcf8d6974f06c22c3b0ab0771a8e1a5969
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143316"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality linee guida minime per la compatibilità hardware del PC

## <a name="features-and-experiences"></a>Funzionalità ed esperienze

Windows 10 offre Windows Mixed Reality'ampia gamma di visori in un set diversificato di hardware per PC.  La potenza del PC determinerà le esperienze che è possibile avere.
Con i PC di fascia più alta, si ottengono alcune funzionalità e funzionalità aggiuntive:

* Oggetti visivi più nitidi e una frequenza di aggiornamento più elevata.
* Più app ed esperienze, inclusi i giochi con maggiore utilizzo di grafica.
* Una finestra "mirror" sul desktop che mostra ciò che si vede nella realtà mista.
* Registrare e condividere video e foto delle esperienze di realtà mista.

## <a name="minimum-pc-hardware-guidelines"></a>Linee guida per l'hardware minimo

Verificare se il PC può essere Windows Mixed Reality esaminando le linee guida hardware riportate di seguito ed eseguendo l'app [Portale realtà mista](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) app.

Tenere presente che le prestazioni variano a seconda della configurazione esatta. È anche necessario assicurarsi che il [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC abbia le porte appropriate per l'Windows Mixed Reality visore immersivo in uso.

>[!NOTE]
>Le linee guida per i PC di sviluppo sono superiori a quelle per i PC degli utenti che eseguono app di realtà mista. Se si è uno sviluppatore di realtà mista, [vedere le specifiche del PC di sviluppo consigliate.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Portale realtà mista app

[Portale realtà mista](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) è il modo migliore per assicurarsi che il PC sia pronto per l'esecuzione Windows Mixed Reality.

Dopo aver eseguito l'app, si otterrà uno dei messaggi seguenti:

* **È tutto a posto.**  Il PC è pronto per eseguire giochi ed esperienze di realtà mista.
* **Supporta alcune funzionalità.** Il PC può eseguire alcune esperienze di realtà mista.
* **Non è possibile eseguire la realtà mista.** Questo PC non soddisfa i requisiti minimi necessari per eseguire Windows Mixed Reality.

Si otterrà quindi un'analisi del PC rispetto all'hardware, ai driver e al sistema operativo necessari.
![Screenshot della Controllo PC Windows Mixed Reality](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>Icona</th><th>Significato</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Il PC passa l'elemento richiesto.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Il PC non soddisfa i requisiti per l'elemento specificato.</td>
</tr>
</table>

 [Ottenere assistenza per i Portale realtà mista risultati](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Linee guida per la compatibilità

> [!IMPORTANT]
> Verrà aggiornato, apportando aggiunte a e potrebbe essere necessario rivedere queste linee guida per Windows Mixed Reality sulla compatibilità dei PC. Consultare regolarmente le linee guida e i requisiti più recenti.

### <a name="high-resolution-headset-requirements"></a>Requisiti per visori VR ad alta risoluzione

A causa della risoluzione più elevata, i requisiti seguenti si applicano alle linee di prodotti HP Reverb G1, G2 e Omnicept per garantire un'esperienza ottimale a 90 Hz con risoluzione completa:

<ul>
<li> Intel Core i5, i7, Intel Xenon E3-1240 v5, equivalente o migliore. AMD Ryzen 5 equivalente o migliore. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o migliore </li>
<li> Memoria: almeno 8 GB di RAM </li>
<li> 1 x porta di visualizzazione 1.3 </li>
<li> USB 3.0 1x Di tipo C con alimentatore (o alimentatore incluso)</li>
<li> Windows 10 aggiornamento di maggio 2019 o versione successiva </li>
</ul>

**Tutti gli altri visori VR compatibili con WMR** <br>
Per tutti gli altri HMD, fare riferimento ai requisiti seguenti:

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality PC a 90 Hz</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality PC a 60 Hz</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operativo</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) o versioni successive: Home, Pro, Business, Education.<br/>    <b>(Nota:</b>non supportato nelle versioni N o Windows 10 Pro in modalità S)</td>
</tr><tr>
    <td style="vertical-align: middle">Processore</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (quarta generazione), quad-core (o versione successiva) <br>AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (o versione migliore)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7a generazione mobile), dual-core con tecnologia Intel Hyper-Threading abilitata (o migliore) <br>AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (o versione migliore)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (o versione migliore)</td>
    <td style="vertical-align: middle; text-align: center;">Doppio canale DDR3 da 8 GB (o versione migliore)</td>
</tr><tr>
    <td style="vertical-align: middle">Spazio libero su disco</td>
    <td style="vertical-align: middle; text-align: center;">Almeno 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">Almeno 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Scheda grafica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>GPU discreta con funzionalità DX12 NVIDIA GTX 1060 (o superiore)</li>
            <li>GPU discreta con funzionalità DX12 amD RX 470/570 (o superiore) </li>
            </ul>
            <b>Nota:</b> La GPU deve essere ospitata in uno slot PCIe 3.0 x4+ Link </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>GPU integrata con supporto DX12 per Intel HD Graphics 620 (o versione <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">successiva) (controllare</a> se il modello è superiore)</li>
        <li>GPU discreta NVIDIA MX150 (o superiore)</li>
        <li>GPU discreta Nvidia GeForce GTX 1050</li>
        <li>GPU discreta Nvidia 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Nota:</b> Le GPU Intel meno recenti, ad esempio HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx, non sono supportate.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Driver di grafica</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Porta di visualizzazione grafica</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 o DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 o DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">Visualizza</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Schermo VGA esterno o integrato connesso (800x600) (o versione migliore)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Connettività USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">Connettività Bluetooth (per <a href="controllers-in-wmr.md">i controller del movimento)</a></td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">Frequenza dei fotogrammi del visore VR prevista</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Potenza</td>
    <td style="vertical-align: middle; text-align: center;">Porte USB 3.0</td>
    <td style="vertical-align: middle; text-align: center;">Porte USB 3.0</td>
</tr>
</table>

**Altre informazioni:**

* I portatili più grandi con schermi di almeno 15" fanno il meglio.
* Le configurazioni grafiche ibride sono compatibili solo con Windows Mixed Reality 90Hz. La scheda grafica discreta in qualsiasi configurazione ibrida deve soddisfare tutti i requisiti elencati nelle linee guida Windows Mixed Reality per schede grafiche discrete.
* Se si dispone di una scheda grafica discreta che deve essere eseguita Windows Mixed Reality 90 Hz, ma per impostazione predefinita ha una frequenza di aggiornamento di 60 Hz (60 fotogrammi al secondo), usare un adattatore DisplayPort to HDMI 2.0 di dimensioni complete per collegare il visore e abilitare una frequenza di aggiornamento a 90 Hz.
* Visori diversi possono richiedere porte hardware diverse, quindi assicurarsi che il PC abbia le porte corrette o le schede [necessarie](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) per connettersi al visore.

>[!NOTE]
>L'hardware grafico discreto e integrato che non soddisfa le specifiche minime confermate non è stato testato, confermato o ottimizzato per Windows Mixed Reality e potrebbe non funzionare correttamente o affatto.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality e Surface

Per un'esperienza Windows Mixed Reality ottimale in un dispositivo Surface, è consigliabile l'ultimo SurfaceBook (15") configurato con almeno NVIDIA GeForce GTX 1060 GB e 16 GB di RAM.  Questa configurazione supporta tutte le Windows Mixed Reality ed è stata testata per Windows Mixed Reality.  Le versioni più recenti Surface Book (13,5"), Surface Studio, Surface Laptop e Surface Pro (2017) supporteranno tutte alcune funzionalità di Windows Mixed Reality se configurate con una CPU Intel Core i5 (o superiore) e almeno 8 GB di RAM.

**Requisiti:**

* I prodotti Surface richiedono che gli aggiornamenti dei driver siano compatibili con Windows Mixed Reality. Questi driver possono essere installati in Surface selezionando Impostazioni > aggiornamento e sicurezza > **controlla la disponibilità di aggiornamenti**.
* I prodotti Surface richiedono un [adattatore](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) dalla porta video (Mini DisplayPort o USB-C, a seconda del PC Surface) a HDMI 2.0 per Windows Mixed Reality visori. La versione più recente dell'adattatore Surface Mini-DisplayPort hdmi AV è compatibile con HDMI 2.0 (la versione precedente non lo è). Analogamente, anche <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">l'adattatore Da USB-C</a> a HDMI di Surface è compatibile con HDMI 2.0.

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Per assistenza, contattare Microsoft](https://support.microsoft.com/contactus/)
* [Schede consigliate per i WINDOWS MIXED REALITY compatibili](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
