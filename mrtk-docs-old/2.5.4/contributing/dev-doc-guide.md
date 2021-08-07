---
title: DevDocGuide
description: Portale per sviluppatori gudie per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, GitHub
ms.openlocfilehash: 62e995ed5db468dc669c98456dd506aaf14d7b5078734ba300d37f70b8e67aab
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212771"
---
# <a name="developer-portal-generation-guide"></a>Guida alla generazione del portale per sviluppatori

MRTK usa [docfx per](https://dotnet.github.io/docfx/index.html) generare documentazione HTML con commenti con barra tripla nel codice e nei file MD nel repository MRTK. La generazione della documentazione di Docfx viene attivata automaticamente da CI sulle richiesta di copia completate nel mrtk_development branch.
Lo stato corrente della documentazione per sviluppatori è disponibile nella pagina [di github.io MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/)

Docfx supporta DFM Docfx Flavored Markdown che include GFM Github Flavored Markdown. La documentazione completa e l'elenco delle funzionalità sono disponibili [qui](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)

Docfx non solo esegue la conversione, ma controlla anche tutti i collegamenti locali usati nella documentazione. Se un percorso non può essere risolto, non verrà convertito nell'equivalente HTML. È quindi importante usare i percorsi relativi solo quando si fa riferimento ad altri file locali.

## <a name="building-docfx-locally"></a>Compilazione di docfx in locale

I file di compilazione docfx nel archivio MRTK possono essere usati per creare una versione locale della documentazione per sviluppatori in una sottocartella doc/ nella radice del progetto.

### <a name="setup"></a>Eseguire la configurazione

* Ottenere la versione più recente di [docfx](https://dotnet.github.io/docfx/index.html)
* estrarre i file in una cartella nel computer
* aggiungere la cartella al percorso nelle variabili di ambiente

### <a name="generation"></a>Generation

* aprire un prompt dei comandi o powershell nella radice del progetto MRTK
* execute `docfx docfx.json` (facoltativamente con l'opzione -f per forzare una ricompilazione dei file doc)
* execute (facoltativamente con -p portnumber se non si vuole usare la porta `docfx serve doc` predefinita 8888) 
* aprire un Web browser con localhost:*portnumber*

Si noti che durante l'esecuzione del comando docfx nel file di compilazione JSON docfx verranno visualizzati tutti i collegamenti interrotti nella documentazione come avviso.
Assicurarsi che ogni volta che si apportano modifiche a uno dei file di documentazione o dell'API per aggiornare tutti i collegamenti che puntano a questi articoli o codice.

## <a name="verifying-docfx-on-github"></a>Verifica di docfx in GitHub

Ogni volta che una richiesta pull include una modifica che potrebbe influire sull'cin ci della documentazione, è necessario eseguire un controllo in docfx per i collegamenti interrotti. Questa operazione può essere attivata pubblicando il comando `/azp run mrtk_docs` nella richiesta pull se l'utente dispone di diritti sufficienti a tale scopo. Il comando attiverà un processo ci che aggiungerà una compilazione della documentazione alla sezione dei controlli della richiesta pull.

## <a name="using-crefs-and-hrefs-in--documented-code"></a>Uso di crefs e hrefs nel codice documentato ///

Docfx supporta crefs nel codice documentato ///. Questi riferimenti verranno tradotti in collegamenti che puntano alla documentazione api generata o a siti Web di documentazione esterni.
I servizi xref esterni per la risoluzione dei collegamenti a librerie/API esterne possono essere aggiunti al docfx.jsnel file di impostazioni di compilazione nella *proprietà xrefService*.

Per le API esterne che non forniscono un href di servizio xref al sito Web della documentazione, è possibile aggiungere ai commenti.

Esempi:

```c#
/// Links to MRTK internal class SystemType
/// <see cref="Microsoft.MixedReality.Toolkit.Utilities.SystemType"/>

/// Links to external API - link provided by xref service
/// <see cref="System.Collections.Generic.ICollection{Type}.Contains"/>

/// Links to Unity web API reference
/// <see href="https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyField.html">EditorGUI.PropertyField</see>
```

## <a name="linking-in-md-documentation-files"></a>Collegamento nei file di documentazione md

Docfx traduce e convalida tutti i collegamenti locali relativi durante la generazione, non è necessaria una sintassi speciale. È sempre consigliabile fare riferimento a un altro articolo della documentazione facendo riferimento al file md corrispondente, mai al file .html automatico. Si noti che tutti i collegamenti ai file locali devono essere relativi al file che si sta modificando.

Il collegamento alla documentazione dell'API può essere eseguito usando [riferimenti incrociati.](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html) Gli UID generati automaticamente da Docfx per tutti i documenti dell'API modificano la firma.

Esempio:

Questo collegamento [all'API BoundarySystem](xref:Microsoft.MixedReality.Toolkit.Boundary) e a questa versione breve: @Microsoft.MixedReality.Toolkit.Boundary

```md
This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary)
as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary
```

## <a name="enumerating-available-xrefs"></a>Enumerazione di xref disponibili

La sintassi Xref può essere difficile da ricordare. È possibile enumerare tutti gli ID xref disponibili eseguendo prima docfx in locale:

> docfx docfx.json

Verrà generato un file xrefmap.yml, che si trova in docs/xrefmap.yml.

Ad esempio, per collegare l'overload seguente di HandleEvent, la sintassi è piuttosto comune:

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

È tuttavia facile cercare il nome e quindi usare l'intero campo **uid** come xref.

In questo esempio xref sarà simile al seguente: (xref:Microsoft.MixedReality.Toolkit. BaseEventSystem.HandleEvent ``1(BaseEventData,ExecuteEvents.EventFunction{`` 0}))

## <a name="adding-new-md-files-to-developer-docs"></a>Aggiunta di nuovi file MD alla documentazione per sviluppatori

Docfx preleverà tutti i file con estensione md nelle cartelle aggiunte come file di contenuto nella sezione build del docfx.jse genererà file HTML da essi. Per le nuove cartelle è necessario aggiungere una voce corrispondente nel file di compilazione.

### <a name="navigation-entries"></a>Voci di navigazione

Per determinare le voci della navigazione nella documentazione per sviluppatori docfx usa toc.yml/toc.md - tabella dei file di contenuto.
Il file toc nella radice del progetto definisce le voci nella barra di spostamento superiore, mentre i file toc.yml nelle sottocartelle del repo definiscono gli argomenti secondari nella barra laterale.
I file toc.yml possono essere usati per la strutturazione e possono essere presenti qualsiasi quantità di tali file. Per altre informazioni sulla definizione delle voci per toc.yml, vedere la voce della documentazione [di docfx in toc](https://dotnet.github.io/docfx/tutorial/intro_toc.html).

## <a name="resource-files"></a>File di risorse

Esistono alcuni file come immagini, video o PDF a cui la documentazione può fare riferimento, ma che non vengono convertiti da docfx. Per questi file è presente una sezione di risorse nella docfx.json. I file in tale sezione verranno copiati solo senza eseguire alcuna conversione su di essi.

Attualmente è disponibile una definizione per i tipi di risorse seguenti:

| ResourceType | Percorso |
| --- | --- |
| Immagini | Documentazione/Immagini/ |

## <a name="releasing-a-new-version"></a>Rilascio di una nuova versione

Sono supportate più versioni della documentazione per sviluppatori e possono essere cambiate dall'elenco a discesa della versione nella barra dei menu superiore. Se si sta rilasciando una nuova versione, seguire questa procedura per avere la versione nella pagina della documentazione per sviluppatori.

1. Facoltativo: l'impostazione delldocfx.jsè impostata su  
A seconda che si voglia fare in modo che "Migliora questo documento" punti a una versione specifica del repository GitHub, sarà necessario aggiungere la voce seguente alla sezione globalMetaData del docfx.jsnel file prima di chiamare il comando docfx:

    ```json
    "_gitContribute": {
        "repo": "https://github.com/Microsoft/MixedRealityToolkit-Unity.git",
        "branch": "mrtk_development"
    }
    ```

    Se non si configura questo docfx, per impostazione predefinita verrà utilizzato il ramo e il repo della cartella corrente da cui si sta chiamando docfx.

1. Creare la documentazione docfx chiamando docfx docfx.jssu nella radice del repo
1. Creare una cartella con il nome della versione nella cartella della versione del ramo gh-pages e copiare il contenuto della cartella doc generata in tale cartella
1. Aggiungere il numero di versione in versionArray in web/version.js
1. Eseguire il push del version.js nel mrtk_development e delle modifiche nel ramo gh-pages

Ci rileverà le modifiche apportate al file version.js e aggiornerà automaticamente l'elenco a discesa della versione.

### <a name="supporting-development-branches-on-ci"></a>Rami di sviluppo di supporto in CI

Il sistema di controllo delle versioni può essere usato anche per visualizzare le versioni della documentazione da altri rami di sviluppo compilati da CI. Quando si configura l'interfaccia della riga di comando per uno di questi rami, assicurarsi che lo script di PowerShell in CI copierà il contenuto dell'output docfx generato in una cartella della versione denominata in base al ramo e aggiungere la voce della versione corrispondente nel file Web/version.js.

## <a name="good-practices-for-developers"></a>Procedure consigliate per gli sviluppatori

* Usare **percorsi relativi ogni** volta che si fa riferimento a pagine interne di MRTK
* Usare **i riferimenti incrociati** per il collegamento a qualsiasi pagina dell'API MRTK usando l'UID **danneggiato**
* Usare **crefs e hrefs per** collegarsi alla documentazione interna o esterna nei **commenti ///**
* Usare le cartelle indicate in questo documento per i file di risorse
* **Eseguire docfx in locale** e verificare la presenza di avvisi nell'output ogni volta che si modificano le API esistenti o si aggiornano le pagine della documentazione
* Dopo aver completato e unito la richiesta pull **in** uno dei rami ufficiali di MRTK, fare attenzione agli avvisi docfx sull'cin ci

## <a name="common-errors-when-generating-docs"></a>Errori comuni durante la generazione di documenti

* Errori toc.yml: si verifica in genere quando un file MD viene spostato/rinominato o rimosso, ma la tabella del file di contenuto (toc.yml) che punta a tale file non è stata aggiornata di conseguenza. Nel sito Web verrà visualizzato un collegamento interrotto nel riquadro di spostamento di livello superiore o laterale
* comments errors
  * Errori di tag xml: docfx come qualsiasi altro parser XML non è in grado di gestire tag XML in formato non valido.
  * errori di digitazione in crefs
  * Identificatori dello spazio dei nomi incompleti: docfx non dovrà avere lo spazio dei nomi completo del simbolo a cui si fa riferimento, ma la parte relativa dello spazio dei nomi non inclusa nello spazio dei nomi circostante del cref.
    * Esempio: se si è in uno spazio dei nomi Microsoft.MixedReality. Toolkit. Core.Providers.UnityInput e il file che si vuole collegare è Microsoft.MixedReality. Toolkit. Core.Interfaces.IMixedRealityServiceRegistrar può avere un aspetto simile al seguente: cref="Interfaces.IMixedRealityServiceRegistrar"
  * Crefs esterni: se non è disponibile alcun servizio xref (ed è elencato nel file di compilazione docfx), le cref per le librerie esterne non funzionano. Se si vuole comunque collegarsi a un simbolo esterno specifico che non dispone di un servizio xref, ma di una documentazione api online, è possibile usare un href. Esempio: collegamento a EditorPref di Unity: `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`

## <a name="see-also"></a>Vedi anche

* [Guida alla documentazione di MRTK](../contributing/documentation-guide.md)
* [Documentazione per sviluppatori MRTK github.io](https://microsoft.github.io/MixedRealityToolkit-Unity/)
* [DocFX](https://dotnet.github.io/docfx/index.html)
