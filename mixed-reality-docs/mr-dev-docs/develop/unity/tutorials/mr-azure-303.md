---
title: HoloLens (prima generazione) e Azure 303 - LuiS (Natural Language Understanding)
description: Completare questo corso per informazioni su come implementare Azure Language Understanding Intelligence Service (LUIS) all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, language understanding intelligence service, luis, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218084"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (prima generazione) e Azure 303: Comprensione del linguaggio naturale (LUIS)

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

In questo corso si apprenderà come integrare Language Understanding in un'applicazione di realtà mista usando Servizi cognitivi di Azure, con l'API Language Understanding.

![Risultato del lab](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* è un servizio Microsoft Azure, che offre alle applicazioni la possibilità di ottenere un significato dall'input dell'utente, ad esempio tramite l'estrazione di ciò che una persona potrebbe volere, con le proprie parole. Questo risultato viene ottenuto tramite Machine Learning, che comprende e apprende le informazioni di input e quindi può rispondere con informazioni dettagliate, rilevanti. Per altre informazioni, visitare la pagina [di Azure Language Understanding (LUIS).](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)

Dopo aver completato questo corso, si avrà un'applicazione visore vr immersiva di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Acquisire la voce di input dell'utente usando il microfono collegato al visore immersivo. 
2.  Inviare la dettatura acquisita a *Azure Language Understanding Intelligent Service* (*LUIS*). 
3.  Chiedere a LUIS di estrarre il significato dalle informazioni di invio, che verranno analizzate, e tentare di determinare la finalità della richiesta dell'utente.

Lo sviluppo includerà la creazione di un'app in cui l'utente potrà usare la voce e/o lo sguardo per modificare le dimensioni e il colore degli oggetti nella scena. L'uso dei controller di movimento non verrà trattato.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è progettato per illustrare come integrare un servizio di Azure con il servizio Unity Project. È compito dell'utente usare le conoscenze acquisite da questo corso per migliorare l'applicazione di realtà mista.

Prepararsi a eseguire il training di LUIS più volte, come descritto [nel capitolo 12](#chapter-12--improving-your-luis-service). Si otterrà risultati migliori più volte è stato esercito il training di LUIS.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR e Azure 303: Comprensione del linguaggio naturale (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in Windows Mixed Reality visore vr immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note su eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare un'eco durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). È possibile usare il software più recente, come elencato nell'articolo installare gli strumenti, anche se non è consigliabile presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md)
- [L'SDK Windows 10 più recente](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Visore [Windows Mixed Reality vr o](../../../discover/immersive-headset-hardware-details.md) visore [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Un set di cuffia con un microfono predefinito (se l'headset non ha un microfono e altoparlanti predefiniti)
- Accesso a Internet per l'installazione di Azure e il recupero di LUIS

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione). 
2.  Per consentire al computer di abilitare la dettatura, passare **Windows Impostazioni > Privacy > Speech, Inking & Typing** e premere il pulsante Turn On speech services and typing **suggestions**(Attivare i servizi voce e i suggerimenti di digitazione).
3.  Il codice di questa esercitazione consente di registrare dal dispositivo **microfono** predefinito impostato nel computer. Assicurarsi che il dispositivo microfono predefinito sia impostato come quello che si vuole usare per acquisire la voce.
4.  Se il visore ha un microfono incorporato, assicurarsi che l'opzione *"Quando* indossi il visore, passa al microfono visore" sia *attivata* nelle impostazioni Portale realtà mista visore.

    ![Configurazione di visori immersivi](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capitolo 1: Configurare il portale di Azure

Per usare il *Language Understanding* in Azure, è necessario configurare un'istanza del servizio per essere resa disponibile per l'applicazione.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra *e* cercare Language Understanding e fare clic su **Invio.** 

    ![Creare una risorsa LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita con **Crea una** risorsa nei portali più nuovi.
 
3.  La nuova pagina a destra fornirà una descrizione del Language Understanding servizio. Nella parte inferiore sinistra di questa pagina selezionare il **pulsante Crea** per creare un'istanza del servizio.

    ![Creazione del servizio LUIS - Nota legale](images/AzureLabs-Lab3-02.png)
 
4.  Dopo aver fatto clic su Crea:

    1. Inserire il nome **desiderato per** questa istanza del servizio.
    2. Selezionare una **Sottoscrizione**.
    3. Selezionare il **piano tariffario** appropriato per l'utente, se questa è la prima volta che si crea un servizio *LUIS,* dovrebbe essere disponibile un livello gratuito (denominato F0). L'allocazione gratuita deve essere più che sufficiente per questo corso.
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto,ad esempio questi corsi, in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo gruppo di risorse](/azure/azure-resource-manager/resource-group-portal).

    5. Determinare **la posizione** per il gruppo di risorse (se si crea un nuovo gruppo di risorse). Il percorso si trova idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.
    6. È anche necessario verificare di aver compreso i termini e le condizioni applicati al servizio.
    7. Selezionare **Crea**.

        ![Creare il servizio LUIS - input utente](images/AzureLabs-Lab3-03.png)
 
5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.
6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica. 
 
    ![Nuova immagine di notifica di Azure](images/AzureLabs-Lab3-04.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Notifica di creazione della risorsa completata](images/AzureLabs-Lab3-05.png)
 
8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà eseguita la nuova istanza del servizio LUIS. 
 
    ![Accesso alle chiavi LUIS](images/AzureLabs-Lab3-06.png)

9.  In questa esercitazione l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita tramite la chiave di sottoscrizione del servizio.
10. Nella  pagina Avvio rapido del servizio *API LUIS* passare al primo *passaggio,* Afferrare le chiavi e fare clic su Chiavi **(** è anche possibile fare clic sul collegamento ipertestuale blu Chiavi, che si trova nel menu di spostamento dei servizi, denotato dall'icona della chiave). Verranno così rivelate le chiavi *del servizio*.
11. Prendere una copia di una delle chiavi visualizzate, in quanto sarà necessaria più avanti nel progetto. 
12. Nella pagina *Servizio* fare clic su *Language Understanding portale* per essere reindirizzati alla pagina Web che verrà utilizzata per creare il nuovo servizio, all'interno dell'app LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capitolo 2 : Portale Language Understanding dati

In questa sezione si apprenderà come creare un'app LUIS nel portale LUIS. 

> [!IMPORTANT]
> Tenere presente che la configurazione delle  *entità,*  delle finalità e delle espressioni all'interno di questo capitolo è solo il primo passaggio per la creazione del servizio LUIS: sarà anche necessario eseguire nuovamente il training del servizio, più volte, in modo da renderlo più accurato. Il nuovo training del servizio è trattato [nell'ultimo capitolo](#chapter-12--improving-your-luis-service) di questo corso, quindi assicurarsi di completarlo.

1.  Quando si raggiunge *il Language Understanding,* potrebbe essere necessario eseguire l'accesso, se non è già stato fatto, con le stesse credenziali del portale di Azure. 

    ![Pagina di accesso a LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se è la prima volta che si usa LUIS, è necessario scorrere verso il basso fino alla fine della pagina iniziale per trovare e fare clic sul pulsante **Crea app LUIS.**

    ![Pagina Crea app LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Dopo aver eseguito **l'accesso, fare clic App personali** (se non si è attualmente in quella sezione). È quindi possibile fare clic su **Crea nuova app**.

    ![LUIS - Immagine delle app personali](images/AzureLabs-Lab3-09.png)
 
4.  Assegnare all'app *un nome*.
5.  Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le impostazioni *cultura* nella lingua appropriata.
6.  Qui è anche possibile aggiungere una *descrizione* della nuova app LUIS.

    ![LUIS: creare una nuova app](images/AzureLabs-Lab3-10.png)

7.  Dopo aver fatto **clic su Fine,** si immetterà la *pagina Build (Compila)* della nuova *applicazione LUIS.*
8.  Esistono alcuni concetti importanti da comprendere qui:

    -   *Intent*, rappresenta il metodo che verrà chiamato dopo una query dell'utente. Una *FINALITÀ* può avere una o più *entità*.
    -   *L'entità* è un componente della query che descrive le informazioni rilevanti per la *FINALITÀ*.
    -   *Le espressioni*, sono esempi di query fornite dallo sviluppatore, che LUIS userà per il training.

Se questi concetti non sono perfettamente chiari, non è necessario preoccuparsi, perché questo corso li chiarirà ulteriormente in questo capitolo.

Si inizierà creando le *entità necessarie* per compilare questo corso.

9.  Sul lato sinistro della pagina fare clic su *Entità*, quindi fare clic **su Crea nuova entità**.

    ![Creare una nuova entità](images/AzureLabs-Lab3-11.png)

10. Chiamare il nuovo colore *entità*, impostarne il tipo su *Semplice*, quindi premere **Fine**.

    ![Creare un'entità semplice - colore](images/AzureLabs-Lab3-12.png)
 
11. Ripetere questo processo per creare tre (3) entità più semplici denominate:

    -   *upsize*
    -   *Ridimensionare*
    -   *target*

Il risultato dovrebbe essere simile all'immagine seguente:

![Risultato della creazione dell'entità](images/AzureLabs-Lab3-13.png)
 
A questo punto è possibile iniziare a creare *finalità*. 

> [!WARNING]
> Non eliminare la **finalità Nessuno.**

12. Sul lato sinistro della pagina fare clic su **Intents (Finalità)** e quindi fare clic **su Create new intent (Crea nuova finalità).**

    ![Creare nuove finalità](images/AzureLabs-Lab3-14.png)

13. Chiamare la nuova *finalità* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Questo *nome* della finalità viene usato all'interno del codice più avanti in questo corso, quindi per ottenere risultati ottimali, usare questo nome esattamente come specificato.

Dopo aver confermato il nome, si verrà indirizzati alla pagina Finalità.

![LUIS - pagina delle finalità](images/AzureLabs-Lab3-15.png)

Si noterà che è presente una casella di testo che richiede di digitare 5 o più *espressioni diverse.*

> [!NOTE]
> LUIS converte tutte le espressioni in lettere minuscole.

14. Inserire *l'espressione seguente* nella casella di testo superiore (attualmente con il testo *Digitare circa 5 esempi...* ) e premere **INVIO:**

```
The color of the cylinder must be red
```

Si noterà che la nuova *espressione* verrà visualizzata in un elenco sottostante.

Seguendo lo stesso processo, inserire le sei (6) espressioni seguenti:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Per ogni espressione creata, è necessario identificare le parole che DEVONO essere usate da LUIS come entità. In questo esempio è necessario etichettare  tutti i colori come entità di colore e tutti i possibili riferimenti a una destinazione come entità *di* destinazione.

15. A tale scopo, provare a fare clic sul *cilindro* di parole nella prima espressione e selezionare *target*.

    ![Identificare le destinazioni dell'espressione](images/AzureLabs-Lab3-16.png)
 
16. Fare clic sulla parola rossa *nella* prima espressione e selezionare *il colore*.

    ![Identificare le entità di espressione](images/AzureLabs-Lab3-17.png)
 
17. Etichettare anche la riga successiva, dove *cube* deve essere una *destinazione* e *black* deve essere un *colore*. Si noti anche l'uso delle parole *'this',* *'it'* e *'this object'*, che vengono fornito, in modo da avere anche tipi di destinazione non specifici disponibili. 

18. Ripetere il processo precedente fino a quando tutte le espressioni non hanno le entità etichettate. Per assistenza, vedere l'immagine seguente.

    > [!TIP]
    > Quando si selezionano le parole da etichettare come entità:
    > - Per le singole parole è sufficiente fare clic su di esse.
    > - Per un set di due o più parole, fare clic all'inizio e quindi alla fine del set.

    > [!NOTE]
    > È possibile usare il *pulsante di attivazione/disattivazione* della visualizzazione token per passare da **Entities/Tokens View**!

19. I risultati dovrebbero essere visualizzati nelle immagini seguenti, che mostrano **la visualizzazione Entità/Token:**

    ![Token & viste entità](images/AzureLabs-Lab3-18.png)
  
20. A questo punto, **premere** il pulsante Train (Train) in alto a destra nella pagina e attendere che il piccolo indicatore arrotondato su di esso sia verde. Ciò indica che è stato eseguito correttamente il training di LUIS per riconoscere questa finalità.

    ![Training di LUIS](images/AzureLabs-Lab3-19.png)
 
21. Come esercizio, creare una nuova finalità denominata **ChangeObjectSize** usando le entità di *destinazione,* *upsize* e *downsize*.
22. Seguendo lo stesso processo della finalità precedente, inserire le otto (8) espressioni seguenti per *la modifica delle* dimensioni:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. Il risultato dovrebbe essere simile a quello nell'immagine seguente:

    ![Configurare i token/entità ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Dopo aver creato ed addestrato entrambe le **finalità, ChangeObjectColor** e **ChangeObjectSize,** fare clic sul **pulsante PUBLISH** nella parte superiore della pagina.

    ![Pubblicare il servizio LUIS](images/AzureLabs-Lab3-21.png)

25. Nella pagina *Pubblica* finalizzare e pubblicare l'app LUIS in modo che sia accessibile dal codice.

    1. Impostare l'elenco a *discesa Pubblica in* come **Produzione**.
    2. Impostare fuso *orario* sul fuso orario.
    3. Selezionare la casella **Includi tutti i punteggi delle finalità stimate**.
    4. Fare clic **su Pubblica nello slot di produzione**.

        ![Impostazioni di pubblicazione](images/AzureLabs-Lab3-22.png)

26. Nella sezione *Risorse e chiavi*:

    1.  Selezionare l'area impostata per l'istanza del servizio nel portale di Azure.
    2.  Si noterà un **Starter_Key** seguente, ignorarlo.
    3.  Fare clic **su Aggiungi chiave** e inserire la *chiave* ottenuta nel portale di Azure quando è stata creata l'istanza del servizio. Se Azure e il portale LUIS sono connessi allo stesso utente, verranno forniti menu a discesa  per Nome *tenant,* Nome sottoscrizione e La chiave che si vuole usare ( avrà lo stesso nome specificato in precedenza nel portale di Azure.

    > [!IMPORTANT] 
    > Sotto *Endpoint*, prendere una copia dell'endpoint corrispondente alla chiave inserita, che verrà presto utilizzata nel codice.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capitolo 3: Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **Nuovo**. 

    ![Avviare il nuovo progetto Unity.](images/AzureLabs-Lab3-24.png)

2.  È ora necessario specificare un nome Project Unity, inserire **MR_LUIS**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Percorso **su** un percorso appropriato per l'utente (tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity aperto, è opportuno controllare che **l'editor di script predefinito** sia impostato su **Visual Studio**. Passare a Modifica > preferenze e quindi dalla nuova finestra passare a **Strumenti esterni**. Modificare **Editor script esterni** in Visual Studio **2017.** Chiudere la **finestra** Preferenze.

    ![Aggiornare le preferenze dell'editor di script.](images/AzureLabs-Lab3-26.png)
 
4.  Passare quindi a **File > Build Impostazioni** e passare alla piattaforma Universal Windows **Platform** facendo clic sul **pulsante Cambia** piattaforma.

    ![Compilare Impostazioni finestra, passare dalla piattaforma alla piattaforma UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Passare a **File > Build Impostazioni** e assicurarsi che:

    1. **Dispositivo di destinazione** impostato su **Qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **Dispositivo di destinazione** su *HoloLens*.

    2. **Il tipo di** compilazione è impostato **su D3D**
    3. **L'SDK** è impostato su **Più recente installato**
    4. **Visual Studio versione è** impostata su **Versione più recente installata**
    5. **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab3-28.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

            ![Creare una nuova cartella di script](images/AzureLabs-Lab3-29.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file*: digitare MR_LuisScene **e** quindi fare clic su **Salva.**

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab3-30.png)

    7. Le impostazioni rimanenti, in *Build Impostazioni*, per il momento devono essere lasciato come predefinite.

6. Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** (Impostazioni lettore). Verrà aperto il pannello correlato nello spazio in cui si trova *il* controllo. 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab3-31.png) 
 
7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1. **La versione del runtime di** scripting deve essere **Stabile** (equivalente a .NET 3.5).
        2. **Il back-end di** scripting deve **essere .NET**
        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab3-32.png)
      
    2. **All'interno della Impostazioni** pubblicazione, in **Funzionalità,** controllare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab3-33.png)

    3. Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Aggiornare il Impostazioni X R.](images/AzureLabs-Lab3-34.png)

8.  Tornare alla *compilazione Impostazioni* i _progetti C# Unity_ non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).
10. Salvare la scena e Project **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-4--create-the-scene"></a>Capitolo 4: Creare la scena

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il [](https://docs.unity3d.com/Manual/AssetPackages.html)codice, è possibile scaricare questo file con estensione [unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [5.](#chapter-5--create-the-microphonemanager-class) 

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *pannello Gerarchia*, in **Oggetto 3D** aggiungere un **piano**.

    ![Creare un piano.](images/AzureLabs-Lab3-35.png)

2.  Tenere presente che quando si  fa di nuovo clic con il pulsante destro del mouse all'interno della gerarchia per creare altri oggetti, se è ancora selezionato l'ultimo oggetto, l'oggetto selezionato sarà l'elemento padre del nuovo oggetto. Evitare di fare clic con il pulsante sinistro del mouse in uno spazio vuoto all'interno della gerarchia e quindi fare clic con il pulsante destro del mouse.

3.  Ripetere la procedura precedente per aggiungere gli oggetti seguenti:

    1. *Sphere*
    2. *Cilindro*
    3. *Cubo*
    4. *Testo 3D*

4.  La gerarchia *della scena* risultante dovrebbe essere simile a quella nell'immagine seguente:

    ![Configurazione della gerarchia della scena.](images/AzureLabs-Lab3-36.png)
 
5.  Fare clic con il pulsante sinistro del  **mouse** sulla fotocamera principale per selezionarla. Nel pannello di controllo verrà visualizzato l'oggetto Camera con tutti i relativi componenti.
6.  Fare clic sul **pulsante Add Component** (Aggiungi componente) nella parte inferiore di Inspector Panel *(Pannello di controllo).*

    ![Aggiungere un'origine audio](images/AzureLabs-Lab3-37.png)
 
7.  Cercare il componente denominato *Origine audio*, come illustrato in precedenza.
8.  Assicurarsi anche che  il componente Trasforma della fotocamera principale sia impostato su (0,0,0). A tale  scopo, premere l'icona a forma di ingranaggio accanto al componente Transform (Trasforma) della fotocamera e selezionare **Reset (Reimposta).**  Il *componente Transform* dovrebbe quindi essere simile al seguente:

    1.  *La* posizione è impostata **su 0, 0, 0.**
    2.  *La* rotazione è impostata **su 0, 0, 0**.

    > [!NOTE] 
    > Per il Microsoft HoloLens, sarà necessario modificare anche quanto segue, che fanno parte del componente **Fotocamera,** che si trova nella **fotocamera principale:**
    > - **Cancella flag:** Colore a tinta unita.
    > - **Sfondo** 'Black, Alpha 0': colore esadecimale: #00000000.

9.  Fare clic sul piano **per** selezionarlo. Nel pannello *Inspector (Controllo)* imposta *il componente Transform* (Trasforma) con i valori seguenti:

    |   Asse X    | Asse Y |   Asse Z    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. Fare clic sulla sfera **per** selezionarla. Nel pannello *Inspector (Controllo)* imposta *il componente Transform* (Trasforma) con i valori seguenti:

    |   Asse X    | Asse Y |   Asse Z    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. Fare clic sul **cilindro per** selezionarlo. Nel pannello *Inspector (Controllo)* imposta *il componente Transform* (Trasforma) con i valori seguenti:

    |   Asse X    | Asse Y |   Asse Z    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. Fare clic sul cubo **per** selezionarlo. Nel pannello *Inspector (Controllo)* imposta *il componente Transform* (Trasforma) con i valori seguenti:

    |        | Transform - *Position* |       |  \| |       | Trasformazione - *Rotazione* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **S**                   | **Z** |  \| | **X** | **S**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Fare clic **sull'oggetto Nuovo testo** per selezionarlo. Nel pannello *Inspector (Controllo)* imposta *il componente Transform* (Trasforma) con i valori seguenti:

    |       | Transform - *Position* |       |  \| |       | Trasforma - *Ridimensiona* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **S**                  | **Z** |  \| | **X** | **S**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Impostare **Dimensioni carattere** nel componente Mesh **testo** su **50.**
15. Modificare il *nome* dell'oggetto **Mesh di** testo in **Testo dettatura**.

    ![Creare un oggetto Testo 3D](images/AzureLabs-Lab3-38.png)
 
16. La struttura del pannello gerarchia dovrebbe ora essere simile alla seguente:

    ![mesh di testo nella visualizzazione scena](images/AzureLabs-Lab3-38b.png)


17. La scena finale dovrebbe essere simile all'immagine seguente:

    ![Visualizzazione della scena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capitolo 5: Creare la classe MicrophoneManager

Il primo script che si sta per creare è la *classe MicrophoneManager.* A questo punto, si creeranno *luisManager,* la classe *Behaviours* e infine la classe *Gaze* (è possibile crearne tutte ora, anche se verrà trattata man mano che si raggiunge ogni capitolo).

La *classe MicrophoneManager* è responsabile di:

-   Rilevamento del dispositivo di registrazione collegato al visore VR o al computer (a seconda di quale sia quello predefinito).
-   Acquisire l'audio (voce) e usare la dettatura per archiviarlo come stringa.
-   Dopo che la voce è stata sospesa, inviare la dettatura alla *classe LuisManager.* 

Per creare questa classe: 

1.  Fare clic con il pulsante destro *del mouse Project pannello di controllo,*> **cartella**. Chiamare la cartella **Scripts**. 

    ![Creare la cartella Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Dopo avere **creato la** cartella Script, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro **del mouse su > script C#.** Assegnare allo script *il nome MicrophoneManager*. 

3.  Fare doppio clic *su MicrophoneManager* per aprirlo con *Visual Studio*.
4.  Aggiungere gli spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *della classe MicrophoneManager:*

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().* Questi verranno chiamati quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  A questo punto è necessario il metodo che l'app usa per avviare e arrestare l'acquisizione vocale e passarlo alla *classe LuisManager,* che verrà compilata a breve. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Aggiungere un *gestore di dettatura* che verrà richiamato quando la voce viene sospesa. Questo metodo passerà il testo di dettatura alla *classe LuisManager.*

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare il *metodo Update()* perché questa classe non lo userà.

9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

    > [!NOTE]
    > A questo punto si noterà un errore visualizzato nel pannello della *console dell'editor di Unity.* Questo perché il codice fa riferimento *alla classe LuisManager* che verrà creata nel capitolo successivo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capitolo 6: Creare la classe LUISManager

È il momento di creare la *classe LuisManager,* che effettua la chiamata al servizio LuiS di Azure. 

Lo scopo di questa classe è ricevere il testo della dettatura dalla classe *MicrophoneManager* e inviarlo *all'API* Language Understanding azure da analizzare.

Questa classe deserializza la *risposta JSON* e chiama i metodi appropriati della *classe Behaviours* per attivare un'azione.

Per creare questa classe: 

1.  Fare doppio clic sulla **cartella** Script per aprirla. 
2.  Fare clic con il pulsante destro del **mouse all'interno** della **cartella Script e scegliere > script C#.** Assegnare allo script *il nome LuisManager*. 
3.  Fare doppio clic sullo script per aprirlo con Visual Studio.
4.  Aggiungere gli spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Si inizierà creando  tre classi all'interno della classe *LuisManager* (all'interno dello stesso file di script, sopra il metodo *Start())* che rappresenteranno la risposta JSON deserializzata da Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Aggiungere quindi le variabili seguenti all'interno *della classe LuisManager:*
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Assicurarsi di inserire l'endpoint LUIS in , che sarà disponibile nel portale LUIS.

8.  È ora *necessario aggiungere il codice* per il metodo Awake(). Questo metodo verrà chiamato quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  A questo punto sono necessari i metodi che questa applicazione usa per inviare la dettatura ricevuta dalla classe *MicrophoneManager* a *LUIS* e quindi ricevere e deserializzare la risposta. 
10. Dopo aver determinato il valore della finalità e delle entità associate, queste vengono passate all'istanza della *classe Behaviours* per attivare l'azione prevista.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Creare un nuovo metodo denominato *AnalyseResponseElements()* che leggerà *l'oggetto AnalysedQuery risultante* e determinerà le entità. Una volta determinate, le entità verranno passate all'istanza della *classe Behaviours* da usare nelle azioni.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare i *metodi Start()* *e Update()* perché questa classe non li userà.

12. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

> [!NOTE]
> A questo punto si noteranno diversi errori visualizzati nel pannello della *console dell'editor di Unity.* Ciò è dovuto al fatto che il codice fa riferimento alla classe *Behaviours* che verrà creata nel capitolo successivo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capitolo 7: Creare la classe Comportamenti

La *classe Behaviours* attiverà le azioni usando le entità fornite dalla *classe LuisManager.*

Per creare questa classe: 

1.  Fare doppio clic sulla **cartella** Script per aprirla. 
2.  Fare clic con il pulsante destro del **mouse all'interno** della **cartella Script e scegliere > script C#.** Assegnare allo script *il nome Comportamenti*. 
3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.
4.  Aggiungere quindi le variabili seguenti all'interno *della classe Behaviours:*

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Aggiungere il *codice del metodo Awake().* Questo metodo verrà chiamato quando la classe inizializza:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  I metodi seguenti vengono chiamati dalla classe *LuisManager* (creata in precedenza) per determinare quale oggetto è la destinazione della query e quindi attivare l'azione appropriata.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Aggiungere il *metodo FindTarget()* per determinare quale *gameobject è* la destinazione dell'intento corrente. Questo metodo imposta come predefinita la destinazione per il *GameObject* da "guardare" se non è definita alcuna destinazione esplicita nelle entità.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare i *metodi Start()* *e Update()* perché questa classe non li userà.

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-8--create-the-gaze-class"></a>Capitolo 8: Creare la classe Gaze

L'ultima classe che sarà necessario completare questa app è la *classe Gaze.* Questa classe aggiorna il riferimento al *GameObject* attualmente nello stato attivo visivo dell'utente.

Per creare questa classe: 

1.  Fare doppio clic sulla **cartella** Script per aprirla. 
2.  Fare clic con il pulsante destro del **mouse all'interno** della **cartella Script e scegliere > script C#.** Assegnare allo script il *nome Gaze*. 
3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.
4.  Inserire il codice seguente per questa classe:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-9--completing-the-scene-setup"></a>Capitolo 9: Completamento della configurazione della scena

1.  Per completare la configurazione della scena, trascinare ogni script creato dalla cartella Scripts (Script) all'oggetto **Main Camera (Fotocamera** principale) nel *pannello Hierarchy (Gerarchia).*
2.  Selezionare **la fotocamera** principale ed esaminare il pannello di controllo. Dovrebbe essere possibile visualizzare ogni script collegato e si noterà che sono presenti parametri per ogni script che devono ancora essere impostati.

    ![Impostazione delle destinazioni di riferimento della fotocamera.](images/AzureLabs-Lab3-41.png)

3.  Per impostare correttamente questi parametri, seguire queste istruzioni:

    1. *MicrophoneManager*:

        - Dal pannello *Hierarchy (Gerarchia)* trascinare **l'oggetto Dictation Text (Testo** dettatura) nella **casella Dictation Text** parameter value (Valore parametro testo dettatura).

    2. *Comportamenti ,* dal pannello *Gerarchia*:

        - Trascinare **l'oggetto** Sphere nella casella Sphere reference target *(Destinazione* riferimento sphere).
        - Trascinare **il cilindro** nella casella *cilindro* di destinazione di riferimento.
        - Trascinare il **cubo** nella casella *Destinazione* riferimento cubo .

    3. *Sguardo fisso*:

        - Impostare *La distanza massima dello* sguardo **fisso su 300** (se non è già presente). 

4.  Il risultato dovrebbe essere simile all'immagine seguente:

    ![Visualizzazione delle destinazioni di riferimento della fotocamera, ora impostate.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capitolo 10 : Test nell'editor di Unity

Verificare che la configurazione della scena sia implementata correttamente.

Assicurarsi che:

-   Tutti gli script sono collegati **all'oggetto Fotocamera** principale. 
-   Tutti i campi nel *pannello controllo fotocamera principale* vengono assegnati correttamente.

1.  Fare clic **sul pulsante** Play (Riproduci) *nell'editor di Unity*. L'app deve essere in esecuzione all'interno del visore immersivo collegato.

2.  Provare alcune espressioni, ad esempio:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se viene visualizzato un errore nella console di Unity sulla modifica del dispositivo audio predefinito, la scena potrebbe non funzionare come previsto. Ciò è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per i visori che li hanno. Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e le operazioni dovrebbero funzionare come previsto.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capitolo 11: Compilare e sideload della soluzione UWP

Dopo aver garantito il funzionamento dell'applicazione nell'editor di Unity, si è pronti per compilare e distribuire.

Per compilare:

1.  Salvare la scena corrente facendo clic su **File > Salva**.
2.  Passare a **File > Build Impostazioni**.
3.  Selezionare la casella denominata **Unity C# Projects** (Progetti C# unity) (utile per visualizzare ed eseguire il debug del codice dopo la creazione del progetto UWP).
4.  Fare clic **su Add Open Scenes (Aggiungi scene aperte)** e quindi su Build **(Compila).**

    ![Finestra Impostazioni compilazione](images/AzureLabs-Lab3-43.png)

4.  Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione. 

5.  Creare una *cartella BUILDS* e all'interno di tale cartella creare un'altra cartella con un nome appropriato. 
6.  Fare **clic su Seleziona** cartella per avviare la compilazione in tale percorso.
 
    ![Crea cartella Compilazioni ](images/AzureLabs-Lab3-44.png)
     ![ Selezionare la cartella Compilazioni](images/AzureLabs-Lab3-45.png)
 
7.  Al termine della compilazione di Unity (potrebbe essere  necessario del tempo), dovrebbe essere aperta una finestra Esplora file nel percorso della compilazione.

Per eseguire la distribuzione nel computer locale:

1.  In *Visual Studio* aprire il file di soluzione creato nel [capitolo precedente.](#chapter-10--test-in-the-unity-editor)
2.  In **Piattaforma soluzione selezionare** **x86**, **Computer locale**.
3.  In **Configurazione soluzione selezionare** **Debug**.

    > Per il Microsoft HoloLens, potrebbe risultare più semplice impostare questa opzione su *Computer* remoto, in modo che non sia necessario eseguire il tethering al computer. Tuttavia, è necessario eseguire anche le operazioni seguenti:
    > - Conoscere **l'indirizzo IP** del HoloLens, disponibile nella Impostazioni > *Network & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Assicurarsi **che la modalità sviluppatore** sia **attivata.** disponibile in *Impostazioni > Update & Security > For developers*.

    ![Distribuire l'app](images/AzureLabs-Lab3-46.png)
 
4.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer.
5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.
6.  Dopo l'avvio, l'app richiederà di autorizzare l'accesso al _microfono_. Usare *i controller di* movimento o *l'input vocale* o la *tastiera* per premere **il pulsante** SÌ. 

## <a name="chapter-12--improving-your-luis-service"></a>Capitolo 12 : Miglioramento del servizio LUIS

>[!IMPORTANT] 
> Questo capitolo è estremamente importante e potrebbe essere necessario eseguire più volte l'iter, perché consente di migliorare l'accuratezza del servizio LUIS: assicurarsi di completare questa operazione.

Per migliorare il livello di comprensione fornito da LUIS, è necessario acquisire nuove espressioni e usarle per eseguire nuovamente il training dell'app LUIS.

Ad esempio, è possibile che sia stato creato un training di LUIS per comprendere "Increase" e "Upsize", ma non si vuole che l'app comprendi anche parole come "Enlarge"?

Dopo aver usato l'applicazione alcune volte, tutto ciò che è stato detto verrà raccolto da LUIS e disponibile nel PORTALE LUIS.

1.  Passare all'applicazione del portale seguendo [questo collegamento](https://www.luis.ai/home)e accedere.
2.  Dopo aver eseguito l'accesso con le credenziali MS, fare clic sul nome *dell'app*.
3.  Fare clic **sul pulsante Rivedi espressioni endpoint** a sinistra della pagina.

    ![Esaminare le espressioni](images/AzureLabs-Lab3-47.png)
 
4.  Verrà visualizzato un elenco delle espressioni inviate a LUIS dall'applicazione di realtà mista.

    ![Elenco di espressioni](images/AzureLabs-Lab3-48.png)
 
Si noteranno alcune *entità evidenziate.* 

Passando il puntatore del mouse su ogni parola evidenziata, è possibile esaminare ogni espressione e determinare quale entità è stata riconosciuta correttamente, quali entità sono erre e quali entità vengono perse.

Nell'esempio precedente è stato rilevato che la parola "lancia" è stata evidenziata come destinazione, quindi è necessario correggere l'errore, che viene fatto passando il puntatore del mouse sulla parola e facendo clic su **Rimuovi etichetta**.

![Controllare le espressioni Rimuovi ](images/AzureLabs-Lab3-49.png)
 ![ immagine etichetta](images/AzureLabs-Lab3-50.png)
 
5.  Se si trovano espressioni completamente erre, è  possibile eliminarle usando il pulsante Elimina sul lato destro della schermata.

    ![Eliminare espressioni erre](images/AzureLabs-Lab3-51.png)

6.  Se invece LUIS ha interpretato correttamente l'espressione, è possibile convalidarne la comprensione usando il pulsante Aggiungi **a finalità allineata.**

    ![Aggiungere alla finalità allineata](images/AzureLabs-Lab3-52.png)

7.  Dopo aver ordinato tutte le espressioni visualizzate, provare a ricaricare la pagina per verificare se sono disponibili altre espressioni.
8.  È molto importante ripetere questo processo il più volte possibile per migliorare la comprensione delle applicazioni. 

**Buon divertimento!**

## <a name="your-finished-luis-integrated-application"></a>Applicazione integrata LUIS completata

È stata creata un'app di realtà mista che sfrutta azure Language Understanding Intelligence Service, per comprendere cosa dice un utente e agire su queste informazioni.

![Risultato del lab](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Durante l'uso di questa applicazione è possibile notare che se si guarda l'oggetto Floor e si chiede di modificarne il colore, l'operazione verrà apportata. È possibile scoprire come impedire all'applicazione di modificare il colore del pavimento?

### <a name="exercise-2"></a>Esercizio 2

Provare ad estendere le funzionalità LUIS e App, aggiungendo funzionalità aggiuntive per gli oggetti nella scena. Ad esempio, creare nuovi oggetti nel punto di hit gaze, a seconda di ciò che l'utente dice, e quindi essere in grado di usare tali oggetti insieme agli oggetti scena correnti, con i comandi esistenti.