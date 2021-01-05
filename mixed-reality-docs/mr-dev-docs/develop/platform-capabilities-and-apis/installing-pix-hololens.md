---
title: Installazione PIX per HoloLens 2
description: Informazioni su come installare PIX per i dispositivi HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, acquisizione, cuffia a realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822923"
---
# <a name="installing-pix-for-hololens-2"></a>Installazione PIX per HoloLens 2

[Pix](https://devblogs.microsoft.com/pix) è uno strumento di ottimizzazione e debug delle prestazioni per le applicazioni DirectX 12 in Windows. 

## <a name="setup"></a>Configurazione

1. Scaricare la [versione]( https://devblogs.microsoft.com/pix/download) più recente di pix dal PC host e connettere HoloLens 2 al PC tramite un cavo USB.

2. Se il HoloLens 2 si trova in una [Build di Windows Insider](https://insider.windows.com) o ha una configurazione che interrompe Pix,  [relampeggiare il dispositivo](https://docs.microsoft.com/hololens/hololens-recovery) per cancellare tutti i dati.

3. Abilitare la **modalità sviluppatore** e il portale per i **dispositivi**:

* Aprire **le impostazioni** dalla Home realtà mista:

![Screenshot del menu HoloLens con il pulsante Impostazioni evidenziato](images/pix-img-01.jpg)

* Selezionare **aggiorna & sicurezza**:

![Screenshot della finestra Impostazioni aperta in HoloLens con il pulsante Aggiorna e sicurezza evidenziato](images/pix-img-02.jpg)

* Seleziona **per gli sviluppatori**:

![Screenshot della finestra sicurezza e aggiornamenti Apri con per gli sviluppatori pulsante evidenziato](images/pix-img-03.jpg)

* Attivare **Usa funzionalità** per gli sviluppatori e **abilitare il portale** per i dispositivi

![Screenshot della finestra per sviluppatori aprire in impostazioni con il pulsante Abilita il portale del dispositivo evidenziato](images/pix-img-04.jpg)

![Screenshot della finestra per sviluppatori aperta in impostazioni con l'opzione Usa sviluppo funzionalità evidenziata](images/pix-img-05.jpg)

* Con il dispositivo ancora connesso, sveglio e con l'utente connesso, avviare Visual Studio.

> [!IMPORTANT]
> Verificare che il dispositivo non sia in modalità standby o in stato di sospensione. In caso di problemi con questo passaggio, fare riferimento alle istruzioni del portale per i [dispositivi Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

## <a name="preparing-for-deployment"></a>Preparazione per la distribuzione

1. In Visual Studio impostare **arm64** come piattaforma e **dispositivo** come dispositivo:

![Screenshot della soluzione Visual Studio con impostazioni della piattaforma e del dispositivo evidenziate](images/pix-img-06.png)

2. Quando Visual Studio richiede un **pin** dal dispositivo:

![Screenshot del popup di Visual Studio che richiede PIN](images/pix-img-07.png)

* Selezionare **le impostazioni** dalla shell
* Selezionare **aggiorna & sicurezza**
* Selezionare **per gli sviluppatori** e premere associa in **Individuazione dispositivo** 

![Screenshot della finestra per sviluppatori aperta in impostazioni con individuazione dispositivo evidenziata](images/pix-img-08.jpg)

![Screenshot del popup del dispositivo a pagamento con il codice di registrazione evidenziato](images/pix-img-09.jpg)

* Immettere il numero di PIN generato in Visual Studio

3. In Visual Studio l'app verrà distribuita nel HoloLens 2 connesso, operazione che può richiedere alcuni minuti a seconda dell'app.

## <a name="launching-pix"></a>Avvio di PIX

Per prima cosa, usare il portale del dispositivo per verificare che l'app non sia in esecuzione nel HoloLens 2. Avviare quindi PIX, connettersi al dispositivo e selezionare **Home**:

![Screenshot della schermata iniziale dell'applicazione PIX](images/pix-img-10.png)

* Selezionare **Connetti** dal menu a sinistra:

![Screenshot del menu a sinistra dell'applicazione PIX con il pulsante Connetti evidenziato](images/pix-img-11.png)

2. Nella scheda **computer** selezionare **Aggiungi** e immettere le credenziali seguenti:
    * Alias: a discrezione dell'utente
    * Nome host o indirizzo IP: 127.0.0.1

3. Selezionare **Connetti** in basso a destra nella scheda **computer** :

![Screenshot della finestra di connessione all'applicazione PIX con alias, nome host, indirizzo IP e pulsante Aggiungi evidenziato](images/pix-img-12.png)

> [!NOTE]
> La prima connessione è sempre più lenta perché i file binari vengono copiati.

4. Quando PIX si è connesso a HoloLens 2, trovare l'app nella sezione **selezionare il processo di destinazione** nella scheda Avvia UWP e selezionare **Avvia**:

![Screenshot dell'applicazione PIX con la finestra selezione processo di destinazione e il pulsante Avvia evidenziato](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU acquisita

1. Avviare l'acquisizione della GPU facendo clic su **Photo** nella sezione **acquisizione GPU** :

![Screenshot dell'applicazione PIX con il pannello di connessione PC aperto con l'acquisizione GPU evidenziato](images/pix-img-14.png)

2. Aprire l'acquisizione per l'analisi facendo clic sullo screenshot generato nel pannello **acquisizione GPU** :

![Screenshot dell'applicazione PIX con la sezione acquisizione GPU aperta con il pannello di acquisizione GPU evidenziato](images/pix-img-15.png)

3. Premere **Start** per avviare l'analisi:

![Screenshot dell'applicazione PIX con il pulsante Start evidenziato](images/pix-img-16.png)

> [!IMPORTANT]
> Se si raccolgono dati di temporizzazione dopo aver eseguito un'acquisizione GPU, sarà necessario riavviare l'auricolare. Si tratta di un riavvio unico del dispositivo ed è necessario per la raccolta dei dati di temporizzazione.

PIX è ora pronto per l'uso.

## <a name="see-also"></a>Vedi anche
* [Home page di PIX](https://devblogs.microsoft.com/pix)