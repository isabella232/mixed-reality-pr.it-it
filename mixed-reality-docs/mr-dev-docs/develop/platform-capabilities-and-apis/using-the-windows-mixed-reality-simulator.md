---
title: Uso del simulatore di Windows Mixed Reality
description: Il Windows Mixed Reality simulatore consente di testare le app di realtà mista nel PC senza Windows Mixed Reality visore immersivo.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, simulatore, test
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220935"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Uso del simulatore di Windows Mixed Reality

Il Windows Mixed Reality simulatore consente di testare le app di realtà mista nel PC senza Windows Mixed Reality visore immersivo. Il simulatore è disponibile con il Windows 10 Creators Update. Il simulatore è simile al [HoloLens Emulator](using-the-hololens-emulator.md), anche se il simulatore non usa una macchina virtuale. Le app simulate vengono eseguite nella sessione Windows 10 utente desktop, proprio come se si usasse un visore immersivo. Gli input umani e ambientali letti dai sensori in un visore vr immersivo vengono invece simulati usando la tastiera, il mouse o il controller Xbox. Le app non necessitano di alcuna modifica per l'esecuzione nel simulatore e non sanno che non sono in esecuzione in un visore vr immersivo.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Abilitazione del simulatore Windows Mixed Reality

1. **Abilitare la modalità sviluppatore** Impostazioni -> -> per gli sviluppatori
2. Avviare il **Portale realtà mista** dal desktop
3. Se è la prima volta che si avvia il portale, è necessario eseguire l'esperienza di configurazione
   1. Selezionare **Introduzione**
   2. Selezionare **Accetto** l'accettazione del contratto
   3. Selezionare **Configura per la simulazione (per gli sviluppatori)** per continuare la configurazione senza un dispositivo fisico
   4. Selezionare **Configura per** confermare la scelta
4. Selezionare il **pulsante Per** sviluppatori sul lato sinistro del Portale realtà mista
5. Attivare l'interruttore **Simulazione**
   * L'abilitazione della simulazione installa e abilita il controller 6-DOF simulato a sinistra per impostazione predefinita.  Prima dell'Windows 10 aggiornamento di maggio 2019, l'installazione di un controller simulato a 6 DOF richiede autorizzazioni di amministratore.  Accettare la finestra di dialogo Controllo account utente, se presente.

A questo punto dovrebbe essere in esecuzione con la simulazione.

Se si vuole disabilitare la modalità sviluppatore in Impostazioni,  è necessario impostare l'interruttore Simulazione su Disattivato nella sezione **Per** sviluppatori del Portale realtà mista.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Distribuzione di app nel simulatore di realtà mista

Poiché il simulatore viene eseguito nel PC locale senza una macchina virtuale, è possibile distribuire le app universal Windows nel **computer** locale durante il debug.

## <a name="basic-simulator-input"></a>Input del simulatore di base

Il controllo del simulatore è simile a molti videogiochi 3D comuni e all HoloLens [emulatore](using-the-hololens-emulator.md). Usando la tastiera, il mouse o il controller Xbox, sono disponibili diverse opzioni di input.

È possibile controllare il simulatore indirizzando le azioni di un utente simulato che indossa un visore immersivo. Le azioni spostano l'utente simulato e causano interazioni con le app che rispondono come farebbe con un visore immersivo.
* **Camminare avanti, indietro, verso sinistra e verso destra**: usa i tasti W, A, S e D della tastiera oppure il joystick sinistro di un controller Xbox.
* **Cerca verso l'alto,** verso il basso, a sinistra e a destra: selezionare e trascinare il mouse, usare i tasti di direzione sulla tastiera o la levetta destra su un controller Xbox.
* **Pulsante di azione premere sul controller:** fare clic con il pulsante destro del mouse, premere INVIO sulla tastiera o usare il pulsante A in un controller Xbox.
* **Premere il pulsante Home** sul controller: premere Windows o F2 sulla tastiera oppure premere il pulsante B in un controller Xbox.
* **Spostamento del controller per lo scorrimento:** tenere premuto ALT e il pulsante destro del mouse, quindi trascinare il mouse verso l'alto o verso il basso. In un controller Xbox tenere premuti il grilletto destro e il pulsante A e spostare il joystick destro verso l'alto e verso il basso.

## <a name="tracked-controllers"></a>Controller monitorati

Il simulatore di realtà mista può simulare fino a due controller di movimento tracciati manualmente. Abilitarli usando le opzioni di attivazione/disattivazione nel Portale realtà mista. Ogni controller simulato ha:
* Posizione e orientamento nello spazio
* Pulsante Home
* Pulsante Menu
* Pulsante Di controllo
* Touchpad
* Levetta personale
* Livello della batteria

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo con Unity che è stato delineato, ci si trova nella fase di distribuzione. Da qui è possibile passare all'argomento [successivo](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) o passare direttamente all'aggiunta di servizi avanzati.

> [!div class="nextstepaction"]
> [Servizi avanzati](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Vedi anche
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Input avanzato del simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapping spaziale in Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](../../develop/native/spatial-mapping-in-directx.md)
