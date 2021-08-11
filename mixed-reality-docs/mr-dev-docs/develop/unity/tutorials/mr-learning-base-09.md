---
title: Uso dei comandi vocali
description: Questa esercitazione illustra come configurare, creare e usare i comandi vocali nelle app di realtà mista con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, comandi vocali, input vocale
ms.localizationpriority: high
ms.openlocfilehash: 448dafbbfdea7ebec26cdafe6c638c37333bcf01399a8272d5637730469ab579
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192299"
---
# <a name="9-using-speech-commands"></a>9. Uso dei comandi vocali

In questa esercitazione verrà spiegato come creare comandi vocali e come controllarli a livello globale. Si imparerà anche a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.

## <a name="objectives"></a>Obiettivi

* Imparare a creare comandi vocali
* Imparare a controllare i comandi vocali a livello globale e locale

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Verificare che la funzionalità Microfono sia abilitata

Nel menu di Unity selezionare Mixed Reality > Toolkit > Utilities > Configure Project for MRTK (Configura Project per **MRTK)** per aprire la finestra **MRTK Project Configurator** e quindi nella sezione UWP Capabilities (Funzionalità **UWP)** verificare che **Enable Microphone Capability** (Abilita funzionalità microfono) sia disattivata:

![Abilitare la funzionalità microfono](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

## <a name="creating-speech-commands"></a>Creazione di comandi vocali

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:

* Espandere la **Speech** (Voce)
* Clonare il profilo **DefaultMixedRealitySpeechCommandsProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealitySpeechCommandsProfile_
* Verificare che **Start Behaviour** (Comportamento di avvio) sia impostato su **Auto Start** (Avvio automatico)

![Creazione di comandi vocali](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).

Nella sezione **Speech Commands** (Comandi vocali) fare clic sul pulsante **+ Add a New Speech Command** (+ Aggiungi un nuovo comando vocale) per aggiungere quattro nuovi comandi vocali all'elenco dei comandi vocali esistenti e quindi nei campi **Keyword** (Parola chiave) immettere quanto segue:

* Abilita indicatore
* Abilita tocco per posizionare
* Abilitare il controllo Bounds
* Disabilitare il controllo Bounds

![Aggiunta di nuovi comandi vocali](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Se il computer non dispone di un microfono, è possibile assegnare un KeyCode ai comandi vocali, che consente di attivarli quando viene premuto il tasto corrispondente.

## <a name="controlling-speech-commands"></a>Controllo dei comandi vocali

Nella finestra Project passare alla cartella Package  >  **Mixed Reality Toolkit Foundation**  >  **SDK**  >  **Features**  >  **UX** Prefabs ToolTip (Descrizione comando dei  >  **prefab**  >   dell'esperienza utente per la realtà mista) per individuare i prefab della descrizione comando:

![Apertura della cartella delle descrizioni comando](images/mr-learning-base/base-09-section3-step1-1.png)

Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse su un'area vuota e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto alla scena.

Denominare l'oggetto **SpeechInputHandler_Global**, quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configurarlo nel modo seguente:

* **Deselezionare** la casella di controllo **Is Focus Required** (È necessario lo stato attivo) in modo che l'utente non debba guardare l'oggetto con il componente SpeechInputHandler per attivare il comando vocale
* Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale

![Configurazione del componente di gestione dell'input vocale](images/mr-learning-base/base-09-section3-step1-2.png)

Nel componente SpeechInputHandler component fare clic tre volte sulla piccola icona **+** per aggiungere tre elementi di parola chiave:

![Aggiunta di elementi parola chiave al gestore di input vocale](images/mr-learning-base/base-09-section3-step1-3.png)

Espandere **Element 0** e configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Abilita indicatore** per fare riferimento al comando vocale Abilita indicatore creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **Indicator** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **GameObject** > **SetActive (bool)** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![Configurare l'elemento parola chiave 0](images/mr-learning-base/base-09-section3-step1-4.png)

Espandere **Element 1** e configurarlo come segue:

* Nel campo **Keyword (Parola** chiave) immettere **Enable Bounds Control**(Abilita controllo limiti) per fare riferimento al comando Enable Bounds Control (Abilita controllo limiti) creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* **Nell'elenco a discesa No Function** (Nessuna funzione) selezionare BoundsControl bool enabled **(Bool boundsControl** abilitato) per aggiornare il valore di questa proprietà quando  >   viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**
* Fai clic sulla piccola icona **+** per aggiungere un altro evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![Configurare l'elemento parola chiave 1](images/mr-learning-base/base-09-section3-step1-5.png)

Espandere **Element 2** e configurarlo come segue:

* Nel campo **Parola** chiave immettere **Disable Bounds Control** per fare riferimento al comando Disable Bounds Control creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* **Nell'elenco a discesa No Function** (Nessuna funzione) selezionare BoundsControl bool enabled **(Bool boundsControl** abilitato) per aggiornare il valore di questa proprietà quando  >   viene attivato l'evento
* Verificare che la casella di controllo dell'argomento sia **deselezionata**
* Fai clic sulla piccola icona **+** per aggiungere un altro evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verificare che la casella di controllo dell'argomento sia **deselezionata**

![Configurare l'elemento parola chiave 2](images/mr-learning-base/base-09-section3-step1-6.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto RoverExplorer > **RoverAssembly** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configuralo nel modo seguente:

* Verificare che la casella di controllo **Is Focus Required** (È necessario lo stato attivo) sia **selezionata**, in modo che l'utente debba guardare l'oggetto con il componente SpeechInputHandler, ovvero RoverAssembly, per attivare il comando vocale
* Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale

![Aggiungere un gestore di input vocale all'assembly Rover](images/mr-learning-base/base-09-section3-step1-7.png)

Nel componente SpeechInputHandler fare clic sulla piccola icona **+** per aggiungere un elemento parola chiave, espandere l'elemento appena creato, quindi configurarlo come segue:

* Nel campo **Keyword** (Parola chiave) immettere **Abilita tocco per posizionare** per fare riferimento al comando vocale Abilita tocco per posizionare creato nella sezione precedente
* Fare clic sulla piccola icona **+** per aggiungere un evento
* Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto stesso, ovvero lo stesso oggetto **RoverAssembly**, al campo **None (Object)** (Nessuno - Oggetto)
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **TapToPlace** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Assicurarsi che la casella di controllo dell'argomento sia **selezionata**

![Configurare il gestore di input vocale nell'assembly Rover](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato spiegato come creare comandi vocali e come controllarli a livello globale. Si è anche imparato a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.

A questo punto si conclude la serie [Esercitazioni introduttive](mr-learning-base-01.md). In queste esercitazioni è stata creata da zero un'esperienza di realtà mista completa tramite MRTK.

Nelle prossime due serie di esercitazioni, [Esercitazioni su Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) e [Esercitazioni sulle funzionalità multiutente](mr-learning-sharing-01.md), verrà spiegato prima di tutto come integrare Ancoraggi nello spazio di Azure in un progetto per ancorare l'esperienza Rover Explorer creata nel mondo reale. Quindi, verrà illustrato come aggiungere funzionalità multiutente al progetto per condividere i movimenti di utenti e oggetti in tempo reale.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, il passaggio successivo consiste nell'acquisire familiarità con i blocchi predefiniti fondamentali delle app di realtà mista.

> [!div class="nextstepaction"]
> [Interazioni di base](/windows/mixed-reality/mrtk-unity/)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](../unity-development-overview.md#1-getting-started) in qualsiasi momento.
