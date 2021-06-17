---
title: Creazione delle interfacce utente
description: Questa esercitazione illustra come usare Mixed Reality Toolkit (MRTK) per creare interfacce utente statiche e dinamiche.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, prefab, ologrammi, descrizioni comandi
ms.localizationpriority: high
ms.openlocfilehash: 0abfb4ea2fac3a2e50837c219a465c4ab002e69d
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110272"
---
# <a name="6-creating-user-interfaces"></a>6. Creazione delle interfacce utente

In questa esercitazione apprenderai come creare un'interfaccia utente semplice usando i prefab di pulsanti e menu di MRTK insieme al componente TextMeshPro di Unity. Apprenderai anche come configurare i pulsanti per attivare gli eventi e aggiungere descrizioni comandi dinamiche come elementi dell'interfaccia utente per fornire all'utente informazioni aggiuntive.

## <a name="objectives"></a>Obiettivi

* Apprendere come organizzare i pulsanti in una raccolta
* Apprendere come usare i prefab di menu di MRTK
* Apprendere come interagire con gli ologrammi usando menu e pulsanti dell'interfaccia utente
* Apprendere come aggiungere elementi di testo
* Apprendere come generare le descrizioni comandi per gli oggetti in modo dinamico

## <a name="creating-a-static-panel-of-buttons"></a>Creazione di un pannello statico di pulsanti

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **RoverExplorer** e scegli **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto come figlio di RoverExplorer, quindi assegna all'oggetto il nome **Buttons** e configura il componente **Transform** (Trasformazione) come indicato di seguito:

* **Position** (Posizione): X = -0.6, Y = 0.036, Z = -0.5
* **Rotation** (Rotazione): X = 90, Y = 0, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Unity con l'oggetto Buttons appena creato selezionato e posizionato](images/mr-learning-base/base-06-section1-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab), fai clic e trascina il prefab **PressableRoundButton** sull'oggetto **Buttons**, quindi fai clic con il pulsante destro del mouse su PressableRoundButton e scegli **Duplicate** (Duplica) per creare una copia. Ripeti queste operazioni fino a ottenere un totale di tre oggetti PressableRoundButton:

![Unity con i prefab PressableRoundButton appena aggiunti](images/mr-learning-base/base-06-section1-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Buttons**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **GridObjectCollection** e configuralo come indicato di seguito:

* **Sort Type** (Tipo ordinamento): Child Order (Ordine elementi figlio)
* **Layout**: Orizzontale
* **Cell Width** (Larghezza cella): 0.2
* **Anchor** (Ancoraggio): Middle Left (In mezzo a sinistra)

Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per aggiornare la posizione degli oggetti figlio dell'oggetto Buttons:

![Oggetto Buttons di Unity con il componente GridObjectCollection aggiunto, configurato e applicato](images/mr-learning-base/base-06-section1-step1-3.png)

Nella finestra Hierarchy (Gerarchia) assegna ai pulsanti i nomi **Hints**, **Explode** e **Reset**.

Per ogni pulsante, seleziona l'oggetto figlio **SeeItSayItLabel** > **TextMeshPro**, quindi nella finestra Inspector (Controllo) modifica il rispettivo testo componente **TextMeshPro - Text** (TextMeshPro - Testo) in modo che corrisponda ai nomi dei pulsanti:

![Unity con le etichette di testo dei pulsanti configurate](images/mr-learning-base/base-06-section1-step1-4.png)

Al termine, comprimi gli oggetti figlio dell'oggetto Buttons.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto pulsante **Hints**, quindi nella finestra Inspector (Controllo) configurare l'evento **Interactable.OnClick ()** come indicato di seguito:

* Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PlacementHintsController** > **TogglePlacementHints ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick dell'oggetto pulsante Hints configurato](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Il componente Interactable è un contenitore all-in-one che consente a tutti gli oggetti di interagire con facilità e rispondere all'input. Interactable agisce come un catch-all per tutti i tipi di input, tra cui il tocco, i raggi della mano, il riconoscimento vocale e così via e incanala tali interazioni in eventi e risposte con temi visivi. Per informazioni su come configurarlo per diversi tipi di input e personalizzarne il tema visivo, è possibile fare riferimento all'argomento [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity/).

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto pulsante **Explode**, quindi nella finestra Inspector (Controllo) configurare l'evento **Interactable.OnClick ()** come indicato di seguito:

* Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ExplodedViewController** > **ToggleExplodedView ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick dell'oggetto pulsante Explode configurato](images/mr-learning-base/base-06-section1-step1-6.png)

Premi il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante della barra spaziatrice per attivare la mano e usa il mouse per premere il pulsante **Hints** per attivare/disattivare la visibilità degli oggetti relativi ai suggerimenti per il posizionamento:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Hints selezionato](images/mr-learning-base/base-06-section1-step1-7.png)

