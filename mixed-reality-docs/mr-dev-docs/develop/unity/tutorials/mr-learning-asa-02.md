---
title: Introduzione ad Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come usare Ancoraggi nello spazio di Azure per ancorare oggetti in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656640"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introduzione ad Ancoraggi nello spazio di Azure

In questa esercitazione esaminerai i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare in un singolo dispositivo gli ancoraggi nello spazio di Azure.

## <a name="objectives"></a>Obiettivi

* Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2
* Apprendi come creare ancoraggi nello spazio e recuperarli da Azure

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

Seguire prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*
2. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#switching-the-build-platform)
3. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Creazione e configurazione della scena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnazione di un nome appropriato, ad esempio *AzureSpatialAnchors*

Segui quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni riportate in Modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarti che il profilo di configurazione di MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale in **Occlusion**.

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Installazione di pacchetti Unity predefiniti e importazione degli asset dell'esercitazione

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.

Nella finestra Project (Progetto) passa ad **Assets (Asset)**  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fai clic e trascina i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

* Prefab **ButtonParent**
* Prefab **DebugWindow**
* Prefab **Instructions**
* Prefab **ParentAnchor**

![Unity con i prefab appena aggiunti selezionati](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a>, come mostrato nell'immagine precedente.

Selezionare **l'oggetto MixedRealityToolkit** nella finestra Hierarchy (Gerarchia) e usare il pulsante **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere i componenti seguenti:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![Oggetto MixedRealityToolkit di Unity con i componenti AR Anchor Manager e DisableDiagnosticsSystem aggiunti ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> Esiste un problema noto con Asa v2.9.0 e v2.10.0-preview.1 che richiede che nella scena siano posizionati altri due oggetti. Usa il **pulsante Aggiungi componente** nella finestra di controllo per aggiungere ar Camera Manager (Script) e una sessione AR (Script) all'oggetto **MixedRealityToolkit.** Assicurati di disabilitare la fotocamera creata automaticamente durante l'aggiunta di AR Camera Manager (Script) deselezionando la casella di controllo accanto all'oggetto Camera nella finestra di controllo. Questo problema verrà risolto nella versione completa di Asa v2.10.0.
>

> [!NOTE]
> Quando aggiungi il componente AR Anchor Manager (Script), il componente AR Session Origin (Script) (Origine sessione AR - Script) viene aggiunto automaticamente perché è richiesto dal componente AR Anchor Manager (Script) (Gestione ancoraggi AR - Script).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e degli ancoraggi nello spazio di Azure in un'app.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**. Nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick del pulsante StartAzureSession configurato](images/mr-learning-asa/asa-02-section5-step1-1.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **StopAzureSession** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StopAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick del pulsante StopAzureSession configurato](images/mr-learning-asa/asa-02-section5-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **CreateAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assegna l'oggetto **ParentAnchor** al campo **None (Game Object)** (Nessuno - Oggetto gioco) vuoto per impostarlo come argomento della funzione CreateAzureAnchor ()

![Unity con l'evento OnClick del pulsante CreateAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **RemoveLocalAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **RemoveLocalAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento
* Assegna l'oggetto **ParentAnchor** al campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco) per impostarlo come argomento della funzione RemoveLocalAnchor ()

![Unity con l'evento OnClick del pulsante RemoveLocalAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-4.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **FindAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **FindAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick del pulsante FindAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-5.png)

Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **DeleteAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:

* Assegnare **l'oggetto ParentAnchor** come listener per l'evento On Click () trascinandolo dalla finestra Hierarchy (Gerarchia) nel campo **None (Object) (Nessuno - Oggetto)**
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **DeleteAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento

![Unity con l'evento OnClick del pulsante DeleteAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Connessione della scena alla risorsa di Azure

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - script). Configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-asa-01.md#prerequisites) per questa serie di esercitazioni:

* Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure
* Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure
* Nel campo **Spatial Anchors Account Domain (Dominio account ancoraggi** nello stato spaziale) incollare il dominio **dell'account** di Ancoraggi nello stato di Azure

![Unity con Spatial Anchor Manager configurato](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Test dei comportamenti di base di Ancoraggi nello spazio di Azure

Poiché non è possibile eseguire ancoraggi nello spazio di Azure in Unity, per testare la funzionalità di questo servizio devi compilare il progetto e distribuire l'app nel tuo dispositivo.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Quando l'app è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su ancoraggi nello spazio di Azure):

1. Sposta il cubo in un'altra posizione
2. Avvia la sessione di Azure
3. Crea l'ancoraggio di Azure (viene creato un ancoraggio nella posizione del cubo)
4. Arresta la sessione di Azure
5. Rimuovi l'ancoraggio locale (consente all'utente di spostare il cubo)
6. Sposta il cubo altrove
7. Avvia la sessione di Azure
8. Trova l'ancoraggio di Azure (il cubo viene collocato nella posizione del passaggio 3)
9. Elimina l'ancoraggio di Azure
10. Arresta la sessione di Azure

![Unity con l'oggetto Instructions selezionato](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Poiché per gli ancoraggi nello spazio di Azure viene usato Internet per salvare e caricare i dati di ancoraggio, assicurati che il dispositivo sia connesso a Internet.

## <a name="anchoring-an-experience"></a>Ancoraggio di un'esperienza

Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato. In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) configura i componenti **Transform** (Trasformazione) come segue:

* Imposta **Scale X** (Scala X) su 1,1
* Imposta **Scale Z** (Scala Z) su 1,1

![Unity con l'oggetto ParentAnchor selezionato, posizionato e ridimensionato](images/mr-learning-asa/asa-02-section8-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **Rover** e quindi fai clic e trascina il prefab **RoverExplorer_Complete** sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:

![Unity con il prefab RoverExplorer_Complete appena aggiunto selezionato](images/mr-learning-asa/asa-02-section8-step1-2.png)

Con l'oggetto RoverModule_Complete appena aggiunto ancora selezionato nella finestra Hierarchy (Gerarchia), trascinalo sull'oggetto **ParentAnchor** per configurarlo come figlio dell'oggetto ParentAnchor:

![Unity con l'oggetto RoverExplorer_Complete impostato come elemento figlio di ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

Se ora ricompili il progetto e distribuisci l'app nel dispositivo, puoi riposizionare l'intera esperienza Rover Explorer (Esplora rover) spostando il cubo ridimensionato.

> [!TIP]
> Un'ampia gamma di flussi di esperienza utente per il riposizionamento delle esperienze, tra cui l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per attivare o disattivare un controllo dei limiti che circonda l'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure. In questa esercitazione hai usato diversi pulsanti per esaminare i vari passaggi da seguire per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.

Nell'esercitazione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'app, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure](mr-learning-asa-03.md)
