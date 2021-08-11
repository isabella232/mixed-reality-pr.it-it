---
title: Installazione PIX per HoloLens 2
description: Informazioni su come installare PIX per HoloLens 2 dispositivi.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, acquisizione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217313"
---
# <a name="installing-pix-for-hololens-2"></a>Installazione PIX per HoloLens 2

[PIX](https://devblogs.microsoft.com/pix) è uno strumento di ottimizzazione e debug delle prestazioni per le applicazioni DirectX 12 Windows. 

## <a name="setup"></a>Eseguire la configurazione

1. Afferrare la versione [PIÙX]( https://devblogs.microsoft.com/pix/download) più recente dal PC host e connettere il HoloLens 2 al PC tramite un cavo USB.

2. Se il HoloLens 2 si trova in una [build Windows Insider](https://insider.windows.com) o ha una configurazione che interrompe PIX, eseguire il [reflash](/hololens/hololens-recovery) del dispositivo per cancellare tutti i dati.

3. Abilitare **la modalità sviluppatore** **e Portale di dispositivi**:

* Aprire **Impostazioni** dalla home page di realtà mista:

![Screenshot del menu HoloLens con il pulsante Impostazioni evidenziato](images/pix-img-01.jpg)

* Selezionare **Aggiorna & sicurezza**:

![Screenshot della finestra delle impostazioni aperta in HoloLens con il pulsante di aggiornamento e sicurezza evidenziato](images/pix-img-02.jpg)

* Selezionare **For Developers (Per sviluppatori):**

![Screenshot della finestra sicurezza e aggiornamenti aperta con il pulsante per gli sviluppatori evidenziato](images/pix-img-03.jpg)

* Attivare Usa **funzionalità per sviluppatori** e Abilita **Portale di dispositivi**

![Screenshot della finestra per gli sviluppatori aperta nelle impostazioni con il pulsante Abilita portale dispositivi evidenziato](images/pix-img-04.jpg)

![Screenshot della finestra per gli sviluppatori aperta nelle impostazioni con l'opzione Usa funzionalità di sviluppo evidenziata](images/pix-img-05.jpg)

* Con il dispositivo ancora connesso, attivo e con l'utente connesso, avviare Visual Studio.

> [!IMPORTANT]
> Assicurarsi che il dispositivo non sia in modalità standby o in stato di sospensione. In caso di problemi con questo passaggio, vedere le istruzioni [Windows Portale di dispositivi .](./using-the-windows-device-portal.md)

## <a name="preparing-for-deployment"></a>Preparazione per la distribuzione

1. In Visual Studio impostare **ARM64** come piattaforma e **Dispositivo** come dispositivo:

![Screenshot della soluzione visual studio con le impostazioni della piattaforma e del dispositivo evidenziate](images/pix-img-06.png)

2. Quando Visual Studio viene richiesto un **PIN** dal dispositivo:

![Screenshot del popup di Visual Studio che richiede il PIN](images/pix-img-07.png)

* Selezionare **Impostazioni** da Shell
* Selezionare **Aggiorna & sicurezza**
* Selezionare **For Developers (Per** sviluppatori) e premere Pair (Associa) in **Device Discovery (Individuazione dispositivi)** 

![Screenshot della finestra per gli sviluppatori aperta nelle impostazioni con l'individuazione dei dispositivi evidenziata](images/pix-img-08.jpg)

![Screenshot del popup del dispositivo a pagamento con il codice di registrazione evidenziato](images/pix-img-09.jpg)

* Immettere il numero PIN generato in Visual Studio

3. Visual Studio distribuirà l'app nel HoloLens 2 connesso, che potrebbe richiedere alcuni minuti a seconda dell'app.

## <a name="launching-pix"></a>Avvio di PIX

Per prima cosa, Portale di dispositivi verificare che l'app non sia in esecuzione nel HoloLens 2. Avviare quindi PIX, connettersi al dispositivo e selezionare **Home**:

![Screenshot della schermata iniziale dell'applicazione PIX](images/pix-img-10.png)

* Selezionare **Connessione** dal menu a sinistra:

![Screenshot del menu a sinistra dell'applicazione PIX con il pulsante Connetti evidenziato](images/pix-img-11.png)

2. Nella scheda **Computer** selezionare **Aggiungi** e immettere le credenziali seguenti:
    * Alias: fino alla discrezione dell'utente
    * Nome host o indirizzo IP: 127.0.0.1

3. Selezionare **Connessione** in basso a destra nella **scheda Computer:**

![Screenshot della finestra di connessione dell'applicazione PIX con alias, nome host, indirizzo IP e pulsante Aggiungi evidenziato](images/pix-img-12.png)

> [!NOTE]
> La prima connessione è sempre più lenta perché i file binari vengono copiati.

4. Quando PIX si è connesso al HoloLens 2, trovare l'app nella sezione **Seleziona** processo di destinazione nella scheda Avvia UWP e selezionare **Avvia**:

![Screenshot dell'applicazione PIX con la finestra seleziona processo di destinazione e il pulsante di avvio evidenziato](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU acquisita

1. Avviare l'acquisizione GPU facendo **clic su Foto** nella sezione Acquisizione **GPU:**

![Screenshot dell'applicazione PIX con il pannello di connessione PC aperto con l'acquisizione GPU evidenziata](images/pix-img-14.png)

2. Aprire l'acquisizione per l'analisi facendo clic sullo screenshot generato nel pannello **Acquisizione GPU:**

![Screenshot dell'applicazione PIX con la sezione acquisizione GPU aperta con il pannello di acquisizione GPU evidenziato](images/pix-img-15.png)

3. Premere **Avvia** per iniziare l'analisi:

![Screenshot dell'applicazione PIX evidenziata dal pulsante Start](images/pix-img-16.png)

> [!IMPORTANT]
> Se si raccolgono dati di intervallo dopo l'acquisizione di una GPU, sarà necessario riavviare il visore. Si tratta di un riavvio una sola volta del dispositivo ed è necessario per la raccolta dei dati di intervallo.

PIX è ora pronto per l'uso.

## <a name="see-also"></a>Vedi anche
* [Home page di PIX](https://devblogs.microsoft.com/pix)