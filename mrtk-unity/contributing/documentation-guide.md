---
title: DocumentationGuide
description: linee guida e standard per la documentazione per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a2f32f95b01f97b84bfc95b6d318aef8f80e2dd4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693328"
---
# <a name="documentation-guidelines"></a>Linee guida sulla documentazione

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

Questo documento descrive le linee guida e gli standard della documentazione per il Toolkit di realtà mista (MRTK). Viene fornita un'introduzione agli aspetti tecnici della scrittura e della generazione della documentazione, per evidenziare i problemi comuni e per descrivere lo stile di scrittura consigliato.

La pagina stessa dovrebbe fungere da esempio, quindi usa lo stile designato e le funzionalità di markup più comuni della documentazione.

- [Origine](#source-documentation)
- [Procedure](#how-to-documentation)
- [Progettazione](#design-documentation)
- [Note sulle prestazioni](#performance-notes)
- [Modifiche di rilievo](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funzionalità e markup

Questa sezione descrive le funzionalità di uso frequente. Per verificarne il funzionamento, esaminare il codice sorgente della pagina.

1. Elenchi numerati
   1. Elenchi numerati annidati con almeno 3 spazi vuoti iniziali
   1. Il numero effettivo nel codice è irrilevante; l'analisi si occuperà di impostare il numero di elemento corretto.

- Elenchi punti elenco
  - Elenchi punti puntati annidati
- Testo in **grassetto** con \* \* asterisco doppio\*\*
-  *testo* corsivo con carattere di \_ sottolineatura \_ o \* asterisco singolo\*
- Testo `highlighted as code` all'interno di una frase \` con le virgolette\`
- Collegamenti alle pagine di docs [MRTK linee guida sulla documentazione](documentation-guide.md)
- Collegamenti a [ancoraggi all'interno di una pagina](#style); gli ancoraggi sono formati sostituendo gli spazi con trattini e convertendo in lettere minuscole

Per gli esempi di codice vengono usati i blocchi con tre apice \` \` \` e si specifica *CSharp* come lingua per l'evidenziazione della sintassi:

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Quando si menziona il codice all'interno di una frase `use a single backtick` .

### <a name="todos"></a>Elementi todo

Evitare di usare TODOs in docs, nel tempo questi oggetti TODOs (come il codice TODOs) tendono a accumularsi e a sapere come devono essere aggiornati e perché andranno persi.

Se è assolutamente necessario aggiungere una TODO, attenersi alla procedura seguente:

1. Inserire un nuovo problema in GitHub che descrive il contesto dietro il TODO e fornire un background sufficiente che un altro collaboratore possa comprendere e quindi risolvere il problema.
2. Fare riferimento all'URL del problema nell'attività todo nella documentazione.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Sezioni evidenziate

Per evidenziare punti specifici del lettore, utilizzare *> [!NOTE]* , *> [!WARNING]* e *> [!IMPORTANT]* per produrre gli stili seguenti. Si consiglia di utilizzare note per punti generali e avvisi/punti importanti solo per i casi speciali rilevanti.

> [!NOTE]
> Esempio di una nota

> [!WARNING]
> Esempio di avviso

> [!IMPORTANT]
> Esempio di commento importante

## <a name="page-layout"></a>Layout di pagina

### <a name="introduction"></a>Introduzione

La parte immediatamente successiva al titolo del capitolo principale dovrebbe fungere da breve introduzione sul capitolo. Non eseguire questa operazione troppo a lungo, bensì aggiungere i sottotitoli. Che consentono di eseguire il collegamento a sezioni e possono essere salvate come segnalibri.

### <a name="main-body"></a>Corpo principale

Usare i titoli a due livelli e a tre livelli per strutturare il resto.

**Sezioni mini**

Consente di utilizzare una riga di testo in grassetto per i blocchi che devono essere rilevati. Questa operazione può essere sostituita da titoli di quattro livelli a un certo punto.

### <a name="see-also-section"></a>Sezione ' See also '

La maggior parte delle pagine deve terminare con un capitolo denominato *vedere anche*. Questo capitolo è semplicemente un elenco puntato ai collegamenti alle pagine correlate a questo argomento. Questi collegamenti possono anche essere visualizzati all'interno del testo della pagina, laddove appropriato, ma ciò non è obbligatorio. Analogamente, il testo della pagina può contenere collegamenti a pagine non correlate all'argomento principale, che non devono essere incluse nell'elenco *vedere anche* . Vedere [anche il capitolo '' di questa pagina](#see-also) come esempio per la scelta dei collegamenti.

## <a name="table-of-contents-toc"></a>Sommario (sommario)

I file di sommario vengono usati per generare le barre di navigazione nella documentazione di MRTK github.io.
Ogni volta che viene aggiunto un nuovo file di documentazione, assicurarsi che sia presente una voce per il file in uno dei file TOC. yml della cartella della documentazione. Solo gli articoli elencati nei file di sommario vengono visualizzati nell'esplorazione della documentazione per sviluppatori. Può essere presente un file di sommario per ogni sottocartella della cartella della documentazione che può essere collegata a qualsiasi file di sommario esistente per aggiungerlo come sottosezione alla parte corrispondente della navigazione.

## <a name="style"></a>Stile

### <a name="writing-style"></a>Stile di scrittura

Regola empirica generale: prova a **suonare Professional**. Che in genere significa evitare un "tono conversazione". Provare anche a evitare iperboli e sensazioni.

1. Non provare a essere (troppo) divertente.
2. Non scrivere mai ' I '
3. Evitare "We". Questo può essere in genere riformulato con facilità, usando invece ' MRTK '. Esempio: "supporto di questa funzionalità"-> "MRTK supporta questa funzionalità" o "sono supportate le funzionalità seguenti...".
4. In modo analogo, provare a evitare "You". Esempio: "con questa semplice modifica lo shader diventa configurabile!" -> "shader può essere reso configurabile con scarso sforzo".
5. Non usare "frasi imprecise".
6. Evitare di sembrare eccessivamente entusiasti, non è necessario vendere niente.
7. Analogamente, evitare di essere eccessivamente drammatici. I punti esclamativi sono raramente necessari.

### <a name="capitalization"></a>Uso delle maiuscole

- Usare **la frase maiuscola per i titoli**. Ad esempio: capitalizzare la prima lettera e i nomi, ma nient'altro.
- Usare la lingua inglese normale per tutti gli altri elementi. Ciò significa che non viene eseguita la **capitalizzazione di parole arbitrarie**, anche se contengono un significato speciale in tale contesto. Preferire il *testo in corsivo* per evidenziare determinate parole, vedere di [seguito](#emphasis-and-highlighting).
- Quando un collegamento viene incorporato in una frase (ovvero il metodo preferito), il nome del capitolo standard usa sempre le lettere maiuscole, suddividendo quindi la regola di nessuna maiuscola arbitraria all'interno del testo. Usare quindi un nome di collegamento personalizzato per correggere le maiuscole. Ad esempio, di seguito è riportato un collegamento alla documentazione relativa al [controllo dei limiti](../features/ux-building-blocks/bounds-control.md) .
- Usare i nomi in maiuscolo, ad esempio *Unity*.
- NON capitalizzare "Editor" durante la scrittura dell' *editor di Unity*.

### <a name="emphasis-and-highlighting"></a>Enfasi ed evidenziazione

Esistono due modi per evidenziare o evidenziare parole, rendendoli in grassetto o in corsivo. L'effetto del testo in grassetto è che il **testo in grassetto è allineato** e pertanto può essere facilmente notato durante lo scorrimento di una parte di testo o anche semplicemente lo scorrimento su una pagina. Grassetto è molto interessante per evidenziare le frasi da ricordare. Tuttavia, **utilizzare raramente il testo in grassetto**, perché in genere si distrae.

Spesso si vuole che un elemento "Group" appartenga logicamente insieme o evidenzi un termine specifico, perché ha un significato speciale. Non è necessario che tali elementi riescano dal testo generale. Usare il testo corsivo come *metodo leggero* per evidenziare un elemento.

Analogamente, quando un nome di file, un percorso o una voce di menu è indicato nel testo, preferisce renderlo in corsivo per raggrupparlo logicamente, senza distrazioni.

In generale, provare a **evitare un'evidenziazione del testo non necessaria**. I termini speciali possono essere evidenziati una volta per far sì che il lettore sia in grado di riconoscere, non ripetere tale evidenziazione in tutto il testo, quando non serve più e solo distrae.

### <a name="mentioning-menu-entries"></a>Menzione voci di menu

Quando si menziona una voce di menu che un utente deve fare clic, la convenzione corrente è: *progetto > file > creare > foglia*

### <a name="links"></a>Collegamenti

Inserire il maggior numero possibile di collegamenti utili ad altre pagine, ma ogni collegamento viene eseguito una sola volta. Si supponga che un lettore faccia clic su ogni collegamento nella pagina e che si pensi a che cosa sarebbe fastidioso, se la stessa pagina si apre 20 volte.

Preferire i collegamenti incorporati in una frase:

- BAD: le linee guida sono utili. Per informazioni dettagliate, vedere [questo capitolo](../contributing/documentation-guide.md) .
- BENE: le [linee guida](documentation-guide.md) sono utili.

Evitare i collegamenti esterni, possono diventare obsoleti o contenere contenuti con copyright.

Quando si aggiunge un collegamento, valutare se deve essere elencato anche nella sezione [vedere anche](#see-also) . Analogamente, controllare se è necessario aggiungere un collegamento alla pagina nuova alla pagina collegata.

### <a name="images--screenshots"></a>Immagini/screenshot

**Usare schermate sporadicamente.** La gestione delle immagini nella documentazione è molto lavoro, le piccole modifiche dell'interfaccia utente possono rendere obsolete diverse schermate. Le regole seguenti ridurrà il lavoro richiesto per la manutenzione:

1. Non usare screenshot per elementi che possono essere descritti nel testo. In particolare, **non è mai stata catturata una griglia di proprietà** al solo scopo di visualizzare i nomi e i valori delle proprietà.
2. Non includere elementi in uno screenshot irrilevanti per quanto visualizzato. Ad esempio, quando viene visualizzato un effetto di rendering, creare una schermata del viewport, ma escludere qualsiasi interfaccia utente intorno ad essa. Visualizzazione di un'interfaccia utente, provare a spostare le finestre in modo tale che solo questa parte importante sia presente nell'immagine.
3. Quando si include l'interfaccia utente screenshot, visualizzare solo le parti importanti. Se, ad esempio, si parla di pulsanti in una barra degli strumenti, creare un'immagine di dimensioni ridotte che mostri i pulsanti importanti della barra degli strumenti, ma escludere tutto il resto.
4. Usare solo immagini facili da riprodurre. Ciò significa che non è possibile disegnare marcatori o evidenziare le schermate. In primo luogo, non esistono regole coerenti come dovrebbero apparire. In secondo luogo, la riproduzione di uno screenshot di questo tipo è un'operazione aggiuntiva. Descrivere invece le parti importanti del testo. Esistono eccezioni a questa regola, ma sono rare.
5. Ovviamente, è molto più impegnativo per ricreare un GIF animato. Si presume che sia responsabile della ricreazione fino alla fine del periodo di tempo o che gli utenti possano lasciarlo, se non vogliono dedicarsi a questo periodo di tempo.
6. Mantieni il numero di immagini in un articolo basso. Spesso un metodo valido consiste nel creare una schermata complessiva di uno strumento, che Mostra tutto e quindi descrivere il resto nel testo. In questo modo è più semplice sostituire lo screenshot quando necessario.

Altri aspetti:

- L'interfaccia utente dell'editor per le schermate dovrebbe usare un editor di tema grigio chiaro, perché non tutti gli utenti hanno accesso al tema scuro e si vuole rendere il più coerente possibile.
- La larghezza dell'immagine predefinita è 500 pixel, in quanto viene visualizzato correttamente nella maggior parte dei monitoraggi. Provare a non deviare troppa parte. 800 pixel larghezza deve essere il valore massimo.
- Usare PNG per gli screenshot dell'interfaccia utente.
- Usare PNG o jpg per gli screenshot del viewport 3D. Preferisce la qualità rispetto al rapporto di compressione.

### <a name="list-of-component-properties"></a>Elenco delle proprietà dei componenti

Quando si documenta un elenco di proprietà, usare il testo in grassetto per evidenziare il nome della proprietà, quindi le interruzioni di riga e il testo normale per descriverli. Non usare i sottocapitoli o gli elenchi di punti elenco.

Inoltre, non dimenticare di terminare tutte le frasi con un punto.

## <a name="page-completion-checklist"></a>Elenco di controllo completamento pagina

1. Verificare che siano state seguite le linee guida del documento.
1. Esplorare la struttura del documento e verificare se il nuovo documento è indicato nella sezione [vedere anche](#see-also) di altre pagine.
1. Se disponibile, chiedere a un utente di conoscere l'argomento di prova: leggere la pagina per la correttezza tecnica.
1. Fare in modo che qualcuno legga la pagina per lo stile e la formattazione. Questo può essere un utente che non ha familiarità con l'argomento, che è anche una corretta idea di ricevere commenti e suggerimenti sulla comprensione della documentazione.

## <a name="source-documentation"></a>Documentazione di origine

La documentazione dell'API verrà generata automaticamente dai file di origine MRTK. Per semplificare questa operazione, è necessario che i file di origine contengano gli elementi seguenti:

- [Blocchi di riepilogo Class, struct, enum](#class-struct-enum-summary-blocks)
- [Proprietà, metodo, blocchi di riepilogo eventi](#property-method-event-summary-blocks)
- [Versione e dipendenze dell'introduzione alle funzionalità](#feature-introduction-version-and-dependencies)
- [Campi serializzati](#serialized-fields)
- [Valori di enumerazione](#enumeration-values)

Oltre a quanto sopra, il codice deve essere commentato in modo da consentire la manutenzione, le correzioni di bug e la facilità di personalizzazione.

### <a name="class-struct-enum-summary-blocks"></a>Blocchi di riepilogo Class, struct, enum

Se è in corso l'aggiunta di una classe, struct o enum a MRTK, è necessario descriverne lo scopo. Questo è il formato di un blocco di riepilogo sopra la classe.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Se sono presenti dipendenze a livello di classe, queste devono essere documentate in un blocco di osservazioni immediatamente sotto il riepilogo.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Le richieste pull inviate senza riepiloghi per classi, strutture o enumerazioni non verranno approvate.

### <a name="property-method-event-summary-blocks"></a>Proprietà, metodo, blocchi di riepilogo eventi

Le proprietà, i metodi e gli eventi (PMEs) e i campi devono essere documentati con blocchi di riepilogo, indipendentemente dalla visibilità del codice (Public, private, protected e Internal). Lo strumento di generazione della documentazione è responsabile del filtraggio e della pubblicazione solo delle funzionalità pubbliche e protette.

Nota: **non** è necessario un blocco di riepilogo per i metodi Unity (ad esempio: svegli, Start, Update).

Per approvare una richiesta pull, è **necessaria** la documentazione PME.

Come parte di un blocco di riepilogo PME, il significato e lo scopo dei parametri e i dati restituiti sono obbligatori.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Versione e dipendenze dell'introduzione alle funzionalità

Come parte della documentazione di riepilogo delle API, informazioni sulla versione di MRTK in cui è stata introdotta la funzionalità e tutte le dipendenze devono essere documentate in un blocco di note.

Le dipendenze devono includere le dipendenze di estensione e/o di piattaforma.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Campi serializzati

È consigliabile usare l'attributo ToolTip di Unity per fornire la documentazione di runtime per i campi di uno script nel controllo.

Per includere le opzioni di configurazione nella documentazione dell'API, è necessario che gli script *includano almeno il* contenuto della descrizione comando in un blocco di riepilogo.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valori di enumerazione

Quando si definisce l'enumerazione e, il codice deve anche documentare il significato dei valori di enumerazione usando un blocco di riepilogo. Facoltativamente, i blocchi di osservazioni possono essere utilizzati per fornire dettagli aggiuntivi per migliorare la comprensione.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentazione relativa alle procedure

Molti utenti del Toolkit di realtà mista potrebbero non dover usare la documentazione dell'API. Questi utenti utilizzeranno gli script e i prefabbricati riutilizzabili predefiniti per creare le proprie esperienze.

Ogni area funzionale conterrà uno o più file Markdown (. MD) che descrivono a un livello piuttosto elevato, cosa viene fornito. A seconda delle dimensioni e/o della complessità di una determinata area funzionale, potrebbe essere necessario aggiungere altri file, fino a una delle funzionalità disponibili.

Quando viene aggiunta una funzionalità (o l'utilizzo viene modificato), è necessario fornire la documentazione introduttiva.

Come parte di questa documentazione, è necessario fornire le sezioni procedure, incluse le illustrazioni, per aiutare i clienti a una nuova funzionalità o a un concetto di Guida introduttiva.

## <a name="design-documentation"></a>Documentazione di progettazione

La realtà mista offre la possibilità di creare mondi completamente nuovi. Parte di questo può comportare la creazione di asset personalizzati da usare con MRTK. Per rendere questa operazione più semplice per i clienti, i componenti devono fornire la documentazione di progettazione che descrive la formattazione o altri requisiti per le risorse dell'arte.

Di seguito sono riportati alcuni esempi in cui la documentazione di progettazione può essere utile:

- Modelli di cursore
- Visualizzazioni di mapping spaziale
- File effetto audio

Questo tipo di documentazione è **fortemente** consigliato e **può** essere richiesto come parte di una verifica della richiesta pull.

Questo può essere diverso dalla raccomandazione di progettazione nel [sito Microsoft Developer](https://docs.microsoft.com/windows/mixed-reality/design)

## <a name="performance-notes"></a>Note sulle prestazioni

Alcune funzionalità importanti hanno un costo in termini di prestazioni. Spesso questo codice dipende in modo molto da come sono configurate.

Ad esempio:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Le note sulle prestazioni sono consigliate per i componenti pesanti CPU e/o GPU e **possono** essere richieste come parte di una verifica della richiesta pull. Eventuali note sulle prestazioni applicabili devono essere incluse nell'API **e** nella documentazione di panoramica.

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

La documentazione di modifiche di rilievo è costituita da un [file](../contributing/breaking-changes.md) di livello superiore che si collega a singoli Breaking-Changes.MD di ogni area di funzionalità.

I file breaking-changes.md dell'area funzionale devono contenere l'elenco di tutte le modifiche di rilievo note per una determinata versione **,** nonché la cronologia delle modifiche di rilievo apportate nelle versioni precedenti.

Ad esempio:

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

Le informazioni contenute nei file breaking-changes.md a livello di funzionalità verranno aggregate alle note sulla versione per ogni nuova versione di MRTK.

Tutte le modifiche di rilievo che fanno parte di una modifica **devono** essere documentate come parte di una richiesta pull.

## <a name="tools-for-editing-markdown"></a>Strumenti per la modifica di MarkDown

[Visual Studio Code](https://code.visualstudio.com/) è un ottimo strumento per modificare i file Markdown che fanno parte della documentazione di MRTK.

Quando si scrive la documentazione, è consigliabile anche installare le due estensioni seguenti:

- Estensione docs Markdown per Visual Studio Code: usare Alt + M per visualizzare un menu di opzioni di creazione di documenti.

- Controllo ortografico codice: le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.

Entrambi sono inclusi nel pacchetto Microsoft Published Docs Authoring Pack.

## <a name="see-also"></a>Vedi anche 

* [Collegamento di esempio](https://www.google.com)