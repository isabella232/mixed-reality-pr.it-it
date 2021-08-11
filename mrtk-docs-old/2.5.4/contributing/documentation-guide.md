---
title: DocumentationGuide
description: linee guida e standard della documentazione per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f80b954aff9cfc6c687fe9ea6328a6fc18d3659d6f4bce46837cfd02076f26dc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193186"
---
# <a name="documentation-guidelines"></a>Linee guida per la documentazione

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

Questo documento illustra le linee guida e gli standard della documentazione per l'Toolkit (MRTK) di realtà mista. Viene fornita un'introduzione agli aspetti tecnici della scrittura e della generazione della documentazione, per evidenziare le insidie comuni e per descrivere lo stile di scrittura consigliato.

La pagina stessa dovrebbe fungere da esempio, pertanto usa lo stile previsto e le funzionalità di markup più comuni della documentazione.

- [Origine](#source-documentation)
- [Procedure](#how-to-documentation)
- [Progettazione](#design-documentation)
- [Note sulle prestazioni](#performance-notes)
- [Modifiche di rilievo](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funzionalità e markup

In questa sezione vengono descritte le funzionalità necessarie di frequente. Per vedere come funzionano, esaminare il codice sorgente della pagina.

1. Elenchi numerati
   1. Elenchi numerati annidati con almeno 3 spazi vuoti iniziali
   1. Il numero effettivo nel codice è irrilevante. l'analisi si occuperà di impostare il numero di elemento corretto.

- Elenchi puntati
  - Elenchi puntati annidati
- Testo in **grassetto con** \* \* doppio asterisco\*\*
- _testo in_ *corsivo* con \_ carattere di \_ sottolineatura o \* asterisco singolo\*
- Testo `highlighted as code` all'interno di una \` frase usando le virgolette\`
- Collegamenti alle pagine della documentazione [delle linee guida per la documentazione di MRTK](documentation-guide.md)
- Collegamenti agli [ancoraggi all'interno di una pagina](#style). Gli ancoraggi vengono formati sostituendo gli spazi con trattini e convertendo in lettere minuscole

Per gli esempi di codice si usano i blocchi con tre backtick e si specifica csharp come linguaggio per \` \` \` l'evidenziazione della sintassi: 

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Quando si cita il codice all'interno di una frase `use a single backtick` .

### <a name="todos"></a>Todos

Evitare l'uso di TODO nella documentazione, perché nel corso del tempo questi TODO (ad esempio toDO di codice) tendono ad accumularsi e informazioni su come devono essere aggiornati e perché si perdono.

Se è assolutamente necessario aggiungere un TODO, seguire questa procedura:

1. Creare un nuovo problema su Github che descrive il contesto alla base del TODO e fornire informazioni sufficienti che un altro collaboratore sarebbe in grado di comprendere e quindi risolvere il TODO.
2. Fare riferimento all'URL del problema nella todo nella documentazione.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Sezioni evidenziate

Per evidenziare punti specifici per il lettore, *> [!NOTE]* usare , e per produrre gli stili *> [!WARNING]* *> [!IMPORTANT]* seguenti. È consigliabile usare le note per i punti generali e i punti di avviso/importanti solo per casi speciali rilevanti.

> [!NOTE]
> Esempio di nota

> [!WARNING]
> Esempio di avviso

> [!IMPORTANT]
> Esempio di commento importante

## <a name="page-layout"></a>Layout di pagina

### <a name="introduction"></a>Introduzione

La parte subito dopo il titolo del capitolo principale deve fungere da breve introduzione sul capitolo. Non renderlo troppo lungo, ma aggiungere titoli secondari. Questi consentono di collegarsi alle sezioni e possono essere salvati come segnalibri.

### <a name="main-body"></a>Corpo principale

Usare titoli a due e tre livelli per strutturare il resto.

**Mini sezioni**

Usare una riga di testo in grassetto per i blocchi che devono distinguersi. È possibile sostituirlo con titoli a quattro livelli a un certo punto.

### <a name="see-also-section"></a>Sezione "Vedere anche"

La maggior parte delle pagine deve terminare con un capitolo *denominato Vedere anche*. Questo capitolo è semplicemente un elenco puntato a un elenco puntato di collegamenti a pagine correlate a questo argomento. Questi collegamenti possono anche essere visualizzati all'interno del testo della pagina, se appropriato, ma non è obbligatorio. Analogamente, il testo della pagina può contenere collegamenti a pagine non correlate all'argomento principale, che non devono essere incluse *nell'elenco* Vedere anche. Vedere [il capitolo "Vedere anche"](#see-also) di questa pagina come esempio per la scelta dei collegamenti.

## <a name="table-of-contents-toc"></a>Sommario

I file toc vengono usati per generare le barre di spostamento nella documentazione github.io MRTK.
Ogni volta che viene aggiunto un nuovo file di documentazione, assicurarsi che sia presente una voce per tale file in uno dei file toc.yml della cartella della documentazione. Solo gli articoli elencati nei file toc verranno visualizzati nel riquadro di spostamento della documentazione per sviluppatori. Può essere presente un file toc per ogni sottocartella nella cartella della documentazione che può essere collegata a qualsiasi file di sommario esistente per aggiungerlo come sottosezione alla parte corrispondente della navigazione.

## <a name="style"></a>Stile

### <a name="writing-style"></a>Stile di scrittura

Regola generale: provare a sembrare **professionale.** Questo significa in genere evitare un "tono di conversazione". Provare anche a evitare iperboli e sensazionalismi.

1. Non provare a essere (e troppo) divertente.
2. Non scrivere mai 'I'
3. Evitare "we". Questo può essere in genere riformiedato facilmente, usando invece "MRTK". Esempio: "questa funzionalità è supportata" -> "MRTK supporta questa funzionalità" o "sono supportate le funzionalità seguenti...".
4. Analogamente, provare a evitare 'you'. Esempio: "Con questa semplice modifica lo shader diventa configurabile!" -> "Gli shader possono essere resi configurabili con poco sforzo".
5. Non usare "frasi sloppy".
6. Evitare di sembrare troppo emozionati, non è necessario vendere nulla.
7. Analogamente, evitare di essere troppo drastici. I punti esclamativi sono raramente necessari.

### <a name="capitalization"></a>Uso delle maiuscole

- Usare **la distinzione tra maiuscole e minuscole per i titoli.** Ad esempio: in maiuscolo la prima lettera e i nomi, ma non altro.
- Usare l'inglese normale per tutto il resto. Ciò significa **che le parole arbitrarie non** vengono maiuscole, anche se contengono un significato speciale in tale contesto. Preferire *il testo in corsivo* per evidenziare determinate parole, vedere di [seguito](#emphasis-and-highlighting).
- Quando un collegamento viene incorporato in una frase (che è il metodo preferito), il nome del capitolo standard usa sempre lettere maiuscole, interrompendo così la regola di nessuna maiuscola arbitraria all'interno del testo. Usare quindi un nome di collegamento personalizzato per correggere le maiuscole e minuscole. Ad esempio, di seguito è riportato un collegamento alla documentazione [sul controllo bounds.](../features/ux-building-blocks/bounds-control.md)
- Non utilizzare le maiuscole per i nomi, ad *esempio Unity.*
- Non scrivere in maiuscolo "editor" durante la scrittura *dell'editor di Unity.*

### <a name="emphasis-and-highlighting"></a>Enfasi ed evidenziazione

Esistono due modi per evidenziare o evidenziare le parole, rendendole in grassetto o in corsivo. L'effetto del testo  in grassetto è che il testo in grassetto viene visualizzato in grassetto e quindi può essere notato facilmente durante lo scorrimento di una parte di testo o persino semplicemente lo scorrimento su una pagina. Il grassetto è ideale per evidenziare le frasi che gli utenti devono ricordare. Tuttavia, **usare raramente il testo in grassetto** perché in genere distrae.

Spesso si vuole "raggruppare" qualcosa che appartiene logicamente insieme o evidenziare un termine specifico, perché ha un significato speciale. Non è necessario che tali elementi si distinguono dal testo complessivo. Usare il testo in corsivo come *metodo leggero per* evidenziare qualcosa.

Analogamente, quando un nome file, un percorso o una voce di menu è indicato nel testo, preferisce renderlo corsivo per raggrupparlo in modo logico, senza distrarre.

In generale, provare a evitare **l'evidenziazione del testo non necessaria.** I termini speciali possono essere evidenziati una sola volta per rendere il lettore consapevole, non ripetere tale evidenziazione in tutto il testo, quando non serve più a scopo e distrae solo.

### <a name="mentioning-menu-entries"></a>Menzione delle voci di menu

Quando si fa riferimento a una voce di menu su cui un utente deve fare clic, la convenzione corrente è: Project > *File > Crea > Foglia*

### <a name="links"></a>Collegamenti

Inserire il maggior numero possibile di collegamenti utili ad altre pagine, ma ogni collegamento viene inserito una sola volta. Si supponga che un lettore fa clic su ogni collegamento nella pagina e pensi a quanto sarebbe fastidioso, se la stessa pagina si apre 20 volte.

Preferire i collegamenti incorporati in una frase:

- BAD: le linee guida sono utili. Per [informazioni dettagliate, vedere](../contributing/documentation-guide.md) questo capitolo.
- BUONA: [le linee guida](documentation-guide.md) sono utili.

Evitare collegamenti esterni, possono diventare obsoleti o contenere contenuti protetti da copyright.

Quando si aggiunge un collegamento, valutare se deve essere elencato anche nella [sezione](#see-also) Vedere anche. Analogamente, controllare se alla pagina collegata deve essere aggiunto un collegamento alla nuova pagina.

### <a name="images--screenshots"></a>Immagini/screenshot

**Usare gli screenshot con parsimonio.** La gestione delle immagini nella documentazione è molto lavoro, le piccole modifiche dell'interfaccia utente possono rendere obsoleti molti screenshot. Le regole seguenti ridurranno il lavoro di manutenzione:

1. Non usare screenshot per elementi che possono essere descritti in testo. In particolare, **non creare mai uno screenshot di una griglia** delle proprietà al solo scopo di visualizzare i nomi e i valori delle proprietà.
2. Non includere elementi in uno screenshot irrilevanti per ciò che viene visualizzato. Ad esempio, quando viene visualizzato un effetto di rendering, creare uno screenshot del viewport, ma escludere qualsiasi interfaccia utente che lo circonda. Mostrando un'interfaccia utente, provare a spostare le finestre in modo che nell'immagine sia presente solo la parte importante.
3. Quando si include l'interfaccia utente dello screenshot, visualizzare solo le parti importanti. Ad esempio, quando si parla di pulsanti in una barra degli strumenti, creare una piccola immagine che mostra i pulsanti importanti della barra degli strumenti, ma esclude tutto ciò che la circonda.
4. Usare solo immagini facili da riprodurre. Ciò significa che non disegnare marcatori o evidenziazioni negli screenshot. In primo luogo, non esistono regole coerenti come dovrebbero apparire, comunque. In secondo momento, riprodurre uno screenshot di questo tipo è un lavoro aggiuntivo. Descrivere invece le parti importanti nel testo. Esistono eccezioni a questa regola, ma sono rare.
5. Ovviamente, è molto più necessario ricreare una GIF animata. Si prevede di essere responsabili di ricrearlo fino alla fine del tempo o di aspettarsi che le persone lo buttino fuori, se non vogliono dedicare questo tempo.
6. Mantenere basso il numero di immagini in un articolo. Spesso un buon metodo è quello di creare uno screenshot complessivo di uno strumento, che mostra tutto e quindi descrivere il resto in testo. In questo modo è facile sostituire lo screenshot quando necessario.

Altri aspetti:

- L'interfaccia utente dell'editor per gli screenshot deve usare l'editor del tema grigio chiaro perché non tutti gli utenti hanno accesso al tema scuro e si desidera mantenere le cose il più coerenti possibile.
- La larghezza predefinita dell'immagine è di 500 pixel, perché viene visualizzata bene nella maggior parte dei monitor. Provare a non deviare troppo da esso. La larghezza massima deve essere di 800 pixel.
- Usare i PNG per gli screenshot dell'interfaccia utente.
- Usare PNG o JPG per gli screenshot del viewport 3D. Preferisce la qualità rispetto al rapporto di compressione.

### <a name="list-of-component-properties"></a>Elenco delle proprietà del componente

Quando si documenta un elenco di proprietà, usare il testo in grassetto per evidenziare il nome della proprietà, quindi le interruzioni di riga e il testo normale per descriverle. Non usare sottosezioni o elenchi puntati.

Inoltre, non dimenticare di completare tutte le frasi con un punto.

## <a name="page-completion-checklist"></a>Elenco di controllo per il completamento della pagina

1. Assicurarsi che siano state seguite le linee guida di questo documento.
1. Esplorare la struttura del documento e verificare se il nuovo documento può essere menzionato nella [sezione Vedere](#see-also) anche di altre pagine.
1. Se disponibile, fare in modo che qualcuno con conoscenza dell'argomento abbia letto la pagina per la correttezza tecnica.
1. Fare in modo che qualcuno eseere in grado di leggere la pagina per lo stile e la formattazione. Può trattarsi di un utente che non ha familiarità con l'argomento, che è anche una buona idea per ottenere commenti e suggerimenti su quanto sia comprensibile la documentazione.

## <a name="source-documentation"></a>Documentazione di origine

La documentazione dell'API verrà generata automaticamente dai file di origine MRTK. Per semplificare questa operazione, i file di origine devono contenere quanto segue:

- [Blocchi di riepilogo di classe, struct e enumerazione](#class-struct-enum-summary-blocks)
- [Blocchi di riepilogo di proprietà, metodi e eventi](#property-method-event-summary-blocks)
- [Versione e dipendenze dell'introduzione alle funzionalità](#feature-introduction-version-and-dependencies)
- [Campi serializzati](#serialized-fields)
- [Valori di enumerazione](#enumeration-values)

Oltre a quanto sopra, il codice deve essere commentato in modo da consentire la manutenzione, le correzioni di bug e la facilità di personalizzazione.

### <a name="class-struct-enum-summary-blocks"></a>Blocchi di riepilogo di classe, struct e enumerazione

Se una classe, uno struct o un'enumerazione viene aggiunto a MRTK, è necessario descriverne lo scopo. Questa operazione deve assumere la forma di un blocco di riepilogo sopra la classe .

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Se sono presenti dipendenze a livello di classe, devono essere documentate in un blocco di osservazioni, immediatamente sotto il riepilogo.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Le richieste pull inviate senza riepiloghi per classi, strutture o enumerazioni non verranno approvate.

### <a name="property-method-event-summary-blocks"></a>Blocchi di riepilogo di proprietà, metodi e eventi

Proprietà, metodi ed eventi (PME) e campi devono essere documentati con blocchi di riepilogo, indipendentemente dalla visibilità del codice (pubblico, privato, protetto e interno). Lo strumento di generazione della documentazione è responsabile del filtraggio e della pubblicazione solo delle funzionalità pubbliche e protette.

NOTA: non è necessario un blocco **di** riepilogo per i metodi Unity (ad esempio, Awake, Start, Update).

La documentazione di PME **è necessaria** per l'approvazione di una richiesta pull.

Come parte di un blocco di riepilogo PME, sono necessari il significato e lo scopo dei parametri e dei dati restituiti.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Versione e dipendenze dell'introduzione alle funzionalità

Come parte della documentazione di riepilogo dell'API, le informazioni relative alla versione di MRTK in cui è stata introdotta la funzionalità e le eventuali dipendenze devono essere documentate in un blocco di osservazioni.

Le dipendenze devono includere dipendenze di estensione e/o piattaforma.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Campi serializzati

È consigliabile usare l'attributo della descrizione comando di Unity per fornire la documentazione di runtime per i campi di uno script nel controllo.

In modo che le opzioni di configurazione siano incluse nella documentazione dell'API, gli script devono *includere* almeno il contenuto della descrizione comando in un blocco di riepilogo.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valori di enumerazione

Durante la definizione e l'enumerazione, il codice deve anche documentare il significato dei valori di enumerazione usando un blocco di riepilogo. I blocchi note possono essere usati facoltativamente per fornire dettagli aggiuntivi per migliorare la comprensione.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentazione dettagliata

Molti utenti di Mixed Reality Toolkit potrebbe non dover usare la documentazione dell'API. Questi utenti sfufruiranno dei prefab e degli script predefiniti e riutilizzabili per creare le proprie esperienze.

Ogni area di funzionalità conterrà uno o più file markdown (md) che descrivono a un livello piuttosto elevato, ciò che viene fornito. A seconda delle dimensioni e/o della complessità di una determinata area di funzionalità, potrebbe essere necessario disporre di file aggiuntivi, fino a uno per ogni funzionalità fornita.

Quando viene aggiunta una funzionalità o viene modificato l'utilizzo, è necessario fornire la documentazione di panoramica.

Come parte di questa documentazione, è necessario fornire sezioni di procedura, incluse le illustrazioni, per assistere i clienti che non hanno una funzionalità o un concetto per iniziare.

## <a name="design-documentation"></a>Documentazione di progettazione

La realtà mista offre l'opportunità di creare mondi completamente nuovi. Parte di questa operazione potrebbe comportare la creazione di asset personalizzati da usare con MRTK. Per rendere il più possibile privo di problemi per i clienti, i componenti devono fornire la documentazione di progettazione che descrive qualsiasi formattazione o altri requisiti per gli asset di grafica.

Alcuni esempi in cui la documentazione di progettazione può essere utile:

- Modelli di cursore
- Visualizzazioni di mapping spaziale
- File di effetti sonori

Questo tipo di documentazione è **fortemente consigliato** e **può** essere richiesto come parte di una revisione della richiesta pull.

Questo potrebbe essere o meno diverso dalla raccomandazione di progettazione nel sito [ms developer](https://docs.microsoft.com/windows/mixed-reality/design)

## <a name="performance-notes"></a>Note sulle prestazioni

Alcune funzionalità importanti hanno un costo per le prestazioni. Spesso questo codice dipende molto dalla modalità di configurazione.

Ad esempio:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Le note sulle prestazioni sono consigliate per i componenti con utilizzo elevato di CPU e/o GPU e possono **essere** richieste come parte di una revisione della richiesta pull. Eventuali note sulle prestazioni applicabili devono essere incluse nella documentazione dell'API **e** della panoramica.

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

La documentazione sulle modifiche che causano un'interruzione è costituita da un [file](../contributing/breaking-changes.md) di primo livello che si collega alle singole aree di breaking-changes.md.

L'area breaking-changes.md file deve contenere l'elenco di tutte le  modifiche di rilievo note per una determinata versione, nonché la cronologia delle modifiche di rilievo rispetto alle versioni precedenti.

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

Le informazioni contenute nel livello di funzionalità breaking-changes.md file verranno aggregate alle note sulla versione per ogni nuova versione di MRTK.

Tutte le modifiche di rilievo che fanno parte di una modifica **devono** essere documentate come parte di una richiesta pull.

## <a name="tools-for-editing-markdown"></a>Strumenti per la modifica di MarkDown

[Visual Studio Code](https://code.visualstudio.com/) è un ottimo strumento per la modifica di file markdown che fanno parte della documentazione di MRTK.

Quando si scrive la documentazione, è consigliabile installare anche le due estensioni seguenti:

- Estensione Docs Markdown per Visual Studio Code: usare ALT+M per visualizzare un menu di opzioni di creazione di documenti.

- Controllo ortografico del codice: le parole con errori di ortografia verranno sottolineate; Fare clic con il pulsante destro del mouse su una parola con errori di ortografia per modificarla o salvarla nel dizionario.

Entrambi i pacchetti sono in pacchetto in Docs Authoring Pack pubblicato da Microsoft.

## <a name="see-also"></a>Vedi anche

- [Guida alla generazione del portale della documentazione](../contributing/dev-doc-guide.md)