e il pulsante **Explode** per attivare e disattivare la visualizzazione esplosa:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Explode selezionato](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Creazione di un menu dinamico che segue l'utente

Nella finestra Project (Progetto) passa alla cartella **Packages**  >  **Mixed Reality Toolkit Foundation** SDK Features UX Prefabs Menus (Menu prefab UX), fai clic e trascina il prefab NearMenu4x1 nella finestra Hierarchy (Gerarchia), imposta transform position (Posizione trasformazione) su  >    >    >    >    >   X = 0, Y = -0.4, Z = 0   e configuralo come segue:

* Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)
* Seleziona la casella di controllo accanto al componente **RadialView** in modo che sia abilitato per impostazione predefinita

![Unity con il prefab NearMenu appena aggiunto selezionato](images/mr-learning-base/base-06-section2-step1-1.png)

Nella finestra Hierarchy (Gerarchia) rinomina l'oggetto come **Menu**, quindi espandi il relativo oggetto figlio **ButtonCollection** per visualizzare i quattro pulsanti:

![Unity con l'oggetto Menu selezionato e l'oggetto ButtonCollection espanso](images/mr-learning-base/base-06-section2-step1-2.png)

Rinominare il primo pulsante in ButtonCollection in Indicator, quindi nella finestra Inspector (Controllo) configurare il componente Button Config Helper (Script) (Helper configurazione pulsanti - Script) come indicato di seguito:

* Modifica il contenuto di **Main Label Text** (Testo etichetta principale) in modo che corrisponda al nome del pulsante
* Assegnare l'oggetto Indicator simile a una scacchistica al campo None (Object) (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **GameObject** > **SetActive (bool)** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Imposta **Icon** (Icona) sull'icona di ricerca

