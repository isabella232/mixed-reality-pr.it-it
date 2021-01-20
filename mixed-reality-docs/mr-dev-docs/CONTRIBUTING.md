---
title: Istruzioni per i contributi
description: Informazioni su come contribuire ai documenti per sviluppatori di realtà mista nella piattaforma docs.microsoft.com usando Markdown di GitHub.
author: mattwojo
ms.author: mattwoj
ms.date: 01/11/2021
ms.topic: article
ms.openlocfilehash: f60179c35f6103c4771ea2777e05829bfb7a8ce4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583046"
---
# <a name="contributing-to-mixed-reality-developer-documentation"></a><span data-ttu-id="eccf8-103">Contributo alla documentazione per sviluppatori di realtà mista</span><span class="sxs-lookup"><span data-stu-id="eccf8-103">Contributing to Mixed Reality developer documentation</span></span>

<span data-ttu-id="eccf8-104">Benvenuti nel [repository pubblico per la documentazione per sviluppatori di realtà mista](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs).</span><span class="sxs-lookup"><span data-stu-id="eccf8-104">Welcome to the [public repo for Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="eccf8-105">Eventuali articoli creati o modificati in questo repository **saranno visibili al pubblico.**</span><span class="sxs-lookup"><span data-stu-id="eccf8-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="eccf8-106">La documentazione relativa alla realtà mista è ora disponibile nella piattaforma docs.microsoft.com, che usa Markdown con le funzionalità di Markdig di GitHub.</span><span class="sxs-lookup"><span data-stu-id="eccf8-106">The Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown with Markdig features.</span></span> <span data-ttu-id="eccf8-107">Il contenuto modificato in questo repository viene formattato in pagine stilizzate visualizzate all'indirizzo https://docs.microsoft.com/windows/mixed-reality .</span><span class="sxs-lookup"><span data-stu-id="eccf8-107">The content you edit in this repo gets formatted into stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="eccf8-108">Questa pagina illustra i passaggi e le linee guida di base per contribuire e i collegamenti alle nozioni di base di Markdown.</span><span class="sxs-lookup"><span data-stu-id="eccf8-108">This page covers the basic steps and guidelines for contributing and links to Markdown basics.</span></span> <span data-ttu-id="eccf8-109">Grazie per il contributo!</span><span class="sxs-lookup"><span data-stu-id="eccf8-109">Thank you for your contribution!</span></span>

## <a name="available-repos"></a><span data-ttu-id="eccf8-110">Repository disponibili</span><span class="sxs-lookup"><span data-stu-id="eccf8-110">Available repos</span></span>

| <span data-ttu-id="eccf8-111">Nome del repository</span><span class="sxs-lookup"><span data-stu-id="eccf8-111">Repository name</span></span> | <span data-ttu-id="eccf8-112">URL</span><span class="sxs-lookup"><span data-stu-id="eccf8-112">URL</span></span> |
| --- | --- |
| <span data-ttu-id="eccf8-113">Realtà mista</span><span class="sxs-lookup"><span data-stu-id="eccf8-113">Mixed Reality</span></span> | [<span data-ttu-id="eccf8-114">MicrosoftDocs/Mixed-Reality</span><span class="sxs-lookup"><span data-stu-id="eccf8-114">MicrosoftDocs/mixed-reality</span></span>](/windows/mixed-reality) |
| <span data-ttu-id="eccf8-115">Guida per gli appassionati di VR</span><span class="sxs-lookup"><span data-stu-id="eccf8-115">VR Enthusiasts Guide</span></span> | [<span data-ttu-id="eccf8-116">MicrosoftDocs/mixed-Real/appassionati-Guida</span><span class="sxs-lookup"><span data-stu-id="eccf8-116">MicrosoftDocs/mixed-reality/enthusiast-guide</span></span>](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) |
| <span data-ttu-id="eccf8-117">HoloLens</span><span class="sxs-lookup"><span data-stu-id="eccf8-117">HoloLens</span></span> | [<span data-ttu-id="eccf8-118">MicrosoftDocs/HoloLens</span><span class="sxs-lookup"><span data-stu-id="eccf8-118">MicrosoftDocs/HoloLens</span></span>](https://github.com/MicrosoftDocs/Hololens) |

## <a name="before-you-start"></a><span data-ttu-id="eccf8-119">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="eccf8-119">Before you start</span></span>

<span data-ttu-id="eccf8-120">Se non si ha già un account, è necessario [creare un account github](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="eccf8-120">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="eccf8-121">Se si è un dipendente Microsoft, collegare il proprio account GitHub al proprio alias Microsoft nel [portale Open source Microsoft](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="eccf8-121">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="eccf8-122">Unisciti alle organizzazioni **"Microsoft"** e **"MicrosoftDocs"** .</span><span class="sxs-lookup"><span data-stu-id="eccf8-122">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="eccf8-123">Quando si configura l'account GitHub, si consigliano anche le precauzioni di sicurezza seguenti:</span><span class="sxs-lookup"><span data-stu-id="eccf8-123">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="eccf8-124">Creare una [password complessa per l'account github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="eccf8-124">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="eccf8-125">Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="eccf8-125">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="eccf8-126">Salvare i [codici di ripristino](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="eccf8-126">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="eccf8-127">Aggiornare le [impostazioni del profilo pubblico](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="eccf8-127">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="eccf8-128">Impostare il nome e prendere in considerazione l'impostazione del *messaggio di posta elettronica pubblico* in modo che *non venga visualizzato l'indirizzo di posta elettronica*</span><span class="sxs-lookup"><span data-stu-id="eccf8-128">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="eccf8-129">Si consiglia di caricare un'immagine del profilo perché viene visualizzata un'anteprima nelle pagine di docs a cui si contribuisce.</span><span class="sxs-lookup"><span data-stu-id="eccf8-129">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="eccf8-130">Se si prevede di usare la riga di comando, è consigliabile impostare [git Credential Manager per Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="eccf8-130">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="eccf8-131">In questo modo, non sarà necessario immettere la password ogni volta che si crea un contributo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-131">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="eccf8-132">Il sistema di pubblicazione è associato a GitHub, quindi questa procedura è importante.</span><span class="sxs-lookup"><span data-stu-id="eccf8-132">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="eccf8-133">L'utente verrà elencato come autore o collaboratore per ogni articolo usando l'alias GitHub.</span><span class="sxs-lookup"><span data-stu-id="eccf8-133">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="eccf8-134">Modifica di un articolo esistente</span><span class="sxs-lookup"><span data-stu-id="eccf8-134">Editing an existing article</span></span>

<span data-ttu-id="eccf8-135">Usare il flusso di lavoro seguente per apportare aggiornamenti a *un articolo esistente* tramite GitHub in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="eccf8-135">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="eccf8-136">Passare all'articolo che si vuole modificare nella cartella "Mixed-Reality-docs".</span><span class="sxs-lookup"><span data-stu-id="eccf8-136">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="eccf8-137">Selezionare il pulsante modifica (icona a matita) in alto a destra, che consente di creare un fork automatico di un ramo eliminabile dal ramo ' Master '.</span><span class="sxs-lookup"><span data-stu-id="eccf8-137">Select the edit button (pencil icon) in the top right, which will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Modificare un articolo.](images/editpage.png)
3. <span data-ttu-id="eccf8-139">Modificare il contenuto dell'articolo secondo le [nozioni di base di Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="eccf8-139">Edit the content of the article according to the ["Markdown basics"](#markdown-basics).</span></span>
4. <span data-ttu-id="eccf8-140">Aggiornare i metadati all'inizio di ogni articolo:</span><span class="sxs-lookup"><span data-stu-id="eccf8-140">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="eccf8-141">**title**: titolo della pagina che viene visualizzato nella scheda del browser quando viene visualizzato l'articolo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-141">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="eccf8-142">I titoli delle pagine vengono usati per la SEO e l'indicizzazione, quindi non modificare il titolo a meno che non sia necessario (sebbene sia meno critico prima che la documentazione diventi pubblica).</span><span class="sxs-lookup"><span data-stu-id="eccf8-142">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="eccf8-143">**Descrizione**: scrivere una breve descrizione del contenuto dell'articolo, che incrementa il SEO e l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="eccf8-143">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="eccf8-144">**autore**: se si è il proprietario principale della pagina, aggiungere qui l'alias github.</span><span class="sxs-lookup"><span data-stu-id="eccf8-144">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="eccf8-145">**ms. Author**: se si è il proprietario principale della pagina, aggiungere qui l'alias Microsoft (non è necessario @microsoft.com , ma solo l'alias).</span><span class="sxs-lookup"><span data-stu-id="eccf8-145">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="eccf8-146">**ms. date**: aggiornare la data se si aggiunge contenuto principale alla pagina, ma non per correzioni quali chiarificazione, formattazione, grammatica o ortografia.</span><span class="sxs-lookup"><span data-stu-id="eccf8-146">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="eccf8-147">**parole chiave**: supporto delle parole chiave in SEO (ottimizzazione del motore di ricerca).</span><span class="sxs-lookup"><span data-stu-id="eccf8-147">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="eccf8-148">Aggiungere parole chiave, separate da una virgola e uno spazio, specifiche dell'articolo, ma senza segni di punteggiatura dopo l'ultima parola chiave nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="eccf8-148">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="eccf8-149">Non è necessario aggiungere parole chiave globali che si applicano a tutti gli articoli, perché sono gestite altrove.</span><span class="sxs-lookup"><span data-stu-id="eccf8-149">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="eccf8-150">Una volta completate le modifiche apportate all'articolo, scorrere verso il basso e selezionare **Proponi modifica file**.</span><span class="sxs-lookup"><span data-stu-id="eccf8-150">When you've completed your article edits, scroll down and select **Propose file change**.</span></span>
6. <span data-ttu-id="eccf8-151">Nella pagina successiva selezionare **Crea richiesta pull** per unire il ramo creato automaticamente in ' Master '.</span><span class="sxs-lookup"><span data-stu-id="eccf8-151">On the next page, select **Create pull request** to merge your automatically created branch into 'master.'</span></span>
7. <span data-ttu-id="eccf8-152">Ripetere i passaggi precedenti per il prossimo articolo che si desidera modificare.</span><span class="sxs-lookup"><span data-stu-id="eccf8-152">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="eccf8-153">Ridenominazione o eliminazione di un articolo esistente</span><span class="sxs-lookup"><span data-stu-id="eccf8-153">Renaming or deleting an existing article</span></span>

<span data-ttu-id="eccf8-154">Se la modifica Rinomina o Elimina un articolo esistente, assicurarsi di aggiungere un reindirizzamento.</span><span class="sxs-lookup"><span data-stu-id="eccf8-154">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="eccf8-155">In questo modo, tutti gli utenti con un collegamento all'articolo esistente continueranno a trovarsi nel posto giusto.</span><span class="sxs-lookup"><span data-stu-id="eccf8-155">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="eccf8-156">I reindirizzamenti vengono gestiti dal .openpublishing.redirection.jssul file nella radice del repository.</span><span class="sxs-lookup"><span data-stu-id="eccf8-156">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="eccf8-157">Per aggiungere un reindirizzamento a .openpublishing.redirection.jsin, aggiungere una voce alla `redirections` matrice:</span><span class="sxs-lookup"><span data-stu-id="eccf8-157">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="eccf8-158">`source_path`È il percorso del repository relativo all'articolo precedente che si sta rimuovendo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-158">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="eccf8-159">Verificare che il percorso inizi con `mixed-reality-docs` e termini con `.md` .</span><span class="sxs-lookup"><span data-stu-id="eccf8-159">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="eccf8-160">`redirect_url`È l'URL pubblico relativo dall'articolo precedente al nuovo articolo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-160">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="eccf8-161">Assicurarsi che l'URL **non** contenga `mixed-reality-docs` o `.md` , perché si riferisce all'URL pubblico e non al percorso del repository.</span><span class="sxs-lookup"><span data-stu-id="eccf8-161">Be sure that this URL **doesn't** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="eccf8-162">Il collegamento a una sezione all'interno del nuovo articolo con `#section` è consentito.</span><span class="sxs-lookup"><span data-stu-id="eccf8-162">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="eccf8-163">Se necessario, è anche possibile usare un percorso assoluto di un altro sito.</span><span class="sxs-lookup"><span data-stu-id="eccf8-163">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="eccf8-164">`redirect_document_id` indica se si desidera memorizzare l'ID del documento del file precedente.</span><span class="sxs-lookup"><span data-stu-id="eccf8-164">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="eccf8-165">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="eccf8-165">The default is `false`.</span></span> <span data-ttu-id="eccf8-166">Usare `true` se si vuole mantenere il `ms.documentid` valore dell'attributo dall'articolo reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="eccf8-166">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="eccf8-167">Se si mantiene l'ID del documento, i dati, ad esempio le visualizzazioni di pagina e le classificazioni, verranno trasferiti all'articolo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="eccf8-167">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="eccf8-168">Eseguire questa operazione se il reindirizzamento è principalmente una ridenominazione e non un puntatore a un articolo diverso che copre solo parte dello stesso contenuto.</span><span class="sxs-lookup"><span data-stu-id="eccf8-168">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="eccf8-169">Se si aggiunge un reindirizzamento, assicurarsi di eliminare anche il vecchio file.</span><span class="sxs-lookup"><span data-stu-id="eccf8-169">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="eccf8-170">Creazione di un nuovo articolo</span><span class="sxs-lookup"><span data-stu-id="eccf8-170">Creating a new article</span></span>

<span data-ttu-id="eccf8-171">Usare il flusso di lavoro seguente per *creare nuovi articoli* nel repository della documentazione tramite GitHub in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="eccf8-171">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="eccf8-172">Creare un fork dal ramo ' Master ' di MicrosoftDocs/Mixed-Reality (usando il pulsante **fork** in alto a destra).</span><span class="sxs-lookup"><span data-stu-id="eccf8-172">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Creare un fork del ramo master.](images/forkbranch.png)
2. <span data-ttu-id="eccf8-174">Nella cartella "Mixed-Reality-docs" selezionare **Crea nuovo file** in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="eccf8-174">In the "mixed-reality-docs" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="eccf8-175">Creare un nome di pagina per l'articolo (usare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere ". MD"</span><span class="sxs-lookup"><span data-stu-id="eccf8-175">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Assegnare un nome alla nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="eccf8-177">Assicurarsi di creare il nuovo articolo dall'interno della cartella "mixed-Real-docs".</span><span class="sxs-lookup"><span data-stu-id="eccf8-177">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="eccf8-178">Per confermare questo problema, verificare la presenza di "/Mixed-Reality-docs/" nella nuova riga nome file.</span><span class="sxs-lookup"><span data-stu-id="eccf8-178">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="eccf8-179">Nella parte superiore della nuova pagina aggiungere il blocco di metadati seguente:</span><span class="sxs-lookup"><span data-stu-id="eccf8-179">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="eccf8-180">Compilare i campi dei metadati pertinenti in base alle istruzioni riportate nella [sezione precedente](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="eccf8-180">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="eccf8-181">Scrivere il contenuto dell'articolo usando le [nozioni fondamentali di Markdown](#markdown-basics)</span><span class="sxs-lookup"><span data-stu-id="eccf8-181">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="eccf8-182">Aggiungere una `## See also` sezione nella parte inferiore dell'articolo con i collegamenti ad altri articoli pertinenti.</span><span class="sxs-lookup"><span data-stu-id="eccf8-182">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="eccf8-183">Al termine, selezionare **commit nuovo file**.</span><span class="sxs-lookup"><span data-stu-id="eccf8-183">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="eccf8-184">Selezionare **nuova richiesta pull** e unire il ramo ' Master ' del fork in MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi la modalità corretta).</span><span class="sxs-lookup"><span data-stu-id="eccf8-184">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="eccf8-186">Nozioni di base su Markdown</span><span class="sxs-lookup"><span data-stu-id="eccf8-186">Markdown basics</span></span>

<span data-ttu-id="eccf8-187">Le risorse seguenti consentiranno di apprendere come modificare la documentazione utilizzando il linguaggio markdown:</span><span class="sxs-lookup"><span data-stu-id="eccf8-187">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="eccf8-188">Informazioni di base su Markdown</span><span class="sxs-lookup"><span data-stu-id="eccf8-188">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="eccf8-189">Poster di riferimento Markdown-at-Glance</span><span class="sxs-lookup"><span data-stu-id="eccf8-189">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="eccf8-190">Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="eccf8-190">Additional resources for writing Markdown for docs.microsoft.com</span></span>](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="eccf8-191">Aggiunta di tabelle</span><span class="sxs-lookup"><span data-stu-id="eccf8-191">Adding tables</span></span>

<span data-ttu-id="eccf8-192">A causa del modo in cui le tabelle docs.microsoft.com stili, non avranno bordi o stili personalizzati, anche se si prova a usare CSS inline.</span><span class="sxs-lookup"><span data-stu-id="eccf8-192">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="eccf8-193">Sembra funzionare per un breve periodo di tempo, ma alla fine la piattaforma eliminerà lo stile dalla tabella.</span><span class="sxs-lookup"><span data-stu-id="eccf8-193">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="eccf8-194">Pianificare in anticipo e semplificare le tabelle.</span><span class="sxs-lookup"><span data-stu-id="eccf8-194">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="eccf8-195">[Ecco un sito che semplifica la semplicità delle tabelle Markdown](https://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="eccf8-195">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="eccf8-196">L' [estensione docs Markdown per Visual Studio Code](/teamblog/docs-extension) rende inoltre semplice la generazione di tabelle se si usa [Visual Studio Code (vedere di seguito)](#using-visual-studio-code) per modificare la documentazione.</span><span class="sxs-lookup"><span data-stu-id="eccf8-196">The [Docs Markdown Extension for Visual Studio Code](/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="eccf8-197">Aggiunta di immagini</span><span class="sxs-lookup"><span data-stu-id="eccf8-197">Adding images</span></span>

<span data-ttu-id="eccf8-198">È necessario caricare le immagini nella cartella "mixed-Real-docs/images" del repository e quindi farvi riferimento in modo appropriato nell'articolo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-198">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="eccf8-199">Le immagini verranno automaticamente visualizzate a dimensione completa, il che significa che le immagini di grandi dimensioni riempiranno l'intera larghezza dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="eccf8-199">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="eccf8-200">Prima di caricarli, è consigliabile pre-dimensionare le immagini.</span><span class="sxs-lookup"><span data-stu-id="eccf8-200">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="eccf8-201">La larghezza consigliata è compresa tra 600 e 700 pixel, anche se è necessario ridimensionare le dimensioni se si tratta di una schermata densa o di una frazione di uno screenshot, rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="eccf8-201">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="eccf8-202">È possibile caricare immagini nel repository con fork solo prima dell'Unione.</span><span class="sxs-lookup"><span data-stu-id="eccf8-202">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="eccf8-203">Se quindi si prevede di aggiungere immagini a un articolo, è necessario [usare Visual Studio Code](#using-visual-studio-code) per aggiungere prima le immagini alla cartella "immagini" del fork oppure verificare di aver eseguito quanto segue in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="eccf8-203">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="eccf8-204">Biforcare il repository di MicrosoftDocs/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="eccf8-204">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="eccf8-205">Modificare l'articolo nel fork.</span><span class="sxs-lookup"><span data-stu-id="eccf8-205">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="eccf8-206">Le immagini a cui si fa riferimento nell'articolo sono state caricate nella cartella "mixed-Real-docs/images" nel fork.</span><span class="sxs-lookup"><span data-stu-id="eccf8-206">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="eccf8-207">Creazione di una **richiesta pull** per unire il fork al ramo ' Master ' di MicrosoftDocs/Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="eccf8-207">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="eccf8-208">Per informazioni su come configurare un repository con fork, seguire le istruzioni per la [creazione di un nuovo articolo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="eccf8-208">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="eccf8-209">Visualizzazione in anteprima del lavoro</span><span class="sxs-lookup"><span data-stu-id="eccf8-209">Previewing your work</span></span>

<span data-ttu-id="eccf8-210">Durante la modifica in GitHub tramite un Web browser, è possibile selezionare la scheda **Anteprima** nella parte superiore della pagina per visualizzare l'anteprima del lavoro prima di eseguire il commit.</span><span class="sxs-lookup"><span data-stu-id="eccf8-210">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="eccf8-211">L'anteprima delle modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft</span><span class="sxs-lookup"><span data-stu-id="eccf8-211">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="eccf8-212">Dipendenti Microsoft: una volta che i contributi sono Stati Uniti nel ramo ' Master ', è possibile esaminare il contenuto prima che diventi pubblico all'indirizzo https://review.docs.microsoft.com/windows/mixed-reality?branch=master .</span><span class="sxs-lookup"><span data-stu-id="eccf8-212">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master.</span></span> <span data-ttu-id="eccf8-213">Trovare l'articolo usando il sommario nella colonna a sinistra.</span><span class="sxs-lookup"><span data-stu-id="eccf8-213">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="eccf8-214">Modifica nel browser rispetto alla modifica con un client desktop</span><span class="sxs-lookup"><span data-stu-id="eccf8-214">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="eccf8-215">La modifica nel browser rappresenta il modo più semplice per apportare modifiche rapide, tuttavia, esistono alcuni svantaggi:</span><span class="sxs-lookup"><span data-stu-id="eccf8-215">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="eccf8-216">Non si ottiene il controllo ortografico.</span><span class="sxs-lookup"><span data-stu-id="eccf8-216">You don't get spell-check.</span></span>
- <span data-ttu-id="eccf8-217">Non si ottiene alcun collegamento intelligente ad altri articoli (è necessario digitare manualmente il nome file dell'articolo).</span><span class="sxs-lookup"><span data-stu-id="eccf8-217">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="eccf8-218">Può trattarsi di un problema per caricare le immagini e farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="eccf8-218">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="eccf8-219">Se si preferisce non gestire questi problemi, utilizzare un client desktop come [Visual Studio Code](https://code.visualstudio.com/) con alcune [estensioni utili](#useful-extensions) per contribuire.</span><span class="sxs-lookup"><span data-stu-id="eccf8-219">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="eccf8-220">Uso di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eccf8-220">Using Visual Studio Code</span></span>

<span data-ttu-id="eccf8-221">Per i motivi elencati in [precedenza](#editing-in-the-browser-vs-editing-with-a-desktop-client), è preferibile usare un client desktop per modificare la documentazione anziché un Web browser.</span><span class="sxs-lookup"><span data-stu-id="eccf8-221">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="eccf8-222">Si consiglia di usare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="eccf8-222">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="eccf8-223">Configurazione</span><span class="sxs-lookup"><span data-stu-id="eccf8-223">Setup</span></span>

<span data-ttu-id="eccf8-224">Per configurare Visual Studio Code per l'uso con questo repository, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="eccf8-224">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="eccf8-225">In un Web browser:</span><span class="sxs-lookup"><span data-stu-id="eccf8-225">In a web browser:</span></span>
    1. <span data-ttu-id="eccf8-226">Installare [git per il PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="eccf8-226">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="eccf8-227">Installare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="eccf8-227">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="eccf8-228">[MicrosoftDocs di divisione/realtà mista,](#creating-a-new-article) se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="eccf8-228">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="eccf8-229">Nel fork selezionare **clona o Scarica** e copiare l'URL.</span><span class="sxs-lookup"><span data-stu-id="eccf8-229">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="eccf8-230">Creare un clone locale del fork in Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="eccf8-230">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="eccf8-231">Scegliere **riquadro comandi** dal menu **Visualizza** .</span><span class="sxs-lookup"><span data-stu-id="eccf8-231">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="eccf8-232">Digitare "git: clone".</span><span class="sxs-lookup"><span data-stu-id="eccf8-232">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="eccf8-233">Incollare l'URL copiato.</span><span class="sxs-lookup"><span data-stu-id="eccf8-233">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="eccf8-234">Scegliere la posizione in cui salvare il clone nel PC.</span><span class="sxs-lookup"><span data-stu-id="eccf8-234">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="eccf8-235">Selezionare **Apri repository** nella finestra popup.</span><span class="sxs-lookup"><span data-stu-id="eccf8-235">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="eccf8-236">Modifica della documentazione</span><span class="sxs-lookup"><span data-stu-id="eccf8-236">Editing documentation</span></span>

<span data-ttu-id="eccf8-237">Usare il flusso di lavoro seguente per apportare modifiche alla documentazione con Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="eccf8-237">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="eccf8-238">Tutte le linee guida per la [modifica](#editing-an-existing-article) e la [creazione](#creating-a-new-article) di articoli e le [nozioni di base per la modifica di Markdown](#markdown-basics)vengono applicate anche quando si usa Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eccf8-238">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="eccf8-239">Verificare che il fork clonato sia aggiornato con il repository ufficiale.</span><span class="sxs-lookup"><span data-stu-id="eccf8-239">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="eccf8-240">In un Web browser creare una richiesta pull per sincronizzare le modifiche recenti da altri collaboratori in MicrosoftDocs/Mixed-Reality ' Master ' al fork (assicurarsi che la freccia indichi il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="eccf8-240">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizza le modifiche da MicrosoftDocs/Mixed-Reality al fork](images/sync_repos.PNG)
   2. <span data-ttu-id="eccf8-242">In Visual Studio Code selezionare il pulsante Sincronizza per sincronizzare il fork aggiornato al momento del clone locale.</span><span class="sxs-lookup"><span data-stu-id="eccf8-242">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Fare clic sull'immagine del pulsante Sincronizza](images/sync_clone.png)
2. <span data-ttu-id="eccf8-244">Creare o modificare gli articoli nel repository clonato usando Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eccf8-244">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="eccf8-245">Modificare uno o più articoli (aggiungere immagini alla cartella "immagini", se necessario).</span><span class="sxs-lookup"><span data-stu-id="eccf8-245">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="eccf8-246">**Salva** le modifiche in **Esplora**.</span><span class="sxs-lookup"><span data-stu-id="eccf8-246">**Save** changes in **Explorer**.</span></span>
      
      ![Scegliere "Salva tutto" in Esplora risorse](images/explorer_save.png)
   3. <span data-ttu-id="eccf8-248">Esegui il **commit di tutte** le modifiche nel **controllo del codice sorgente** (Scrivi messaggio di commit quando richiesto).</span><span class="sxs-lookup"><span data-stu-id="eccf8-248">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Scegliere "Esegui commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. <span data-ttu-id="eccf8-250">Selezionare il pulsante **Sincronizza** per sincronizzare le modifiche con l'origine (il fork in GitHub).</span><span class="sxs-lookup"><span data-stu-id="eccf8-250">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_back.png)
3. <span data-ttu-id="eccf8-252">In un Web browser creare una richiesta pull per sincronizzare le nuove modifiche nel fork con MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="eccf8-252">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="eccf8-254">Estensioni utili</span><span class="sxs-lookup"><span data-stu-id="eccf8-254">Useful extensions</span></span>

<span data-ttu-id="eccf8-255">Le estensioni Visual Studio Code seguenti sono utili per la modifica della documentazione:</span><span class="sxs-lookup"><span data-stu-id="eccf8-255">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="eccf8-256">[Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : usare **ALT + M** per visualizzare un menu di opzioni di creazione di documenti, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="eccf8-256">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="eccf8-257">Eseguire ricerche e fare riferimento alle immagini caricate.</span><span class="sxs-lookup"><span data-stu-id="eccf8-257">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="eccf8-258">Aggiungere la formattazione, ad esempio elenchi, tabelle e chiamate specifiche di docs come `>[!NOTE]` .</span><span class="sxs-lookup"><span data-stu-id="eccf8-258">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="eccf8-259">Cerca e fa riferimento a collegamenti e segnalibri interni (collegamenti a sezioni specifiche all'interno di una pagina).</span><span class="sxs-lookup"><span data-stu-id="eccf8-259">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="eccf8-260">Gli errori di formattazione sono evidenziati (posizionare il puntatore del mouse sull'errore per altre informazioni).</span><span class="sxs-lookup"><span data-stu-id="eccf8-260">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="eccf8-261">[Controllo ortografico codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.</span><span class="sxs-lookup"><span data-stu-id="eccf8-261">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>