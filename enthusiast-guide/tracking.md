---
title: Domande frequenti sul rilevamento
description: Tenere traccia Windows Mixed Reality risoluzione dei problemi che vanno oltre la documentazione di supporto consumer standard.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Rilevamento
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199477"
---
# <a name="tracking-faqs"></a>Domande frequenti sul rilevamento

## <a name="my-headset-has-stopped-tracking"></a>Il visore VR ha smesso di monitorare

Assicurarsi che le luci siano accese e che non ci siano elementi che ostruino le fotocamere di tracciamento interne nella parte anteriore del visore VR. Se il rilevamento viene perso, la ripresa può richiedere alcuni secondi. Riavviare il Windows Mixed Reality che il portale sta verificando non viene riavviato.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso guardarmi attorno ma non posso tradurre (sono bloccato in 3DOF)

Ciò significa che il sistema di rilevamento non può generare la posizione o che l'applicazione ha interrotto l'uso di nuovi dati di posizione per il rendering. Per correggere il problema:

* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi che la stanza abbia dettagli sufficienti per tenere traccia.
* Scollegare il dispositivo, Windows Mixed Reality e collegare nuovamente il dispositivo.
* Se il messaggio persiste, contattare il [supporto tecnico](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>La visualizzazione nell'HMD è bloccata

Ciò significa in genere che l'applicazione o un componente a livello di sistema ha avuto esito negativo. Provare a:

1. Premere il pulsante "Home" per uscire dall'applicazione.
2. Scollegare il dispositivo, chiudere MRP e collegare nuovamente il dispositivo.
3. Riavvia il PC.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Il mondo si è brevemente bloccato e inclinato o capovolto capovolto prima di tornare alla normalità

Ciò potrebbe essere causato da un componente a livello di applicazione o di sistema che ha rilevato un errore irreversibile o una mancanza temporanea di memoria o risorse della CPU. Per verificare:

1. Aprire Gestione attività e assicurarsi che almeno il 20% della CPU sia disponibile, che siano disponibili 400 MB di memoria e che l'I/O del disco sia inferiore all'80%.
2. Passare a **Visualizzatore eventi > Windows log >'applicazione** per cercare eventuali errori relativi al momento del blocco. Cercare qualsiasi elemento che faccia HoloLens sensori, realtà mista o l'applicazione in esecuzione in quel periodo. Questi log potrebbero spiegare la causa dell'errore.
3. Riavviare il PC se il problema persiste.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Il mondo si capovolge momentaneamente verso il basso e torna alla normalità

Ciò è in genere causato da errori nel recupero dei dati del sensore dal visore VR per informare gli algoritmi di rilevamento. Se ciò si verifica di frequente:

1. Collegare il visore VR a una porta USB 3.0 diversa.
2. Collegare il visore VR direttamente nel PC anziché in un hub USB 3.0.
3. Se il problema persiste, contattare il [supporto tecnico](https://support.microsoft.com/).

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Il mondo è in inclinazione, ma è possibile spostarsi e spostarsi in Windows Mixed Reality

Se gli errori relativi ai dati dei sensori vengono registrati nei dati dell'ambiente nel PC, è possibile che Windows Mixed Reality si presentino in posizione di inclinazione, a volte in modo permanente. Per risolvere il problema:

1. Scollegare il visore VR, Windows Mixed Reality e collegare nuovamente il visore VR.
2. Riavvia il PC.
3. Cancellare i dati dell'ambiente.