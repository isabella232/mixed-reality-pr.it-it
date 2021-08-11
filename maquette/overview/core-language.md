---
title: Linguaggio di base
description: Informazioni sui dettagli del linguaggio principale di Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipazione, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Feedback, Hub di Feedback, bug
ms.openlocfilehash: 290b1442c3cc7fed10b315f4beeebfe2eab4a775d4909d5411c651362e24d94e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197401"
---
# <a name="maquettescript-core-language-details"></a>Dettagli del linguaggio principale MaquetteScript

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language Details (Dettagli del linguaggio principale MaquetteScript)

## <a name="accessing-maquette-object-and-namespace"></a>Accesso `Maquette` all'oggetto e allo spazio dei nomi

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette espone interfacce e oggetti interni in JavaScript tramite `Maquette` l'oggetto e i relativi elementi figlio. Questa funzionalità è descritta nella documentazione [relativa all'oggetto Maquette e allo spazio dei](https://www.maquette.ms/doc_staging/objects/Maquette.html) nomi. 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
L'oggetto dispone di funzioni di primo livello per semplificare l'interazione con Maquette e semplificare la risoluzione dei `Maquette` problemi ripetitivi. Questa operazione è descritta nella documentazione di [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Avvio e caricamento di Maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette carica e valuta file JavaScript specifici per abilitare la configurazione, l'installazione e l'inizializzazione nei momenti seguenti:

Durante l'avvio di Maquette:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

Ogni volta che viene caricato un progetto:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

I progetti caricano i rispettivi script di progetto:
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>Implementazione di JavaScript

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
L'interprete JavaScript usato in Maquette si basa su [Jint.](https://github.com/sebastienros/jint) Jint è compatibile con ECMAScript 5.1 e supporta estensioni [aggiuntive da ECMAScript 6.](https://github.com/sebastienros/jint/issues/343) 

`.mqjs`L'estensione viene usata per distinguere i file JavaScript Maquette dal normale JavaScript.

## <a name="see-also"></a>Vedere anche 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->