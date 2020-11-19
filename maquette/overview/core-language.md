---
title: Linguaggio di base
description: Informazioni sui dettagli del linguaggio di base di maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Realtà mista di Windows, maquette, prototipi, realtà mista, realtà virtuale, VR, MR, feedback, hub di feedback, bug
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935538"
---
# <a name="maquettescript-core-language-details"></a>Dettagli del linguaggio di base di MaquetteScript

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language Details

## <a name="accessing-maquette-object-and-namespace"></a>Accesso all' `Maquette` oggetto e allo spazio dei nomi

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette espone gli oggetti interni e le interfacce in JavaScript tramite l' `Maquette` oggetto e i relativi elementi figlio. Questa funzionalità è descritta nell' [oggetto maquette e nella documentazione dello spazio dei nomi](https://www.maquette.ms/doc_staging/objects/Maquette.html) . 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
L' `Maquette` oggetto dispone di funzioni di primo livello per semplificare l'interazione con maquette e per semplificare la risoluzione dei problemi ripetuti. Questa operazione è descritta nella documentazione di [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).

## <a name="maquette-startup-and-loading"></a>Avvio e caricamento di maquette

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette caricherà e valuterà file JavaScript specifici per abilitare la configurazione, l'installazione e l'inizializzazione nei momenti seguenti:

Durante l'avvio di maquette:
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
L'interprete JavaScript usato in Maquette è basato su [o Jint](https://github.com/sebastienros/jint). O Jint è compatibile con ECMAScript 5,1 e supporta [estensioni aggiuntive da ECMAScript 6](https://github.com/sebastienros/jint/issues/343). 

L'estensione `.mqjs` viene usata per distinguere i file JavaScript Maquette dal normale linguaggio JavaScript.

## <a name="see-also"></a>Vedere anche 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->