---
title: Portale realtà mista messaggi di errore
description: Risoluzione avanzata Windows Mixed Reality dei messaggi del portale che vanno oltre la documentazione di supporto consumer standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Portale realtà mista
appliesto:
- Windows 10
ms.openlocfilehash: c85030da129d90bb0a150ad50a6990e30b68c21bc7a3899c4182e87acd4b4fa5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186871"
---
# <a name="mixed-reality-portal-error-messages"></a>Portale realtà mista messaggi di errore

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Viene visualizzato il messaggio di errore "Si è verificato un errore" o si verificano problemi nel Portale realtà mista.

Riavviare Windows Mixed Reality:
1. Disconnettere entrambi i cavi del visore VR dal PC.
2. Riavvia il PC.
3. Riconnettere il visore VR.

Se il problema non funziona, assicurarsi che il PC riconosca il visore VR:
1. Selezionare Avvia.
2. Digitare "gestione dispositivi" nella casella di ricerca e selezionarlo nell'elenco. 
3. Espandere "Mixed reality devices" (Dispositivi di realtà mista) e verificare se il visore VR è elencato. 

Se non è elencato:
1. Collegare il visore VR a porte diverse nel PC, se disponibile.
2. Verificare la disponibilità degli aggiornamenti software più recenti Windows Update.
3. Disinstallare e reinstallare Windows Mixed Reality:
    1. Disconnettere entrambi i cavi del visore VR dal PC.
    2. Selezionare **Impostazioni > Realtà mista > Disinstalla**.
    3. Selezionare **Impostazioni > dispositivi > Bluetooth & altri dispositivi per** annullare l'associazione dei controller del movimento. Selezionare ogni controller e quindi selezionare "Rimuovi dispositivo".
    4. Collegare di nuovo il visore VR al PC per reinstallare Windows Mixed Reality.
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>Viene visualizzato il messaggio di errore "Controllare il cavo USB".

Connessione il visore VR su una porta USB diversa (e assicurarsi che si tratta di un dispositivo USB SuperSpeed 3.0). Provare anche a rimuovere eventuali dispositivi extender o hub tra il visore VR e il computer.

## <a name="im-getting-a-check-your-display-cable-error-message"></a>Viene visualizzato il messaggio di errore "Controllare il cavo video".

Per risolvere il problema, seguire questa procedura:
* Connessione il visore VR a DisplayPort 1.2 o versione successiva o HDMI 1.4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.
* Se si usa un adapter, assicurarsi che sia in grado di supportarne 4K.
* Provare a usare una porta HDMI diversa.
* Se si dispone di un monitor esterno collegato a una porta HDMI, provare a collegarlo a un displayport e usare la porta HDMI per il visore VR.
