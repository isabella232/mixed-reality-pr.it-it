---
title: Accessori hardware
description: Descrive i tipi di accessori disponibili per l'uso con Windows Mixed Reality e come configurarli.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: procedura, accessori, bluetooth, bt, controller, gamepad, clicker, xbox, hardware, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, controller del movimento
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188456"
---
# <a name="hardware-accessories"></a>Accessori hardware

Windows Mixed Reality dispositivi supportano accessori. È possibile usare porte Bluetooth o USB per associare gli accessori supportati a un visore VR immersive dal PC.

Per informazioni sull'uso Bluetooth accessori con HoloLens, vedere Connessione to Bluetooth and USB-C devices (Usare Bluetooth [dispositivi USB-C).](/hololens/hololens-connect-devices)

Windows Mixed Reality visori VR immersive richiedono accessori per l'input oltre lo [sguardo fisso](../design/gaze-and-commit.md) e [la voce.](../design/voice-input.md) Gli accessori supportati includono **tastiera e mouse,** **game pad** e controller **[del movimento.](../design/motion-controllers.md)**

## <a name="pairing-bluetooth-accessories"></a>Associazione Bluetooth accessori

L'associazione di Bluetooth periferica con un visore VR immersive è simile all'associazione di una periferica Bluetooth con un dispositivo Windows 10 desktop o mobile:

1. Dal menu Start aprire l'app **Impostazioni** app
2. Passare a **Dispositivi**
3. Attivare la radio Bluetooth se è disattivata usando l'interruttore del dispositivo di scorrimento
4. Posizionare il Bluetooth dispositivo in modalità di associazione. Questo processo varia da dispositivo a dispositivo, ma nella maggior parte Bluetooth dispositivi premuti uno o più pulsanti.
5. Attendere che il nome del dispositivo sia visualizzato nell'elenco dei Bluetooth dispositivi. Al termine, selezionare il dispositivo e quindi selezionare il **pulsante** Associa. Se sono nelle vicinanze molti dispositivi Bluetooth, potrebbe essere necessario scorrere fino alla fine dell'elenco dei dispositivi Bluetooth per visualizzare il dispositivo che si sta tentando di associare.
6. Quando si associano Bluetooth periferiche con funzionalità di input (ad esempio: tastiere Bluetooth), potrebbe essere visualizzato un pin di 6 o 8 cifre. Assicurarsi di digitare il segnaposto sulla periferica e quindi premere INVIO per completare l'associazione con il visore VR.

## <a name="motion-controllers"></a>Controller del movimento

Windows Mixed Reality controller [del movimento sono](../design/motion-controllers.md) supportati da visori VR immersive, ma non HoloLens. Questi controller offrono un monitoraggio preciso e reattivo dello spostamento nel campo di visualizzazione. I sensori nel visore VR immersive ese tracciano il rilevamento, vale a dire che non è necessario installare hardware sulle pareti dello spazio. Ogni controller dispone di diversi metodi di input.

![Windows Mixed Reality controller del movimento](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth tastiere

Le tastiere Qwerty Bluetooth possono essere abbinate e usate ovunque sia possibile usare la tastiera olografica. Ottenere una tastiera di qualità fa la differenza, quindi è consigliabile usare [Microsoft Universal Foldable Keyboard](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o Microsoft Designer Bluetooth [Desktop.](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)

## <a name="bluetooth-gamepads"></a>Bluetooth game pad

È possibile usare un controller con app e giochi che abilitano in modo specifico il supporto del game pad. I game pad non possono essere usati per controllare HoloLens'interfaccia utente.

Controller wireless Xbox che vengono con il Xbox One S o venduti come accessori per la funzionalità Xbox One S Bluetooth connettività, in modo da poterli usare con HoloLens e visori VR immersive. Il controller wireless Xbox [deve essere aggiornato](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) prima di poter essere usato con HoloLens.

Altri marchi di Bluetooth game pad possono funzionare con Windows Mixed Reality dispositivi, ma il supporto varia in base all'applicazione.

## <a name="other-bluetooth-accessories"></a>Altri Bluetooth accessori

Purché la periferica supporti i profili HID Bluetooth o GATT, può essere associata a HoloLens. Altri Bluetooth HID e GATT oltre a tastiera, mouse e clicker HoloLens possono richiedere un'applicazione complementare Microsoft HoloLens essere completamente funzionante.

Le periferiche non supportate includono:

* Le periferiche nei Bluetooth profili audio non sono supportate.
* Bluetooth dispositivi audio come altoparlanti e visori VR possono essere disponibili nell'app Impostazioni, ma non sono supportati con Microsoft HoloLens come endpoint audio.
* Bluetooth pc e telefoni abilitati per l'associazione non sono supportati per l'associazione e i trasferimenti di file.

## <a name="unpairing-a-bluetooth-peripheral"></a>Annullamento del pagamento di una Bluetooth periferica

1. Dal menu Start aprire l'app **Impostazioni** app
2. Passare a **Dispositivi**
3. Attivare la Bluetooth radio se è disattivata
4. Trovare il dispositivo nell'elenco dei dispositivi Bluetooth disponibili
5. Selezionare il dispositivo dall'elenco e quindi selezionare il **pulsante** Rimuovi