---
title: Billboarding e tag-along
description: Informazioni su come usare gli oggetti con la creazione di oggetti, che si orientano sempre per affrontare l'utente in applicazioni di realtà mista.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, gioco di tag, tag, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600340"
---
# <a name="billboarding-and-tag-along"></a>Billboarding e tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Che cos'è la distribuzione in più?

L'organizzazione è un concetto comportamentale che può essere applicato agli oggetti nella realtà mista. Gli oggetti con l'eserezione si orientano sempre verso l'utente. I sistemi di testo e menu sono casi d'uso comuni, in cui gli oggetti statici inseriti nell'ambiente dell'utente (bloccati nel mondo) verrebbero altrimenti nascosti o illeggibili quando gli utenti si spostano.

Gli oggetti con l'a capo automatico abilitato possono ruotare liberamente nell'ambiente dell'utente. Possono anche essere vincolati a un singolo asse a seconda delle considerazioni di progettazione. Tenere presente che gli oggetti con i recinti possono ritagliarsi o occludere se posizionati troppo vicini ad altri oggetti o in HoloLens, superfici analizzate troppo vicine. Per evitare questo problema, pensare al footprint totale che un oggetto può produrre quando viene ruotato sull'asse abilitato per la rotazione.

<br>

---
## <a name="what-is-a-tag-along"></a>Che cos'è un tag-along?

Il tag-along è un concetto comportamentale che può essere aggiunto agli ologrammi. Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.

![Il pannello dei pin di HoloLens è un ottimo esempio del comportamento dell'aggiunta di tag](images/tagalong-1000px.jpg)<br>
*L'menu Start HoloLens è un ottimo esempio di comportamento basato su tag*

Gli oggetti con tag hanno parametri che possono ottimizzare il comportamento. Il contenuto può essere in movimento all'esterno o all'esterno della linea di vista dell'utente mentre l'utente si sposta all'esterno dell'ambiente. Mentre ci si sposta, il contenuto tenta di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione. Il contenuto potrebbe essere temporaneamente fuori visualizzazione a seconda della velocità di spostamento dell'utente. Quando l'utente guarda verso l'oggetto tag-along, viene visualizzato in modo più completo. Si pensi a un contenuto sempre "a colpo d'occhio", in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.

Parametri aggiuntivi possono fare in modo che l'oggetto lungo il tag sia collegato alla testa dell'utente da una banda di gomma. La riduzione dell'accelerazione o della decelerazione dà peso all'oggetto rendendolo più fisicamente presente. Questo comportamento di spring è un affordance che consente all'utente di creare un modello psichiale accurato del funzionamento del tag-along. L'audio consente di fornire altri segnali quando gli utenti hanno oggetti in modalità tag-along. L'audio deve rafforzare la velocità di spostamento; Un turno rapido della testa dovrebbe fornire un effetto sonoro più evidente, mentre l'esecuzione a una velocità naturale dovrebbe avere effetti audio minimi o nessun effetto.

Proprio come il contenuto effettivamente bloccato con la testa, gli oggetti tag-along possono risultare travolgenti o inaspriti se si spostano in modo severo o sono troppo grandi nella visualizzazione dell'utente. Quando un utente si guarda attorno, si arresta rapidamente e il suo senso indica di essersi arrestato. Il loro equilibrio informa che la testa ha smesso di ruotare e che la loro visione vede il mondo smettere di ruotare. Tuttavia, se il tag-along continua a spostarsi quando l'utente si è arrestato, potrebbe confondere i propri significati.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unione e tag-along in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script per il comportamento di etichettatura e tag. Assegnare lo script Manifesto.cs a qualsiasi oggetto per aggiungere un comportamento di controllo e fare in modo che l'oggetto si faccia sempre viso. Per aggiungere un comportamento basato su tag, usare lo script RadialView.cs. È possibile modificare varie opzioni, ad esempio il tempo di lerping, la distanza e il grado.

* [MRTK - Risolutore di vista radiale](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK - Script di controllo](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)