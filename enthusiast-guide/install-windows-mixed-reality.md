---
title: Installare il software Windows Mixed Reality
description: Dopo aver collegato il visore Windows Mixed Reality, usare l'app Portale realtà mista per iniziare e scaricare Windows Mixed Reality funzionalità.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, introduzione, configurazione, Portale realtà mista
appliesto:
- Windows 10
ms.openlocfilehash: a0ce559372d854e5f0bd51d25d112ba285e4d81e
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944742"
---
# <a name="install-windows-mixed-reality-software"></a>Installare il software Windows Mixed Reality

> [!div class="nextstepaction"]
> [Ottenere Portale realtà mista](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab)

## <a name="launch-mixed-reality-portal"></a>Avviare Portale realtà mista

Dopo aver collegato il visore Windows Mixed Reality e aver installato correttamente il driver, il Portale realtà mista (MRP) verrà avviato automaticamente sul desktop. Se il portale non viene avviato, è sempre possibile aprire il portale di realtà mista da **Start > Portale realtà mista**. Dopo aver avviato il portale, selezionare **Introduzione**

![Benvenuti in Realtà mista](images/1050px-mixedrealityportal.png)

In Portale realtà mista, è possibile:

* Visualizzare un livestream della visualizzazione nel visore (solo Windows Mixed Reality Ultra) selezionando "Arresta anteprima" o "Avvia anteprima". È anche possibile attivare e disattivare l'anteprima dal modello di realtà mista menu Start.
* Visualizzare lo stato del visore e dei controller. Selezionare "Menu" per visualizzare tutte le informazioni.
* Configurare nuovi controller. Selezionare **Menu > Configura controller**.
* Attivare o disattivare il limite. Selezionare **Menu > limite on/off**. Se lo spegni, dovrai rimanere in un unico posto per motivi di sicurezza.
* Creare un nuovo limite. Selezionare **Menu > Esegui configurazione**.
* Accedere alle foto di realtà mista. Selezionare **Menu > Visualizza foto di realtà mista.**
* Ottieni app e giochi di realtà mista. Selezionare **Menu > Get mixed reality apps (Ottieni app di realtà mista).**

## <a name="download-windows-mixed-reality"></a>Scaricare Windows Mixed Reality

Windows Mixed Reality dimensioni sono di 1 GB e i tempi di download variano a seconda della connessione Internet. Se viene visualizzato il messaggio "Non è stato possibile scaricare il software di realtà mista", esaminare questi passaggi per la [risoluzione dei problemi.](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading)

## <a name="general-troubleshooting"></a>Risoluzione dei problemi generali

Se si verificano problemi o si ottiene un messaggio di errore durante l'Portale realtà mista, provare queste soluzioni.

**Riavviare Windows Mixed Reality**

1. Disconnettere il visore VR dal PC (entrambi i cavi).
2. Riavviare il PC, quindi riconnettere il visore VR.

**Assicurarsi che il PC riconosca il visore VR**

Se il riavvio non funziona, assicurarsi che il visore VR sia riconosciuto dal PC. Selezionare Start, digitare Gestione dispositivi nella casella di ricerca e quindi selezionarlo nell'elenco. Espandere Dispositivi di realtà mista e verificare se il visore VR è elencato.

Se non è elencato, provare a eseguire le operazioni seguenti:

* Collegare il visore VR a porte diverse nel PC, se disponibile.
* Verificare la disponibilità degli aggiornamenti software più recenti [da Windows Update](https://support.microsoft.com/help/12373).
* Disinstallare e reinstallare Windows Mixed Reality:
    1. Disconnettere il visore VR dal PC (entrambi i cavi).
    2. Selezionare **Impostazioni > realtà mista > Disinstalla**.
    3. Scollegare i controller di movimento: selezionare **Impostazioni > dispositivi > Bluetooth & altri dispositivi**. Selezionare ogni controller e quindi selezionare **Rimuovi dispositivo**.
    4. Per reinstallare Windows Mixed Reality, collegare nuovamente il visore al PC.

## <a name="common-error-messages"></a>Messaggi di errore comuni

Ecco alcuni aspetti da provare per i [messaggi di errore](error-codes.md) che potrebbero essere visualizzati.

| Se viene visualizzato questo messaggio | Prova |
| --- | --- |
| Controllare il cavo USB | Connettere il visore a un'altra porta USB (e assicurarsi che si tratta di un DISPOSITIVO USB SuperSpeed 3.0). Provare anche a rimuovere eventuali extender o hub tra il visore e il computer. |
| Controllare il cavo di visualizzazione | Attenersi alla procedura seguente: <ul><li>Connettere il visore a displayport 1.2 o versione successiva o HDMI 1.4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.</li><li>Se si usa un adattatore, assicurarsi che sia in grado di usare 4K</li><li>Provare a usare una porta HDMI diversa</li><li>Se si dispone di un monitor esterno collegato a una porta HDMI, provare a collegarlo a un displayport e usare la porta HDMI per il visore</li></ul> |
| Si è verificato un errore | Seguire la procedura di risoluzione dei problemi generale precedente. |

## <a name="review-and-accept-terms-and-conditions"></a>Esaminare e accettare termini e condizioni

Per continuare con la configurazione, è necessario avere 2 GB di spazio libero nel PC. Rivedere e premere **Accetto** i termini e le condizioni per continuare

![Accettare termini e condizioni](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>Controllo di compatibilità

Il passaggio successivo è il controllo compatibile. Portale realtà mista verifica che il PC sia compatibile con la realtà mista. **I controlli** verdi significano che il PC ha superato l'elemento richiesto. **I** triangoli arancioni significano che potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC. **Rosso** X significa che il PC non soddisfa i requisiti per l'elemento specificato.

![Verifica della compatibilità](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>Preparazione

Sullo schermo verrà visualizzato il messaggio "Getting ready to set you up" (Prepararsi alla configurazione) con un'icona rotante, che dovrebbe richiedere solo alcuni istanti:

![Prepararsi alla configurazione](images/1050px-gettingsetup.png)

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi di installazione](installation_errors.md)
* [Risoluzione dei problemi di installazione](wmr-setup-faq.yml)
* [Configurare Windows Mixed Reality](set-up-windows-mixed-reality.md)
