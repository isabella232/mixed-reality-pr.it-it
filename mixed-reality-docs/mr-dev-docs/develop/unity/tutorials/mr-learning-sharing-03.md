---
title: Connessione di più utenti
description: In questo corso viene illustrato come connettere più utenti in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200737"
---
# <a name="3-connecting-multiple-users"></a>3. Connessione di più utenti

In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa. Al termine dell'esercitazione sarà possibile eseguire l'app in più dispositivi e fare in modo che ogni utente visualizzi l'avatar degli altri utenti muoversi in tempo reale.

## <a name="objectives"></a>Obiettivi

* Imparare a connettere più utenti in un'esperienza condivisa

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passare alla cartella **Assets**  (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e quindi fare clic e trascinare i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

* Prefab **NetworkLobby**
* Prefab **SharedPlayground**

![Unity con i prefab NetworkLobby e SharedPlayground appena aggiunti selezionati](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fare clic e trascinare il prefab seguente sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

* Prefab **DebugWindow**

![Unity con il prefab DebugWindow appena aggiunto selezionato](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configurazione di PUN per creare un'istanza del prefab dell'utente

In questa sezione si configurerà il progetto per l'uso del prefab PhotonUser.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)

![Unity con il componente Photon Room parzialmente configurato](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prova dell'esperienza con più utenti

Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si attiva la modalità di gioco mentre l'app è in esecuzione in HoloLens, si visualizzerà l'avatar dell'utente HoloLens muoversi quando si muove la testa (HoloLens):

![Animazione che mostra Unity con utenti collegati in rete](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Poiché l'app deve connettersi a Photon, assicurarsi che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri. Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mr-learning-sharing-04.md)
