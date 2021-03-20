---
title: Uso del tracciamento oculare
description: Questa esercitazione illustra come usare il tracciamento oculare nelle app di realtà mista con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, tracciamento oculare
ms.localizationpriority: high
ms.openlocfilehash: 08793622917ca977c51be56267d8710e5abb78e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237177"
---
# <a name="8-using-eye-tracking"></a>8. Uso del tracciamento oculare

In questa esercitazione si apprenderà come abilitare il tracciamento oculare per HoloLens 2 e aggiungere questa funzionalità agli oggetti, in modo da attivare le azioni quando l'utente rivolge loro lo sguardo.

> [!NOTE]
> Se si distribuisce questo progetto anche in HoloLens (prima generazione), tenere presente che il tracciamento oculare è supportato solo in HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Imparare ad abilitare il tracciamento oculare per HoloLens 2
* Imparare a usare il tracciamento oculare per attivare un'azione

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:

![Finestra MRTK Project Configurator di Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Abilitazione dello sguardo fisso nel provider di dati per lo sguardo fisso

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:

* Clonare il profilo **DefaultHoloLens2InputSystemProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_HoloLens2InputSystemProfile_
* Espandere la sezione **Pointers** (Puntatori)
* Clonare il profilo **DefaultMixedRealityPointerProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityPointerProfile_
* Individuare la sezione **Gaze Settings** (Impostazioni sguardo) e selezionare la casella di controllo **Is Eye Tracking Enabled** (Tracciamento oculare abilitato)

![Componente MixedRealityToolkit di Unity con i profili appena creati applicati e il tracciamento oculare abilitato](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili di MRTK, fare riferimento alle istruzioni riportate in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Abilitazione del tracciamento oculare simulato per l'editor di Unity

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**, nella finestra Inspector (Controllo) passare alla scheda **Input** e quindi:

* Espandere la sezione **Input Data Providers** > **Input Simulation Service** (Provider di dati di input > Servizio di simulazione input)
* Clonare il profilo **DefaultMixedRealityInputSimulationProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityInputSimulationProfile_
* Individuare la **simulazione degli** sguardi a occhio e impostare la **modalità di simulazione degli sguardi** con occhi predefiniti sull' **asse di avanzamento della fotocamera**

![Unity con l'oggetto TextMeshPro selezionato](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Aggiunta del tracciamento oculare agli oggetti

Nella finestra gerarchia espandere i   >  **pulsanti** RoverExplorer, quindi selezionare tutti e tre gli oggetti Button figlio:

![Unity con oggetto Button selezionato](images/mr-learning-base/base-08-section4-step1-1.png)

Con tutti e tre gli oggetti pulsante ancora selezionati, nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **EyeTrackingTarget** a tutti gli oggetti selezionati:

![Unity con l'oggetto TextMeshPro selezionato e componenti aggiunti](images/mr-learning-base/base-08-section4-step1-2.png)

Nella finestra gerarchia espandere **RoverExplorer**  >  **Buttons**  >  **hints**  >  **SeeItSayItLabel**  >  **TextMeshPro**

Nella finestra gerarchia selezionare quindi l'oggetto pulsante **hints** e configurare il componente **EyeTrackingTarget** nel modo seguente:

* Nella sezione dell'evento **On Look At Start ()** (Quando viene rivolto lo sguardo all'inizio)
  * Fare clic sull'icona **+** piccola per aggiungere un altro evento
  * Assegnare l'oggetto  **TextMeshPro** dal pulsante **hints** al campo **None (Object)** .
  * Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento
  * Impostare l'argomento su **0,06** per aumentare del 50% le dimensioni correnti del carattere 0,04
* Nella sezione dell'evento **On Look Away ()** (Quando viene distolto lo sguardo)
  * Fare clic sull'icona **+** piccola per aggiungere un altro evento
  * Assegnare l'oggetto  **TextMeshPro** dal pulsante **hints** al campo **None (Object)** .
  * Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento
  * Impostare l'argomento su **0,04** per ripristinare le dimensioni del carattere a 0,04

![Unity con l'oggetto TextMeshPro di Hints selezionato e il componente EyeTrackingTarget configurato](images/mr-learning-base/base-08-section4-step1-3.png)

**Ripetere** questo passaggio per l'oggetto pulsante **Esplodi** e **Reimposta** per configurare la verifica degli occhi per i pulsanti rimanenti.

Se si immette la modalità di gioco e si preme il pulsante destro del mouse mentre si sposta il mouse fino a quando lo sguardo raggiunge uno dei pulsanti, si noterà che le dimensioni del carattere del testo aumentano del 50% e vengono reimpostate sulle dimensioni originali quando si è interessati:

![Doppia visualizzazione della modalità Play di Unity con lo sguardo che incontra l'obiettivo del tracciamento oculare costituito dall'etichetta del pulsante Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come abilitare il tracciamento oculare per HoloLens 2 e come aggiungere questa funzionalità agli oggetti per attivare le azioni quando l'utente rivolge loro lo sguardo.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 9. Uso dei comandi vocali](mr-learning-base-09.md)
