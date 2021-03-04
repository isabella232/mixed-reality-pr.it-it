---
title: DevDocGuide
description: Portale per sviluppatori gudie per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, GitHub
ms.openlocfilehash: 29956570e88b6bfbdcc06721bfd2cf9e43769c17
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782945"
---
# <a name="developer-portal-generation-guide"></a>Guida alla generazione del portale per sviluppatori

MRTK USA [docfx](https://dotnet.github.io/docfx/index.html) per generare la documentazione HTML dai commenti a barra tripla nei file di codice e MD nel repository MRTK. La generazione della documentazione di Docfx viene attivata automaticamente da CI nelle richieste pull completate nel ramo mrtk_development.
Lo stato corrente della documentazione per gli sviluppatori è disponibile nella [pagina MRTK github.io](https://microsoft.github.io/MixedRealityToolkit-Unity/)

Docfx supporta DFM Docfx Flavored Markdown, che include GFM GitHub Flavored Markdown. La documentazione completa e l'elenco delle funzionalità sono disponibili [qui](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)

Docfx non solo converte ma controlla anche tutti i collegamenti locali usati nella documentazione. Se non è possibile risolvere un percorso, non verrà convertito nell'equivalente HTML. Per questo è importante usare i percorsi relativi solo quando si fa riferimento ad altri file locali.

## <a name="building-docfx-locally"></a>Compilazione di docfx localmente

I file di compilazione docfx nel repository MRTK possono essere usati per creare una versione locale della documentazione per gli sviluppatori in una sottocartella/documento nella radice del progetto.

### <a name="setup"></a>Configurazione

* ottenere la versione più recente di [docfx](https://dotnet.github.io/docfx/index.html)
* estrarre i file in una cartella del computer
* aggiungere la cartella al percorso nelle variabili di ambiente

### <a name="generation"></a>Generation

* aprire un prompt di PowerShell o cmd nella radice del progetto MRTK
* Execute `docfx docfx.json` (facoltativamente con l'opzione-f per forzare una ricompilazione dei file doc)
* Execute `docfx serve doc` (facoltativamente con-p *NumeroPorta* se non si vuole usare la porta predefinita 8888)
* aprire un Web browser con localhost:*NumeroPorta*

Si noti che durante l'esecuzione del comando docfx nel file di compilazione JSON docfx visualizzerà eventuali collegamenti interrotti nella documentazione come avviso.
Assicurarsi che ogni volta che si apportano modifiche ai file di documentazione o all'API per aggiornare tutti i collegamenti che puntano a questi articoli o codice.

## <a name="verifying-docfx-on-github"></a>Verifica di docfx su GitHub

Ogni volta che una richiesta pull include una modifica che potrebbe influire sulla documentazione CI deve essere eseguita per eseguire un controllo in docfx per i collegamenti interrotti. Questa operazione può essere attivata inviando il comando `/azp run mrtk_docs` nella richiesta pull se l'utente dispone di diritti sufficienti a tale scopo. Il comando attiverà un processo CI che consente di aggiungere una compilazione di docs alla sezione dei controlli della richiesta pull.

## <a name="using-crefs-and-hrefs-in--documented-code"></a>Uso di cRefs e hrefs in///codice documentato

Docfx supporta cRefs nel codice documentato///. Questi riferimenti verranno tradotti nei collegamenti che puntano alla documentazione dell'API generata o ai siti Web della documentazione esterna.
È possibile aggiungere i servizi External xrif per la risoluzione dei collegamenti a librerie/API esterne al docfx.jsnel file di impostazioni di compilazione nella proprietà *xrefService*.

Per le API esterne che non forniscono un href del servizio dell'xrif al sito Web della documentazione, è possibile aggiungere ai commenti.

Esempi:

```c#
/// Links to MRTK internal class SystemType
/// <see cref="Microsoft.MixedReality.Toolkit.Utilities.SystemType"/>

/// Links to external API - link provided by xref service
/// <see cref="System.Collections.Generic.ICollection{Type}.Contains"/>

/// Links to Unity web API reference
/// <see href="https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyField.html">EditorGUI.PropertyField</see>
```

## <a name="linking-in-md-documentation-files"></a>Collegamento in file di documentazione. MD

Docfx sta traducendo e convalidando tutti i collegamenti locali relativi alla generazione, non è necessaria alcuna sintassi speciale. Per fare riferimento a un altro articolo della documentazione, è necessario fare riferimento al file. MD corrispondente, mai al file HTML generato automaticamente. Si noti che tutti i collegamenti ai file locali devono essere relativi al file che si sta modificando.

Il collegamento alla documentazione dell'API può essere eseguito usando [riferimenti incrociati](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html). Docfx ha generato automaticamente gli UID per tutti i documenti dell'API facendo la firma.

Esempio:

Questo collegamento all' [API BoundarySystem](xref:Microsoft.MixedReality.Toolkit.Boundary) , oltre a questa breve versione: @Microsoft.MixedReality.Toolkit.Boundary

```md
This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary)
as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary
```

## <a name="enumerating-available-xrefs"></a>Enumerazione degli xrif disponibili

La sintassi dell'xrif può essere difficile da ricordare: è possibile enumerare tutti gli ID di riferimento di riferimento disponibili eseguendo prima docfx localmente:

> docfx docfx.json

Verrà generato un file xrefmap. yml, disponibile in docs/xrefmap. yml.

Ad esempio, per collegare l'overload seguente di HandleEvent, la sintassi è piuttosto Arcale:

```yml
- uid: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name: HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  href: api/Microsoft.MixedReality.Toolkit.BaseEventSystem.html#Microsoft_MixedReality_Toolkit_BaseEventSystem_HandleEvent__1_BaseEventData_ExecuteEvents_EventFunction___0__
  commentId: M:Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name.vb: HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  fullName: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  fullName.vb: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  nameWithType: BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  nameWithType.vb: BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
```

Tuttavia, è facile cercare il nome e quindi usare l'intero **campo uid** come xrif.

In questo esempio, l'xrif avrà un aspetto simile al seguente: (xrif: Microsoft. MixedReality. Toolkit. BaseEventSystem. HandleEvent ``1(BaseEventData,ExecuteEvents.EventFunction{`` 0}))

## <a name="adding-new-md-files-to-developer-docs"></a>Aggiunta di nuovi file. MD alla documentazione per sviluppatori

Docfx rileverà tutti i file. MD in cartelle che vengono aggiunte come file di contenuto nella sezione build del docfx.jsin e generano file HTML. Per le nuove cartelle è necessario aggiungere una voce corrispondente nel file di compilazione.

### <a name="navigation-entries"></a>Voci di navigazione

Per determinare le voci della navigazione nella documentazione per sviluppatori docfx USA TOC. yml/TOC. MD-Table of content files.
Il file TOC nella radice del progetto definisce le voci nella barra di spostamento superiore mentre i file TOC. yml nelle sottocartelle del repository definiscono gli argomenti secondari nell'esplorazione della barra laterale.
i file TOC. yml possono essere usati per la strutturazione ed è possibile che siano presenti quantità di tali file. Per altre informazioni sulla definizione delle voci per TOC. yml, vedere la [voce della documentazione di docfx in sommario](https://dotnet.github.io/docfx/tutorial/intro_toc.html).

## <a name="resource-files"></a>File di risorse

Sono disponibili alcuni file, ad esempio immagini, video o file PDF a cui la documentazione può fare riferimento ma che non sono stati convertiti da docfx. Per questi file è presente una sezione relativa alle risorse nell'docfx.js. I file in tale sezione verranno copiati solo senza eseguire alcuna conversione su di essi.

Attualmente esiste una definizione per i tipi di risorse seguenti:

| ResourceType | Percorso |
| --- | --- |
| Immagini | Documentazione/immagini/ |

## <a name="releasing-a-new-version"></a>Rilascio di una nuova versione

Sono supportate più versioni dei documenti per sviluppatori e possono essere disattivate dall'elenco a discesa versione nella barra dei menu superiore. Se si sta rilasciando una nuova versione, seguire questa procedura per avere la versione nella pagina dei documenti per sviluppatori.

1. Facoltativo: modifica della docfx.js  
A seconda se si vuole che il "miglioramento di questo documento" in modo che punti a una versione specifica del repository GitHub, sarà necessario aggiungere la voce seguente alla sezione globalMetaData nel file docfx.jssu prima di chiamare il comando docfx:

    ```json
    "_gitContribute": {
        "repo": "https://github.com/Microsoft/MixedRealityToolkit-Unity.git",
        "branch": "mrtk_development"
    }
    ```

    Se non si configura questa impostazione, docfx utilizzerà per impostazione predefinita il ramo e il repository della cartella corrente da cui si sta chiamando docfx.

1. Creare la documentazione di docfx chiamando docfx docfx.json nella radice del repository
1. Creare una cartella con il nome della versione nella cartella Version del ramo GH-Pages e copiare il contenuto della cartella doc generata in tale cartella.
1. Aggiungere il numero di versione in versionArray in Web/version.js
1. Eseguire il push del version.js modificato per mrtk_development ramo e le modifiche nel ramo GH-Pages

CI rileverà le modifiche apportate al file di version.js e aggiornerà automaticamente l'elenco a discesa della versione.

### <a name="supporting-development-branches-on-ci"></a>Supporto di rami di sviluppo in CI

Il sistema di controllo delle versioni può essere usato anche per visualizzare le versioni dei documenti da altri branch di sviluppo compilati da CI. Quando si configura l'integrazione continua per uno di questi rami, assicurarsi che lo script di PowerShell in CI copi il contenuto dell'output docfx generato in una cartella della versione denominata dopo il ramo e aggiungere la corrispondente voce di versione nel file Web/version.js.

## <a name="good-practices-for-developers"></a>Procedure ottimali per gli sviluppatori

* Usare **percorsi relativi** ogni volta che si fa riferimento a pagine interne MRTK
* Usare i **riferimenti incrociati** per il collegamento a qualsiasi pagina dell'API MRTK usando l' **UID modificato**
* Usare **cRefs e hrefs** per collegarsi alla documentazione interna o esterna nei **Commenti///**
* Usa le cartelle indicate in questo documento per i file di risorse
* **Eseguire docfx localmente** e verificare la presenza di avvisi nell'output ogni volta che si modificano le API esistenti o si aggiornano le pagine della documentazione
* Guarda gli avvisi di docfx **su ci** dopo il completamento e l'Unione della richiesta pull in uno dei rami MRTK ufficiali

## <a name="common-errors-when-generating-docs"></a>Errori comuni durante la generazione di documenti

* errori TOC. yml: in genere si verifica quando un file con estensione MD viene spostato/rinominato o rimosso, ma la tabella del file di contenuto (TOC. yml) che punta a tale file non è stata aggiornata di conseguenza. Sul sito Web verrà visualizzato un collegamento interruppe nel primo livello o nell'esplorazione laterale
* errori relativi ai commenti
  * errori dei tag XML: docfx come qualsiasi altro parser XML non è in grado di gestire i tag XML in formato non valido.
  * errori di digitazione in cRefs
  * identificatori dello spazio dei nomi incompleti: docfx non richiede lo spazio dei nomi completo al simbolo a cui si fa riferimento, ma la parte relativa dello spazio dei nomi non inclusa nello spazio dei nomi adiacente di cref.
    * Esempio: se ci si trova in uno spazio dei nomi Microsoft. MixedReality. Toolkit. Core. Providers. UnityInput e il file che si vuole collegare è Microsoft. MixedReality. Toolkit. Core. Interfaces. IMixedRealityServiceRegistrar, il cref può essere simile al seguente: cref = "Interfaces. IMixedRealityServiceRegistrar"
  * External cRefs: se non è disponibile alcun servizio dell'elenco di funzioni di riferimento (ed è elencato nel file di compilazione docfx), cRefs alle librerie esterne non funzionerà. Se si vuole ancora creare un collegamento a un simbolo esterno specifico che non dispone di un servizio dell'xrif, ma una documentazione sull'API online, è invece possibile usare href. Esempio: collegamento a EditorPrefs di Unity: `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`

## <a name="see-also"></a>Vedi anche

* [Guida alla documentazione di MRTK](../contributing/documentation-guide.md)
* [Documentazione per gli sviluppatori MRTK su github.io](https://microsoft.github.io/MixedRealityToolkit-Unity/)
* [DocFX](https://dotnet.github.io/docfx/index.html)
