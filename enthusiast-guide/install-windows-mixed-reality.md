---
title: Installare il software Windows Mixed Reality
description: Dopo aver collegato il visore VR Windows Mixed Reality, usare l'app Portale realtà mista per iniziare e scaricare Windows Mixed Reality funzionalità.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, introduzione, configurazione, Portale realtà mista
appliesto:
- Windows 10
ms.openlocfilehash: 1ac7ab79b6d28a44636fc16859456eb7af329a215e2d6718d0190b86281d0b67
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186947"
---
# <a name="install-windows-mixed-reality-software"></a>Installare il software Windows Mixed Reality

> [!div class="nextstepaction"]
> [Ottenere Portale realtà mista](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab)

## <a name="launch-mixed-reality-portal"></a>Avviare Portale realtà mista

Dopo aver collegato il visore VR Windows Mixed Reality e aver installato correttamente il driver, il Portale realtà mista (MRP) verrà avviato automaticamente sul desktop. Se il portale non viene avviato, è sempre possibile aprire il portale realtà mista da **Start > Portale realtà mista**. Dopo aver avviato il portale, selezionare **Informazioni di base**

![Benvenuti in Realtà mista](images/1050px-mixedrealityportal.png)

In Portale realtà mista è possibile:

* Visualizzare un livestream della visualizzazione nel visore VR (solo Windows Mixed Reality Ultra) selezionando "Arresta anteprima" o "Avvia anteprima". È anche possibile attivare e disattivare l'anteprima dal menu Start.
* Visualizzare lo stato del visore VR e dei controller. Selezionare "Menu" per visualizzare tutte le informazioni.
* Configurare nuovi controller. Selezionare **Menu > Set up controllers (Configura controller).**
* Attivare o disattivare il limite. Selezionare **Menu > Limite su/Disattivato.** Se la si disattiva, è necessario rimanere in un'unica posizione per motivi di sicurezza.
* Creare un nuovo limite. Selezionare **Menu > Esegui installazione.**
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
* Verificare la disponibilità degli aggiornamenti software più recenti [da Windows Update.](https://support.microsoft.com/help/12373)
* Disinstallare e reinstallare Windows Mixed Reality:
    1. Disconnettere il visore VR dal PC (entrambi i cavi).
    2. Selezionare **Impostazioni > Realtà mista > Disinstalla**.
    3. Annullare l'associazione dei controller del movimento: **Impostazioni > dispositivi > Bluetooth & altri dispositivi.** Selezionare ogni controller e quindi selezionare **Rimuovi dispositivo.**
    4. Per reinstallare Windows Mixed Reality, collegare di nuovo il visore VR al PC.

## <a name="common-error-messages"></a>Messaggi di errore comuni

Ecco alcuni aspetti da provare per i [messaggi di errore](error-codes.md) che potrebbero essere visualizzati.

| Se viene visualizzato questo messaggio | Prova |
| --- | --- |
| Controllare il cavo USB | Connessione il visore VR su una porta USB diversa (e assicurarsi che si tratta di un dispositivo USB SuperSpeed 3.0). Provare anche a rimuovere eventuali dispositivi extender o hub tra il visore VR e il computer. |
| Controllare il cavo di visualizzazione | Attenersi alla procedura seguente: <ul><li>Connessione il visore VR a DisplayPort 1.2 o versione successiva o HDMI 1.4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.</li><li>Se si usa un adapter, assicurarsi che sia in grado di supportarne 4K</li><li>Provare a usare una porta HDMI diversa</li><li>Se si dispone di un monitor esterno collegato a una porta HDMI, provare a collegarlo a un displayport e usare la porta HDMI per il visore VR</li></ul> |
| Si è verificato un errore | Seguire la procedura di risoluzione dei problemi generale precedente. |

## <a name="review-and-accept-terms-and-conditions"></a>Esaminare e accettare termini e condizioni

Per continuare la configurazione, è necessario avere 2 GB di spazio libero nel PC. Rivedere e premere **Accetto** le condizioni per continuare

![Accettare termini e condizioni](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>Controllo di compatibilità

Il successivo è il controllo compatibile. Portale realtà mista verifica che il PC sia compatibile con la realtà mista. **I controlli** verdi significano che il PC ha superato l'elemento richiesto. **I** triangoli arancioni significano che potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC. **Rosso** X significa che il PC non soddisfa i requisiti per l'elemento specificato.

![Controllo della compatibilità](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>Preparazione

Sullo schermo verrà visualizzato il messaggio "Prepararsi per la configurazione" con un'icona rotante, che dovrebbe richiedere solo alcuni istanti:

![Prepararsi alla configurazione](images/1050px-gettingsetup.png)

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi di installazione](installation_errors.md)
* [Risoluzione dei problemi di installazione](wmr-setup-faq.yml)
* [Configurare Windows Mixed Reality](set-up-windows-mixed-reality.md)
