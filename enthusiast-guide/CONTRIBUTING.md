---
title: Istruzioni per i contributi
description: Informazioni sui passaggi e le linee guida di base per contribuire alla guida per gli appassionati di realtà mista di Windows. Ringraziamo commenti, modifiche, aggiunte e guida.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: d8b4e23603a09d39fef076b600364a55410d12c3
ms.sourcegitcommit: 0b406ccbc7ce619e42809ba8dfdc47d83f4917ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97691435"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contributo alla guida per gli appassionati di realtà mista

Grazie per l'interesse dimostrato nella Guida per gli appassionati. Ringraziamo commenti, modifiche, aggiunte e assistenza per migliorare i documenti. In questa pagina vengono illustrati i passaggi e le linee guida di base per i contributi.

> [!IMPORTANT]
> Tutti i repository che pubblicano contenuto in docs.microsoft.com adottano il [Codice di comportamento Open Source di Microsoft](https://opensource.microsoft.com/codeofconduct/). Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul Codice di comportamento Open Source di Microsoft) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.<br>
>
> Le correzioni minori o i chiarimenti inviati per la documentazione e gli esempi di codice nei repository pubblici sono coperti dalle [Condizioni per l'utilizzo di docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Per le novità o le modifiche significative verrà generato un commento nella richiesta pull con la richiesta di inviare un contratto di licenza online per i contributi (Contribution License Agreement, CLA) se non si è dipendenti Microsoft. Prima che la richiesta pull venga accettata, è necessario completare il modulo online.

## <a name="before-you-start"></a>Prima di iniziare

Se non si ha già un account, è necessario [creare un account github](https://github.com/join).

>[!NOTE]
>Se si è un dipendente Microsoft, collegare il proprio account GitHub al proprio alias Microsoft nel [portale Open source Microsoft](https://repos.opensource.microsoft.com/). Unisciti alle organizzazioni **"Microsoft"** e **"MicrosoftDocs"** .

Quando si configura l'account GitHub, si consigliano anche le precauzioni di sicurezza seguenti:
- Creare una [password complessa per l'account github](https://github.com/settings/admin).
- Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).
- Salvare i [codici di ripristino](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.
- Aggiornare le [impostazioni del profilo pubblico](https://github.com/settings/profile).
   - Impostare il nome e prendere in considerazione l'impostazione del *messaggio di posta elettronica pubblico* in modo che *non venga visualizzato l'indirizzo di posta elettronica*
   - Si consiglia di caricare un'immagine del profilo perché viene visualizzata un'anteprima nelle pagine di docs a cui si contribuisce.
- Se si prevede di usare la riga di comando, è consigliabile impostare [git Credential Manager per Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). In questo modo, non sarà necessario immettere la password ogni volta che si crea un contributo.

Il sistema di pubblicazione è associato a GitHub, quindi questa procedura è importante. L'utente verrà elencato come autore o collaboratore per ogni articolo usando l'alias GitHub.

## <a name="how-to-make-a-change"></a>Come apportare una modifica

| Per suggerire una modifica alla documentazione, segui questa procedura: | Schermate |
| :------------------- | :--------: |
| 1. Se si visualizza una pagina Docs.microsoft.com, fare clic sul pulsante **Edit (modifica** ) in alto a destra nella pagina.  Verrai reindirizzato al file di origine Markdown corretto nel [repository GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Pulsante modifica](images/edit_button.jpg) |
| 2. se non si ha già un account GitHub, fare clic su **Iscriviti** in alto a destra e creare un nuovo account. | ![Pulsante di iscrizione](images/signup-for-github-button.png)|
| 3. nella pagina di GitHub corrispondente visualizzata fare clic su modifica (icona a matita). | ![Pulsante matita](images/pencil_button.jpg)|
| 4. nel riquadro Modifica file [aggiornare i metadati dei file](#updating-metadata) e utilizzare il linguaggio Markdown per modificare il contenuto. ([Come scrivere Markdown).](https://help.github.com/articles/basic-writing-and-formatting-syntax/)| ![Modifica file](images/edit-in-github.png)|
| 5. fare clic su Anteprima modifiche per verificare che la formattazione appaia come previsto. | ![Anteprima modifiche](images/edit-in-github.png)|
| 6. al termine, scorrere fino alla fine della pagina e fare clic su "Proponi modifica file". verrà visualizzata la pagina "confronto di modifiche", che consente di verificare le modifiche. Fare quindi clic sul pulsante "Crea richiesta pull" per inviare le modifiche. L'operazione è così conclusa. | ![Proporre una modifica](images/propose.jpg)|

Dopo aver inviato le modifiche (tramite una richiesta pull), verranno esaminate da un membro del team della documentazione. Se la richiesta viene accettata, gli aggiornamenti vengono pubblicati in [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .

* Solo per la revisione interna, è possibile visualizzare le modifiche in [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Aggiornamento dei metadati

Aggiornare i metadati all'inizio di ogni articolo:
   * **title**: titolo della pagina che viene visualizzato nella scheda del browser quando viene visualizzato l'articolo. I titoli delle pagine vengono usati per la SEO e l'indicizzazione, quindi non modificare il titolo a meno che non sia necessario (sebbene sia meno critico prima che la documentazione diventi pubblica).
   * **Descrizione**: scrivere una breve descrizione del contenuto dell'articolo, che incrementa il SEO e l'individuazione.
   * **autore**: se si è il proprietario principale della pagina, aggiungere qui l'alias github.
   * **ms. Author**: se si è il proprietario principale della pagina, aggiungere qui l'alias Microsoft (non è necessario @microsoft.com , ma solo l'alias).
   * **ms. date**: aggiornare la data se si aggiunge contenuto principale alla pagina, ma non per correzioni quali chiarificazione, formattazione, grammatica o ortografia.
   * **parole chiave**: supporto delle parole chiave in SEO (ottimizzazione del motore di ricerca). Aggiungere parole chiave, separate da una virgola e uno spazio, specifiche dell'articolo, ma senza segni di punteggiatura dopo l'ultima parola chiave nell'elenco. Non è necessario aggiungere parole chiave globali che si applicano a tutti gli articoli, perché sono gestite altrove. 

### <a name="renaming-or-deleting-an-existing-article"></a>Ridenominazione o eliminazione di un articolo esistente

Se la modifica Rinomina o Elimina un articolo esistente, assicurarsi di aggiungere un reindirizzamento. In questo modo, tutti gli utenti con un collegamento all'articolo esistente continueranno a trovarsi nel posto giusto. I reindirizzamenti vengono gestiti dal .openpublishing.redirection.jssul file nella radice del repository.

Per aggiungere un reindirizzamento a .openpublishing.redirection.jsin, aggiungere una voce alla `redirections` matrice:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`È il percorso del repository relativo all'articolo precedente che si sta rimuovendo. Verificare che il percorso inizi con `mixed-reality-docs/enthusiast-guide` e termini con `.md` .
- `redirect_url`È l'URL pubblico relativo dall'articolo precedente al nuovo articolo. Assicurarsi che l'URL **non** contenga `mixed-reality-docs/enthusiast-guide` o `.md` , perché si riferisce all'URL pubblico e non al percorso del repository. Il collegamento a una sezione all'interno del nuovo articolo con `#section` è consentito. Se necessario, è anche possibile usare un percorso assoluto di un altro sito.
- `redirect_document_id` indica se si desidera memorizzare l'ID del documento del file precedente. Il valore predefinito è `false`. Usare `true` se si vuole mantenere il `ms.documentid` valore dell'attributo dall'articolo reindirizzato. Se si mantiene l'ID del documento, i dati, ad esempio le visualizzazioni di pagina e le classificazioni, verranno trasferiti all'articolo di destinazione. Eseguire questa operazione se il reindirizzamento è principalmente una ridenominazione e non un puntatore a un articolo diverso che copre solo parte dello stesso contenuto.

Se si aggiunge un reindirizzamento, assicurarsi di eliminare anche il vecchio file.

### <a name="creating-a-new-article"></a>Creazione di un nuovo articolo

Usare il flusso di lavoro seguente per *creare nuovi articoli* nel repository della documentazione tramite GitHub in un Web browser:

1. Creare un fork dal ramo MicrosoftDocs/mixed-Real/Tree/docs/entusiasta-guide ' Master ' (usando il pulsante **fork** in alto a destra).

   ![Creare un fork del ramo master.](images/forkbranch.png)
2. Nella cartella "mixed-realtà/entusiasta-guide" selezionare **Crea nuovo file** in alto a destra.
3. Creare un nome di pagina per l'articolo (usare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere ". MD"

   ![Assegnare un nome alla nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Assicurarsi di creare il nuovo articolo dalla cartella "mixed-Real-docs/entusiasta". Per confermare questo problema, verificare la presenza di "/Mixed-Reality-docs/Enthusiast-Guide" nella nuova riga nome file.

4. Nella parte superiore della nuova pagina aggiungere il blocco di metadati seguente:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Compilare i campi dei metadati pertinenti in base alle istruzioni riportate nella [sezione precedente](#updating-metadata).
6. Scrivere il contenuto dell'articolo usando le [nozioni fondamentali di Markdown](#markdown-basics)
7. Aggiungere una `## See also` sezione nella parte inferiore dell'articolo con i collegamenti ad altri articoli pertinenti.
8. Al termine, selezionare **commit nuovo file**.
9. Selezionare **nuova richiesta pull** e unire il ramo ' Master ' del fork in MicrosoftDocs/mixed-Real/entusiasta-guide ' Master ' (assicurarsi che la freccia indichi il modo corretto).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/mixed-Real/entusiasta-guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Uso dei rami

Il [repository GitHub della Guida per gli appassionati della realtà mista](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) usa due rami padre principali: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), questo contenuto può essere esaminato nel [sito di staging](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)e in [tempo reale](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)per il contenuto visualizzato nel [sito Live](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).

Quando si effettuano i contributi, inviare la richiesta pull al ramo **Master** . Questo ramo può essere visualizzato nel sito di gestione temporanea e deve contenere solo i contributi pronti per la pubblicazione. È anche possibile creare e inviare un ramo con il proprio nome di ramo univoco, che può essere selezionato e visualizzato nel sito di gestione temporanea. Il ramo **Live** può essere usato solo dagli amministratori del contenuto.

## <a name="markdown-basics"></a>Nozioni di base su Markdown

Le risorse seguenti consentiranno di apprendere come modificare la documentazione utilizzando il linguaggio markdown:

- [Informazioni di base su Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Poster di riferimento Markdown-at-Glance](images/MarkdownPoster.pdf)
- [Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Aggiunta di tabelle

A causa del modo in cui le tabelle docs.microsoft.com stili, non avranno bordi o stili personalizzati, anche se si prova a usare CSS inline. Sembra funzionare per un breve periodo di tempo, ma alla fine la piattaforma eliminerà lo stile dalla tabella. Pianificare in anticipo e semplificare le tabelle. [Ecco un sito che semplifica la semplicità delle tabelle Markdown](https://www.tablesgenerator.com/markdown_tables).

L' [estensione docs Markdown per Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) rende inoltre semplice la generazione di tabelle se si usa [Visual Studio Code (vedere di seguito)](#using-visual-studio-code) per modificare la documentazione.

### <a name="adding-images"></a>Aggiunta di immagini

È necessario caricare le immagini nella cartella "mixed-Real-docs/images" del repository e quindi farvi riferimento in modo appropriato nell'articolo. Le immagini verranno automaticamente visualizzate a dimensione completa, il che significa che le immagini di grandi dimensioni riempiranno l'intera larghezza dell'articolo. Prima di caricarli, è consigliabile pre-dimensionare le immagini. La larghezza consigliata è compresa tra 600 e 700 pixel, anche se è necessario ridimensionare le dimensioni se si tratta di una schermata densa o di una frazione di uno screenshot, rispettivamente.

>[!IMPORTANT]
>È possibile caricare immagini nel repository con fork solo prima dell'Unione. Se quindi si prevede di aggiungere immagini a un articolo, è necessario [usare Visual Studio Code](#using-visual-studio-code) per aggiungere prima le immagini alla cartella "immagini" del fork oppure verificare di aver eseguito quanto segue in un Web browser:
>
>1. Biforcare il repository di MicrosoftDocs/realtà mista.
>2. Modificare l'articolo nel fork.
>3. Le immagini a cui si fa riferimento nell'articolo sono state caricate nella cartella "mixed-Real-docs/images" nel fork.
>4. Creazione di una **richiesta pull** per unire il fork al ramo ' Master ' di MicrosoftDocs/Mixed Reality.
>
>Per informazioni su come configurare un repository con fork, seguire le istruzioni per la [creazione di un nuovo articolo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizzazione in anteprima del lavoro

Durante la modifica in GitHub tramite un Web browser, è possibile selezionare la scheda **Anteprima** nella parte superiore della pagina per visualizzare l'anteprima del lavoro prima di eseguire il commit. 

>[!NOTE]
>L'anteprima delle modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft

Dipendenti Microsoft: una volta che i contributi sono Stati Uniti nel ramo ' Master ', è possibile esaminare il contenuto prima che diventi pubblico all'indirizzo https://review.docs.microsoft.com/windows/mixed-reality?branch=master . Trovare l'articolo usando il sommario nella colonna a sinistra.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Modifica nel browser rispetto alla modifica con un client desktop

La modifica nel browser rappresenta il modo più semplice per apportare modifiche rapide, tuttavia, esistono alcuni svantaggi:

- Non si ottiene il controllo ortografico.
- Non si ottiene alcun collegamento intelligente ad altri articoli (è necessario digitare manualmente il nome file dell'articolo).
- Può trattarsi di un problema per caricare le immagini e farvi riferimento.

Se si preferisce non gestire questi problemi, utilizzare un client desktop come [Visual Studio Code](https://code.visualstudio.com/) con alcune [estensioni utili](#useful-extensions) per contribuire.

## <a name="using-visual-studio-code"></a>Uso di Visual Studio Code

Per i motivi elencati in [precedenza](#editing-in-the-browser-vs-editing-with-a-desktop-client), è preferibile usare un client desktop per modificare la documentazione anziché un Web browser. Si consiglia di usare [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configurazione

Per configurare Visual Studio Code per l'uso con questo repository, seguire questa procedura:

1. In un Web browser:
    1. Installare [git per il PC](https://git-scm.com/downloads).
    2. Installare [Visual Studio Code](https://code.visualstudio.com/).
    3. [MicrosoftDocs di divisione/realtà mista,](#creating-a-new-article) se non è già stato fatto.
    4. Nel fork selezionare **clona o Scarica** e copiare l'URL.
2. Creare un clone locale del fork in Visual Studio Code:
    1. Scegliere **riquadro comandi** dal menu **Visualizza** .
    2. Digitare "git: clone".
    3. Incollare l'URL copiato.
    4. Scegliere la posizione in cui salvare il clone nel PC.
    5. Selezionare **Apri repository** nella finestra popup.

### <a name="editing-documentation"></a>Modifica della documentazione

Usare il flusso di lavoro seguente per apportare modifiche alla documentazione con Visual Studio Code:

>[!NOTE]
>Tutte le linee guida per la [modifica](#how-to-make-a-change) e la [creazione](#creating-a-new-article) di articoli e le [nozioni di base per la modifica di Markdown](#markdown-basics)vengono applicate anche quando si usa Visual Studio Code.

1. Verificare che il fork clonato sia aggiornato con il repository ufficiale.
   1. In un Web browser creare una richiesta pull per sincronizzare le modifiche recenti da altri collaboratori in MicrosoftDocs/Mixed-Reality ' Master ' al fork (assicurarsi che la freccia indichi il modo corretto).
      
      ![Sincronizza le modifiche da MicrosoftDocs/Mixed-Reality al fork](images/sync_repos.PNG)
   2. In Visual Studio Code selezionare il pulsante Sincronizza per sincronizzare il fork aggiornato al momento del clone locale.
      
      ![Fare clic sull'immagine del pulsante Sincronizza](images/sync_clone.png)
2. Creare o modificare gli articoli nel repository clonato usando Visual Studio Code.
   1. Modificare uno o più articoli (aggiungere immagini alla cartella "immagini", se necessario).
   2. **Salva** le modifiche in **Esplora**.
      
      ![Scegliere "Salva tutto" in Esplora risorse](images/explorer_save.png)
   3. Esegui il **commit di tutte** le modifiche nel **controllo del codice sorgente** (Scrivi messaggio di commit quando richiesto).
      
      ![Scegliere "Esegui commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. Selezionare il pulsante **Sincronizza** per sincronizzare le modifiche con l'origine (il fork in GitHub).
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_back.png)
3. In un Web browser creare una richiesta pull per sincronizzare le nuove modifiche nel fork con MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi il modo corretto).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Estensioni utili

Le estensioni Visual Studio Code seguenti sono utili per la modifica della documentazione:

- [Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : usare **ALT + M** per visualizzare un menu di opzioni di creazione di documenti, ad esempio:
   - Eseguire ricerche e fare riferimento alle immagini caricate.
   - Aggiungere la formattazione, ad esempio elenchi, tabelle e chiamate specifiche di docs come `>[!NOTE]` .
   - Cerca e fa riferimento a collegamenti e segnalibri interni (collegamenti a sezioni specifiche all'interno di una pagina).
   - Gli errori di formattazione sono evidenziati (posizionare il puntatore del mouse sull'errore per altre informazioni).
- [Controllo ortografico codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Uso di problemi per fornire commenti e suggerimenti sulla guida a appassionati di realtà mista di Windows

Per fornire commenti e suggerimenti o segnalare un problema, anziché modificare direttamente le pagine di documentazione effettive, [creare un problema](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) e i proprietari di contenuti effettueranno il proprio meglio per risolvere il problema in modo tempestivo.

Se si sta creando un problema relativo a una pagina specifica, assicurarsi di includere il titolo dell'argomento e l'URL.

Grazie per aver supportato il contenuto.
