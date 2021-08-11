---
title: Esercitazioni di MRTK - 4. Posizionamento degli oggetti nella scena
description: Questa esercitazione illustra come posizionare gli oggetti nella scena e come usare Mixed Reality Toolkit (MRTK) per organizzare gli oggetti in una griglia.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, risolutori, raccolta di oggetti griglia
ms.localizationpriority: high
ms.openlocfilehash: b21f2833067c3496febcf5bdd1cfffe491597e9083845b18e9c220c75d3e7cee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228003"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Posizionamento degli oggetti nella scena

## <a name="overview"></a>Panoramica

In questa esercitazione verranno posizionati gli oggetti forniti dagli asset dell'esercitazione nella scena.

## <a name="objectives"></a>Obiettivi

* Imparare a posizionare gli oggetti nella scena
* Imparare a usare la funzionalità Grid Object Collection (Raccolta di oggetti griglia) di MRTK

## <a name="importing-the-textmeshpro-essential-resources"></a>Importazione delle risorse essenziali TextMeshPro
Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK. Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scaricare il pacchetto personalizzato Unity seguente. Questo pacchetto include asset 3D, ad esempio Mars Rover, che verranno utilizzati in questa esercitazione.

* [MRTK. HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Per importare un pacchetto personalizzato unity, nel menu Unity selezionare **Asset Importa** pacchetto personalizzato  >    >  **pacchetto...** per aprire Importa pacchetto. Finestra:

![Importazione di un pacchetto personalizzato](images/mr-learning-base/base-02-section7-step1-1.png)

Nel pacchetto Di importazione... , selezionare **MRTK. HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** scaricato e fare clic sul pulsante Apri:

![Selezione di un pacchetto di asset](images/mr-learning-base/base-02-section7-step1-2.png)

Nella finestra Importa pacchetto Unity fare clic sul pulsante Tutti per assicurarsi che siano selezionati tutti gli asset, quindi fare clic sul pulsante Importa per importare gli asset:

![Selezione di tutti gli asset da importare](images/mr-learning-base/base-02-section7-step1-3.png)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestra del progetto Unity dopo l'importazione di asset](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a>Creazione dell'oggetto padre

Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse su un'area vuota e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto alla scena:

![Menu popup contestuale Create Empty di Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Per visualizzare le finestre della scena e di gioco affiancate, come mostrato nell'immagine precedente, trascinare la finestra di gioco a destra della finestra della scena. Per altre informazioni sulla personalizzazione dell'area di lavoro, consultare l'argomento relativo alla <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalizzazione dell'area di lavoro</a> nella documentazione di Unity.

Fare clic con il pulsante destro del mouse sull'oggetto appena creato, scegliere **Rename** (Rinomina) e modificare il nome in **RoverExplorer**:

![Menu popup contestuale Rename di Unity](images/mr-learning-base/base-04-section1-step1-2.png)

Con l'oggetto RoverExplorer ancora selezionato, nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:

* **Position** (Posizione): X = 0, Y = -0.6, Z = 2
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Unity con l'oggetto RoverExplorer selezionato e posizionato](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> La fotocamera rappresenta la testa dell'utente ed è posizionata in corrispondenza dell'origine, X = 0, Y = 0, Z = 0. In generale, 1 unità in Unity corrisponde a circa 1 metro nel mondo fisico. Vi sono tuttavia eccezioni, ad esempio quando gli oggetti sono figli di oggetti ridimensionati. Nello scenario precedente, RoverExplorer è posizionato 2 metri in avanti e 0,6 metri in basso rispetto alla testa dell'utente.

## <a name="adding-the-tutorial-prefabs"></a>Aggiunta dei prefab per l'esercitazione

Nella finestra Project (Progetto) passare alla cartella **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab):

![Finestra Project di Unity con la cartella Prefabs selezionata](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> è un GameObject preconfigurato che viene archiviato come asset Unity e può essere riutilizzato nel progetto.

Dalla finestra Project (Progetto) fare clic e trascinare il prefab **Table** sull'oggetto **RoverExplorer** per renderlo figlio dell'oggetto RoverExplorer, quindi nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:

* **Position** (Posizione): X = 0, Y = -0.005, Z = 0
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 1.2, Y = 0.01, Z = 1.2

![Unity con il prefab Table appena aggiunto selezionato e posizionato](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> Per visualizzare la scena come illustrato nell'immagine seguente, usare <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo della scena), nell'angolo in alto a destra della finestra della scena, per regolare l'angolo di visualizzazione in modo che si trovi sulll'asse Z in avanti, fare doppio clic sull'oggetto MixedRealityPlayspace per posizionare lo stato attivo sulla fotocamera ed eseguire lo zoom avanti necessario.

Dalla finestra Project (Progetto) fare clic e trascinare il prefab **RoverAssembly** sull'oggetto **RoverExplorer** per renderlo figlio dell'oggetto RoverExplorer, quindi nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:

* **Position** (Posizione): X = -0.1, Y = 0, Z = 0
* **Rotation** (Rotazione): X = 0, Y = -135, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Unity con il prefab RoverAssembly appena aggiunto selezionato e posizionato](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Organizzazione di oggetti in una raccolta

Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse sull'oggetto **RoverExplorer** e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto come figlio di RoverExplorer, quindi assegnare all'oggetto il nome **RoverParts** e configurare il componente **Transform** (Trasformazione) come indicato di seguito:

* **Position** (Posizione): X = 0, Y = 0.06, Z = 0
* **Rotation** (Rotazione): X = 0, Y = 90, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Unity con l'oggetto RoverParts appena creato selezionato e posizionato](images/mr-learning-base/base-04-section3-step1-1.png)

Nella finestra Hierarchy (Gerarchia) selezionare tutti gli oggetti figlio RoverExplorer > RoverAssembly > RoverModel > **Parts**, fare clic con il pulsante destro del mouse su di essi e scegliere **Duplicate** (Duplica) per creare una copia di ognuna delle parti:

![Unity con tutte le voci di Parts selezionate e il menu popup contestuale Duplicate](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Per selezionare più oggetti adiacenti, selezionare il primo e l'ultimo oggetto con il mouse tenendo premuto MAIUSC.

Con gli oggetti figlio Parts appena duplicati ancora selezionati, fare clic e trascinarli sull'oggetto **RoverParts** per renderli oggetti figlio dell'oggetto RoverParts:

![Unity con le parti appena duplicate come elementi figlio dell'oggetto RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

Per rendere più agevole l'uso della scena, nella finestra Hierarchy (Gerarchia) fare clic sull'icona a forma di **occhio** sulla sinistra dell'oggetto per disattivare la **visibilità nella scena** per l'oggetto **RoverAssembly**. In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco:

![Unity con la visibilità della scena di RoverAssembly disabilitata](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> Per altre informazioni sui controlli per la visibilità nella scena e su come usarli per ottimizzare la vista e il flusso di lavoro della scena, consultare l'argomento sulla <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità nella scena</a> nella documentazione di Unity.

Nella finestra Hierarchy (Gerarchia), ripulire i nomi degli oggetti figlio RoverParts sostituendo la parte finale **(1)** con **_Part**:

![Unity con il nome delle parti duplicate ripuliti](images/mr-learning-base/base-04-section3-step1-5.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **RoverParts**, quindi nella finestra Inspector (Controllo) fare clic sul pulsante **Add Component** (Aggiungi componente) e cercare e selezionare **GridObjectCollection** per aggiungere il componente GridObjectCollection all'oggetto RoverParts:

![Oggetto RoverParts di Unity con l'aggiunta del componente Grid Object Collection in corso](images/mr-learning-base/base-04-section3-step1-6.png)

Configurare i valori del componente **GridObjectCollection** come segue:

* **Sort Type** (Tipo di ordinamento): Alfabetico
* **Layout**: Orizzontale
* **Cell Width** (Larghezza cella): 0,25
* **Distance from parent** (Distanza dal padre): 0,38

![Unity con il componente GridObjectCollection configurato](images/mr-learning-base/base-04-section3-step1-7.png)

Fare quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per aggiornare la posizione degli oggetti figlio RoverParts:

![Unity con il componente GridObjectCollection applicato](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato illustrato come posizionare gli oggetti nella scena in relazione all'utente e come usare la funzionalità Grid Object Collection (Raccolta di oggetti griglia) di MRTK per organizzare gli oggetti in una raccolta.

> [!div class="nextstepaction"]
>[Esercitazione successiva: 5. Creazione di contenuto dinamico tramite risolutori](mr-learning-base-05.md)
