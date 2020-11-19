---
title: Panoramica sulla programmazione
description: Informazioni su come accedere a oggetti e interfacce Maquette con lo scripting.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realtà mista di Windows, maquette, prototipi, realtà mista, realtà virtuale, VR, MR, feedback, hub di feedback, bug
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935508"
---
# <a name="programming-overview"></a>Panoramica sulla programmazione

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) Panoramica sulla programmazione

Microsoft Maquette usa JavaScript (ECMAScript 5,1 con estensioni) in base all'interprete [o Jint](https://github.com/sebastienros/jint) . L'estensione `.mqjs` viene usata per distinguere i file JavaScript Maquette dal normale linguaggio JavaScript.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Gli oggetti e le interfacce Maquette sono accessibili e configurabili tramite script tramite l' `Maquette` oggetto. La documentazione sugli oggetti e le interfacce Maquette è disponibile nella Guida di riferimento alle API di maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript è una nuova aggiunta e in Flux, pertanto le modifiche dovrebbero essere previste. Documentazione più dettagliata e aggiornamenti disponibili a breve.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Spotlight sullo scripting

* In evidenza di scripting da definire come esempi/esercitazioni
  * 2x immagini/didascalia-collegamento alla pagina Spotlight

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Introduzione a MaquetteScript

* Confronto tra Mqjs e JS
* Modello di programmazione
  * Modifica rispetto a in esecuzione
* Collegamento al flusso di lavoro di programmazione
* Collegamento ai risultati della condivisione

## <a name="programming-workflow"></a>Flusso di lavoro di programmazione

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Operazione di scripting
* Operazione del debugger
* Ciclo di debug
* Copia/incolla del codice?

## <a name="running-mqjs-scripts"></a>Esecuzione di script. mqjs

<!-- TODO(Stefan): Need screenshot -->
Per eseguire un file MaquetteScript. mqjs, passare alla finestra complementare di maquette e aprire la scheda script per individuare gli script.

> [!NOTE] 
> Alcune opzioni non funzioneranno ancora perché gli script non sono stati spediti.

## <a name="vscode-editor-workflow"></a>Flusso di lavoro dell'editor VSCode

Per valutare lo script in Maquette dall'interno di VSCode, l'utente deve essere a conoscenza di due comandi:

   `CTRL-5` valuta il testo selezionato o l'intera riga in cui si trova il cursore. 

   `CTRL-SHIFT-5` valuta l'intero file.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Il testo viene inviato a maquette, valutato nell'ambiente JavaScript e il risultato viene restituito alla console di output di VSCode. Può essere usato come REPL (Read-Eval-Print-Loop).

## <a name="example-first-step"></a>Primo passaggio di esempio

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copiare il codice seguente in un file in VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Selezionare il codice o solo le sezioni e premere `CTRL-5` per eseguire. Questa operazione dovrebbe creare un cubo, posizionarlo davanti all'utente e modificarne il colore.

Sono disponibili altri esempi per trovare l'estensione.

## <a name="sharing-results"></a>Condivisione dei risultati

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Come condividere una condivisione tra gli utenti e i team
* Progetto zip nella directory documenti
* Copia progetto in condivisione file
* Aggiunta del percorso file degli invii di condivisione team al team Maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Include, riferimento al codice altrove con percorsi relativi/assoluti, moduli
* Librerie?
* Supporto di runtime
* Esterni non risolti: comportamento quando le voci mancano o si arrestano in modo anomalo
* È possibile aggiungere o modificare/osservare lo script associato a oggetti specifici?
  * È possibile copiare e incollare lo script altrove?
  * Quali sono le proprietà degli oggetti?
  * Denominazione di oggetti nella scena (ridenominazione di script con it)
  * Parola chiave or SELF per script associato a un oggetto
  * Facendo clic con il pulsante destro del mouse su un oggetto, è possibile visualizzare il codice associato (e tutte le relative gerarchie)
  * È possibile selezionare l'interfaccia utente ed essere visualizzata nel codice in VSCode?
  * Conservazione del codice associato a un oggetto "insieme" nel file di origine dello script
  * Quando si fa clic su una finestra delle proprietà di un oggetto, In VR e nella scheda principale?
* Problemi di sicurezza
* Test: potrebbe essere da definire da definire, ma è possibile suggerire video o frame in base allo script
* Se si dispone di un meccanismo di segnalazione dei bug, è possibile che venga reso accessibile tramite script per altri utenti (?)... Dopo
* Distribuzione: come "condividere" il risultato, pacchetto come EXE
* Esecuzione/controllo di una demo o spettatori/monitoraggio
* Modalità lettore
* È possibile che sia presente un segmento su come rendere "i componenti" per la condivisione? (potrebbe essere da definire)
  * #Include? Questo consente di gestire il JS puro, ma potrebbe avere conflitti di spazio dei nomi.
  * C'è qualcosa che è possibile fare per un maquette di incorporare altri Maquette con oggetti denominati per trovare la corrispondenza con il codice JS?
