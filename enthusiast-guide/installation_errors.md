---
title: Errori di installazione
description: Risoluzione degli errori di installazione della realtà mista di Windows avanzata che va oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, installazione
appliesto:
- Windows 10
ms.openlocfilehash: 6837824346ce2390437daef0bc8eeab447f9e1f4
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686221"
---
# <a name="installation-errors"></a>Errori di installazione

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Il PC non può eseguire la realtà mista di Windows"

Il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessari per eseguire la realtà mista di Windows. Il problema potrebbe essere dovuto al fatto che la configurazione hardware del computer non è compatibile con la realtà mista di Windows o perché è necessario eseguire l' [aggiornamento alla versione più recente di Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq). 

Si noti che la realtà mista di Windows richiede un driver di schede di grafica che supporta almeno WDDM 2,2, quindi assicurarsi di disporre dell'aggiornamento più recente del driver dal produttore. Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Ci siamo quasi lì: questo PC non soddisfa i requisiti minimi necessari per eseguire la realtà mista di Windows"

Il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessari per ottenere la migliore esperienza nella realtà mista di Windows. Il PC potrebbe essere in grado di eseguire un auricolare immersivo, ma potrebbe non essere in grado di eseguire determinate applicazioni o potrebbe avere problemi con le prestazioni.

Si noti che la realtà mista di Windows richiede un driver di schede di grafica che supporta almeno WDDM 2,2, quindi assicurarsi di disporre dell'aggiornamento più recente del driver dal produttore. Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Prima di poter configurare la realtà mista di Windows, l'amministratore dovrà abilitarlo per l'organizzazione. Altre informazioni "

Probabilmente si è in una rete gestita dall'organizzazione e l'organizzazione usa Windows Server Update Services (WSUS) o altri criteri che potrebbero bloccare il download. Contattare il reparto IT dell'organizzazione o l'amministratore di sistema per [abilitare la realtà mista di Windows](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Non è stato possibile scaricare il software per realtà mista" o "blocco durante il download"

* A volte un aggiornamento in sospeso può bloccare il download del software per realtà mista. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attiva. Scaricare e installare tutti gli aggiornamenti in attesa. Se viene ricevuto un errore Windows Update, vedere la [Guida.](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)
* Verificare che il PC sia connesso a Internet e che disponga di almeno 2 GB di spazio di archiviazione disponibile. Verificare lo stato della rete in: **impostazioni > rete & Internet > stato** . Se non è possibile connettersi a Internet, ottenere assistenza [qui](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues).  
* Riavviare il computer e riprovare. 

Se queste soluzioni non funzionano, provare a:
* Se la connessione di rete Wi-Fi è impostata su a [consumo](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq), impostarla su non a consumo. Per disattivare una connessione a consumo, passare a: **impostazioni > rete & Internet > stato > modificare le proprietà di connessione > imposta come connessione a consumo** e selezionare "disattivato".  
* Se di recente è stato installato un aggiornamento, è possibile che si verifichino problemi. Non è consigliabile rimuovere gli aggiornamenti installati, in particolare gli aggiornamenti della sicurezza che mantengono il PC sicuro, ma a volte la rimozione dell'aggiornamento più recente può aiutare a determinare l'origine del problema. Per eseguire questa operazione: 
    * Passare a **impostazioni > aggiorna & sicurezza > Visualizza cronologia aggiornamenti installati > Disinstalla aggiornamenti**
    * Selezionare l'ultimo aggiornamento installato e "Disinstalla".
    * Quando viene richiesto di disinstallare l'aggiornamento? rispondere "Sì". Se si verifica un errore durante il tentativo di eseguire questi passaggi, fare clic [qui](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors). 
    * Riavviare il computer e riprovare. 
    * Se la realtà mista di Windows viene installata correttamente, reinstallare gli aggiornamenti più recenti in **impostazioni > Windows Update > verificare la disponibilità di aggiornamenti** e verificare se la realtà mista di Windows continua a funzionare. Se l'installazione non viene eseguita correttamente, reinstallare gli aggiornamenti e contattare il supporto tecnico di Windows. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Si è verificato un errore e non è stato possibile avviare la realtà mista di Windows"
Per ottenere altre informazioni su un codice di errore specifico, vedere [qui](error-codes.md). È anche possibile provare a:

* Scollegare entrambi i cavi auricolare dal PC.
* Riavvia il PC.
* Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Scaricare e installare gli aggiornamenti in attesa.
* Riconnettere l'auricolare al PC, quindi riprovare a eseguire l'installazione.

Se questi passaggi non funzionano, disinstallare e reinstallare la realtà mista di Windows:
* Passare a **impostazioni > realtà mista > disinstallare** e selezionare "Disinstalla". 
* Riavvia il PC. 
* Per avviare nuovamente il processo di installazione, è sufficiente collegare la cuffia al PC.
