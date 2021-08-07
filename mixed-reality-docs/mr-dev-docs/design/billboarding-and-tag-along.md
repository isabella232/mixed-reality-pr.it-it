---
title: Billboarding e tag-along
description: Informazioni su come usare gli oggetti con la creazione di manifesti pubblicitari, che si orientano sempre per affrontare l'utente in applicazioni di realtà mista.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, creazione di manifesti, tag-along, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 7ffcbe1d3401601e92eb1ac81dfd84f2af9e8e79eeea809b01a1e943a85f0db9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214165"
---
# <a name="billboarding-and-tag-along"></a>Billboarding e tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Che cos'è la pubblicità pubblicitaria?

La progettazione di manifesti pubblicitari è un concetto comportamentale che può essere applicato agli oggetti nella realtà mista. Gli oggetti con un manifesto orientano sempre se stessi ad affrontare l'utente. I sistemi di testo e menu sono casi d'uso comuni, in cui gli oggetti statici posizionati nell'ambiente dell'utente (bloccati in tutto il mondo) verrebbero altrimenti nascosti o illeggibili quando gli utenti si spostano.

Gli oggetti con la funzionalità di disposizione dei manifesti abilitata possono ruotare liberamente nell'ambiente dell'utente. Possono anche essere vincolati a un singolo asse a seconda delle considerazioni di progettazione. Tenere presente che gli oggetti posizionati in un manifesto possono ritagliarsi o occludere se sono troppo vicini ad altri oggetti o, in HoloLens, troppo vicine alle superfici analizzate. Per evitare questo problema, si pensi al footprint totale che un oggetto può produrre quando viene ruotato sull'asse abilitato per la creazione di manifesti.

<br>

---
## <a name="what-is-a-tag-along"></a>Che cos'è un tag-along?

Tag-along è un concetto comportamentale che può essere aggiunto agli ologrammi. Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.

![Il HoloLens dei segnaposto è un ottimo esempio del comportamento del tag-along](images/tagalong-1000px.jpg)<br>
*Il HoloLens menu Start è un ottimo esempio di comportamento di tag-along*

Gli oggetti tag-along hanno parametri, che possono ottimizzare il comportamento. Il contenuto può essere in o all'esterno della linea di vista dell'utente mentre l'utente si sposta nel proprio ambiente. Durante lo spostamento, il contenuto tenta di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione. Il contenuto potrebbe essere temporaneamente fuori visualizzazione a seconda della velocità di spostamento dell'utente. Quando l'utente guarda verso l'oggetto tag-along, viene visualizzato in modo più completo. Si pensi che il contenuto sia sempre "a colpo d'occhio", in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.

I parametri aggiuntivi possono rendere l'oggetto tag-along collegato alla testa dell'utente da un elastico. L'accelerazione o la decelerazione di smorzamento dà peso all'oggetto rendendolo più fisicamente presente. Questo comportamento spring è un affordance che consente all'utente di creare un modello mentale accurato del funzionamento del tag-along. L'audio consente di fornire altri segnali quando gli utenti hanno oggetti in modalità tag-along. L'audio deve rafforzare la velocità di spostamento; un rapido turno della testa dovrebbe fornire un effetto sonoro più evidente, mentre la velocità di una velocità naturale dovrebbe avere effetti audio minimi o nessun effetto.

Proprio come il contenuto effettivamente bloccato dalla testa, gli oggetti tag-along possono risultare travolgenti o insoddettabili se si spostano in modo severo o si spostano troppo nella visualizzazione dell'utente. Quando un utente si guarda intorno, quindi si arresta rapidamente, i sensi gli diranno di essersi arrestati. Il loro equilibrio li informa che la testa ha smesso di ruotare e che la visione vede il mondo smettere di ruotare. Tuttavia, se il tag-along continua a spostarsi quando l'utente si è arrestato, può confondere i sensi.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Etichettatura e etichettatura in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script per il comportamento di creazione di tag e di creazione di tag. Assegnare lo script Disasp.cs a qualsiasi oggetto per aggiungere un comportamento di creazione di un manifesto pubblicitario e rendere l'oggetto sempre viso. Per aggiungere un comportamento di tag lungo, usare lo script RadialView.cs. È possibile modificare diverse opzioni, ad esempio il tempo di lerping, la distanza e il grado.

* [MRTK - Risolutore visualizzazione radiale](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK - Script di Manifesto](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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