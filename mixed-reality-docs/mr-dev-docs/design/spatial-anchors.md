---
title: Ancoraggi nello spazio
description: Informazioni sulle procedure consigliate per l'uso di ancoraggi spaziali per eseguire il rendering di ologrammi stabili in applicazioni di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziali, scala del mondo, mondo, scala, posizione, orientamento, ancoraggio, ancoraggio spaziale, world-locked, world-locking, persistenza, condivisione, visore per realtà mista, visore di realtà mista windows, visore per realtà virtuale, HoloLens
ms.openlocfilehash: dc9b57d51f4202499d82abb8d210261d2ee36dc60bb90ed039a7554f82af79a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193515"
---
# <a name="spatial-anchors"></a>Ancoraggi nello spazio

Un ancoraggio spaziale rappresenta un punto importante nel mondo che il sistema tiene traccia nel tempo. Ogni ancoraggio ha un sistema di [coordinate](coordinate-systems.md)regolabile, basato su altri ancoraggi o fotogrammi di riferimento, per garantire che gli ologrammi ancorati rimangano esattamente sul posto.  Il rendering di un ologramma nel sistema di coordinate di un ancoraggio offre il posizionamento più preciso per tale ologramma in qualsiasi momento. Questo avviene a costo di piccole modifiche nel tempo alla posizione dell'ologramma quando il sistema lo sposta continuamente in posizione in base al mondo reale.

È anche possibile salvare in modo permanente e condividere ancoraggi spaziali tra le sessioni dell'applicazione e tra dispositivi:
* Salvando gli ancoraggi spaziali locali su disco e caricandoli di nuovo in un secondo momento, l'applicazione può calcolare la stessa posizione nel mondo reale in più sessioni dell'applicazione in una singola HoloLens.
* Usando <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per creare un ancoraggio cloud, l'applicazione può condividere un ancoraggio spaziale tra più dispositivi HoloLens, iOS e Android. Facendo in modo che ogni dispositivo eserciti il rendering di un ologramma usando lo stesso ancoraggio spaziale, l'ologramma verrà visualizzato nello stesso punto del mondo reale. Ciò rende possibili esperienze condivise in tempo reale.
* È anche possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per la persistenza ologramma asincrona HoloLens dispositivi iOS e Android. Condividendo un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se tali dispositivi non sono presenti contemporaneamente.

