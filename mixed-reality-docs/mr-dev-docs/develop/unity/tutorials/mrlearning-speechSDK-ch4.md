---
title: Configurazione di finalità e comprensione del linguaggio naturale
description: In questo corso viene illustrato come configurare la finalità e la comprensione del linguaggio naturale nelle applicazioni di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10, LUIS, portale LUIS, finalità, entità, espressioni, comprensione del linguaggio naturale
ms.localizationpriority: high
ms.openlocfilehash: ab9c1db7ca90a59e4ef688a8faa3d294e433cff6
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403462"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configurazione della comprensione delle finalità e del linguaggio naturale

In questa esercitazione esplorerai il riconoscimento delle finalità del servizio vocale di Azure. Il riconoscimento delle finalità consente di dotare l'applicazione di comandi vocali basati sull'intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e ottenere il riconoscimento delle finalità da parte del sistema.

## <a name="objectives"></a>Obiettivi

* Ottenere informazioni su come configurare finalità, entità ed espressioni nel portale LUIS
* Ottenere informazioni su come implementare la comprensione delle finalità e del linguaggio naturale nell'applicazione

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech 1](images/mrlearning-speech/tutorial4-section1-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **RocketLauncher**, trascina il prefab **RocketLauncher_Complete** nella finestra Hierarchy (Gerarchia) e quindi posizionalo in un punto appropriato davanti alla fotocamera, ad esempio:

* Trasforma la **posizione** X = 0, Y = -0.4, Z = 1
* Trasforma la **rotazione** X = 0, Y = 90, Z = 0

![mrlearning-speech 2](images/mrlearning-speech/tutorial4-section1-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona di nuovo l'oggetto **Lunarcom**, quindi espandi l'oggetto **RocketLauncher_Complete** > **Button** e assegna ognuno degli oggetti figlio dell'oggetto **Buttons** al campo **Lunar Launcher Buttons** (Pulsanti lancio lunare) corrispondente:

![mrlearning-speech 3](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Creazione della risorsa Azure Language Understanding

In questa sezione creerai una risorsa di stima di Azure per l'app LUIS (Language Understanding Intelligent Service) che verrà creata nella sezione successiva.

Accedi ad <a href="https://portal.azure.com" target="_blank">Azure</a> e fai clic su **Crea una risorsa**. Cerca quindi e seleziona **Language Understanding**:

![mrlearning-speech 4](images/mrlearning-speech/tutorial4-section2-step1-1.png)

Fai clic sul pulsante **Create** (Crea) per creare un'istanza del servizio:

![mrlearning-speech 5](images/mrlearning-speech/tutorial4-section2-step1-2.png)

Nella pagina Create (Crea) fai clic sull'opzione **Prediction** (Stima) e immetti i valori seguenti:

* In **Subscription** (Sottoscrizione) seleziona **Free Trail** (Prova gratuita) se disponi di una sottoscrizione di prova gratuita, altrimenti seleziona una delle altre sottoscrizioni
* Per il **gruppo di risorse** fare clic sul collegamento Crea nuovo, immettere un nome appropriato, ad esempio *MRKT-Tutorials,* e quindi fare clic su **OK** 

![mrlearning-speech 6](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> Al momento della stesura di questo articolo, non è necessario creare una risorsa di creazione perché quando viene creata l'app LUIS (Language Understanding Intelligent Service) nella sezione successiva viene generata automaticamente una chiave di prova per la creazione in LUIS.

> [!TIP]
> Se disponi già di un altro gruppo di risorse appropriato nell'account di Azure, ad esempio se hai completato l'esercitazione sugli [ancoraggi nello spazio di Azure](mr-learning-asa-01.md), puoi usarlo anziché crearne uno nuovo.

Sempre nella pagina Create (Crea) immetti i valori seguenti:

* In **Name** (Nome) immetti un nome appropriato per il servizio, ad esempio *MRTK-Tutorials-AzureSpeechServices*
* In **Prediction location** (Posizione di stima) scegli una posizione vicina alla posizione fisica degli utenti dell'app, ad esempio *(US) West US* (Stati Uniti occidentali)
* Ai fini di questa esercitazione, in **Prediction pricing tier** (Piano tariffario di stima) seleziona **F0 (5 Calls per second, 10K Calls per month)** (F0 - 5 chiamate al secondo, 10.000 chiamate al mese)

![mrlearning-speech 7](images/mrlearning-speech/tutorial4-section2-step1-4.png)

Fare quindi  clic sulla scheda Rivedi e crea,  esaminare i dettagli e quindi fare clic sul pulsante Crea nella parte inferiore della pagina per creare la risorsa, nonché il nuovo gruppo di risorse, se ne è stato configurato uno da creare:

![mrlearning-speech 8](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> Dopo aver fatto clic sul pulsante Create (Crea), dovrai attendere alcuni minuti per la creazione del servizio.

Al termine del processo di creazione delle risorse, visualizzerai il messaggio **Your deployment is complete** (Distribuzione completata):

![mrlearning-speech 9](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Creazione di un'app LUIS (Language Understanding Intelligent Service)

In questa sezione eseguirai la creazione di un'app LUIS, la configurazione e il training del modello di stima e la connessione alla risorsa di stima di Azure creata nel passaggio precedente.

In particolare, creerai una finalità in base alla quale se l'utente pronuncia un'azione da eseguire, l'app attiverà l'evento Interactable.OnClick() su uno dei tre pulsanti rossi della scena, a seconda del pulsante a cui fa riferimento l'utente.

Se ad esempio l'utente pronuncia **go ahead and launch the rocket** (vai avanti e lancia il missile), l'app stimerà che **vai avanti** indica un'**azione** da eseguire e che l'evento Interactable.OnClick() **target** sia il pulsante di **lancio**.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Creare un'app LUIS
2. Creare finalità
3. Creare espressioni di esempio
4. Creare entità
5. Assegnare entità alle espressioni di esempio
6. Eseguire il training, il test e la pubblicazione dell'app
7. Assegnare una risorsa di stima di Azure all'app

### <a name="1-create-a-luis-app"></a>1. Creare un'app LUIS

Con lo stesso account utente usato durante la creazione della risorsa di Azure nella sezione precedente, accedi a <a href="https://www.luis.ai" target="_blank">LUIS</a>, seleziona il tuo paese e accetta le condizioni per l'utilizzo. Nel passaggio successivo, quando viene visualizzata la richiesta **Link your Azure account** (Collega il tuo account Azure), scegli **Continue using your trial key** (Continua a usare la chiave di prova) per usare invece una risorsa di creazione di Azure.

> [!NOTE]
> Se hai già effettuato l'iscrizione a LUIS e la chiave di prova per la creazione è scaduta, puoi fare riferimento alla documentazione [Eseguire la migrazione a una chiave di creazione delle risorse di Azure](/azure/cognitive-services/luis/luis-migration-authoring) per passare ad Azure per la risorsa di creazione LUIS.

Dopo aver eseguito l'accesso, fare clic su **Nuova app** e immettere i valori seguenti nella finestra popup Crea **nuova app:**

* In **Name** (Nome) immetti un nome appropriato, ad esempio *MRTK Tutorials - AzureSpeechServices*
* In **Culture** (Impostazioni cultura) seleziona **English** (Inglese)
* In **Description** (Descrizione) immetti facoltativamente una descrizione appropriata
* Per **Risorsa stima** selezionare l'elenco a discesa della risorsa di stima per che è stato creato nel portale di Azure.

Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova app:

![mrlearning-speech 10](images/mrlearning-speech/tutorial4-section3-step1-1.png)

Al termine della creazione della nuova app, visualizzerai la pagina **Dashboard** dell'app:

![mrlearning-speech 11](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. Creare finalità

Dalla pagina Dashboard passare alla pagina Build > App Assets > **Intents** (Finalità dell'app build > app), quindi fare clic su **Create** (Crea) e immettere il valore seguente nella finestra popup **Create new intent** (Crea nuova finalità):

* In **Intent name** (Nome finalità) immetti **PressButton**

Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova finalità:

![mrlearning-speech 12](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento a questa finalità in base al nome, ad esempio 'PressButton'. Di conseguenza, è estremamente importante assegnare alla finalità esattamente lo stesso nome.

Al termine della creazione della nuova finalità, visualizzerai la pagina corrispondente:

![mrlearning-speech 14](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. Creare espressioni di esempio

Aggiungi le espressioni di esempio seguenti all'elenco **Example utterance** (Espressioni di esempio) della finalità **PressButton**:

* activate launch sequence (attiva sequenza di lancio)
* show me a placement hint (mostra un suggerimento per il posizionamento)
* initiate the launch sequence (avvia la sequenza di lancio)
* press placement hints button (premi il pulsante dei suggerimenti per il posizionamento)
* give me a hint (fornisci un suggerimento)
* push the launch button (premi il pulsante di lancio)
* i need a hint (ho bisogno di un suggerimento)
* press the reset button (premi il pulsante di reimpostazione)
* time to reset the experience (tempo per reimpostare l'esperienza)
* go ahead and launch the rocket (vai avanti e lancia il missile)

Dopo aver aggiunto tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:

![mrlearning-speech 15](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento alle parole 'hint' (suggerimento), 'hints' (suggerimenti), 'reset' (reimpostazione) e 'launch' (lancia). Di conseguenza, è estremamente importante che le parole vengano scritte esattamente nello stesso modo.

### <a name="4-create-entities"></a>4. Creare entità

Dalla pagina finalità PressButton passare alla pagina Build > App Assets > Entities (Crea asset app > **Entities),** quindi fare clic su **Create** (Crea) e immettere i valori seguenti nella finestra popup **Create new entity** (Crea nuova entità):

* In **Entity name** (Nome entità) immetti **Action** (Azione)
* Per **Tipo di entità** selezionare Machine **learned**

Fare quindi clic **sul pulsante** Crea per creare la nuova entità:

![mrlearning-speech 16](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**Ripeti** il passaggio precedente per creare un'altra entità denominata **Target**, in modo da avere due entità denominate Action (Azione) e Target:

![mrlearning-speech 17](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento a queste entità in base al nome, ad esempio 'Action' (Azione) e 'Target'. Di conseguenza, è estremamente importante assegnare alle entità esattamente lo stesso nome.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. Assegnare entità alle espressioni di esempio

Dalla pagina Entities (Entità) torna alla pagina della finalità **PressButton**.

Dopo essere tornato alla pagina della finalità PressButton, fai clic sulla parola **go** (vai) e quindi sulla parola **ahead** (avanti) e infine scegli **Action (Simple)** (Azione - Semplice) dal menu popup contestuale per etichettare **go ahead** (vai avanti) come valore dell'entità **Action** (Azione):

![mrlearning-speech 18](images/mrlearning-speech/tutorial4-section3-step5-1.png)

La frase **go ahead** (vai avanti) è ora definita come valore dell'entità **Action** (Azione). È ora possibile notare il valore dell'entità azione sotto la parola andare avanti:

![mrlearning-speech 19](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> La linea rossa visualizzata sotto l'etichetta nell'immagine precedente indica che il valore dell'entità non è stato stimato. Questa operazione verrà risolta quando esegui il training del modello nella sezione successiva.

Fai quindi clic sulla parola **launch** (lancia) e infine scegli **Target (Simple)** (Target - Semplice) dal menu popup contestuale per etichettare **launch** (lancia) come valore dell'entità **Target**:

![mrlearning-speech 20](images/mrlearning-speech/tutorial4-section3-step5-3.png)

La **parola** di avvio è ora definita come valore **dell'entità** Target. È ora possibile notare il valore dell'entità Target sotto la parola launch :

![mrlearning-speech 21](images/mrlearning-speech/tutorial4-section3-step5-4.png)

L'espressione di esempio della finalità PressButton 'go ahead and launch the rocket' (vai avanti e lancia il missile) è ora configurata per essere stimata come indicato di seguito:

* Finalità: PressButton
* Entità Action (Azione): go ahead (vai avanti)
* Entità Target: launch (lancia)

**Ripeti**  il processo in due passaggi sopra descritto per assegnare un'etichetta di entità Action (Azione) e Target a ogni espressione di esempio, tenendo presente che le parole seguenti devono essere etichettate come entità **Target**:

* **hint** (suggerimento) (il target è HintsButton nel progetto Unity)
* **hints** (suggerimenti) (il target è HintsButton nel progetto Unity)
* **reset** (reimpostazione) (il target è ResetButton nel progetto Unity)
* **launch** (lancia) (il target è LaunchButton nel progetto Unity)

Dopo aver etichettato tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:

![mrlearning-speech 22](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a>6. Eseguire il training, il test e la pubblicazione dell'app

Per eseguire il training dell'app, fai clic sul pulsante **Train** (Esegui training) e attendi il completamento del processo di training:

![mrlearning-speech 23](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> Come puoi vedere nell'immagine precedente, le linee rosse sotto tutte le etichette sono state rimosse, a indicare che tutti i valori delle entità sono stati stimati. Osserva inoltre che l'icona di stato a sinistra del pulsante Train (Esegui training) ha cambiato colore da rosso a verde.

Al termine dell'elaborazione del training, fai clic sul pulsante **Test**, quindi digita **go ahead and launch the rocket** (vai avanti e lancia il missile) e premi INVIO:

![mrlearning-speech 24](images/mrlearning-speech/tutorial4-section3-step6-2.png)

Dopo l'elaborazione dell'espressione di test, fai clic su **Inspect** (Ispeziona) per visualizzare il risultato del test:

* Finalità: PressButton (con un'attendibilità del 98,5%)
* Entità Action (Azione): go ahead (vai avanti)
* Entità Target: launch (lancia)

![mrlearning-speech 25](images/mrlearning-speech/tutorial4-section3-step6-3.png)

Per pubblicare l'app, fare clic sul pulsante Pubblica in alto a destra, quindi nella finestra popup Scegliere lo **slot** di pubblicazione e le impostazioni selezionare Produzione e fare clic **sul pulsante** Fine:  

![mrlearning-speech 26](images/mrlearning-speech/tutorial4-section3-step6-4.png)

Attendi il completamento del processo di pubblicazione:

![mrlearning-speech 27](images/mrlearning-speech/tutorial4-section3-step6-5.png)

Passare alla pagina Gestisci > applicazione > risorse di **Azure.** La pagina Risorse di Azure dovrebbe essere simile alla seguente:

![mrlearning-speech 28](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Connessione del progetto Unity all'app LUIS

Nella pagina Manage (Gestisci) > Application Settings (Impostazioni applicazione) **Azure Resources** (Risorse di Azure) fai clic sull'icona di **copia** per copiare il contenuto di **Example Query** (Query di esempio):

![mrlearning-speech 29](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Tornato nel progetto Unity, nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) individua il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) e configuralo come indicato di seguito:

* Nel campo **LUIS Endpoint** (Endpoint LUIS) incolla il contenuto di **Example Query** (Query di esempio) copiato nel passaggio precedente:

![mrlearning-speech 30](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>Test e miglioramento del riconoscimento delle finalità

Per usare il riconoscimento delle finalità direttamente nell'editor di Unity, devi consentire al computer di sviluppo di usare la dettatura. Per verificare questa impostazione, apri **Impostazioni** di Windows, quindi scegli **Privacy** > **Comandi vocali** e assicurati che sia attivato **Riconoscimento vocale online**:

![mrlearning-speech 31](images/mrlearning-speech/tutorial4-section5-step1-1.png)

Se ora attivi la modalità di gioco, puoi testare il riconoscimento delle finalità selezionando prima il pulsante relativo al missile. Supponendo quindi che il computer disponga di un microfono, quando pronunci la prima espressione di esempio, **go ahead and launch the rocket** (vai avanti e lancia il missile) potrai osservare il lancio del modulo lunare LunarModule nello spazio:

![mrlearning-speech 32](images/mrlearning-speech/tutorial4-section5-step1-2.png)

Prova tutte le **espressioni di esempio**, quindi alcune **varianti delle espressioni di esempio**, nonché alcune **espressioni casuali**.

Torna quindi a <a href="https://www.luis.ai" target="_blank">LUIS</a> e passa alla pagina Build (Compila) > Improve app performance (Migliora prestazioni app) > **Review endpoint utterances** (Rivedi espressioni endpoint), usa il pulsante di **attivazione/disattivazione** per passare dalla vista predefinita Entities View (Vista entità) a **Tokens View** (Vista token) e quindi rivedi le espressioni:

* Nella colonna **Utterance** (Espressione) modifica e rimuovi in base alle esigenze le etichette assegnate in modo da allinearle alla finalità
* Nella colonna **Aligned intent** (Finalità allineata) verifica che la finalità sia corretta
* Nella colonna **Add/Delete** (Aggiungi/Elimina) fai clic sul pulsante con il segno di spunta verde per aggiungere l'espressione o il pulsante con la x rossa per eliminarla.

Dopo aver esaminato tutte le espressioni desiderate, fai clic sul pulsante **Train** (Esegui training) per ripetere il training del modello e quindi sul pulsante **Publish** (Pubblica) per ripubblicare l'app aggiornata:

![mrlearning-speech 33](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> Se un'espressione dell'endpoint non è allineata alla finalità PressButton, ma vuoi indicare al modello che l'espressione non ha finalità, puoi modificare Aligned intent (Finalità allineata) impostando None (Nessuna).

**Ripeti** questo processo il numero di volte desiderato per migliorare il modello di app.

## <a name="congratulations"></a>Lezione completata

Il progetto ora dispone di comandi di riconoscimento vocale basati sull'intelligenza artificiale, consentendo all'applicazione di riconoscere le finalità degli utenti anche se non pronunciano comandi precisi. Esegui l'applicazione sul dispositivo per verificare che la funzionalità venga eseguita correttamente.
