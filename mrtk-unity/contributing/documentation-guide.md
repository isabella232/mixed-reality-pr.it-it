---
title: Guida alla documentazione
description: linee guida e standard della documentazione per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121389"
---
# <a name="documentation-guidelines"></a>Linee guida per la documentazione

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

Questo documento illustra le linee guida e gli standard della documentazione per Mixed Reality Toolkit (MRTK). Viene fornita un'introduzione agli aspetti tecnici della scrittura e della generazione della documentazione, per evidenziare le insidie comuni e per descrivere lo stile di scrittura consigliato.

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
   1. Il numero effettivo nel codice è irrilevante. L'analisi si occuperà di impostare il numero di elemento corretto.

- Elenchi puntati
  - Elenchi di punti elenco annidati
- Testo in **grassetto con** doppio \* \* asterisco\*\*
- _testo in_ *corsivo* con carattere \_ di \_ sottolineatura o \* asterisco singolo\*
- Testo `highlighted as code` all'interno di una \` frase usando le virgolette\`
- Collegamenti alle pagine della documentazione linee [guida per la documentazione di MRTK](documentation-guide.md)
- Collegamenti agli [ancoraggi all'interno di una pagina;](#style) Gli ancoraggi vengono formati sostituendo gli spazi con trattini e convertendo in minuscolo

Per gli esempi di codice si usano i blocchi con tre puntini di secondo e si specifica csharp come linguaggio per \` \` \` l'evidenziazione della sintassi: 

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Quando si cita il codice all'interno di una frase `use a single backtick` .

### <a name="todos"></a>Todos

Evitare di usare gli oggetti TODO nella documentazione, perché nel corso del tempo questi todo (ad esempio gli elementi TOTOD del codice) tendono ad accumularsi e a ottenere informazioni su come devono essere aggiornati e perché andare persi.

Se è assolutamente necessario aggiungere un todo, seguire questa procedura:

1. Descrizione del contesto alla base del TODO in GitHub e informazioni di base sufficienti per consentire a un altro collaboratore di comprendere e quindi risolvere il problema.
2. Fare riferimento all'URL del problema nella todo nella documentazione.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Sezioni evidenziate

Per evidenziare punti specifici del lettore, usare *> [!NOTE]* , e per produrre gli stili *> [!WARNING]* *> [!IMPORTANT]* seguenti. È consigliabile usare le note per i punti generali e i punti di avviso/importanti solo per casi speciali rilevanti.

> [!NOTE]
> Esempio di nota

> [!WARNING]
> Esempio di avviso

> [!IMPORTANT]
> Esempio di commento importante

## <a name="page-layout"></a>Layout di pagina

### <a name="introduction"></a>Introduzione

La parte subito dopo il titolo del capitolo principale deve essere una breve introduzione sul capitolo. Non rendere questa operazione troppo lunga, ma aggiungere titoli secondari. Questi consentono di collegarsi alle sezioni e possono essere salvati come segnalibri.

### <a name="main-body"></a>Corpo principale

Usare titoli a due e tre livelli per strutturare il resto.

**Mini sezioni**

Usare una riga di testo in grassetto per i blocchi che devono distinguersi. Questo potrebbe essere sostituito da titoli in quattro livelli a un certo punto.

### <a name="see-also-section"></a>Sezione "Vedere anche"

La maggior parte delle pagine deve terminare con un capitolo denominato *Vedere anche*. Questo capitolo è semplicemente un elenco puntato di collegamenti a pagine correlate a questo argomento. Questi collegamenti possono anche essere visualizzati all'interno del testo della pagina, dove appropriato, ma questa operazione non è necessaria. Analogamente, il testo della pagina può contenere collegamenti a pagine non correlate all'argomento principale, che non devono essere incluse nell'elenco *Vedere* anche. Vedere [il capitolo "Vedere anche"](#see-also) di questa pagina come esempio per la scelta dei collegamenti.

## <a name="table-of-contents-toc"></a>Sommario

I file toc vengono usati per generare le barre di spostamento nella documentazione github.io MRTK.
Ogni volta che viene aggiunto un nuovo file di documentazione, assicurarsi che sia presente una voce per tale file in uno dei file toc.yml della cartella della documentazione. Solo gli articoli elencati nei file di sommario verranno visualizzati nella navigazione della documentazione per sviluppatori. Può essere presente un file di sommario per ogni sottocartella nella cartella della documentazione che può essere collegato a qualsiasi file di sommario esistente per aggiungerlo come sottosezione alla parte corrispondente della navigazione.

## <a name="style"></a>Stile

### <a name="writing-style"></a>Stile di scrittura

Regola generale: provare a sembrare **professionale.** Ciò significa in genere evitare un "tono colloquiale". Provare anche a evitare iperboli e emozionanti.

1. Non tentare di essere (e troppo) insoddrò.
2. Non scrivere mai 'I'
3. Evitare "we". Questa operazione può essere in genere riformiedata facilmente, usando invece "MRTK". Esempio: "questa funzionalità è supportata" -> "MRTK supporta questa funzionalità" o "le funzionalità seguenti sono supportate...".
4. Analogamente, provare a evitare "you". Esempio: "Con questa semplice modifica lo shader diventa configurabile!" -> "Gli shader possono essere resi configurabili con un minimo sforzo".
5. Non usare "frasi sloppy".
6. Evitare di sembrare emozionati e non è necessario vendere nulla.
7. Allo stesso modo, evitare di essere troppo erre. I punti esclamativi sono raramente necessari.

### <a name="capitalization"></a>Uso delle maiuscole

- Usare **la distinzione tra maiuscole e minuscole per i titoli**. Ad esempio: in maiuscolo la prima lettera e i nomi, ma non altro.
- Usare l'inglese normale per tutti gli altri elementi. Ciò significa **che le parole arbitrarie non vengono** maiuscole, anche se contengono un significato speciale in tale contesto. Preferire *il testo in corsivo* per l'evidenziazione di determinate parole, vedere di [seguito.](#emphasis-and-highlighting)
- Quando un collegamento è incorporato in una frase (che è il metodo preferito), il nome del capitolo standard usa sempre lettere maiuscole, interrompendo così la regola dell'assenza di maiuscole/minuscole arbitrarie all'interno del testo. Usare quindi un nome di collegamento personalizzato per correggere l'uso di maiuscole e minuscole. Di seguito è riportato, ad esempio, un collegamento alla documentazione [relativa al controllo dei](../features/ux-building-blocks/bounds-control.md) limiti.
- Non convertire in lettere maiuscole i nomi, ad *esempio Unity.*
- NON scrivere in maiuscolo l'"editor" quando si scrive *l'editor di Unity.*

### <a name="emphasis-and-highlighting"></a>Enfasi ed evidenziazione

Esistono due modi per evidenziare o evidenziare le parole, rendendole in grassetto o corsivo. L'effetto del testo  in grassetto è che il testo in grassetto viene visualizzato e pertanto può essere facilmente notato durante lo scorrimento di una parte di testo o anche semplicemente lo scorrimento su una pagina. Il grassetto è ideale per evidenziare le frasi che gli utenti devono ricordare. Tuttavia, **usare raramente il testo in grassetto** perché in genere è distrazione.

Spesso si vuole "raggruppare" un elemento che appartiene logicamente o evidenziare un termine specifico, perché ha un significato speciale. Non è necessario che tali elementi si distinguono dal testo complessivo. Usare il testo in corsivo *come metodo leggero per* evidenziare un elemento.

Analogamente, quando un nome file, un percorso o una voce di menu viene menzionato nel testo, preferisce renderlo corsivo per raggrupparlo in modo logico, senza distrarlo.

In generale, provare a evitare **l'evidenziazione del testo non necessaria.** I termini speciali possono essere evidenziati una sola volta per rendere il lettore consapevole, non ripetere tale evidenziazione in tutto il testo, quando non serve più a nessuno scopo e si distrae solo.

### <a name="mentioning-menu-entries"></a>Menzione delle voci di menu

Quando si cita una voce di menu su cui un utente deve fare clic, la convenzione corrente è: *Project > Files > Create > Leaf*

### <a name="links"></a>Collegamenti

Inserire il maggior numero possibile di collegamenti utili ad altre pagine, ma ogni collegamento viene inserito una sola volta. Si supponga che un lettore fa clic su ogni collegamento nella pagina e pensi a quanto sarebbe fastidioso, se la stessa pagina si apre 20 volte.

Preferisce collegamenti incorporati in una frase:

- BAD: le linee guida sono utili. Per [informazioni dettagliate,](../contributing/documentation-guide.md) vedere questo capitolo.
- BUONA: [le linee guida](documentation-guide.md) sono utili.

Evitare collegamenti esterni, che possono diventare obsoleti o contenere contenuti protetti da copyright.

Quando si aggiunge un collegamento, valutare se deve essere elencato anche nella [sezione Vedere](#see-also) anche. Analogamente, controllare se è necessario aggiungere un collegamento alla nuova pagina alla pagina collegata.

### <a name="images--screenshots"></a>Immagini/screenshot

**Usare gli screenshot con moderamento.** La gestione delle immagini nella documentazione è molto lavoro, le piccole modifiche all'interfaccia utente possono rendere obsoleti molti screenshot. Le regole seguenti ridurranno le attività di manutenzione:

1. Non usare screenshot per elementi che possono essere descritti in testo. In particolare, **non creare mai screenshot di una griglia delle** proprietà al solo scopo di visualizzare i nomi e i valori delle proprietà.
2. Non includere elementi in uno screenshot irrilevanti per quanto visualizzato. Ad esempio, quando viene visualizzato un effetto di rendering, creare uno screenshot del viewport, ma escludere qualsiasi interfaccia utente che lo circonda. Mostrando un'interfaccia utente, provare a spostare le finestre in modo che solo la parte importante sia presente nell'immagine.
3. Quando si include l'interfaccia utente dello screenshot, vengono mostrate solo le parti importanti. Ad esempio, quando si parla di pulsanti in una barra degli strumenti, creare una piccola immagine che mostra i pulsanti importanti della barra degli strumenti, ma escludere tutto ciò che la circonda.
4. Usare solo immagini facili da riprodurre. Ciò significa che non disegnare marcatori o evidenziazioni negli screenshot. In primo luogo, non esistono regole coerenti sull'aspetto che dovrebbero avere. In secondo momento, riprodurre uno screenshot di questo tipo è un'attività aggiuntiva. Descrivere invece le parti importanti del testo. Esistono eccezioni a questa regola, ma sono rare.
5. Ovviamente, è molto più necessario ricreare un'immagine GIF animata. Si prevede di essere responsabile di ricrearla fino alla fine del tempo o di aspettarsi che gli utenti lo scartino, se non vogliono dedicare tale tempo.
6. Mantenere basso il numero di immagini in un articolo. Spesso un metodo efficace è creare uno screenshot complessivo di uno strumento, che mostra tutti gli elementi e quindi descrivere il resto nel testo. In questo modo è facile sostituire lo screenshot quando necessario.

Altri aspetti:

- L'interfaccia utente dell'editor per gli screenshot deve usare l'editor del tema grigio chiaro perché non tutti gli utenti hanno accesso al tema scuro e si desidera mantenere gli elementi il più coerenti possibile.
- La larghezza predefinita dell'immagine è 500 pixel, perché viene visualizzata bene nella maggior parte dei monitor. Provare a non deviare troppo da esso. La larghezza massima deve essere di 800 pixel.
- Usare i PNG per gli screenshot dell'interfaccia utente.
- Usare PNG o JPG per gli screenshot del viewport 3D. Preferisce la qualità rispetto al rapporto di compressione.

### <a name="list-of-component-properties"></a>Elenco delle proprietà del componente

Quando si documenta un elenco di proprietà, usare il testo in grassetto per evidenziare il nome della proprietà, quindi le interruzioni di riga e il testo normale per descriverle. Non usare sottosezioni o elenchi puntati.

Non dimenticare inoltre di completare tutte le frasi con un punto.

## <a name="page-completion-checklist"></a>Elenco di controllo per il completamento della pagina

1. Assicurarsi che siano state seguite le linee guida di questo documento.
1. Esplorare la struttura del documento e verificare se il nuovo documento può essere menzionato nella [sezione](#see-also) Vedere anche di altre pagine.
1. Se disponibile, fare in modo che qualcuno con conoscenza dell'argomento leggi la pagina per la correttezza tecnica.
1. Fare in modo che qualcuno letta la prova della pagina per lo stile e la formattazione. Può trattarsi di una persona che non ha familiarità con l'argomento, che è anche una buona idea per ottenere commenti e suggerimenti su quanto sia comprensibile la documentazione.

## <a name="source-documentation"></a>Documentazione di origine

La documentazione dell'API verrà generata automaticamente dai file di origine di MRTK. Per semplificare questa operazione, i file di origine devono contenere quanto segue:

- [Blocchi di riepilogo di classi, struct e enumerazioni](#class-struct-enum-summary-blocks)
- [Blocchi di riepilogo di proprietà, metodi e eventi](#property-method-event-summary-blocks)
- [Versione e dipendenze dell'introduzione alle funzionalità](#feature-introduction-version-and-dependencies)
- [Campi serializzati](#serialized-fields)
- [Valori di enumerazione](#enumeration-values)

Oltre a quanto sopra, il codice deve essere ben commentato per consentire la manutenzione, le correzioni di bug e la facilità di personalizzazione.

### <a name="class-struct-enum-summary-blocks"></a>Blocchi di riepilogo di classi, struct e enumerazioni

Se una classe, uno struct o un'enumerazione viene aggiunto a MRTK, è necessario descriverne lo scopo. Questa operazione deve assumere la forma di un blocco di riepilogo sopra la classe .

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Se sono presenti dipendenze a livello di classe, devono essere documentate in un blocco note, immediatamente sotto il riepilogo.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Le richieste pull inviate senza riepiloghi per classi, strutture o enumerazioni non verranno approvate.

### <a name="property-method-event-summary-blocks"></a>Blocchi di riepilogo di proprietà, metodi e eventi

Le proprietà, i metodi e gli eventi (PME) e i campi devono essere documentati con blocchi di riepilogo, indipendentemente dalla visibilità del codice (pubblica, privata, protetta e interna). Lo strumento di generazione della documentazione è responsabile dell'applicazione di filtri e della pubblicazione solo delle funzionalità pubbliche e protette.

NOTA: non è necessario un blocco **di** riepilogo per i metodi Unity (ad esempio: Attivo, Avvia, Aggiorna).

La documentazione pmE è **necessaria** per l'approvazione di una richiesta pull.

Come parte di un blocco di riepilogo PME, sono necessari il significato e lo scopo dei parametri e dei dati restituiti.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Versione e dipendenze dell'introduzione alle funzionalità

Come parte della documentazione di riepilogo dell'API, le informazioni relative alla versione di MRTK in cui è stata introdotta la funzionalità ed eventuali dipendenze devono essere documentate in un blocco note.

Le dipendenze devono includere le dipendenze di estensione e/o piattaforma.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Campi serializzati

È consigliabile usare l'attributo tooltip di Unity per fornire la documentazione di runtime per i campi di uno script nel controllo.

In modo che le opzioni di configurazione siano  incluse nella documentazione dell'API, gli script devono includere almeno il contenuto della descrizione comando in un blocco di riepilogo.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valori di enumerazione

Durante la definizione e l'enumerazione, il codice deve documentare anche il significato dei valori di enumerazione usando un blocco di riepilogo. Facoltativamente, i blocchi note possono essere usati per fornire dettagli aggiuntivi per migliorare la comprensione.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentazione delle procedura

Molti utenti di Mixed Reality Toolkit potrebbero non dover usare la documentazione dell'API. Questi utenti sfufruiranno dei prefab e degli script predefiniti e riutilizzabili per creare le proprie esperienze.

Ogni area di funzionalità conterrà uno o più file markdown (md) che descrivono a un livello piuttosto elevato, ciò che viene fornito. A seconda delle dimensioni e/o della complessità di una determinata area di funzionalità, potrebbe essere necessario disporre di file aggiuntivi, fino a uno per ogni funzionalità fornita.

Quando viene aggiunta una funzionalità (o viene modificato l'utilizzo), è necessario fornire la documentazione di panoramica.

Come parte di questa documentazione, è consigliabile includere sezioni di procedura, incluse le illustrazioni, per assistere i clienti che non hanno mai iniziato a usare una funzionalità o un concetto.

## <a name="design-documentation"></a>Documentazione di progettazione

La realtà mista offre l'opportunità di creare ambienti completamente nuovi. Parte di questo processo implica probabilmente la creazione di asset personalizzati da usare con MRTK. Per rendere questa operazione il più possibile gratuita per i clienti, i componenti devono fornire la documentazione di progettazione che descrive qualsiasi formattazione o altri requisiti per gli asset di grafica.

Alcuni esempi in cui la documentazione di progettazione può essere utile:

- Modelli di cursore
- Visualizzazioni di mapping spaziale
- File dell'effetto sonoro

Questo tipo di documentazione è **fortemente** consigliato **e** può essere richiesto come parte di una revisione della richiesta pull.

Questo può essere diverso o meno dalla raccomandazione di progettazione nel [sito ms developer](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Note sulle prestazioni

Alcune funzionalità importanti hanno un costo in termini di prestazioni. Spesso questo codice dipende molto dalla modalità di configurazione.

Ad esempio:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Le note sulle prestazioni sono consigliate per i componenti con utilizzo elevato della CPU e/o della GPU e possono **essere** richieste come parte di una revisione della richiesta pull. Eventuali note sulle prestazioni applicabili devono essere incluse nella documentazione di API **e** panoramica.

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

La documentazione relativa alle modifiche di rilievo è costituita da un [file](../contributing/breaking-changes.md) di primo livello che si collega alle singole aree di funzionalità breaking-changes.md.

L'area breaking-changes.md file devono contenere l'elenco di tutte le  modifiche di rilievo note per una determinata versione, nonché la cronologia delle modifiche di rilievo rispetto alle versioni precedenti.

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

Le informazioni contenute nel livello di breaking-changes.md file verranno aggregate alle note sulla versione per ogni nuova versione di MRTK.

Tutte le modifiche di rilievo che fanno parte di una modifica **devono** essere documentate come parte di una richiesta pull.

## <a name="tools-for-editing-markdown"></a>Strumenti per la modifica di MarkDown

[Visual Studio Code](https://code.visualstudio.com/) è un ottimo strumento per la modifica dei file markdown che fanno parte della documentazione di MRTK.

Quando si scrive la documentazione, è consigliabile installare anche le due estensioni seguenti:

- Estensione Docs Markdown per Visual Studio Code: usare ALT+M per visualizzare un menu di opzioni di creazione della documentazione.

- Controllo ortografico del codice: le parole con errori di ortografia verranno sottolineate. Fare clic con il pulsante destro del mouse su una parola con errori di ortografia per modificarla o salvarla nel dizionario.

Entrambi i pacchetti sono in pacchetto in Docs Authoring Pack pubblicato da Microsoft.

## <a name="see-also"></a>Vedere anche 

* [Collegamento di esempio](https://www.google.com)