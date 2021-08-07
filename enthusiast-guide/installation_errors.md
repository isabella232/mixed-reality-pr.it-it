---
title: Errori di installazione
description: Risoluzione Windows Mixed Reality di errore di installazione avanzata che va oltre la documentazione del supporto clienti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Installazione
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213189"
---
# <a name="installation-errors"></a>Errori di installazione

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Il PC non può essere eseguito Windows Mixed Reality"

Il PC non soddisfa i [requisiti minimi necessari per](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) eseguire Windows Mixed Reality. La configurazione hardware del computer potrebbe non essere compatibile con Windows Mixed Reality oppure potrebbe essere necessario eseguire l'aggiornamento alla versione più [recente di Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

Windows Mixed Reality richiede un driver di scheda grafica che supporta almeno WDDM 2.2. Assicurarsi di avere l'aggiornamento del driver più recente del produttore. Se Windows Mixed Reality configurazione indica che la scheda grafica non soddisfa i requisiti e si pensa che lo sia, assicurarsi che il visore sia collegato alla scheda corretta.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Il PC non soddisfa i requisiti minimi necessari per l'esecuzione Windows Mixed Reality"

Il PC non soddisfa i [requisiti minimi necessari](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per la migliore esperienza Windows Mixed Reality. Il PC potrebbe essere in grado di eseguire un visore vr immersivo, ma potrebbero verificarsi problemi di prestazioni e non essere in grado di eseguire determinate applicazioni.

Windows Mixed Reality richiede un driver di scheda grafica che supporta almeno WDDM 2.2. Assicurarsi di avere l'aggiornamento del driver più recente del produttore. Se Windows Mixed Reality configurazione indica che la scheda grafica non soddisfa i requisiti e si pensa che lo sia, assicurarsi che il visore sia collegato alla scheda corretta.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Prima di poter configurare Windows Mixed Reality, l'amministratore dovrà abilitarlo per l'organizzazione. Altre informazioni"

Probabilmente si usa una rete gestita dall'organizzazione e l'organizzazione usa Windows Server Update Services (WSUS). Questi e altri criteri che possono bloccare il download. Contattare il reparto IT o l'amministratore di sistema dell'organizzazione per [abilitare Windows Mixed Reality](/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Non è stato possibile scaricare il software di realtà mista" o "Blocco stretto durante il download"

* A volte un aggiornamento in sospeso può bloccare il download di Mixed Reality Software. Passare a **Impostazioni > update & security > Windows Update** e assicurarsi che l'Windows Update sia stato installato. Scaricare e installare quindi eventuali aggiornamenti in attesa. Se viene visualizzato un errore Windows update, vedere [qui](https://support.microsoft.com/help/10164/fix-windows-update-errors).
* Assicurarsi che il PC sia connesso a Internet e abbia almeno 2 GB di spazio di archiviazione disponibile. Controllare lo stato della rete in: **Impostazioni > Rete & Internet > stato**. Se non è possibile connettersi a Internet, ottenere assistenza [qui.](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)  
* Riavviare il PC e riprovare. 

Se queste soluzioni non funzionano, provare:
* Se la Wi-Fi di rete è [impostata](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)su a consumo, impostarla su unmetered. Per **disattivare** una connessione a consumo, passare Impostazioni > Stato Impostazioni > Rete & Internet > > Modifica proprietà connessione > Imposta come connessione a consumo e selezionare "Disattivato".  
* Se di recente è stato installato un aggiornamento, possono verificarsi problemi. Non è consigliabile rimuovere gli aggiornamenti installati, in particolare gli aggiornamenti della sicurezza che mantengono al sicuro il PC. Tuttavia, a volte la rimozione dell'aggiornamento più recente può aiutare a determinare l'origine del problema: 
    * Passare a Impostazioni > **Aggiornamento & sicurezza > Cronologia** aggiornamenti installati > disinstalla aggiornamenti
    * Selezionare l'ultimo aggiornamento installato e "Disinstalla".
    * Quando viene richiesto "Si è certi che si vuole disinstallare questo aggiornamento?" risposta "Sì". Se viene visualizzato un errore durante il tentativo di eseguire questa procedura, ottenere altri dettagli su come [correggere gli errori di Windows Update.](https://support.microsoft.com//help/10164/fix-windows-update-errors) 
    * Riavviare il PC e riprovare. 
    * Se Windows Mixed Reality correttamente, reinstallare gli aggiornamenti più recenti **in Impostazioni > Windows Update > Controlla** aggiornamenti e verificare se Windows Mixed Reality continua a funzionare. Se non viene installato correttamente, reinstallare gli aggiornamenti e contattare il Windows supporto tecnico. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Si è verificato un errore e non è stato possibile avviare Windows Mixed Reality"
Per altre informazioni su un codice di errore specifico, vedere [qui](error-codes.md). È anche possibile provare a:

* Scollegare entrambi i cavi del visore dal PC.
* Riavvia il PC.
* Passare a Impostazioni > Update & security > Windows Update (Aggiornamento > Windows **sicurezza)** e verificare che l'Windows Update sia attivato. Scaricare e installare eventuali aggiornamenti in attesa.
* Riconnettere il visore al PC e quindi riprovare a configurare.

Se questi passaggi non funzionano, disinstallare e quindi reinstallare Windows Mixed Reality:
* Passare a **Impostazioni > realtà mista > disinstalla e** selezionare "Disinstalla". 
* Riavvia il PC. 
* Per avviare di nuovo il processo di configurazione, è sufficiente collegare il visore al PC.