Per esperienze di scalabilità in piedi o in camera per visori desktop con tethering [](coordinate-systems.md#stage-frame-of-reference) che rimarranno entro un diametro di 5 metri, è in genere possibile usare il frame di riferimento della fase anziché ancoraggi nello spazio, che fornisce un singolo sistema di coordinate in cui eseguire il rendering di tutto il contenuto. Tuttavia, se l'applicazione consente agli utenti di andare oltre i 5 metri in HoloLens, magari operando in un intero piano di un edificio, saranno necessari ancoraggi nello spazio per mantenere il contenuto stabile.

Gli ancoraggi nello spazio sono uno strumento utilissimo per gli ologrammi che devono rimanere fissi nel mondo. Tuttavia, una volta posizionati, non possono essere spostati. Esistono alternative agli ancoraggi più appropriati per gli ologrammi dinamici che contrassegnano insieme all'utente. È meglio posizionare ologrammi dinamici usando un fotogramma di riferimento stazionario (la base per le coordinate globali di Unity) o un frame di riferimento associato.

## <a name="best-practices"></a>Procedure consigliate

Queste linee guide relative agli ancoraggi nello spazio consentiranno di eseguire il rendering di ologrammi stabili in grado di tenere traccia accuratamente del mondo reale.

### <a name="create-spatial-anchors-where-users-place-them"></a>Creare gli ancoraggi nello spazio nei punti in cui gli utenti li posizionano

In genere, gli utenti sono quelli che posizionano in modo esplicito ancoraggi spaziali.

Ad esempio, in HoloLens, un'applicazione può intersecare il raggio dello sguardo dell'utente con la mesh di [mapping](spatial-mapping.md) spaziale per consentire all'utente di decidere dove posizionare un ologramma. [](gaze-and-commit.md) Quando l'utente tocca per posizionare l'ologramma, creare un ancoraggio spaziale nel punto di intersezione e quindi posizionare l'ologramma all'origine del sistema di coordinate dell'ancoraggio.

Gli ancoraggi nello spaziale locale sono semplici ed performanti da creare. Il sistema combina i dati interni se più ancoraggi possono condividere i dati del sensore sottostante. È consigliabile creare un nuovo ancoraggio spaziale locale per ogni ologramma che un utente inserisce in modo esplicito, tranne nei casi descritti di seguito, ad esempio gruppi rigidi di ologrammi.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Eseguire sempre il rendering degli ologrammi ancorati entro 3 metri dal relativo ancoraggio

Gli ancoraggi nello spazio stabilizzano il relativo sistema di coordinate vicino alla loro origine. Se si esegue il rendering di ologrammi a più di 3 metri dall'origine, gli ologrammi potrebbero verificarsi errori posizionali evidenti in proporzione alla distanza da tale origine a causa degli effetti del lever-arm. Questa operazione funziona se l'utente si trova vicino all'ancoraggio, poiché l'ologramma è lontano dall'utente. In altre parole, l'errore angolare dell'ologramma distante sarà piccolo. Tuttavia, se l'utente si accosta a quell'ologramma distante, sarà grande a loro vista, rendendo evidenti gli effetti a leve-arm dall'origine dell'ancoraggio lontano.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Raggruppare gli ologrammi che devono formare un gruppo rigido

Più ologrammi possono condividere lo stesso ancoraggio spaziale se l'applicazione prevede che tali ologrammi mantengano relazioni fisse tra loro.

Ad esempio, se si anima un sistema solare olografico in una stanza, è meglio associare tutti gli oggetti del sistema solare a un singolo ancoraggio al centro. In questo modo, si sposteranno senza problemi in base l'uno all'altro. In questo caso, è il sistema solare nel suo complesso a essere ancorato, anche se le parti dei componenti si spostano dinamicamente intorno all'ancoraggio.

L'avvertenza chiave per mantenere la stabilità dell'ologramma è seguire la regola di 3 metri precedente.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Eseguire il rendering degli ologrammi a elevata dinamicità usando la cornice di riferimento non spostabile invece di un ancoraggio nello spazio locale

Se si dispone di un ologramma altamente dinamico, ad esempio un carattere che si aggira in una stanza o un'interfaccia utente mobile che segue lungo la [](coordinate-systems.md#stationary-frame-of-reference)parete vicino all'utente, è consigliabile ignorare gli ancoraggi spaziali locali ed eseguire il rendering di tali ologrammi direttamente nel sistema di coordinate fornito dal frame di riferimento zionario. In Unity si ottiene questo risultato posizionando gli ologrammi direttamente nelle coordinate del mondo senza WorldAnchor. Ologrammi in un frame di riferimento stazionario potrebbe verificarsi una deriva quando l'utente è lontano dall'ologramma. Ma questo è meno probabile che sia evidente per gli ologrammi dinamici: l'ologramma è in continuo movimento o il suo movimento lo mantiene costantemente vicino all'utente in cui la deriva verrà ridotta al minimo.

Un caso interessante di ologrammi dinamici è costituito da un oggetto che si anima da un sistema di coordinate ancorato a un altro. Ad esempio, si potrebbero avere due casti a 10 metri di distanza, ognuno sul proprio ancoraggio spaziale con un castello che spari una palla di cannone all'altro. Quando la palla di cannone viene lanciata, è possibile eseguirne il rendering nella posizione appropriata nel frame di riferimento zionario in modo che coincida con il cannone nel sistema di coordinate ancorato del primo castello. La palla può quindi seguire la sua traiettoria nella cornice di riferimento non spostabile mentre percorre 10 metri in aria. Quando la palla di cannone raggiunge l'altro castello, è possibile spostarla nel sistema di coordinate ancorato del secondo castello per consentire calcoli fisici con i corpi rigidi del castello.

Se si condivide un ologramma altamente dinamico tra dispositivi, selezionare un ancoraggio nello spazio cloud per fungere da padre perché i fotogrammi di riferimento stazionari non possono essere condivisi tra i dispositivi.  Tuttavia, è necessario assicurarsi che l'ologramma dinamico o i dispositivi che lo visualizzano rimangano entro il raggio di 3 metri dell'ancoraggio in modo che l'ologramma sia stabile in tutti i dispositivi.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitare di creare una griglia di ancoraggi nello spazio

Si potrebbe essere tentati di fare in modo che l'applicazione eserciti una griglia regolare di ancoraggi spaziali mentre l'utente si sposta, spostando gli oggetti dinamici dall'ancoraggio all'ancoraggio mentre si spostano. Tuttavia, ciò comporta una maggiore gestione per l'applicazione, senza il vantaggio dei dati del sensore profondo che il sistema stesso gestisce internamente. In questi casi, si o riusciranno a ottenere risultati migliori inserendo gli ologrammi nel frame di riferimento zionario, come descritto nella sezione precedente.
Quando si pre-posiziona un set di ancoraggi nello spazio cloud intorno a uno spazio statico, è consigliabile posizionare gli ancoraggi nello spazio nelle posizioni degli ologrammi chiave che l'utente presenta in base al principio precedente anziché creare una griglia arbitraria di ancoraggi. Ciò garantisce la massima stabilità per tali ologrammi chiave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Rilasciare gli ancoraggi nello spazio locali non più necessari

Mentre un ancoraggio spaziale locale è attivo, il sistema assegna la priorità mantenendo i dati del sensore vicino a tale ancoraggio. Se non si usa più un ancoraggio spaziale, interrompere l'accesso al sistema di coordinate. In questo modo i dati del sensore sottostante possono essere rimossi in base alle esigenze.

Ciò è particolarmente importante per gli ancoraggi locali resi persistenti nell'archivio di ancoraggi nello stato spaziale. I dati del sensore dietro questi ancoraggi verranno mantenuti in modo permanente per consentire all'applicazione di trovare l'ancoraggio nelle sessioni future, riducendo così lo spazio disponibile per tenere traccia di altri ancoraggi. Rendere persistenti solo gli ancoraggi locali che è necessario trovare di nuovo nelle sessioni future. È consigliabile rimuoverli dall'archivio quando non sono più significativi per l'utente.

Per gli ancoraggi nello spazio del cloud, le dimensioni dello spazio di archiviazione possono adattarsi come richiesto dallo scenario. È possibile archiviare tutti gli ancoraggi cloud necessari, rilasciandoli quando si sa che gli utenti non necessitano di nuovo l'ancoraggio.

## <a name="see-also"></a>Vedi anche

* [Sistemi di coordinate](coordinate-systems.md)
* [Esperienze condivise nella realtà mista](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Persistenza in Unity](../develop/unity/persistence-in-unity.md)
* [Ancoraggi nello spazio in DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Guardare attraverso fori nella realtà](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)