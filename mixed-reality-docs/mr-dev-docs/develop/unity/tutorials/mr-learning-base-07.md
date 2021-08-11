---
title: Interazione con oggetti 3D
description: Questa esercitazione illustra come usare Mixed Reality Toolkit (MRTK) per interagire con gli oggetti 3D nelle app di realtà mista e manipolarli.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, interazioni tra oggetti, controlli limiti
ms.localizationpriority: high
ms.openlocfilehash: d620e0150510bd7d882036786f90db8f74229e6d139a313dc6f026dc10be8047
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191435"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interazione con oggetti 3D

In questa esercitazione apprenderai come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti. Si apprenderà anche come aggiungere il controllo dei limiti intorno agli oggetti 3D per semplificare il controllo della manipolazione degli oggetti.

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare gli oggetti 3D in modo che sia possibile interagire con essi
* Informazioni su come aggiungere il controllo dei limiti agli oggetti 3D

## <a name="manipulating-3d-objects"></a>Manipolazione di oggetti 3D

In questa sezione aggiungerai la possibilità di manipolare tutte le parti rover organizzate sul tavolo durante l'esercitazione [Posizionamento degli oggetti nella scena](mr-learning-base-04.md).

Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente Object Manipulator (Script) (Manipolatore oggetti - script) a tutti gli oggetti parte
2. Aggiungere il componente NearInteractionGrabbable a tutti gli oggetti parte
3. Configurare il componente Object Manipulator (Script) (Manipolatore oggetti - script)

> [!NOTE]
> Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
>
> Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:
>
> * Componente **Collider** (Collisore), ad esempio un collisore cuboide
> * Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
> * Componente **NearInteractionGrabbable**

Configurerai inoltre Rover Explorer (Esplora rover) in modo che sia possibile posizionare le parti rover sul rover per renderlo un assembly di rover completo.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio e l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:

* Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
* Componente **NearInteractionGrabbable**
* Componente **Part Assembly Controller (Script)** (Controllo assembly parti - script)

![Unity con RoverAssembly e tutti gli oggetti parte rover selezionati e i componenti aggiunti](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Per selezionare più oggetti non adiacenti, tieni premuto CTRL mentre usi il mouse per selezionare un oggetto.

> [!NOTE]
> Quando si aggiunge un manipolatore di oggetti (script), in questo caso, gestione vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.

> [!NOTE]
> Ai fini di questa esercitazione, i collisori sono già stati aggiunti alle parti rover. Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.

> [!NOTE]
> Part Assembly Controller (Script) (Controllo assembly parti - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.

Con tutti gli oggetti parte rover e l'oggetto RoverAssembly ancora selezionati, nella finestra Inspector (Controllo) configura il componente **Object Manipulator (Script)** (Manipolatore oggetti - script) come indicato di seguito:

* Dall'elenco a discesa **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) deseleziona Scale (Scala) in modo che siano abilitate solo le opzioni **Move** (Sposta) e **Rotate** (Ruota)

![Unity con Two Handed Manipulation Type configurato](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> A questo punto hai abilitato la manipolazione per tutti gli oggetti parte rover e per l'oggetto RoverAssembly.

Nella finestra Project pacchetti passare a **Packages**  >  **Mixed Reality Toolkit Standard Assets** Audio (Asset standard  >  **audio)** per individuare le clip audio:

![Finestra Project di Unity con la cartella Audio selezionata](images/mr-learning-base/base-07-section1-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona di nuovo gli **oggetti parte rover** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Audio Sources** (Origini audio) e configuralo come indicato di seguito:

* Assegna il clip audio **MRTK_Scale_Start** al campo **AudioClip**
* Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo)
* Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1

![Unity con tutte le parti rover selezionate e il componente Audio Source aggiunto e configurato](images/mr-learning-base/base-07-section1-step1-4.png)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** RoverAssembly per visualizzare tutti gli oggetti suggerimento di posizionamento, quindi seleziona la parte rover Camera_part RoverParts > **Camera_Part** e configura il componente **Part Assembly Controller (Script) come** indicato di seguito:

* Assegna l'oggetto **Camera_PlacementHint** al campo **Location To Place** (Punto di posizionamento)

![Unity con il componente PartAssemblyController di Camera_Part configurato](images/mr-learning-base/base-07-section1-step1-5.png)

**Ripeti** questo passaggio per ognuno degli oggetti parte rover rimanenti e per l'oggetto RoverAssembly per configurare il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:

* Per **Generator_Part**, assegna l'oggetto **Generator_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **Lights_Part**, assegna l'oggetto **Lights_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **UHFAntenna_Part**, assegna l'oggetto **UHFAntenna_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **Spectrometer_Part**, assegna l'oggetto **Spectrometer_PlacementHint** al campo **Location To Place** (Punto di posizionamento)
* Per **RoverAssembly**, assegna l'oggetto stesso., ovvero l'oggetto **RoverAssembly** stesso, al campo **Location To Place** (Punto di posizionamento)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto pulsante RoverExplorer > Buttons (Pulsanti) > **Reset** (Reimposta) e quindi nella finestra Inspector (Controllo) configura l'evento **OnClick ()** con supporto per interazioni come indicato di seguito:

* Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PartAssemblyController** > **ResetPlacement ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick dell'oggetto pulsante Reset configurato](images/mr-learning-base/base-07-section1-step1-6.png)

Se attivi ora la modalità di gioco, puoi usare l'interazione da vicino o da lontano per posizionare le parti rover sul rover. Quando è vicina al suggerimento di posizionamento corrispondente, la parte si blocca in posizione e diventa parte del rover. Per reimpostare i posizionamenti, puoi scegliere il pulsante Reset (Reimposta):

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Reset selezionato](images/mr-learning-base/base-07-section1-step1-7.png)

Per altre informazioni sul componente Object Manipulator (Manipolatore oggetti) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity/).

## <a name="adding-bounds-control"></a>Aggiunta del controllo Bounds

Controllo limiti rende più semplice e intuitivo modificare gli oggetti con una mano per l'interazione da vicino e da lontano fornendo handle che possono essere usati per il ridimensionamento e la rotazione.

In questo esempio si aggiungerà un boundsControl all'oggetto RoverExplorer in modo che l'intera esperienza possa essere facilmente spostata, ruotata e ridimensionata. Inoltre, si configurerà il menu in modo da poter attivare e disattivare il controllo Limiti.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverExplorer**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti:

* **Componente BoundsControl**
* Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)

