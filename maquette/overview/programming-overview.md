---
title: Cenni preliminari sulla programmazione
description: Informazioni su come accedere a oggetti e interfacce Maquette con gli script.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipazione, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Feedback, Hub di Feedback, bug
ms.openlocfilehash: 969a4aedb60d947782acb41742b33f275e7c841c1989144b586b0329db3c3b57
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197875"
---
# <a name="programming-overview"></a>Cenni preliminari sulla programmazione

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) Cenni preliminari sulla programmazione

Microsoft Maquette usa JavaScript (ECMAScript 5.1 con estensioni) basato sull'interprete [Jint.](https://github.com/sebastienros/jint) `.mqjs`L'estensione viene usata per distinguere i file JavaScript Maquette dal normale JavaScript.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Gli oggetti e le interfacce Maquette sono accessibili e gestibili tramite script tramite `Maquette` l'oggetto . La documentazione sugli oggetti e le interfacce Maquette è disponibile nelle informazioni di riferimento sulle API di Maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript è una nuova aggiunta e in flusso, quindi è necessario che siano previste modifiche. Documentazione e aggiornamenti più dettagliati saranno presto disponibili.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>In evidenza sullo scripting

* TBD- Scripting Spotlights focused as Samples/Tutorials
  * 2x Images/Caption : collegamento alla pagina spotlight

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Introduzione a MaquetteScript

* Confronto tra Mqjs e JS
* Modello di programmazione
  * Modifica e in esecuzione
* Collegamento al flusso di lavoro di programmazione
* Collegamento ai risultati della condivisione

## <a name="programming-workflow"></a>Flusso di lavoro di programmazione

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
DA DEFINIRE
* REPL
* Operazione di scripting
* Operazione del debugger
* Ciclo di debug
* Copiare/incollare il codice?

## <a name="running-mqjs-scripts"></a>Esecuzione di script con estensione mqjs

<!-- TODO(Stefan): Need screenshot -->
Per eseguire un file maquetteScript con estensione mqjs, passare alle finestre complementari di Maquette e aprire la scheda script per individuare gli script.

> [!NOTE] 
> Alcune opzioni non funzionano ancora perché gli script non sono stati forniti.

## <a name="vscode-editor-workflow"></a>Flusso di lavoro dell'editor di VSCode

Per valutare lo script in Maquette dall'interno di VSCode, l'utente deve conoscere due comandi:

   `CTRL-5` valuta il testo selezionato o l'intera riga in cui si trova il cursore. 

   `CTRL-SHIFT-5` valuta l'intero file.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Il testo viene inviato a Maquette, valutato nell'ambiente JavaScript e il risultato viene restituito alla console di output di VSCode. Può essere usato come REPL (read-eval-print-loop).

## <a name="example-first-step"></a>Primo passaggio di esempio

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copiare il codice seguente in un file in VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Selezionare il codice o solo le sezioni e premere `CTRL-5` per eseguire. Questo dovrebbe creare un cubo, posizionarlo davanti all'utente e modificarne il colore.

Esistono altri esempi da trovare tramite l'estensione.

## <a name="sharing-results"></a>Condivisione dei risultati

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Come condividere utenti/team
* Progetto ZIP nella directory documents
* Copiare il progetto nella condivisione file
* Aggiunta del percorso file degli invii di condivisione del team al team Maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
DA DEFINIRE
* Include, riferimento al codice altrove con percorsi relativi/assoluti, moduli
* Librerie?
* Supporto di runtime
* Esterni non risolti: comportamento quando le voci mancano o si arresta in modo anomalo
* È possibile aggiungere/modificare/osservare lo script associato a oggetti specifici?
  * È possibile copiare e incollare questo script altrove?
  * E le proprietà degli oggetti?
  * Denominare gli oggetti nella scena? (ridenominazione dello script)
  * Parola chiave THIS o SELF per lo script associato a un oggetto
  * Se si fa clic con il pulsante destro del mouse su un oggetto, è possibile visualizzare il codice associato (e tutta la gerarchia)
  * È possibile selezionare nell'interfaccia utente e visualizzare il codice in VSCode?
  * Mantenere il codice associato a un oggetto "insieme" nel file di origine dello script?
  * Visualizzare la finestra delle proprietà di un oggetto quando si fa clic su di esso? Nella realtà virtuale e nella scheda principale?
* Problemi di sicurezza
* Test: potrebbe essere tbd, ma è possibile suggerire la cattura di video o fotogrammi tramite script
* Se è disponibile un meccanismo di segnalazione di bug, è possibile renderlo accessibile tramite script per altri (?) ... Dopo
* Distribuzione: come "condividere" il risultato, pacchetto come EXE
* Esecuzione/controllo di una demo o specificazione/monitoraggio
* Modalità lettore
* Potrebbe esserci un segmento su come creare "componenti" per la condivisione? (potrebbe essere tbd)
  * Sono disponibili #include? Questo gestisce js puro, si supponga, ma può avere conflitti tra spazi dei nomi.
  * È possibile eseguire qualsiasi operazione perché un maquette incorpori un altro maquette con oggetti denominati in modo che corrisponda al codice JS?