![Unity con il componente Button Config Helper dell'oggetto pulsante Indicator configurato](images/mr-learning-base/base-06-section2-step1-3.png)

Per disabilitare l'oggetto Indicatore di avanzamento, nella finestra Hierarchy (Gerarchia) selezionare l'oggetto Indicator simile a chevron e quindi nella finestra Inspector (Controllo):

* Deseleziona la casella di controllo accanto al nome per rendere inattivo il componente per impostazione predefinita
* Usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Directional Indicator Controller (Script)** (Controller destinazione direzionale - Script)

![Unity con l'oggetto Indicator selezionato e disabilitato e il componente DirectionalIndicatorController aggiunto](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> A questo punto, all'avvio dell'app, l'indicatore di avanzamento è disabilitato per impostazione predefinita e può essere abilitato premendo il pulsante Indicatore.

> [!NOTE]
> Directional Indicator Controller (Script) (Controllo indicatore direzionale - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.

Rinomina il secondo pulsante come **TapToPlace**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - Script) come indicato di seguito:

* Modifica il contenuto di **Main Label Text** (Testo etichetta principale) in modo che corrisponda al nome del pulsante
* Assegna l'oggetto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **selezionata**
* Imposta **Icon** (Icona) sull'icona della mano con raggio

![Unity con il componente Button Config Helper dell'oggetto pulsante TapToPlace configurato](images/mr-learning-base/base-06-section2-step1-5.png)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) configura il componente **Tap To Place (Script)** (Tocco per posizionamento - Script) come indicato di seguito:

* Deseleziona la casella di controllo accanto al nome per rendere inattivo il componente per impostazione predefinita
* Nella sezione dell'evento **On Placing Stopped ()** (All'arresto del posizionamento) fare clic sull'icona **+** per aggiungere un nuovo evento:
* Assegna l'oggetto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento
* Verifica che la casella di controllo dell'argomento sia **deselezionata**

![Unity con il componente TapToPlace riconfigurato](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> A questo punto, all'avvio dell'app, la funzionalità di tocco per posizionamento è disabilitata per impostazione predefinita e può essere abilitata premendo il pulsante TaptoPlace. Inoltre, quando il tocco per posizionamento viene completato, si disabilita automaticamente.

## <a name="adding-text-to-the-scene"></a>Aggiunta di testo alla scena

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **Table** (Tabella) e scegli **3D Object** (Oggetto 3D)  > **Text - TextMeshPro** (Testo - TextMeshPro) per aggiungere un oggetto di testo come figlio dell'oggetto Table (Tabella), quindi nella finestra Inspector (Controllo) configura il componente **Rect Transform** (Trasformazione rettangolare) come indicato di seguito:

* Imposta **Pos Y** (Posizione Y) su 1
* Imposta **Width** (Larghezza) su 1
* Imposta **Height** (Altezza) su 1
* Imposta **Rotation X** (Rotazione X) su 90

![Unity con l'oggetto TextMeshPro appena creato selezionato](images/mr-learning-base/base-06-section3-step1-1.png)

Quindi configura il componente **TextMeshPro - Text** (TextMeshPro - Testo) come indicato di seguito:

* Imposta **Text** (Testo) su Rover Explorer
* Imposta **Font Style** (Stile carattere) su Bold (Grassetto)
* Imposta **Font Size** (Dimensione carattere) su 1
* Imposta Extra Settings (Impostazioni aggiuntive) > **Margins** (Margini) su 0.03

![Unity con il componente TextMeshPro configurato](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Aggiunta di descrizioni comandi

Nella finestra Project (Progetto) passa alla cartella **Packages**  >  Mixed Reality Toolkit Foundation SDK Features  >    >    >  **UX**  >  Prefabs ToolTip (Descrizione comando UX **Prefabs)**  >   per individuare i prefab di descrizione comando:

![Finestra Project di Unity con la cartella ToolTips selezionata](images/mr-learning-base/base-06-section4-step1-1.png)

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **ToolTipSpawner** e configuralo come indicato di seguito:

* Verifica che la casella di controllo **Focus Enabled** (Stato attivo abilitato) sia selezionata per richiedere all'utente di guardare la parte per visualizzare la descrizione comando
* Assegnare il prefab **della descrizione comando** Riga semplice dalla finestra Progetto al **campo Prefab**
* Imposta ToolTip Override Settings (Impostazioni di override descrizione comando) > **Settings Mode** (Modalità impostazioni) su **Override**
* Imposta ToolTip Override Settings (Impostazioni di override descrizione comando) > **Manual Pivot Local Position Y** (Posizione Y locale pivot manuale) su **1.5**

![Unity con tutti gli oggetti parte rover selezionati e il componente ToolTipSpawner aggiunto e configurato](images/mr-learning-base/base-06-section4-step1-2.png)

Nella finestra Hierarchy (Gerarchia) selezionare Camera_Part, RoverParts **> Camera_Part** e configurare il componente **ToolTipSpawner** come indicato di seguito:

* Modifica **Tool Tip Text** (Testo descrizione comando) in modo che rifletta il nome della parte, ovvero **Camera**

![Unity con l'opzione Tool Tip Text della fotocamera configurata](images/mr-learning-base/base-06-section4-step1-3.png)

**Ripeti** questo passaggio per ogni oggetto parte rover per configurare il componente **ToolTipSpawner** come indicato di seguito:

* Per **Generator_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Generator**
* Per **Lights_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Lights**
* Per **UHFAntenna_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **UHF Antenna**
* Per **Spectrometer_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Spectrometer**

Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante destro del mouse mentre muovi il mouse finché lo sguardo non incontra una delle parti. Verrà così visualizzata la descrizione comando relativa a tale parte:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con descrizione comando attivata dallo sguardo fisso](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come creare un'interfaccia utente semplice usando i prefab per pulsanti e menu forniti da MRTK insieme al componente TextMeshPro di Unity e come configurare i pulsanti per attivare eventi quando vengono premuti. Hai inoltre appreso come aggiungere elementi descrizione comando dinamici per l'interfaccia utente per fornire all'utente informazioni aggiuntive.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 7. Interazione con oggetti 3D](mr-learning-base-07.md)
