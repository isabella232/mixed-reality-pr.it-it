---
title: Istruzioni per la collaborazione
description: Informazioni sui passaggi di base e le linee guida per contribuire Windows Mixed Reality per gli appassionati. I commenti, le modifiche, le aggiunte e la guida sono molto apprezzati.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Feedback, Hub di Feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188171"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribuire alla Guida per gli appassionati di realtà mista

Grazie per l'interesse per la Guida per gli appassionati. I commenti, le modifiche, le aggiunte e il miglioramento della documentazione sono molto apprezzati. Questa pagina illustra i passaggi di base e le linee guida per contribuire.

> [!IMPORTANT]
> Tutti i repository che pubblicano contenuto in docs.microsoft.com adottano il [Codice di comportamento Open Source di Microsoft](https://opensource.microsoft.com/codeofconduct/). Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul Codice di comportamento Open Source di Microsoft) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.<br>
>
> Le correzioni minori o i chiarimenti inviati per la documentazione e gli esempi di codice nei repository pubblici sono coperti dalle [Condizioni per l'utilizzo di docs.microsoft.com](/legal/termsofuse). Per le novità o le modifiche significative verrà generato un commento nella richiesta pull con la richiesta di inviare un contratto di licenza online per i contributi (Contribution License Agreement, CLA) se non si è dipendenti Microsoft. Prima che la richiesta pull venga accettata, è necessario completare il modulo online.

## <a name="before-you-start"></a>Prima di iniziare

Se non è già presente, è necessario creare un [account GitHub account](https://github.com/join).

>[!NOTE]
>I dipendenti Microsoft possono collegare l'account GitHub all'alias Microsoft nel portale [Microsoft Open Source.](https://repos.opensource.microsoft.com/) Partecipare alle **organizzazioni "Microsoft"** **e "MicrosoftDocs".**

Quando si configura l'account GitHub, è consigliabile adottare anche queste precauzioni di sicurezza:
- Creare una [password complessa per l'account GitHub.](https://github.com/settings/admin)
- Abilitare [l'autenticazione a due fattori.](https://github.com/settings/two_factor_authentication/configure)
- Salvare i [codici di ripristino](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.
- Aggiornare le [impostazioni del profilo pubblico](https://github.com/settings/profile).
   - Impostare il nome e provare a impostare Indirizzo di posta *elettronica pubblico* su Non *visualizzare l'indirizzo di posta elettronica.*
   - È consigliabile caricare un'immagine del profilo perché viene visualizzata un'anteprima nelle pagine della documentazione a cui si contribuisce.
- Se si prevede di usare la riga di comando, è consigliabile configurare [Git Gestione credenziali per Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). In questo modo, non sarà necessario immettere la password ogni volta che si apporta un contributo.

Il sistema di pubblicazione è associato GitHub, quindi questi passaggi sono importanti. Si verrà elencati come autore o collaboratore per ogni articolo usando l'alias GitHub.

## <a name="how-to-make-a-change"></a>Come apportare una modifica

| Per suggerire una modifica alla documentazione, segui questa procedura: | Schermate |
| :------------------- | :--------: |
| 1. Se si sta visualizzando una Docs.microsoft.com, fare clic sul **pulsante** Modifica in alto a destra nella pagina.  Verrai reindirizzato al file di origine Markdown corretto nel [repository GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Pulsante Modifica](images/edit_button.jpg) |
| 2. Se non si ha già un account GitHub, fare clic su **Iscrizione** in alto a destra e creare un nuovo account. | ![Pulsante iscrizione](images/signup-for-github-button.png)|
| 3. Nella pagina di GitHub visualizzata fare clic su Modifica (icona a forma di matita). | ![Pulsante a forma di matita](images/pencil_button.jpg)|
| 4. Nel riquadro Modifica file aggiornare i metadati dei [file](#updating-metadata) e usare la lingua Markdown per modificare il contenuto. ([Come scrivere markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Modifica file](images/edit-in-github.png)|
| 5. Fare clic su Anteprima modifiche per verificare che la formattazione sia come previsto. | ![Anteprima modifiche](images/edit-in-github.png)|
| 6. Al termine, scorrere fino alla fine della pagina e fare clic su "Propose file change" (Proponi modifica file), verrà visualizzata una pagina "Comparing changes" (Confronto delle modifiche), che consente di verificare le modifiche. Fare quindi clic sul pulsante "Crea richiesta pull" per inviare le modifiche. L'operazione è così conclusa. | ![Proporre una modifica](images/propose.jpg)|

Dopo aver inviato le modifiche (tramite una richiesta pull), queste verranno esaminate da un membro del team della documentazione. Se la richiesta viene accettata, gli aggiornamenti vengono pubblicati in [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) .

*Solo per la revisione interna, è possibile visualizzare le modifiche in [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Aggiornamento dei metadati

Aggiornare i metadati all'inizio di ogni articolo:
   * **title:** titolo della pagina visualizzato nella scheda del browser quando viene visualizzato l'articolo. I titoli di pagina vengono usati per seO e indicizzazione, quindi non modificare il titolo a meno che non sia necessario (anche se questo è meno importante prima che la documentazione venga pubblicata).
   * **description:** scrivere una breve descrizione del contenuto dell'articolo, che migliora seO e individuazione.
   * **author:** se si è il proprietario primario della pagina, aggiungere l'alias GitHub qui.
   * **ms.author:** se si è il proprietario primario della pagina, aggiungere qui l'alias Microsoft (non è necessario , ma @microsoft.com solo l'alias).
   * **ms.date:** aggiornare la data se si aggiunge contenuto principale alla pagina, ma non per correzioni come chiarimenti, formattazione, grammatica o ortografia.
   * **keywords:** le parole chiave sono di supporto per SEO (ottimizzazione del motore di ricerca). Aggiungere parole chiave, separate da una virgola e uno spazio, specifiche dell'articolo, ma senza punteggiatura dopo l'ultima parola chiave nell'elenco. Non è necessario aggiungere parole chiave globali applicabili a tutti gli articoli, perché vengono gestite altrove. 

### <a name="renaming-or-deleting-an-existing-article"></a>Ridenominazione o eliminazione di un articolo esistente

Se la modifica rinomina o elimina un articolo esistente, assicurarsi di aggiungere un reindirizzamento. In questo modo, chiunque abbia un collegamento all'articolo esistente finirà comunque nella posizione giusta. I reindirizzamenti vengono gestiti dal .openpublishing.redirection.jsnel file nella radice del repo.

Per aggiungere un reindirizzamento .openpublishing.redirection.jssu , aggiungere una voce alla `redirections` matrice :

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- è `source_path` il percorso relativo del repository dell'articolo precedente che si sta rimuovendo. Assicurarsi che il percorso inizi con `mixed-reality-docs/enthusiast-guide` e termini con `.md` .
- è `redirect_url` l'URL pubblico relativo dall'articolo precedente al nuovo articolo. Assicurarsi che questo URL **non contenga** o , perché fa riferimento `mixed-reality-docs/enthusiast-guide` `.md` all'URL pubblico e non al percorso del repository. È consentito il collegamento a una sezione all'interno del nuovo articolo `#section` usando . Se necessario, è anche possibile usare un percorso assoluto a un altro sito.
- `redirect_document_id` indica se si vuole mantenere l'ID documento dal file precedente. Il valore predefinito è `false`. Usare `true` se si vuole mantenere il valore `ms.documentid` dell'attributo dall'articolo reindirizzato. Se si mantiene l'ID documento, i dati, ad esempio le visualizzazioni pagina e le classificazioni, verranno trasferiti all'articolo di destinazione. Eseguire questa operazione se il reindirizzamento è principalmente una ridenominazione e non un puntatore a un articolo diverso che copre solo parte dello stesso contenuto.

Se si aggiunge un reindirizzamento, assicurarsi di eliminare anche il file precedente.

### <a name="creating-a-new-article"></a>Creazione di un nuovo articolo

Usare il flusso di lavoro *seguente per creare nuovi* articoli nel repo della documentazione tramite GitHub in un Web browser:

1. Creare un fork dal ramo MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide 'master' (usando il pulsante **Fork** in alto a destra).

   ![Creare una copia con fork del ramo master.](images/forkbranch.png)
2. Nella cartella "mixed-reality/enthusiast-guide" selezionare Create new file (Crea **nuovo file)** in alto a destra.
3. Creare un nome di pagina per l'articolo (usare trattini anziché spazi e non usare segni di punteggiatura o apostrofi) e aggiungere ".md"

   ![Assegnare un nome alla nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Assicurarsi di creare il nuovo articolo dalla cartella "mixed-reality-docs/enthusiast". È possibile verificarlo controllando la presenza di "/mixed-reality-docs/enthusiast-guide" nella nuova riga del nome file.

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

5. Compilare i campi dei metadati pertinenti in base alle istruzioni nella [sezione precedente.](#updating-metadata)
6. Scrivere il contenuto dell'articolo [usando le nozioni di base di Markdown.](#markdown-basics)
7. Aggiungere una `## See also` sezione nella parte inferiore dell'articolo con collegamenti ad altri articoli pertinenti.
8. Al termine, selezionare **Commit new file (Esegui commit nuovo file).**
9. Selezionare Nuova richiesta **pull** e unire il ramo "master" del fork in MicrosoftDocs/mixed-reality/enthusiast-guide 'master' (assicurarsi che la freccia sia rivolta nel modo corretto).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/mixed-reality/enthusiast-guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Uso dei rami

Il [repository della Guida](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) per gli appassionati di realtà mista GitHub usa due rami padre principali: [Master,](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)questo contenuto può essere esaminato nel sito di [staging](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)e [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)per il contenuto visualizzato nel [sito live.](/windows/mixed-reality/enthusiast-guide)

Quando si inviano contributi, inviare la richiesta pull al **ramo** master. Questo ramo può essere visualizzato nel sito di gestione temporanea e deve contenere solo i contributi pronti per la pubblicazione. È anche possibile creare e inviare un ramo con il proprio nome di ramo univoco che può essere selezionato e visualizzato nel sito di staging. Il **ramo Live** può essere utilizzato solo dagli amministratori del contenuto.

## <a name="markdown-basics"></a>Nozioni di base su Markdown

Le risorse seguenti consentono di imparare a modificare la documentazione usando il linguaggio Markdown:

- [Informazioni di base su Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Poster di riferimento markdown-at-a-glance](images/MarkdownPoster.pdf)
- [Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Aggiunta di tabelle

A causa del modo in cui docs.microsoft.com stili, non hanno bordi o stili personalizzati, anche se si prova css inline. Sembra funzionare per un breve periodo di tempo, ma alla fine la piattaforma rimuoverà lo stile dalla tabella. Pianificare in anticipo e mantenere le tabelle semplici. [Ecco un sito che semplifica le tabelle Markdown.](https://www.tablesgenerator.com/markdown_tables)

[L'estensione Docs Markdown per Visual Studio Code](/teamblog/docs-extension) semplifica anche la generazione di tabelle se si usa Visual Studio Code (vedere di [seguito)](#using-visual-studio-code) per modificare la documentazione.

### <a name="adding-images"></a>Aggiunta di immagini

È necessario caricare le immagini nella cartella "mixed-reality-docs/images" nel repo e quindi fare riferimento alle immagini in modo appropriato nell'articolo. Le immagini verranno visualizzate automaticamente a dimensioni complete, ovvero le immagini di grandi dimensioni riempiranno l'intera larghezza dell'articolo. È consigliabile pre-ridimensionare le immagini prima di caricarle. La larghezza consigliata è compresa tra 600 e 700 pixel, anche se è consigliabile ridimensionare rispettivamente se si tratta di uno screenshot denso o di una frazione di uno screenshot.

>[!IMPORTANT]
>È possibile caricare le immagini solo nel repo con fork prima dell'unione. Pertanto, se si prevede di aggiungere immagini a un articolo, è necessario usare [Visual Studio Code](#using-visual-studio-code) per aggiungere prima le immagini alla cartella "images" del fork o assicurarsi di aver eseguito le operazioni seguenti in un Web browser:
>
>1. Forked del repo MicrosoftDocs/mixed-reality.
>2. L'articolo è stato modificato nel fork.
>3. Le immagini a cui si fa riferimento nell'articolo sono caricate nella cartella "mixed-reality-docs/images" nel fork.
>4. È stata **creata una richiesta pull** per unire il fork nel ramo "master" di MicrosoftDocs/mixed-reality.
>
>Per informazioni su come configurare il proprio repo con fork, seguire le istruzioni per [la creazione di un nuovo articolo.](#creating-a-new-article)

## <a name="previewing-your-work"></a>Anteprima del lavoro

Durante la modifica in GitHub tramite un Web  browser, è possibile selezionare la scheda Anteprima nella parte superiore della pagina per visualizzare in anteprima il lavoro prima di eseguire il commit. 

>[!NOTE]
>L'anteprima delle modifiche review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft

Dipendenti Microsoft: dopo aver unito i contributi nel ramo "master", è possibile esaminare il contenuto prima che sia pubblico all'indirizzo https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Trovare l'articolo usando il sommario nella colonna di sinistra.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Modifica nel browser e modifica con un client desktop

La modifica nel browser è il modo più semplice per apportare modifiche rapide, ma esistono alcuni svantaggi:

- Il controllo ortografico non viene visualizzato.
- Non si ottiene alcun collegamento intelligente ad altri articoli (è necessario digitare manualmente il nome file dell'articolo).
- Può essere un'insidola per caricare e fare riferimento alle immagini.

Se si preferisce non gestire questi problemi, usare un client desktop come [Visual Studio Code](https://code.visualstudio.com/) con un paio di estensioni [utili](#useful-extensions) quando si contribuisce.

## <a name="using-visual-studio-code"></a>Uso di Visual Studio Code

Per i motivi [elencati in](#editing-in-the-browser-vs-editing-with-a-desktop-client)precedenza, è preferibile usare un client desktop per modificare la documentazione anziché un Web browser. È consigliabile usare [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Eseguire la configurazione

Seguire questa procedura per configurare Visual Studio Code usare questo repo:

1. In un Web browser:
    1. Installare [Git per il PC.](https://git-scm.com/downloads)
    2. Installare [Visual Studio Code](https://code.visualstudio.com/).
    3. [Creare il fork di MicrosoftDocs/mixed-reality,](#creating-a-new-article) se non è già stato fatto.
    4. Nel fork selezionare **Clona o scarica e** copia l'URL.
2. Creare un clone locale del fork in Visual Studio Code:
    1. Scegliere **Riquadro comandi** dal menu **Visualizza**.
    2. Digitare "Git: Clone".
    3. Incollare l'URL copiato.
    4. Scegliere dove salvare il clone nel PC.
    5. Selezionare **Apri il repo** nel popup.

### <a name="editing-documentation"></a>Documentazione di modifica

Usare il flusso di lavoro seguente per apportare modifiche alla documentazione con Visual Studio Code:

>[!NOTE]
>Tutte le linee [](#creating-a-new-article) guida per [la modifica](#how-to-make-a-change) e la creazione di articoli e le nozioni di base sulla modifica di [Markdown](#markdown-basics)da sopra si applicano anche quando si Visual Studio Code.

1. Assicurarsi che il fork clonato sia aggiornato con il repo ufficiale.
   1. In un Web browser creare una richiesta pull per sincronizzare le modifiche recenti da altri collaboratori in MicrosoftDocs/mixed-reality 'master' al fork (assicurarsi che la freccia sia rivolta nel modo giusto).
      
      ![Sincronizzare le modifiche da MicrosoftDocs/mixed-reality al fork](images/sync_repos.PNG)
   2. In Visual Studio Code selezionare il pulsante di sincronizzazione per sincronizzare il fork appena aggiornato con il clone locale.
      
      ![Fare clic sull'immagine del pulsante di sincronizzazione](images/sync_clone.png)
2. Creare o modificare articoli nel repo clonato usando Visual Studio Code.
   1. Modificare uno o più articoli (aggiungere immagini alla cartella "images", se necessario).
   2. **Salvare** le modifiche in **Esplora risorse**.
      
      ![Scegliere "Salva tutto" in Esplora risorse](images/explorer_save.png)
   3. **Eseguire il commit** di tutte le modifiche nel controllo del codice **sorgente** (scrivere un messaggio di commit quando richiesto).
      
      ![Scegliere "Commit all" nel controllo del codice sorgente](images/source_control_commit.png)
   4. Selezionare il **pulsante sincronizza** per sincronizzare le modifiche all'origine (fork GitHub).
      
      ![Fare clic sul pulsante di sincronizzazione](images/sync_back.png)
3. In un Web browser creare una richiesta pull per sincronizzare le nuove modifiche nel fork con MicrosoftDocs/mixed-reality 'master' (assicurarsi che la freccia sia rivolta nel modo corretto).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Estensioni utili

Le estensioni Visual Studio Code seguenti sono utili quando si modifica la documentazione:

- [Estensione Docs Markdown per Visual Studio Code-](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) Usare **ALT+M** per visualizzare un menu di opzioni di creazione della documentazione, ad esempio:
   - Cercare e fare riferimento alle immagini caricate.
   - Aggiungere formattazione come elenchi, tabelle e call-out specifici della documentazione, ad esempio `>[!NOTE]` .
   - Cercare e fare riferimento a collegamenti e segnalibri interni (collegamenti a sezioni specifiche all'interno di una pagina).
   - Gli errori di formattazione sono evidenziati (passare il mouse sull'errore per altre informazioni).
- [Controllo ortografico del codice:](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) le parole con errori di ortografia verranno sottolineate. Fare clic con il pulsante destro del mouse su una parola con errori di ortografia per modificarla o salvarla nel dizionario.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Uso di problemi per fornire commenti e suggerimenti Windows Mixed Reality guida per gli appassionati

Per inviare commenti e suggerimenti o fare riferimento a [](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) un problema, anziché modificare direttamente le pagine di documentazione effettive, creare un problema e i proprietari del contenuto si adoderanno per risolvere il problema in modo immediato.

Assicurarsi di includere il titolo dell'argomento e l'URL se si sta creando un problema relativo a una pagina specifica.

Grazie per il supporto di questo contenuto.