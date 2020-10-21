---
title: Prima di iniziare
description: Come verificare che il PC sia compatibile con e pronto per la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, compatibilità, compatibilità, introduzione, configurazione, PC, requisiti di sistema
appliesto:
- Windows 10
ms.openlocfilehash: b10fc9962d899b0a2c2ee15e6d039fc6bfb6d503
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293060"
---
# <a name="before-you-start"></a>Prima di iniziare

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Cosa è necessario per eseguire la realtà mista di Windows

* [Visualizzazione montata in realtà mista di Windows (HMD)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).
* Un nuovo [PC pronto per la realtà mista di Windows](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) o un PC compatibile con Windows Mixed Reality che esegue Windows 10 versione 1709 o successiva.
* Una connessione Internet
* Schede di visualizzazione, USB e Bluetooth (se non incorporate in cuffia o computer)
* Controller di movimento, controller Xbox o mouse e tastiera
* Cuffie con microfono (se i HMD non sono stati incorporati)
* Ampio spazio aperto

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>Verificare che il PC sia compatibile con la realtà mista di Windows

Per verificare se il PC è compatibile con la realtà mista di Windows, verificare i [requisiti hardware per la realtà mista di Windows](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o eseguire il portale per la [realtà mista di Windows](install-windows-mixed-reality.md#launch-mixed-reality-portal) nel PC.

Per ulteriori informazioni sui problemi di compatibilità dei PC, vedere [qui](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality).

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Verificare che sia installato Windows 10 versione 1709 o versione successiva

Per usare la realtà mista di Windows, è necessario che sia in esecuzione Windows 10 versione 1709 (Fall Creators Update) o versione successiva. Le versioni compatibili di Windows 10 includono:
* Windows 10 versione 1709 (Fall Creators Update, Build 16299)
* Windows 10 versione 1803 (Spring Update, Build 17134)
* Windows 10 versione 1809 (aggiornamento di ottobre, Build 17763)

Per visualizzare la versione di Windows 10 attualmente in esecuzione nel dispositivo, selezionare il pulsante **Start** , quindi selezionare **impostazioni > sistema > informazioni su**.

Per assicurarsi che Windows 10 sia aggiornato nel computer, fare clic sul pulsante **Start** , quindi selezionare **impostazioni > aggiorna & sicurezza > Windows Update**.  Selezionare **Verifica disponibilità aggiornamenti**. Se sono disponibili aggiornamenti, installarli.

Per ulteriori informazioni su come rendere aggiornato il PC, vedere [qui](https://support.microsoft.com/en-us/help/12373/windows-update-faq)

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Verificare che il PC sia connesso a Internet

Verificare che il PC sia connesso a Internet. È necessario scaricare i driver e un altro software per ottenere la realtà mista di Windows in esecuzione.  Se la connessione di rete Wi-Fi è impostata su a consumo, impostarla su non a consumo. [Altre informazioni](https://support.microsoft.com/en-us/help/4028458/windows-metered-connections-in-windows-10)

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Assicurarsi di disporre di un driver della grafica compatibile

Per completare la configurazione della realtà mista di Windows, è necessario che il PC disponga di un driver grafico WDDM 2,2 o versione successiva. Se non dispone già di un driver di grafica compatibile, provare le origini seguenti:

* Controllare gli aggiornamenti più recenti dei driver critici usando Windows Update (**avviare > impostazioni di Windows > aggiornamento e sicurezza > verifica della disponibilità di aggiornamenti**)
* Verificare la disponibilità di aggiornamenti più recenti dei driver facoltativi:
    1. Fare clic con il pulsante destro del mouse su **> Device Manager**.
    2. Espandere **schede di visualizzazione**.
    3. Fare clic con il pulsante destro del mouse sulla scheda grafica e scegliere **Aggiorna driver > cercare automaticamente il software driver aggiornato**.
* Controllare il sito Web del produttore (OEM) del computer.
* Controllare il sito Web del produttore della scheda grafica nel PC (ad esempio, AMD, Intel o NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Assicurarsi di disporre di tutti gli adapter necessari

Il PC compatibile con la realtà mista di Windows potrebbe non avere le porte HDMI e USB 3,0 di dimensioni complete necessarie per connettere l'auricolare immersivo. In alternativa, potrebbe essere necessaria una scheda Bluetooth per soddisfare i requisiti del portale per la realtà mista di Windows.  In tal caso, sarà necessario disporre di adapter per connettere l'auricolare e i controller di movimento. Assicurarsi di esaminare un elenco di [tipi di adapter che potrebbero essere necessari e alcune raccomandazioni su modelli di adapter specifici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

## <a name="make-sure-that-you-have-input-devices"></a>Assicurarsi di avere dispositivi di input

La realtà mista di Windows è progettata per funzionare al meglio con i controller di movimento della realtà mista di Windows, che forniscono interazioni naturali e precise senza necessità di installare hardware sulle pareti. È anche possibile usare un controller Xbox o un mouse e una tastiera.

## <a name="get-headphones-if-your-headset-didnt-come-with-them"></a>Ricevi cuffie se la cuffia non è stata associata

A meno che non siano stati acquistati cuffie Samsung HMD Odyssey, HP Reverb o HP reverbi G2 (che hanno integrato cuffie AKG e un microfono dual array integrato), è necessario ottenere un auricolare audio con una coppia di cuffie che può essere collegata al jack audio headset's 3,5 mm di HMD.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Assicurarsi di disporre di una grande quantità di spazio aperto

Se si desidera spostarsi quando si usa la realtà mista di Windows, è necessario avere uno spazio aperto di grandi dimensioni.  Durante l'installazione verrà richiesto di scegliere tra "seduti e in piedi" o "tutte le esperienze". Scegliere "tutte le esperienze" e configurare un limite se si desidera spostarsi. Per comprendere i requisiti di spazio, rivedere le [linee guida per l'integrità, la sicurezza e la comodità dell'auricolare immersive](wmr-health-safety-comfort.md) .

### <a name="seated-and-standing-no-boundary"></a>Seduto e in piedi (nessun limite)

Se si seleziona "seduto e in piedi", si userà l'auricolare senza un limite. Ciò significa che è necessario rimanere in un punto qualsiasi quando si usa la cuffia, in modo da evitare ostacoli fisici e rischi di inciampare. È possibile rimanere in attesa, ma non è consigliabile spostarsi. Alcune app possono essere progettate per funzionare con un limite, quindi è possibile che non sia possibile usarle o che non abbiano la stessa esperienza se vengono usate senza un limite.

### <a name="all-experiences-boundary"></a>Tutte le esperienze (limite)

Se si sceglie "tutte le esperienze", si configurerà un limite e sarà possibile spostarsi e usare app ed esperienze che funzionano con un limite, oltre a quelle che non ne richiedono una. È necessario preparare lo spazio per assicurarsi che non ci siano ostacoli, rischi o elementi fragili nell'area che verrà usata (anche sopra la testa). Non impostare nella parte superiore di una scala o sotto una ventola a soffitto molto bassa. Rimuovere fragili e gli ostacoli dall'area e assicurarsi che tutti gli utenti che usano l'auricolare leggano e conoscano le [linee guida](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)per la sicurezza.

## <a name="see-also"></a>Vedere anche

* [Collegare il HMD](plug-in-your-headset.md)
* [Requisiti hardware minimi per il PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)