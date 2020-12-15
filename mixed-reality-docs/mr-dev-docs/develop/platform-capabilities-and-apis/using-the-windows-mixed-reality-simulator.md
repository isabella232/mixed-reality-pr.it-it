---
title: Uso del simulatore di Windows Mixed Reality
description: Il simulatore di realtà mista di Windows consente di testare app per realtà mista nel PC senza una cuffia mista a realtà mista di Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Realtà mista di Windows, simulatore, test
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530298"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Uso del simulatore di Windows Mixed Reality

Il simulatore di realtà mista di Windows consente di testare app per realtà mista nel PC senza una cuffia mista a realtà mista di Windows. Il simulatore è disponibile con Windows 10 Creators Update. Il simulatore è simile all' [emulatore di HoloLens](using-the-hololens-emulator.md), anche se il simulatore non usa una macchina virtuale. Le app simulate vengono eseguite nella sessione utente desktop di Windows 10, proprio come se si stesse usando un auricolare immersivo. Gli input umani e ambientali letti dai sensori su un auricolare immersivo vengono invece simulati usando la tastiera, il mouse o il controller Xbox. Le app non richiedono alcuna modifica per l'esecuzione nel simulatore e non sanno che non sono in esecuzione su un auricolare immersivo.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Abilitazione del simulatore di realtà mista di Windows

1. **Abilitare la modalità sviluppatore** da impostazioni-> aggiornamento e > sicurezza per gli sviluppatori
2. Avviare il **portale di realtà mista** dal desktop
3. Se è la prima volta che si avvia il portale, è necessario eseguire l'installazione
   1. Selezionare **inizia**
   2. Selezionare **Accetto** il contratto
   3. Selezionare **Configura per la simulazione (per gli sviluppatori)** per continuare l'installazione senza un dispositivo fisico
   4. Selezionare **Configura** per confermare la scelta
4. Selezionare il pulsante **per sviluppatori** sul lato sinistro del portale per la realtà mista
5. Attivare l' **opzione di attivazione** della simulazione
   * L'abilitazione della simulazione installa e Abilita il controller 6-DOF a sinistra per impostazione predefinita.  Prima di eseguire l'aggiornamento di Windows 10 maggio 2019, l'installazione di un controller 6-DOF simulato richiede autorizzazioni di amministratore.  Accettare la finestra di dialogo controllo dell'account utente, se visualizzata.

A questo punto dovrebbe essere in esecuzione la simulazione.

Se si vuole disabilitare la modalità sviluppatore nelle impostazioni, è necessario prima **di tutto attivare** l'opzione di attivazione della simulazione nella sezione **per sviluppatori** del portale per la realtà mista.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Distribuzione di app al simulatore di realtà mista

Poiché il simulatore viene eseguito nel PC locale senza una macchina virtuale, è possibile distribuire le app di Windows universali nel **computer locale** durante il debug.

## <a name="basic-simulator-input"></a>Input del simulatore Basic

Il controllo del simulatore è simile a molti giochi video 3D comuni e all' [emulatore di HoloLens](using-the-hololens-emulator.md). Usando la tastiera, il mouse o il controller Xbox, sono disponibili diverse opzioni di input.

Per controllare il simulatore, è possibile indirizzare le azioni di un utente simulato con un headset immersivo. Le azioni spostano l'utente simulato e provocano interazioni con le app che rispondono come in un auricolare immersivo.
* **Camminare avanti, indietro, verso sinistra e verso destra**: usa i tasti W, A, S e D della tastiera oppure il joystick sinistro di un controller Xbox.
* **Cercare, in basso, a sinistra e fare** clic con il pulsante destro del mouse e trascinare il mouse, usare i tasti di direzione sulla tastiera o la chiavetta destra su un controller Xbox.
* **Pulsante azione premere il controller** , fare clic con il pulsante destro del mouse, premere il tasto INVIO sulla tastiera oppure usare il pulsante a in un controller Xbox.
* **Pulsante Home premere il controller** : premere il tasto Windows o il tasto F2 sulla tastiera oppure premere il pulsante B in un controller Xbox.
* **Spostamento del controller per lo scorrimento** : tenendo premuto il tasto ALT e il pulsante destro del mouse, quindi trascinare il mouse verso l'alto o verso il basso. In un controller Xbox, mantenere il trigger destro e un pulsante e spostare la levetta destra verso l'alto e verso il basso.

## <a name="tracked-controllers"></a>Controller rilevati

Il simulatore di realtà mista può simulare fino a due controller di movimento rilevati e gestiti manualmente. Abilitarli usando le opzioni di attivazione/disattivazione nel portale per la realtà mista. Ogni controller simulato ha:
* Posizione e orientamento nello spazio
* Pulsante Home
* Pulsante Menu
* Pulsante grip
* Touchpad
* Levetta
* Livello batteria

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo con Unity che è stato delineato, ci si trova nella fase di distribuzione. Da qui è possibile passare all' [argomento](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) successivo o passare direttamente all'aggiunta di servizi avanzati.

> [!div class="nextstepaction"]
> [Servizi avanzati](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Vedere anche
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Input avanzato del simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapping spaziale in Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](../../develop/native/spatial-mapping-in-directx.md)
