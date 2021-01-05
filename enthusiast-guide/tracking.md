---
title: Domande frequenti sul rilevamento
description: Rilevamento della risoluzione dei problemi di realtà mista di Windows che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, monitoraggio
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725832"
---
# <a name="tracking-faqs"></a>Domande frequenti sul rilevamento

## <a name="my-headset-has-stopped-tracking"></a>Il rilevamento dell'auricolare è stato interrotto

Assicurarsi che le spie siano accese e che non sia presente alcun ostacolo alle fotocamere di rilevamento interne all'interno dell'auricolare. Se il rilevamento viene perso, la ripresa potrebbe richiedere alcuni secondi. Riavviare il portale di realtà mista di Windows. il rilevamento non viene riavviato.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso esaminare ma non riesco a tradurre (sono bloccato in 3DOF)

Ciò significa che il sistema di rilevamento non è in grado di generare la richiesta o che l'applicazione ha interrotto l'uso dei nuovi dati di post per il rendering. Per correggere il problema:

* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi che la chat room disponga di informazioni sufficienti per la traccia.
* Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegare il dispositivo.
* Se il messaggio viene mantenuto, contattare il [supporto](https://support.microsoft.com/) tecnico

## <a name="the-view-in-the-hmd-is-frozen"></a>La visualizzazione in HMD è bloccata

Ciò significa in genere che l'applicazione o un componente a livello di sistema non è riuscito. Provare a:

1. Per uscire dall'applicazione, fare clic sul pulsante "Home".
2. Scollegare il dispositivo, chiudere MRP e collegare di nuovo il dispositivo.
3. Riavvia il PC.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Il mondo è stato brevemente bloccato e inclinato o capovolto prima di tornare al normale

Il problema potrebbe essere causato da un'applicazione o da un componente a livello di sistema che si è verificato un errore irreversibile o una mancanza temporanea di memoria o risorse della CPU. Per verificare:

1. Aprire Task Manager e assicurarsi che almeno il 20% della CPU sia disponibile, 400 MB di memoria e i/o del disco siano inferiori al 80%.
2. Passare a **Visualizzatore eventi > registri di Windows > applicazione** per individuare eventuali errori che si sono verificati a partire dall'ora del blocco. Cercare qualsiasi elemento che si riferisca ai sensori HoloLens, alla realtà mista o all'applicazione in esecuzione in quel momento. Questi log potrebbero spiegare la causa dell'errore.
3. Riavviare il computer se il problema persiste.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Il mondo è stato capovolto momentaneamente e restituito al normale

Questa situazione è in genere causata da errori durante il recupero dei dati dei sensori dall'auricolare per informare gli algoritmi di rilevamento. Se il problema si verifica di frequente:

1. Collegare la cuffia a una porta USB 3,0 diversa.
2. Collegare la cuffia direttamente al PC anziché in un hub USB 3,0.
3. Se il problema persiste, contattare il [supporto](https://support.microsoft.com/)tecnico.

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Il mondo è inclinato, ma è possibile spostarsi e aggirare la realtà mista di Windows

Se i dati del sensore vengono registrati nei dati dell'ambiente nel PC, è possibile che la realtà mista di Windows appaia inclinata, a volte in modo permanente. Per risolvere il problema:

1. Scollegare l'auricolare, chiudere la realtà mista di Windows e collegare di nuovo l'auricolare.
2. Riavvia il PC.
3. Cancellare i dati dell'ambiente.