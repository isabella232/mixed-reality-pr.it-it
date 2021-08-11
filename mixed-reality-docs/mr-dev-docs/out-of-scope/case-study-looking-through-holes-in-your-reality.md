---
title: Case study - Guardare attraverso fori nella realtà
description: Questo case study illustra l'implementazione dell'effetto "finestra magica" su HoloLens, consentendo all'utente di vedere dietro le pareti, sotto il piano e nelle aperte virtuali.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, finestra magic, parallassa
ms.openlocfilehash: 0769d8a7bd2b5bdf1ef1fe50f1bbcd2f284b8503bf66b8fdb09b2206b716ea65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228183"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Case study - Guardare attraverso fori nella realtà

Quando gli utenti pensano alla realtà mista e a cosa possono fare con Microsoft HoloLens, in genere si attenono a domande come "Quali oggetti è possibile aggiungere alla stanza?" o "What can I layer on top of my space?" Mi piace evidenziare un'altra area che è possibile prendere in considerazione, essenzialmente un magic trick, usando la stessa tecnologia per esaminare o usare oggetti fisici reali intorno all'utente.

## <a name="the-tech"></a>La tecnologia

Se si è provato a sfondare le pareti in **[RoboRaid,](https://www.youtube.com/watch?v=Hf9qkURqtbM)** si è sbloccata una cassaforte per le pareti in **[Frammenti](case-study-creating-an-immersive-experience-in-fragments.md)** o si è visto il hangar UNSC Infinity nell'esperienza Halo 5 alla E3 nel **[2015,](https://www.youtube.com/watch?v=QDw5QjDtFy8)** si è visto di cosa si sta parlando. A seconda dell'azzarre, questo trick visivo può essere usato per inserire fori temporanei nella tera o per nascondere i mondo sotto una lavagna.

![RoboRaid aggiunge pipe tridimensionali e altre strutture dietro le pareti, visibili solo tramite fori creati durante l'attraversamento dei tachi.](../develop/unity/images/roboraid-640px.png)

RoboRaid aggiunge pipe tridimensionali e altre strutture dietro le pareti, visibili solo tramite fori creati durante l'attraversamento dei tachi.

Usando uno di questi ologrammi univoci in HoloLens, un'app può fornire l'idea del contenuto dietro le pareti o attraverso il piano nello stesso modo in cui la realtà si presenta attraverso una finestra effettiva. Spostati a sinistra e puoi vedere tutto quello che c'è sul lato destro. Più da vicino, è possibile vedere un po' più di tutto. La differenza principale è che i fori reali consentono di passare, mentre il tuo piano non ti permetterà di passare a quel contenuto olografico di grande effetto. Si aggiungerà un'attività al backlog.

## <a name="behind-the-scenes"></a>Dietro le quinte

Questo trick è una combinazione di due effetti. In primo luogo, il contenuto olografico viene aggiunto al mondo usando "ancoraggi nello spaziale". L'uso di ancoraggi per rendere il contenuto "bloccato al mondo" significa che ciò che si sta guardando non si allontana visivamente dagli oggetti fisici vicini, anche quando ci si sposta o il sistema di mapping spaziale sottostante aggiorna il modello 3D della stanza.

In secondo luogo, il contenuto olografico è visivamente limitato a uno spazio molto specifico, quindi puoi vedere solo il foro nella realtà. Questa occlusione è necessaria per richiedere di guardare attraverso un foro logico, una finestra o una porta, che vende il trick. Senza qualcosa che blocca la maggior parte della visualizzazione, una crepa nello spazio di una dimensione segreta di Jurassic potrebbe sembrare semplicemente un dinosauro posizionato in modo non sufficiente.

![Non si tratta di uno screenshot effettivo, ma di un'illustrazione dell'aspetto del segreto di Mr Basics 101 HoloLens. L'enclosure nera non viene visualizzata, ma è possibile visualizzare il contenuto attraverso un foro virtuale. Quando si guarda attraverso un dispositivo reale, il piano sembra scomparire ancora di più perché gli occhi si concentrano a una distanza maggiore come se non fosse ancora presente.](images/origamiholecomposited-640px.png)

Non si tratta di uno screenshot effettivo, ma di un'illustrazione dell'aspetto del segreto di [Mr Basics 101](../develop/unity/tutorials/holograms-101.md) HoloLens. L'enclosure nera non viene visualizzata, ma è possibile visualizzare il contenuto attraverso un foro virtuale. Quando si guarda attraverso un dispositivo reale, il piano sembra scomparire ancora di più perché gli occhi si concentrano a una distanza maggiore come se non fosse ancora presente.

### <a name="world-locking-holographic-content"></a>Contenuto olografico che blocca il mondo

In Unity, fare in modo che il contenuto olografico rimanga bloccato a livello mondiale è facile quanto aggiungere un componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

Il componente WorldAnchor regola costantemente la posizione e la rotazione del gameobject (e quindi qualsiasi altro elemento sotto tale oggetto nella gerarchia) per mantenerlo stabile rispetto agli oggetti fisici vicini. Quando si crea il contenuto, crearlo in modo che il pivot radice dell'oggetto sia centrato in corrispondenza di questo foro virtuale. Se il pivot dell'oggetto si trova in profondità nella barriera, le lievi modifiche nella posizione e nella rotazione saranno molto più evidenti e il foro potrebbe non sembrare molto stabile.

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding everything but the virtual hole

Esistono diversi modi per bloccare in modo selettivo la visualizzazione su ciò che è nascosto nelle pareti. Il più semplice sfrutta il fatto che HoloLens usa uno schermo additivo, il che significa che gli oggetti completamente neri appaiono invisibili. È possibile eseguire questa operazione in Unity senza eseguire particolari trucchi per shader o materiali. È sufficiente creare un materiale nero e assegnarlo a un oggetto che contiene le caselle nel contenuto. Se non si vuole eseguire la modellazione 3D, è sufficiente usare alcuni oggetti Quad predefiniti e sovrapporli leggermente. Esistono diversi svantaggi di questo approccio, ma è il modo più rapido per far funzionare qualcosa e ottenere un modello di verifica a bassa fedeltà è ideale, anche se si ritiene di volerne eseguire il refactoring in un secondo momento.

Uno degli svantaggi principali dell'approccio "black box" precedente è che non fotografa bene. Anche se l'effetto potrebbe essere perfetto tramite la visualizzazione di HoloLens, tutti gli screenshot che si eseranno mostreranno un oggetto nero di grandi dimensioni anziché ciò che rimane della superficie o del piano. Il motivo è che l'hardware fisico e screenshot ologrammi compositi e realtà in modo diverso. Distouriamo per un momento alcuni calcoli matematici falsi...

*Avviso matematico falso. Questi numeri e formule sono concepiti per illustrare un punto, non per essere una metrica accurata.*

Ciò che viene visualizzato tramite HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Elementi visualizzati in screenshot e video:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

In inglese: ciò che si vede tramite HoloLens è una semplice combinazione di realtà scura (ad esempio tramite occhiali da sole) e qualsiasi ologramma che l'app vuole mostrare. Tuttavia, quando si esegue uno screenshot, l'immagine della fotocamera viene sfumita con gli ologrammi dell'app in base al valore di trasparenza per pixel.

Un modo per aggirare questo problema è modificare il materiale "black box" per scrivere solo nel buffer di profondità e ordinare con tutti gli altri materiali opachi. Per un esempio, vedere il [file WindowOcclusion.shader in MixedRealityToolkit in GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Le righe pertinenti vengono copiate qui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

Si noti che la riga "Offset 50, 100" è quella di gestire i problemi non correlati, quindi è probabile che sia opportuno non farlo.

Implementazione di un materiale di occlusione invisibile come che consente all'app di disegnare una casella con un aspetto corretto nello schermo e negli screenshot di realtà mista. Per i punti bonus, puoi provare a migliorare ulteriormente le prestazioni di tale scatola eseguendo operazioni intelligenti per disegnare ancora meno pixel invisibili, ma ciò può effettivamente entrare nelle alveare e in genere non sarà necessario.

![Ecco il segreto di MR Basics 101, che Unity disegna, ad eccezione delle parti esterne della scatola occluding. Si noti che il pivot per l'infermo si trova al centro della scatola, che consente di mantenere il foro il più stabile possibile rispetto al piano effettivo.](images/underworld-occluded-640px.png)

Ecco il segreto di [MR Basics 101,](../develop/unity/tutorials/holograms-101.md) che Unity disegna, ad eccezione delle parti esterne della scatola occluding. Si noti che il pivot per l'infermo si trova al centro della scatola, che consente di mantenere il foro il più stabile possibile rispetto al piano effettivo.

## <a name="do-it-yourself"></a>Provare

Si ha HoloLens e si vuole provare l'effetto per se stessi? La cosa più semplice da fare (senza scrivere codice) è installare l'app Visualizzatore 3D gratuita e quindi caricare il file con estensione [fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) fornito in GitHub per visualizzare un modello di fiori nella stanza. Caricarlo in HoloLens ed è possibile vedere l'avaria al lavoro. Quando ci si trova davanti al modello, è possibile vedere solo nel piccolo foro, tutto il resto è invisibile. Osservare il modello da qualsiasi altro lato e scompare completamente. Usare i controlli di spostamento, rotazione e scala dell'Visualizzatore 3D per posizionare il foro virtuale su qualsiasi superficie verticale a cui si possa pensare per generare alcune idee.

![La visualizzazione di questo modello nell'editor di Unity mostrerà un'ampia black box intorno alla fioriera. In HoloLens, la casella scompare, cedendo il controllo a un effetto magico della finestra.](images/magicwindowflowerpotineditor.png)

La visualizzazione di questo modello nell'editor di Unity mostrerà un'ampia black box intorno alla fioriera. In HoloLens, la casella scompare, cedendo il controllo a un effetto magico della finestra.

Se vuoi creare un'app che usa questa tecnica, consulta l'esercitazione Nozioni di base [mr 101](../develop/unity/tutorials/holograms-101.md) nelle esercitazioni [sulla realtà mista.](../develop/unity/tutorials.md) Il capitolo 7 termina con un'esplosione nel piano che rivela un mondo nascosto (come illustrato in precedenza). Who detto che le esercitazioni dovevano essere noiose?

Ecco alcune idee su dove è possibile prendere questa idea in seguito:
* Si pensi a come rendere interattivo il contenuto all'interno del foro virtuale. Lasciare che gli utenti possano avere un certo impatto oltre le proprie pareti può effettivamente migliorare il senso di stupore che questo scemino può offrire.
* Si pensi a come visualizzare gli oggetti fino ad aree note. Ad esempio, come è possibile inserire un foro olografico nel tavolo per il caffè e vedere il piano sotto di esso?

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Senior Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Nozioni di base MR 101: Progetto completo con dispositivo](../develop/unity/tutorials/holograms-101.md)
* [Sistemi di coordinate](../design/coordinate-systems.md)
* [Ancoraggi nello spazio](../design/spatial-anchors.md)
* [Mapping spaziale](../design/spatial-mapping.md)