Deselezionare **quindi la** casella di controllo accanto a tutti i componenti per renderli **disabilitati per** impostazione predefinita:

![Unity con l'oggetto RoverExplorer selezionato e i componenti aggiunti e disabilitati](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> La visualizzazione Controllo limiti viene creata in fase di esecuzione e, pertanto, non è visibile prima di entrare nella modalità di gioco.

> [!NOTE]
> Il manipolatore di oggetti (script) aggiunge automaticamente Gestione vincoli (script)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto Menu > **ButtonCollection** per visualizzare i quattro pulsanti e rinomina il terzo pulsante **BoundsControl_Enable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script) (Helper** configurazione pulsanti - Script) come indicato di seguito:

* Imposta **Main Label Text** (Testo etichetta principale) su **Enable** (Abilita)
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* **Nell'elenco a discesa No Function** (Nessuna funzione) selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Fai clic sull'icona **+** piccola per aggiungere un altro evento
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Lasciare **l'icona** dell'icona "cubo con controllo limiti"

![Unity con l BoundsControl_Enable o object button selezionato e il componente Button Config Helper configurato](images/mr-learning-base/base-07-section2-step1-2.png)

Rinominare l'ultimo pulsante BoundsControl_Disable , quindi nella finestra Inspector (Controllo) configurare il componente **Button Config Helper (Script) (Helper configurazione** pulsanti - Script) come indicato di seguito:

* Imposta **Main Label Text** (Testo etichetta principale) su **Disable** (Disabilita)
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* **Nell'elenco a discesa No Function** (Nessuna funzione) selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verificare che la casella di controllo dell'argomento sia **deselezionata**
* Fai clic sull'icona **+** piccola per aggiungere un altro evento
* Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **deselezionata**
* Modificare **l'icona** con l'icona del controllo cubo con limiti

![Unity con l BoundsControl_Disable o object button selezionato e il componente Button Config Helper configurato](images/mr-learning-base/base-07-section2-step1-3.png)

Se ora si passa alla modalità di gioco e si abilita il controllo limiti facendo clic sul pulsante Abilita, è possibile usare l'interazione da vicino o da lontano per spostare, ruotare e ridimensionare il controllo limiti e usare il pulsante Disabilita per disabilitare di nuovo il controllo limiti:

![Doppia visualizzazione della modalità di riproduzione unity con il controllo Bounds modificato](images/mr-learning-base/base-07-section2-step1-4.png)

Per altre informazioni sul componente Bounds Control e sulle proprietà associate, è possibile visitare la guida [Bounds Control](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) (Controllo limiti) nel portale [della documentazione di MRTK.](/windows/mixed-reality/mrtk-unity/)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti. Si è anche appreso come aggiungere il controllo Bounds intorno agli oggetti 3D per semplificare il controllo della manipolazione degli oggetti.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 8. Uso del tracciamento oculare](mr-learning-base-08.md)