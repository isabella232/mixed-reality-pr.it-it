---
title: Windows Mixed Reality Linee guida per la compatibilità dei PC
description: Grafico di panoramica che delinea i requisiti minimi di sistema del PC per la compatibilità con Windows Mixed Reality.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Ultra, compatibile, compatibilità, requisiti di sistema, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436733"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality linee guida minime per la compatibilità hardware del PC

![Immagine del hero di compatibilità del PC](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Funzionalità ed esperienze

Windows 10 e Windows 11 si Windows Mixed Reality su un'ampia gamma di visori VR in un set eterogeneo di hardware per PC.  La potenza del PC determinerà le esperienze che è possibile avere.
Con i PC di fascia alta, si ottengono alcune funzionalità e funzionalità aggiuntive:

* Oggetti visivi più nitidi e una frequenza di aggiornamento più elevata.
* Altre app ed esperienze, tra cui i giochi più a elevato utilizzo di grafica.
* Una finestra "mirror" sul desktop che mostra ciò che viene visualizzato nella realtà mista.
* Registra e condividi video e foto delle tue esperienze di realtà mista.

## <a name="minimum-pc-hardware-guidelines"></a>Linee guida per l'hardware minimo

Verificare se il PC può essere Windows Mixed Reality esaminando le linee guida hardware riportate di seguito ed eseguendo l'app [Portale realtà mista.](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)

Tenere presente che le prestazioni variano a seconda della configurazione esatta. È anche necessario assicurarsi che il [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC abbia le porte appropriate per il visore VR Windows Mixed Reality immersive in uso.

>[!NOTE]
>Le linee guida per i PC di sviluppo sono superiori a quelle per i PC dei consumer che eseguono app di realtà mista. Gli sviluppatori di realtà mista possono vedere [le specifiche consigliate per i PC di sviluppo.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Portale realtà mista app

[Portale realtà mista](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) è il modo migliore per assicurarsi che il PC sia pronto per l'esecuzione Windows Mixed Reality.

Dopo aver eseguito l'app, si otterrà uno dei messaggi seguenti:

* **È tutto a posto.**  Il PC è pronto per eseguire giochi ed esperienze di realtà mista.
* **Supporta alcune funzionalità.** Il PC può eseguire alcune esperienze di realtà mista.
* **Non è possibile eseguire la realtà mista.** Questo PC non soddisfa i requisiti minimi necessari per l'esecuzione Windows Mixed Reality.

Si otterrà quindi un'analisi del PC rispetto all'hardware, ai driver e al sistema operativo necessari.
![Screenshot del controllo Windows Mixed Reality PC](images/screenshot-mr-pc-check.jpg)

| Icona | Significato |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | Il PC passa l'elemento richiesto. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | Potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | Il PC non soddisfa i requisiti per l'elemento specificato. |

 [Ottenere assistenza per i Portale realtà mista risultati](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Linee guida sulla compatibilità

> [!IMPORTANT]
> Verrà aggiornato, apportando aggiunte a e potrebbe essere necessario rivedere queste linee guida per Windows Mixed Reality sulla compatibilità dei PC. Consultare regolarmente le linee guida e i requisiti più recenti.

### <a name="high-resolution-headset-requirements"></a>Requisiti per visori VR ad alta risoluzione

A causa della risoluzione più elevata, i requisiti seguenti si applicano alle linee di prodotti HP Reverb G1, G2 e Omnicept per garantire un'esperienza ottimale a 90 Hz con risoluzione completa:

- Intel Core i5, i7, Intel Xeon E3-1240 v5, equivalente o migliore. AMD Ryzen 5 equivalente o migliore.  
- NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente o migliore  
- Memoria: almeno 8 GB di RAM  
- 1 x porta di visualizzazione 1.3  
- USB 3.0 1x Di tipo C con alimentatore (o alimentatore incluso) 
- Windows 10 Aggiornamento di maggio 2019 o versione successiva  
 
**Tutti gli altri visori VR compatibili con WMR** <br>
Per tutti gli altri HMD, fare riferimento ai requisiti seguenti:

| | Windows Mixed Reality PC a 90 Hz | Windows Mixed Reality PC a 60 Hz |
| --- | --- | --- |
| Sistema operativo | Windows 10 Fall Creators Update (RS3) o versioni successive: Home, Pro, Business, Education. <br/>    <b>(Nota:</b>non supportato nelle versioni N o Windows 10 Pro in modalità S) |
| Processore | Intel Core i5 4590 (quarta generazione), quad-core (o versione successiva) <br> AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (o versione migliore) | Intel Core i5 7200U (7a generazione mobile), dual-core con tecnologia Intel Hyper-Threading abilitata (o migliore) <br> AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (o versione migliore) |
| RAM | 8 GB DDR3 (o versione migliore) | Doppio canale DDR3 da 8 GB (o versione migliore) |
| Spazio libero su disco | Almeno 10 GB | Almeno 10 GB |
| Scheda grafica| <ul> <li>GPU discreta con funzionalità DX12 NVIDIA GTX 1060 (o superiore) </li> <li>GPU discreta con funzionalità DX12 amD RX 470/570 (o superiore) </li> </ul> <br> <b>Nota:</b> La GPU deve essere ospitata in uno slot PCIe 3.0 x4+ Link |  <ul>  <li>GPU integrata con supporto DX12 per Intel HD Graphics 620 (o versione <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">successiva) (controllare</a> se il modello è superiore)</li> <li>GPU discreta NVIDIA MX150 (o superiore)</li> <li>GPU discreta Nvidia GeForce GTX 1050</li> <li>GPU discreta Nvidia 965M</li> <li>AMD Radeon RX 460/560</li> </ul> <b>Nota:</b> Le GPU Intel meno recenti, ad esempio HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx, non sono supportate. |
| Driver di grafica | Windows Display Driver Model (WDDM) 2.2 |  |
| [Porta di visualizzazione grafica](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | HDMI 2.0 o DisplayPort 1.2 | HDMI 1.4 o DisplayPort 1.2 |
| Visualizza | Schermo VGA esterno o integrato connesso (800x600) (o versione migliore) | 
| [Connettività USB](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| Bluetooth connettività (per i [controller del movimento)](controllers-in-wmr.md) | Bluetooth 4.0 | |
| Frequenza dei fotogrammi del visore VR prevista | 90 Hz | 60Hz |
| Elettricità | Porte USB 3.0 | Porte USB 3.0 |

**Altre informazioni:**

* I portatili più grandi con schermi di almeno 15 pollici fanno il meglio.
* Le configurazioni grafiche ibride sono compatibili solo con Windows Mixed Reality 90Hz. La scheda grafica discreta in qualsiasi configurazione ibrida deve soddisfare tutti i requisiti elencati nelle linee guida Windows Mixed Reality per schede grafiche discrete.
* Se si dispone di una scheda grafica discreta che deve essere eseguita Windows Mixed Reality 90Hz, ma per impostazione predefinita ha una frequenza di aggiornamento di 60 Hz (60 fotogrammi al secondo), usare un adattatore DisplayPort a HDMI 2.0 di dimensioni complete per collegare il visore VR e abilitare una frequenza di aggiornamento di 90 Hz.
* Visori VR diversi possono richiedere porte hardware diverse, quindi assicurarsi che il PC abbia le porte corrette o le schede [necessarie](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) per connettersi al visore VR.

>[!NOTE]
>L'hardware grafico discreto e integrato che non soddisfa le specifiche minime confermate non è stato testato, confermato o ottimizzato per Windows Mixed Reality e potrebbe non funzionare correttamente o affatto.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality e Surface

Per un'esperienza di Windows Mixed Reality ottimale in un dispositivo Surface, è consigliabile usare la versione più recente di SurfaceBook (15") configurata con almeno NVIDIA GeForce GTX 1060 GB e 16 GB di RAM.  Questa configurazione supporta tutte le funzionalità Windows Mixed Reality ed è stata testata per Windows Mixed Reality.  Le versioni più recenti Surface Book (13,5"), Surface Studio, Surface Laptop e Surface Pro (2017) supporteranno tutte alcune funzionalità di Windows Mixed Reality se configurate con una CPU Intel Core i5 (o superiore) e almeno 8 GB di RAM.

**Requisiti:**

* I prodotti Surface richiedono la compatibilità degli aggiornamenti dei driver con Windows Mixed Reality. Questi driver possono essere installati in Surface selezionando Impostazioni > Aggiornamento e sicurezza > **controlla la disponibilità di aggiornamenti.**
* I prodotti Surface richiedono un [adattatore](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) dalla porta video (Mini DisplayPort o USB-C, a seconda del PC Surface) a HDMI 2.0 per Windows Mixed Reality visori VR. La versione più recente dell'adattatore Surface Mini-DisplayPort a HDMI AV è compatibile con HDMI 2.0 (la versione precedente non lo è). Analogamente, anche <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">l'adattatore Surface USB-C</a> per HDMI è compatibile con HDMI 2.0.

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Schede consigliate per i WINDOWS MIXED REALITY compatibili](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
