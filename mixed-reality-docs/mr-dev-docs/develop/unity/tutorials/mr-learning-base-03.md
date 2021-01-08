---
title: Esercitazioni di MRTK - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questa esercitazione illustra come configurare i profili di Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, consapevolezza spaziale
ms.localizationpriority: high
ms.openlocfilehash: 48bb6aa8705c9d874e6af8867d1edbe2385cb853
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613245"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configurazione dei profili di Mixed Reality Toolkit

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.

I <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">profili di MRTK</a> sono profili annidati in una struttura ad albero che costituiscono le informazioni di configurazione per la modalità di inizializzazione dei sistemi e delle funzionalità di MRTK. Il profilo di primo livello, quello di configurazione, contiene profili annidati per ognuno dei sistemi core principali. Ogni profilo annidato è progettato per la configurazione del comportamento del sistema corrispondente.

Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale. Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.

Come rilevato quando è stato distribuito il progetto in HoloLens 2 nell'[esercitazione precedente](mr-learning-base-02.md#congratulations), la mesh <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> è una raccolta di mesh che rappresentano la geometria dell'ambiente. Si tratta di una visualizzazione utile nella fase iniziale, ma che in genere è disabilitata per evitare distrazioni a livello visivo e l'impatto aggiuntivo che produrrebbe sulle prestazioni.

## <a name="objectives"></a>Obiettivi

* Imparare a personalizzare e configurare i profili di MRTK
* Nascondere il mesh di consapevolezza spaziale

## <a name="changing-the-spatial-awareness-display-option"></a>Modifica delle opzioni di visualizzazione di consapevolezza spaziale

Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:

1. Clonare il profilo di configurazione predefinito
2. Abilitare il sistema di consapevolezza spaziale
3. Clonare il profilo predefinito del sistema di consapevolezza spaziale
4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale
5. Modificare la visibilità della mesh di consapevolezza spaziale

> [!NOTE]
> per impostazione predefinita, i profili di MRTK non sono modificabili. Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati. Sono disponibili diversi livelli annidati di profili. È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonare il profilo di configurazione predefinito

> [!NOTE]
> Il profilo di configurazione è il profilo di primo livello. Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](images/mr-learning-base/base-03-section1-step1-1.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step1-2.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step1-3.png)

Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step1-4.png)

Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.

> [!TIP]
> Ricordarsi di salvare il lavoro durante l'esercitazione.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Abilitare il sistema di consapevolezza spaziale

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonare il profilo predefinito del sistema di consapevolezza spaziale

Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](images/mr-learning-base/base-03-section1-step3-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step3-2.png)

Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale

Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](images/mr-learning-base/base-03-section1-step4-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step4-2.png)

Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Modificare la visibilità della mesh di consapevolezza spaziale

In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante. Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.

hai appreso come modificare un'impostazione nel profilo di MRTK. Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti. Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite. Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Posizionamento degli oggetti nella scena](mr-learning-base-04.md)
