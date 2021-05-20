---
title: Sguardo fisso e commit
description: Informazioni sul modello di input di sguardo fisso e commit, inclusi due tipi di sguardo fisso (sguardo con la testa e sguardo fisso) e vari tipi di commit.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo fisso, targeting dello sguardo fisso, interazione, progettazione, tracciamento oculare, tracciamento della testa, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196566"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="a8078-104">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="a8078-104">Gaze and commit</span></span>

<span data-ttu-id="a8078-105">_Sguardo fisso e commit_ è un modello di input fondamentale strettamente correlato al modo in cui si interagisce con i computer usando il mouse: puntamento & _clic su_.</span><span class="sxs-lookup"><span data-stu-id="a8078-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="a8078-106">In questa pagina vengono presentati due tipi di input dello sguardo fisso (con la testa e lo sguardo fisso) e diversi tipi di azioni di commit.</span><span class="sxs-lookup"><span data-stu-id="a8078-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="a8078-107">_Lo sguardo fisso e_ il commit sono considerati un modello di input lontano con manipolazione indiretta.</span><span class="sxs-lookup"><span data-stu-id="a8078-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="a8078-108">È ideale per interagire con contenuto olografico non raggiungibile.</span><span class="sxs-lookup"><span data-stu-id="a8078-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="a8078-109">I visori VR di realtà mista possono usare la posizione e l'orientamento della testa dell'utente per determinare il vettore di direzione della testa.</span><span class="sxs-lookup"><span data-stu-id="a8078-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="a8078-110">Si pensi a uno sguardo fisso che punta direttamente tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="a8078-111">Questa è una grossolana approssimazione del punto guardato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="a8078-112">L'applicazione può intersecare questo raggio con oggetti virtuali o reali e disegnare un cursore in tale posizione per instradare l'utente alla destinazione.</span><span class="sxs-lookup"><span data-stu-id="a8078-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="a8078-113">Oltre allo sguardo fisso con la testa, alcuni visori VR di realtà mista, ad esempio HoloLens 2, includono sistemi di tracciamento oculare che producono un vettore di sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="a8078-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="a8078-114">In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="a8078-115">In entrambi i casi, lo sguardo fisso rappresenta un segnale importante per la finalità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="a8078-116">Maggiore è la capacità del sistema di interpretare e prevedere le azioni previste dall'utente, maggiore sarà la soddisfazione e le prestazioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="a8078-117">Di seguito sono riportati alcuni esempi di come uno sviluppatore di realtà mista può trarre vantaggio dalla testa o dallo sguardo fisso:</span><span class="sxs-lookup"><span data-stu-id="a8078-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="a8078-118">L'app può intersecare lo sguardo con gli ologrammi nella scena per determinare dove si trova l'attenzione dell'utente (più precisa con lo sguardo fisso).</span><span class="sxs-lookup"><span data-stu-id="a8078-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="a8078-119">L'app può canale movimenti e pressione del controller in base al sguardo dell'utente, che consente all'utente di selezionare, attivare, afferrare, scorrere o interagire in altro modo con i propri ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a8078-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="a8078-120">L'app può consentire all'utente di posizionare ologrammi su superfici reali intersecando il raggio dello sguardo con la mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="a8078-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="a8078-121">L'app può sapere quando l'utente non sta cercando nella direzione di un oggetto importante, il che può portare l'app a fornire segnali visivi e audio per rivolgersi a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="a8078-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="a8078-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a8078-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a8078-123"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="a8078-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="a8078-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a8078-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a8078-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a8078-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a8078-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="a8078-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a8078-127">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="a8078-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="a8078-128">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="a8078-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a8078-129">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="a8078-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="a8078-130">➕ Opzione alternativa</span><span class="sxs-lookup"><span data-stu-id="a8078-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="a8078-131">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="a8078-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="a8078-132">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="a8078-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="a8078-133">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="a8078-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="a8078-134">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="a8078-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="a8078-135">Demo dei concetti di progettazione del rilevamento oculare e della testa</span><span class="sxs-lookup"><span data-stu-id="a8078-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="a8078-136">Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video Designing Holograms - Head Tracking and Eye Tracking (Progettazione di **ologrammi - Tracciamento** testina e tracciamento oculare) riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="a8078-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="a8078-137">Al termine, continuare per un'analisi più dettagliata di argomenti specifici.</span><span class="sxs-lookup"><span data-stu-id="a8078-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="a8078-138">*Questo video è stato tratto dall'app "Designing Holograms" (Progettazione di ologrammi) HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="a8078-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="a8078-139">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="a8078-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="a8078-140">Sguardo o sguardo con la testa?</span><span class="sxs-lookup"><span data-stu-id="a8078-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="a8078-141">Di fronte alla domanda se è consigliabile usare il modello di input "eye-gaze and commit" o "head-gaze and commit", è necessario tenere presente alcune considerazioni.</span><span class="sxs-lookup"><span data-stu-id="a8078-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="a8078-142">Se si sviluppa per un visore vr immersivo o per HoloLens (prima generazione), la scelta è semplice: sguardo a testa e commit.</span><span class="sxs-lookup"><span data-stu-id="a8078-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="a8078-143">Se si sta sviluppando per HoloLens 2, la scelta diventa un po' più difficile.</span><span class="sxs-lookup"><span data-stu-id="a8078-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="a8078-144">È importante comprendere i vantaggi e le sfide che si presentano con ognuno di essi.</span><span class="sxs-lookup"><span data-stu-id="a8078-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="a8078-145">Nella tabella seguente sono stati compilati alcuni pro e contro generali per contrapporre il targeting della testa e dello sguardo oculare.</span><span class="sxs-lookup"><span data-stu-id="a8078-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="a8078-146">Questa operazione non è completa e si consiglia di apprendere di più sul targeting dello sguardo visivo nella realtà mista qui:</span><span class="sxs-lookup"><span data-stu-id="a8078-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="a8078-147">[Tracciamento oculare HoloLens 2:](eye-tracking.md)introduzione generale della nuova funzionalità di tracciamento oculare HoloLens 2 incluse alcune indicazioni per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="a8078-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="a8078-148">[Interazione con lo sguardo fisso:](eye-gaze-interaction.md)considerazioni e raccomandazioni di progettazione quando si prevede di usare il tracciamento oculare come input.</span><span class="sxs-lookup"><span data-stu-id="a8078-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="a8078-149"><strong>Targeting con sguardo fisso</strong></span><span class="sxs-lookup"><span data-stu-id="a8078-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="a8078-150"><strong>Selezione della destinazione mediante puntamento con la testa</strong></span><span class="sxs-lookup"><span data-stu-id="a8078-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-151">veloce!</span><span class="sxs-lookup"><span data-stu-id="a8078-151">Fast!</span></span></td>
        <td><span data-ttu-id="a8078-152">più lento</span><span class="sxs-lookup"><span data-stu-id="a8078-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-153">Minimo sforzo (sono necessari movimenti del corpo)</span><span class="sxs-lookup"><span data-stu-id="a8078-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="a8078-154">Può essere fatiguing: possibile disaffezione (ad esempio, affaticamento)</span><span class="sxs-lookup"><span data-stu-id="a8078-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-155">Non richiede un cursore, ma è consigliabile un feedback discreto</span><span class="sxs-lookup"><span data-stu-id="a8078-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="a8078-156">Richiede la visualizzazione di un cursore</span><span class="sxs-lookup"><span data-stu-id="a8078-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-157">Nessun movimento oculare uniforme, ad esempio non è una buona idea per disegnare</span><span class="sxs-lookup"><span data-stu-id="a8078-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="a8078-158">Più controllato ed esplicito</span><span class="sxs-lookup"><span data-stu-id="a8078-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-159">Difficile per destinazioni di piccole dimensioni (ad esempio, pulsanti di piccole dimensioni o collegamenti Web)</span><span class="sxs-lookup"><span data-stu-id="a8078-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="a8078-160">Affidabile!</span><span class="sxs-lookup"><span data-stu-id="a8078-160">Reliable!</span></span> <span data-ttu-id="a8078-161">Ottimo fallback.</span><span class="sxs-lookup"><span data-stu-id="a8078-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a8078-162">...</span><span class="sxs-lookup"><span data-stu-id="a8078-162">...</span></span></td>
        <td><span data-ttu-id="a8078-163">...</span><span class="sxs-lookup"><span data-stu-id="a8078-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="a8078-164">Che si usi lo sguardo con la testa o lo sguardo fisso per il modello di input con sguardo fisso e commit, ognuno presenta diversi set di vincoli di progettazione.</span><span class="sxs-lookup"><span data-stu-id="a8078-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="a8078-165">Questi argomenti sono trattati separatamente negli articoli [sguardo fisso, commit](gaze-and-commit-eyes.md) e [sguardo con la testa e commit.](gaze-and-commit-head.md)</span><span class="sxs-lookup"><span data-stu-id="a8078-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="a8078-166">Cursore</span><span class="sxs-lookup"><span data-stu-id="a8078-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a8078-167">Per lo sguardo fisso con la testa, la maggior parte delle app deve usare un [cursore](cursors.md) o un'altra indicazione visiva/audity per fornire all'utente la certezza di ciò con cui sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="a8078-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="a8078-168">Questo cursore viene in genere posizionato nel mondo in cui il raggio dello sguardo con la testa interseca per la prima volta un oggetto, che può essere un ologramma o una superficie reale.</span><span class="sxs-lookup"><span data-stu-id="a8078-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="a8078-169">Per lo sguardo fisso, in genere è consigliabile non visualizzare un cursore, perché ciò può diventare rapidamente distrazione e distogliere l'attenzione dell'utente. </span><span class="sxs-lookup"><span data-stu-id="a8078-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="a8078-170">Evidenziare invece in modo non necessario le destinazioni visive o usare un cursore oculare a forma di occhio per fornire attendibilità sugli elementi con cui l'utente sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="a8078-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="a8078-171">Per altre informazioni, vedere le linee guida [per la progettazione per l'input basato sugli](eye-tracking.md) occhi HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a8078-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="a8078-172">![Esempio di cursore visivo per mostrare lo sguardo fisso](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8078-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="a8078-173">*Immagine: cursore visivo di esempio per mostrare lo sguardo fisso*</span><span class="sxs-lookup"><span data-stu-id="a8078-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="a8078-174">Commit</span><span class="sxs-lookup"><span data-stu-id="a8078-174">Commit</span></span>
<span data-ttu-id="a8078-175">Dopo aver parlato di diversi modi _per_ guardare una destinazione, si esamini la parte di _commit_ nello sguardo fisso e si esegue _il commit_ di .</span><span class="sxs-lookup"><span data-stu-id="a8078-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="a8078-176">Dopo aver selezionato come destinazione un oggetto o un elemento dell'interfaccia utente, l'utente può interagire o fare clic su di esso usando un input secondario.</span><span class="sxs-lookup"><span data-stu-id="a8078-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="a8078-177">Questo processo è noto come passaggio di commit del modello di input.</span><span class="sxs-lookup"><span data-stu-id="a8078-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="a8078-178">Sono supportati i metodi di commit seguenti:</span><span class="sxs-lookup"><span data-stu-id="a8078-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="a8078-179">Movimento della mano del tocco dell'aria(ovvero, alzare la mano davanti all'utente e riunire l'indice e il pollice)</span><span class="sxs-lookup"><span data-stu-id="a8078-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="a8078-180">Pronunciare _"select"_ o uno dei comandi vocali di destinazione</span><span class="sxs-lookup"><span data-stu-id="a8078-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="a8078-181">Premere un singolo pulsante su [un clicker HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="a8078-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="a8078-182">Premere il pulsante "A" in un gamepad Xbox</span><span class="sxs-lookup"><span data-stu-id="a8078-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="a8078-183">Premere il pulsante "A" su un controller adattivo Xbox</span><span class="sxs-lookup"><span data-stu-id="a8078-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="a8078-184">Movimento di tocco dello sguardo e dell'aria</span><span class="sxs-lookup"><span data-stu-id="a8078-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="a8078-185">Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale.</span><span class="sxs-lookup"><span data-stu-id="a8078-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="a8078-186">Per usare un tocco d'aria, alzare il dito dell'indice fino alla posizione pronta, quindi avvicinare il pollice e alzare il dito dell'indice per rilasciare.</span><span class="sxs-lookup"><span data-stu-id="a8078-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="a8078-187">In HoloLens (prima generazione), il tocco dell'aria è l'input secondario più comune.</span><span class="sxs-lookup"><span data-stu-id="a8078-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="a8078-188">![Dito nella posizione pronta](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8078-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="a8078-189">**Dito nella posizione pronta**</span><span class="sxs-lookup"><span data-stu-id="a8078-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a8078-190">![Premere il dito verso il basso per toccare o fare clic](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8078-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="a8078-191&quot;>**Premere il dito verso il basso per toccare o fare clic**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-191&quot;>**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id=&quot;a8078-192&quot;>Il tocco dell'aria è disponibile anche HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-192&quot;>Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id=&quot;a8078-193&quot;>È stato rimosso dalla versione originale.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-193&quot;>It has been relaxed from the original version.</span></span> <span data-ttu-id=&quot;a8078-194&quot;>Quasi tutti i tipi di pizzicamento sono ora supportati purché la mano sia in posizione verticale e in attesa.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-194&quot;>Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id=&quot;a8078-195&quot;>Questo rende molto più semplice per gli utenti imparare e usare il movimento.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-195&quot;>This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id=&quot;a8078-196&quot;>Questo nuovo tocco in aria sostituisce quello precedente tramite la stessa API, quindi le applicazioni esistenti avranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-196&quot;>This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a><span data-ttu-id=&quot;a8078-197&quot;>Sguardo fisso e comando vocale &quot;Seleziona&quot;</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-197&quot;>Gaze and &quot;Select&quot; voice command</span></span>
<span data-ttu-id=&quot;a8078-198&quot;>Il comando vocale è uno dei metodi di interazione principali nella realtà mista.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-198&quot;>Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id=&quot;a8078-199&quot;>Fornisce un potente meccanismo hands-free per controllare il sistema.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-199&quot;>It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id=&quot;a8078-200&quot;>Esistono diversi tipi di modelli di interazione vocale:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-200&quot;>There are different types of voice interaction models:</span></span>

- <span data-ttu-id=&quot;a8078-201&quot;>Comando generico &quot;Select&quot; che usa un'applicazione click o un commit come input secondario.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a8078-201&quot;>The generic &quot;Select&quot; command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id=&quot;a8078-202&quot;>I comandi oggetto(ad esempio, &quot;Close&quot; o &quot;Make it bigger") eseguono ed eseguono il commit in un'azione come input secondario.</span><span class="sxs-lookup"><span data-stu-id="a8078-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="a8078-203">I comandi globali , ad esempio "Vai all'avvio", non richiedono una destinazione.</span><span class="sxs-lookup"><span data-stu-id="a8078-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="a8078-204">Le interfacce utente di conversazione o le entità come Cortana hanno una funzionalità del linguaggio naturale di intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="a8078-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="a8078-205">Comandi vocali personalizzati</span><span class="sxs-lookup"><span data-stu-id="a8078-205">Custom voice commands</span></span>

<span data-ttu-id="a8078-206">Per altre informazioni sui dettagli e un elenco completo dei comandi vocali disponibili e su come usarli, vedere le linee guida per l'esecuzione [di comandi](../out-of-scope/voice-design.md) vocali.</span><span class="sxs-lookup"><span data-stu-id="a8078-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="a8078-207">Sguardo fisso e clicker HoloLens</span><span class="sxs-lookup"><span data-stu-id="a8078-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a8078-208">HoloLens Clicker è il primo dispositivo periferico creato specificamente per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8078-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="a8078-209">È incluso in HoloLens (prima generazione) Development Edition.</span><span class="sxs-lookup"><span data-stu-id="a8078-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="a8078-210">Il clicker HoloLens consente a un utente di fare clic con un movimento minimo della mano ed eseguire il commit come input secondario.</span><span class="sxs-lookup"><span data-stu-id="a8078-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="a8078-211">Il clicker HoloLens si connette a HoloLens (prima generazione) o HoloLens 2 usando Bluetooth Low Energy (BTLE).</span><span class="sxs-lookup"><span data-stu-id="a8078-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="a8078-212">Altre informazioni e istruzioni per associare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="a8078-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="a8078-213">*Immagine: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="a8078-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Dispositivo Clicker HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="a8078-215">Sguardo fisso e controller wireless Xbox</span><span class="sxs-lookup"><span data-stu-id="a8078-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a8078-216">Il controller wireless Xbox esegue un clic come input secondario usando il pulsante "A".</span><span class="sxs-lookup"><span data-stu-id="a8078-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="a8078-217">Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="a8078-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="a8078-218">Se si vuole personalizzare il controller, usare l'Accessori Xbox per configurare il controller wireless Xbox.</span><span class="sxs-lookup"><span data-stu-id="a8078-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="a8078-219">Come associare un controller Xbox al PC</span><span class="sxs-lookup"><span data-stu-id="a8078-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="a8078-220">*Immagine: Controller wireless Xbox*</span><span class="sxs-lookup"><span data-stu-id="a8078-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="a8078-222">Sguardo fisso e controller adattivo Xbox</span><span class="sxs-lookup"><span data-stu-id="a8078-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="a8078-223">Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità limitata, Xbox Adaptive Controller è un hub unificato per i dispositivi che consente di rendere la realtà mista più accessibile.</span><span class="sxs-lookup"><span data-stu-id="a8078-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="a8078-224">Xbox Adaptive Controller esegue un'actuation click come input secondario usando il pulsante "A".</span><span class="sxs-lookup"><span data-stu-id="a8078-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="a8078-225">Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="a8078-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="a8078-226">Se si vuole personalizzare il controller, usare l'applicazione Accessori Xbox per configurare il controller adattivo Xbox.</span><span class="sxs-lookup"><span data-stu-id="a8078-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="a8078-227">![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8078-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="a8078-228">*Controller adattivo Xbox*</span><span class="sxs-lookup"><span data-stu-id="a8078-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="a8078-229">Connettere dispositivi esterni come interruttori, pulsanti, montanti e tasti per creare un'esperienza di controller personalizzata univoca.</span><span class="sxs-lookup"><span data-stu-id="a8078-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="a8078-230">Gli input di pulsanti, puntini di sospensione e trigger sono controllati con dispositivi di assistive connessi tramite jack da 3,5 mm e porte USB.</span><span class="sxs-lookup"><span data-stu-id="a8078-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="a8078-231">![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8078-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="a8078-232">*Porte del controller adattivo Xbox*</span><span class="sxs-lookup"><span data-stu-id="a8078-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="a8078-233">Istruzioni per associare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="a8078-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="a8078-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a></span><span class="sxs-lookup"><span data-stu-id="a8078-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="a8078-235">Movimenti compositi</span><span class="sxs-lookup"><span data-stu-id="a8078-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="a8078-236">Simulazione del tocco</span><span class="sxs-lookup"><span data-stu-id="a8078-236">Air tap</span></span>
<span data-ttu-id="a8078-237">Il movimento del tocco dell'aria (e gli altri movimenti seguenti) reagisce solo a un tocco specifico.</span><span class="sxs-lookup"><span data-stu-id="a8078-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="a8078-238">Per rilevare altri tocchi, ad esempio Menu o Afferra, l'applicazione deve usare direttamente le interazioni di livello inferiore descritte nella sezione precedente relativa ai due movimenti dei componenti chiave.</span><span class="sxs-lookup"><span data-stu-id="a8078-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="a8078-239">Tocco e pressione prolungata</span><span class="sxs-lookup"><span data-stu-id="a8078-239">Tap and hold</span></span>
<span data-ttu-id="a8078-240">La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="a8078-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="a8078-241">La combinazione di tocco e sospensione dell'aria consente varie interazioni più complesse di "clic e trascinamento" quando vengono combinate con lo spostamento del braccio, ad esempio la selezione di un oggetto invece di attivarlo o le interazioni secondarie tramite mouse, ad esempio la visualizzazione di un menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="a8078-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="a8078-242">È tuttavia consigliabile prestare attenzione quando si progetta per questo movimento, in quanto gli utenti possono essere inclini a distensione delle posture della mano durante qualsiasi movimento esteso.</span><span class="sxs-lookup"><span data-stu-id="a8078-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="a8078-243">modifica</span><span class="sxs-lookup"><span data-stu-id="a8078-243">Manipulation</span></span>
<span data-ttu-id="a8078-244">I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a8078-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="a8078-245">Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.</span><span class="sxs-lookup"><span data-stu-id="a8078-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="a8078-246">La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento.</span><span class="sxs-lookup"><span data-stu-id="a8078-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="a8078-247">Una volta avviato il tocco e il blocco, qualsiasi manipolazione dell'oggetto viene gestita dai movimenti della mano, che liberano l'utente di guardarsi intorno mentre manipolano.</span><span class="sxs-lookup"><span data-stu-id="a8078-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="a8078-248">Spostamento</span><span class="sxs-lookup"><span data-stu-id="a8078-248">Navigation</span></span>
<span data-ttu-id="a8078-249">I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali.</span><span class="sxs-lookup"><span data-stu-id="a8078-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="a8078-250">Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale.</span><span class="sxs-lookup"><span data-stu-id="a8078-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="a8078-251">È possibile spostare la mano lungo l'asse X, Y o Z da un valore compreso tra -1 e 1, con 0 come punto iniziale.</span><span class="sxs-lookup"><span data-stu-id="a8078-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="a8078-252">La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.</span><span class="sxs-lookup"><span data-stu-id="a8078-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="a8078-253">La navigazione con le guide si riferisce alla possibilità di riconoscere i movimenti in un determinato asse fino a quando non viene raggiunta una determinata soglia su tale asse.</span><span class="sxs-lookup"><span data-stu-id="a8078-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="a8078-254">Ciò è utile solo quando lo sviluppatore attiva lo spostamento in più di un asse in un'applicazione, ad esempio se un'applicazione è configurata per riconoscere i movimenti di navigazione sull'asse X, Y ma anche l'asse X specificato con guide.</span><span class="sxs-lookup"><span data-stu-id="a8078-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="a8078-255">In questo caso, il sistema riconoscerà i movimenti delle mani sull'asse X purché rimangano all'interno di guide immaginarie sull'asse X, se il movimento della mano si verifica anche sull'asse Y.</span><span class="sxs-lookup"><span data-stu-id="a8078-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="a8078-256">Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="a8078-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="a8078-257">In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="a8078-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="a8078-258">Gli utenti possono selezionare quali di queste azioni vengono eseguite selezionando gli strumenti nella barra sopra l'applicazione, selezionando il pulsante o pronunciando "Strumento di scorrimento<scorrimento/trascinamento/zoom>".</span><span class="sxs-lookup"><span data-stu-id="a8078-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="a8078-259">Altre informazioni sui movimenti compositi</span><span class="sxs-lookup"><span data-stu-id="a8078-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="a8078-260">Strumenti di riconoscimento dei movimenti</span><span class="sxs-lookup"><span data-stu-id="a8078-260">Gesture recognizers</span></span>

<span data-ttu-id="a8078-261">Uno dei vantaggi dell'uso del riconoscimento dei movimenti è che è possibile configurare un sistema di riconoscimento dei movimenti solo per i movimenti che l'ologramma di destinazione può accettare.</span><span class="sxs-lookup"><span data-stu-id="a8078-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="a8078-262">La piattaforma non distingue solo le ambiguità necessarie per distinguere i movimenti supportati specifici.</span><span class="sxs-lookup"><span data-stu-id="a8078-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="a8078-263">In questo modo, un ologramma che supporta solo il tocco può accettare qualsiasi periodo di tempo tra la pressione e il rilascio, mentre un ologramma che supporta sia il tocco che il tocco può alzare di livello il tocco a un blocco dopo la soglia di tempo di attesa.</span><span class="sxs-lookup"><span data-stu-id="a8078-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="a8078-264">Riconoscimento della mano</span><span class="sxs-lookup"><span data-stu-id="a8078-264">Hand recognition</span></span>
<span data-ttu-id="a8078-265">HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a8078-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="a8078-266">HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato).</span><span class="sxs-lookup"><span data-stu-id="a8078-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="a8078-267">Quando le mani sono in altre posizioni, HoloLens le ignora.</span><span class="sxs-lookup"><span data-stu-id="a8078-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="a8078-268">Per ogni mano rilevata da HoloLens, puoi accedere alla sua posizione senza orientamento e stato premuto.</span><span class="sxs-lookup"><span data-stu-id="a8078-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="a8078-269">Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8078-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="a8078-270">Cornice di movimento</span><span class="sxs-lookup"><span data-stu-id="a8078-270">Gesture frame</span></span>
<span data-ttu-id="a8078-271">Per i movimenti in HoloLens, la mano deve essere all'interno di un fotogramma del movimento, in un intervallo che le fotocamere di rilevamento dei movimenti possono vedere in modo appropriato, dal rosso al tocco e tra le tra le trame.</span><span class="sxs-lookup"><span data-stu-id="a8078-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="a8078-272">Gli utenti devono essere formati su quest'area di riconoscimento sia per il successo dell'azione che per il proprio comfort.</span><span class="sxs-lookup"><span data-stu-id="a8078-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="a8078-273">Molti utenti presuppongono inizialmente che il fotogramma del movimento sia all'interno della visualizzazione tramite HoloLens e che non si agitino per interagire.</span><span class="sxs-lookup"><span data-stu-id="a8078-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="a8078-274">Quando si usa il clicker HoloLens, non è necessario che le mani siano all'interno del fotogramma del movimento.</span><span class="sxs-lookup"><span data-stu-id="a8078-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="a8078-275">Per i movimenti continui, in particolare, c'è il rischio che gli utenti slocino le mani all'esterno del fotogramma del movimento mentre sono durante il movimento durante lo spostamento di un oggetto olografico, ad esempio, e la perdita del risultato previsto.</span><span class="sxs-lookup"><span data-stu-id="a8078-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="a8078-276">Sono tre gli aspetti da considerare:</span><span class="sxs-lookup"><span data-stu-id="a8078-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="a8078-277">Formazione dell'utente sull'esistenza del fotogramma del movimento e sui limiti approssimativi.</span><span class="sxs-lookup"><span data-stu-id="a8078-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="a8078-278">Questo viene insegnato durante l'installazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8078-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="a8078-279">Notificare agli utenti quando i movimenti si avvicinano o infrangono i limiti del frame del movimento all'interno di un'applicazione al punto che un movimento perso porta a risultati indesiderati.</span><span class="sxs-lookup"><span data-stu-id="a8078-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="a8078-280">Le ricerche hanno dimostrato le qualità chiave di un sistema di notifica di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="a8078-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="a8078-281">La shell di HoloLens fornisce un buon esempio di questo tipo di notifica, ovvero l'oggetto visivo, sul cursore centrale, che indica la direzione in cui si sta svolgendo l'attraversamento dei limiti.</span><span class="sxs-lookup"><span data-stu-id="a8078-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="a8078-282">Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento.</span><span class="sxs-lookup"><span data-stu-id="a8078-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="a8078-283">In generale, ciò significa che il risultato di un movimento deve essere arrestato al limite e non invertito.</span><span class="sxs-lookup"><span data-stu-id="a8078-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="a8078-284">Ad esempio, se un utente sposta un oggetto olografico in una stanza, lo spostamento deve interrompersi quando il frame del movimento viene violato e non viene restituito al punto iniziale.</span><span class="sxs-lookup"><span data-stu-id="a8078-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="a8078-285">L'utente potrebbe provare una certa frustrazione, ma potrebbe comprendere più rapidamente i limiti e non dover riavviare ogni volta le azioni necessarie.</span><span class="sxs-lookup"><span data-stu-id="a8078-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="a8078-286">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a8078-286">See also</span></span>
* [<span data-ttu-id="a8078-287">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="a8078-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="a8078-288">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a8078-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="a8078-289">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="a8078-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a8078-290">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="a8078-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a8078-291">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="a8078-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a8078-292">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="a8078-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="a8078-293">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="a8078-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a8078-294">Input vocale</span><span class="sxs-lookup"><span data-stu-id="a8078-294">Voice input</span></span>](voice-input.md)