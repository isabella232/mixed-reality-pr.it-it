---
title: Esercitazioni sulle funzionalità multiutente - 4. Condivisione dei movimenti di oggetti con più utenti
description: In questo corso viene illustrato come condividere i movimenti di oggetti con più utente in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4a8d98bbabd3061e8fb9f4262e202dac680d584b
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353419"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Condivisione dei movimenti di oggetti con più utenti

In questa esercitazione si apprenderà come condividere i movimenti degli oggetti in modo che tutti i partecipanti di un'esperienza condivisa possano collaborare e visualizzare le interazioni reciproche.

## <a name="objectives"></a>Obiettivi

* Configurare il progetto per condividere i movimenti degli oggetti
* Imparare a creare un'app collaborativa multiutente di base

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione.

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascinare il prefab **TableAnchor** nell'oggetto **SharedPlayground** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto SharedPlayground:

![Unity con il prefab TableAnchor appena aggiunto selezionato](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configurazione di PUN per creare un'istanza degli oggetti

In questa sezione si configurerà il progetto in modo da usare l'esperienza di Rover Explorer creata durante le [esercitazioni introduttive](mr-learning-base-01.md) e definire il punto in cui verrà creata un'istanza.

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Rover Explorer Prefab** (Prefab Rover Explorer) assegnare il prefab **RoverExplorer_Complete_Variant** dalla cartella Resources (Risorse)

![Unity con il componente Photon Room parzialmente configurato](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Con l'oggetto figlio **NetworkRoom** ancora selezionato, nella finestra Hierarchy (Gerarchia) espandi l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:

* Al campo **Rover Explorer Location** (Posizione Rover Explorer) assegnare l'oggetto figlio TableAnchor > **Table** (Tabella) dalla finestra Hierarchy (Gerarchia)

![Unity con il componente Photon Room configurato](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Prova dell'esperienza con il movimento di un oggetto condiviso

Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si preme il pulsante Play per attivare la modalità di gioco mentre l'app è in esecuzione in HoloLens, si osserverà l'oggetto muoversi in Unity quando viene spostato in HoloLens:

![Animazione che mostra Unity con oggetti collegati in rete](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Lezione completata

Il progetto è stato configurato in modo che i movimenti degli oggetti siano sincronizzati e gli utenti possano vedere gli oggetti muoversi quando vengono mossi da altri utenti. Nell'esercitazione successiva verrà implementata la funzionalità per allineare l'esperienza nel mondo fisico. In questo modo, gli utenti si vedranno reciprocamente nella posizione fisica effettiva e gli oggetti verranno visualizzati nella stessa rotazione e posizione fisica per tutti gli utenti.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mr-learning-sharing-05.md)
