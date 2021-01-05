---
title: Installare il software Windows Mixed Reality
description: Dopo aver inserito l'auricolare della realtà mista di Windows, usare l'app portale per la realtà mista per iniziare e scaricare le funzionalità della realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, introduzione, configurazione, portale per realtà mista
appliesto:
- Windows 10
ms.openlocfilehash: 72782d14218e0a95b5a88297310f791c977fe094
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726072"
---
# <a name="install-windows-mixed-reality-software"></a>Installare il software Windows Mixed Reality

> [!div class="nextstepaction"]
> [Ottenere il portale per la realtà mista](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab)

## <a name="launch-mixed-reality-portal"></a>Avviare il portale di realtà mista

Dopo aver collegato l'auricolare della realtà mista di Windows e aver installato correttamente il driver, il portale per la realtà mista (MRP) verrà avviato automaticamente sul desktop. Se il portale non viene avviato, è sempre possibile aprire il portale per la realtà mista da **Start > portale per la realtà mista**. Una **volta avviato il portale, selezionare inizia**

![Benvenuti in Realtà mista](images/1050px-mixedrealityportal.png)

Nel portale per la realtà mista è possibile:

* Visualizzare un Livestream della visualizzazione nell'auricolare (solo per la realtà mista di Windows) selezionando "arresta anteprima" o "Avvia anteprima". È anche possibile attivare e disattivare l'anteprima dal menu Start della realtà mista.
* Vedere lo stato dell'auricolare e dei controller. Selezionare "menu" per visualizzare tutte le informazioni.
* Configurare nuovi controller. Selezionare **Menu > configurare i controller**.
* Attivare o disattivare il limite. Selezionare **Menu > limite**. Se si disattiva questa opzione, è necessario rimanere in un'unica posizione per la sicurezza.
* Creare un nuovo limite. Selezionare **Menu > Esegui installazione**.
* Consente di ottenere le foto della realtà mista. Selezionare il **Menu > vedere le foto della realtà mista**.
* Ottieni app e giochi per realtà mista. Selezionare il **Menu > ottenere le app per la realtà mista**.

## <a name="download-windows-mixed-reality"></a>Scarica realtà mista di Windows

La realtà mista di Windows ha una dimensione di 1 GB e i tempi di download variano a seconda della connessione Internet. Se viene visualizzato un messaggio che indica che non è stato possibile scaricare il software per la realtà mista, esaminare le procedure per la [risoluzione dei problemi](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading).

## <a name="general-troubleshooting"></a>Risoluzione dei problemi generali

Se si verificano problemi o si riceve un messaggio di errore durante l'uso del portale per la realtà mista, provare a eseguire queste soluzioni.

**Riavvia realtà mista di Windows**

1. Disconnettere l'auricolare dal PC (entrambi i cavi).
2. Riavviare il computer, quindi riconnettere l'auricolare.

**Verificare che il PC riconosca la cuffia**

Se il riavvio non funziona, assicurarsi che la cuffia sia riconosciuta dal PC. Selezionare Start, digitare gestione dispositivi nella casella di ricerca e quindi selezionarlo nell'elenco. Espandere dispositivi di realtà mista e verificare se l'auricolare è elencato.

Se non è elencato, provare a eseguire le operazioni seguenti:

* Collegare la cuffia a porte diverse sul PC, se disponibile.
* Verificare la disponibilità degli aggiornamenti software più recenti da [Windows Update](https://support.microsoft.com/help/12373).
* Disinstallare e reinstallare la realtà mista di Windows:
    1. Disconnettere l'auricolare dal PC (entrambi i cavi).
    2. Selezionare **impostazioni > realtà mista > disinstallare**.
    3. Disaccoppiare i controller di movimento: selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi**. Selezionare ogni controller, quindi selezionare **Rimuovi dispositivo**.
    4. Per reinstallare la realtà mista di Windows, collegare la cuffia al PC.

## <a name="common-error-messages"></a>Messaggi di errore comuni

Ecco alcuni aspetti da provare per [i messaggi di errore](error-codes.md) che potrebbero essere visualizzati.

| Se viene visualizzato questo messaggio | Prova |
| --- | --- |
| Controllare il cavo USB | Connettere la cuffia a una porta USB diversa (e assicurarsi che si tratta di una supervelocità USB 3,0). Provare anche a rimuovere le estensioni o gli hub tra la cuffia e il computer. |
| Controllare il cavo di visualizzazione | Attenersi alla procedura seguente: <ul><li>Connettere la cuffia a DisplayPort 1,2 o versione successiva o HDMI 1,4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.</li><li>Se si usa un adapter, assicurarsi che sia in grado di supportare 4K</li><li>Provare a usare una porta HDMI diversa</li><li>Se si dispone di un monitor esterno collegato a una porta HDMI, provare a connetterlo a una DisplayPort e usare la porta HDMI per la cuffia</li></ul> |
| Si è verificato un errore | Attenersi alla procedura generale per la risoluzione dei problemi descritta sopra. |

## <a name="review-and-accept-terms-and-conditions"></a>Esaminare e accettare i termini e le condizioni

Per continuare l'installazione, è necessario disporre di 2 GB di spazio libero nel PC. Esaminare e premere **Accetto** i termini e le condizioni per continuare

![Accetta termini e condizioni](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>Verifica di compatibilità

Next up è il controllo compatibile. Il portale per la realtà mista verificherà la compatibilità del PC con la realtà mista. I controlli **verdi** indicano che il computer ha superato l'elemento richiesto. Il triangoli **arancione** significa che possono verificarsi problemi con il PC per il requisito specificato. Se si riscontrano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il computer. **Rosso** XS significa che il PC non soddisfa i requisiti per l'elemento specificato.

![Verifica compatibilità](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>Preparazione

Verrà visualizzato il messaggio "preparazione della configurazione" sullo schermo con un'icona di rotazione, che dovrebbe richiedere solo alcuni istanti:

![Preparazione per la configurazione](images/1050px-gettingsetup.png)

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi di installazione](installation_errors.md)
* [Risoluzione dei problemi di installazione](wmr-setup-faq.md)
* [Configurare Windows Mixed Reality](set-up-windows-mixed-reality.md)
