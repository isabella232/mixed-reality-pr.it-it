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
ms.openlocfilehash: f4743b6548def227675944fcd742b1596963cb3c
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725492"
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

Verificare i [requisiti hardware](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) per la realtà mista di Windows per il PC o eseguire il [portale di realtà mista di Windows](install-windows-mixed-reality.md#launch-mixed-reality-portal) nel PC per verificare la compatibilità con la realtà mista Windows.

Per informazioni dettagliate, vedere [problemi di compatibilità dei PC](https://support.microsoft.com/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality) .

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Verificare che sia installato Windows 10 versione 1709 o versione successiva

Per usare la realtà mista di Windows, è necessario che sia in esecuzione Windows 10 versione 1903 o successiva. Le versioni compatibili di Windows 10 includono:

* Windows 10 versione 1903
* Windows 10 versione 1909
* Windows 10 versione 2004
* Versione di Windows 10 20H2

Per visualizzare la versione di Windows 10 attualmente in esecuzione nel dispositivo, selezionare il pulsante **Start** , quindi selezionare **impostazioni > sistema > informazioni su**.

Per assicurarsi che Windows 10 sia aggiornato nel computer, fare clic sul pulsante **Start** , quindi selezionare **impostazioni > aggiorna & sicurezza > Windows Update**.  Selezionare **Verifica disponibilità aggiornamenti**. Se sono disponibili aggiornamenti, installarli.

Per ulteriori informazioni, consultare la pagina relativa [all'aggiornamento del computer](https://support.microsoft.com/help/12373/windows-update-faq) .

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Verificare che il PC sia connesso a Internet

Verificare che il PC sia connesso a Internet e scaricare i driver ed eventuali software aggiuntivi per ottenere la realtà mista di Windows in esecuzione.

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Assicurarsi di disporre di un driver della grafica compatibile

Per completare la configurazione di realtà mista di Windows, per il PC è necessario un driver di grafica WDDM 2,2 o versione successiva. Se non dispone già di un driver di grafica compatibile, provare le origini seguenti:

* Controllare gli aggiornamenti più recenti dei driver critici usando Windows Update (**avviare > impostazioni di Windows > aggiornamento e sicurezza > verifica della disponibilità di aggiornamenti**)
* Verificare la disponibilità di aggiornamenti più recenti dei driver facoltativi:
    1. Fare clic con il pulsante destro del mouse su **> Device Manager**.
    2. Espandere **schede di visualizzazione**.
    3. Fare clic con il pulsante destro del mouse sulla scheda grafica e scegliere **Aggiorna driver > cercare automaticamente il software driver aggiornato**.
* Controllare il sito Web del produttore (OEM) del computer.
* Controllare il sito Web del produttore della scheda grafica nel PC (ad esempio, AMD, Intel o NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Assicurarsi di disporre di tutti gli adapter necessari

Il PC compatibile con la realtà mista di Windows potrebbe non avere le porte HDMI e USB 3,0 di dimensioni complete necessarie per connettere l'auricolare immersivo. Potrebbe inoltre essere necessaria una scheda Bluetooth per soddisfare i requisiti del portale per la realtà mista di Windows.  In tal caso, sarà necessario disporre di adapter per connettere l'auricolare e i controller di movimento. Assicurarsi di esaminare l'elenco dei [tipi di adapter e le raccomandazioni per i modelli di adapter specifici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

## <a name="make-sure-that-you-have-input-devices"></a>Assicurarsi di avere dispositivi di input

La realtà mista di Windows è progettata per funzionare al meglio con i controller di movimento della realtà mista di Windows, che forniscono interazioni naturali e precise senza necessità di installare hardware sulle pareti. È anche possibile usare un controller Xbox o un mouse e una tastiera.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Assicurarsi di disporre di una grande quantità di spazio aperto

Se si desidera spostarsi quando si usa la realtà mista di Windows, è necessario avere uno spazio aperto di grandi dimensioni.  Durante l'installazione, verrà chiesto di scegliere tra "seduti e in piedi" o "tutte le esperienze". Scegliere "tutte le esperienze" e configurare un limite se si desidera spostarsi. Per comprendere i requisiti di spazio, rivedere le [linee guida per l'integrità, la sicurezza e la comodità dell'auricolare immersive](wmr-health-safety-comfort.md) .

### <a name="seated-and-standing-no-boundary"></a>Seduto e in piedi (nessun limite)

Se si seleziona "seduto e in piedi", si userà l'auricolare senza un limite. Ciò significa che è necessario rimanere in una sola posizione quando si usa l'auricolare per evitare ostacoli fisici e rischi di intervento. È possibile rimanere in attesa, ma non è consigliabile spostarsi. Alcune app possono essere progettate per funzionare con un limite, quindi potrebbero non funzionare o fornire la stessa esperienza se vengono usate senza uno.

### <a name="all-experiences-boundary"></a>Tutte le esperienze (limite)

Se si sceglie "tutte le esperienze", sarà possibile configurare un limite ed essere in grado di spostarsi tra le esperienze delle app che funzionano con un limite e quelle che non ne richiedono una. Preparare lo spazio assicurandosi che non ci siano ostacoli, rischi o elementi fragili nell'area che verrà usata, incluso sopra l'intestazione. Non impostare nella parte superiore di una scala o sotto una ventola a soffitto molto bassa. Rimuovere fragili e gli ostacoli dall'area e assicurarsi che tutti gli utenti usino l'auricolare leggano e conoscano le [linee guida](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)per la sicurezza.

## <a name="see-also"></a>Vedi anche

* [Collegare il HMD](plug-in-your-headset.md)
* [Requisiti hardware minimi per il PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)