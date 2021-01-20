---
title: Sguardo fisso e commit
description: Informazioni sul modello di input sguardo e commit, inclusi due tipi di sguardi (Head-sguardi e occhio) e diversi tipi di commit.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting, interazione, progettazione, monitoraggio degli occhi, rilevamento Head, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: bfbf58ad065f91b27208d36ba63672ee5c28dfdd
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582329"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="7d3d8-104">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="7d3d8-104">Gaze and commit</span></span>

<span data-ttu-id="7d3d8-105">_Sguardi e commit_ sono un modello di input fondamentale che è strettamente correlato al modo in cui si interagisce con i computer usando il mouse: _Point & fare clic su_.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="7d3d8-106">In questa pagina vengono introdotti due tipi di input di sguardi (occhio e sguardo) e diversi tipi di azioni di commit.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="7d3d8-107">_Sguardi e commit_ sono considerati un modello di input molto lungo con manipolazione indiretta.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="7d3d8-108">È consigliabile usarlo per interagire con contenuto olografico non raggiungibile.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="7d3d8-109">Gli auricolari per la realtà mista possono usare la posizione e l'orientamento dell'intestazione dell'utente per determinare il vettore di direzione della direzione.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="7d3d8-110">Si pensi a sguardi come un laser che punta direttamente direttamente tra gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="7d3d8-111">Questa è una grossolana approssimazione del punto guardato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="7d3d8-112">L'applicazione può intersecare questo raggio con oggetti virtuali o reali e creare un cursore in tale posizione per consentire all'utente di sapere di cosa sono destinati.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="7d3d8-113">Oltre al controllo, alcuni auricolari con realtà mista, ad esempio HoloLens 2, includono sistemi di rilevamento degli occhi che producono un vettore di sguardi oculari.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="7d3d8-114">In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="7d3d8-115">In entrambi i casi, lo sguardo rappresenta un segnale importante per lo scopo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="7d3d8-116">Maggiore è il sistema in grado di interpretare e prevedere le azioni previste dall'utente, maggiore è il miglioramento delle prestazioni e della soddisfazione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="7d3d8-117">Di seguito sono riportati alcuni esempi di come uno sviluppatore di realtà mista può trarre vantaggio da un occhio d'occhio:</span><span class="sxs-lookup"><span data-stu-id="7d3d8-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="7d3d8-118">L'app può intersecare sguardi con gli ologrammi nella scena per determinare il punto in cui l'attenzione dell'utente è (più precisa con occhio).</span><span class="sxs-lookup"><span data-stu-id="7d3d8-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="7d3d8-119">L'app può effettuare il canale di movimenti e pressioni del controller in base allo sguardo dell'utente, che consente all'utente di selezionare, attivare, acquisire, scorrere o interagire in altro modo con i loro ologrammi.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="7d3d8-120">L'app può consentire all'utente di posizionare gli ologrammi su superfici reali intersecando il raggio di sguardi con la mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="7d3d8-121">L'app può sapere quando l'utente non sta osservando la direzione di un oggetto importante, che può portare l'app a fornire suggerimenti visivi e audio per la rotazione verso tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="7d3d8-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="7d3d8-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7d3d8-123"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="7d3d8-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="7d3d8-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d3d8-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7d3d8-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7d3d8-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7d3d8-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d3d8-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7d3d8-127">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="7d3d8-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="7d3d8-128">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="7d3d8-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="7d3d8-129">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7d3d8-130">➕ Opzione alternativa</span><span class="sxs-lookup"><span data-stu-id="7d3d8-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="7d3d8-131">Sguardo fisso e commit</span><span class="sxs-lookup"><span data-stu-id="7d3d8-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="7d3d8-132">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="7d3d8-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="7d3d8-133">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7d3d8-134">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="7d3d8-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="7d3d8-135">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="7d3d8-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="7d3d8-136">Occhio o Head-sguardi?</span><span class="sxs-lookup"><span data-stu-id="7d3d8-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="7d3d8-137">Ci sono diverse considerazioni quando si affronta la domanda se è necessario usare il modello di input "sguardo attento e commit" o "Head-sguardi e commit".</span><span class="sxs-lookup"><span data-stu-id="7d3d8-137">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="7d3d8-138">Se si sta sviluppando per un auricolare immersivo o per HoloLens (1st Gen), la scelta è semplice: Head-sguardi e commit.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-138">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="7d3d8-139">Se si sta sviluppando per HoloLens 2, la scelta diventa leggermente più complessa.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-139">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="7d3d8-140">È importante comprendere i vantaggi e le esigenze di ognuno di essi.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-140">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="7d3d8-141">Nella tabella riportata di seguito sono stati compilati alcuni Pro e con le versioni precedenti per confrontare Head-vs. Eye-sguardi targeting.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-141">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="7d3d8-142">Questo è molto più completo e si consiglia di saperne di più sugli sguardi mirati in realtà mista:</span><span class="sxs-lookup"><span data-stu-id="7d3d8-142">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="7d3d8-143">[Eye tracking on HoloLens 2](eye-tracking.md): introduzione generale della nuova funzionalità di rilevamento degli occhi in HoloLens 2, incluse alcune istruzioni per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-143">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="7d3d8-144">[Interazione con gli sguardi oculari](eye-gaze-interaction.md): considerazioni sulla progettazione e consigli per la pianificazione dell'uso del rilevamento degli occhi come input.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-144">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="7d3d8-145"><strong>Targeting degli sguardi</strong></span><span class="sxs-lookup"><span data-stu-id="7d3d8-145"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="7d3d8-146"><strong>Selezione della destinazione mediante puntamento con la testa</strong></span><span class="sxs-lookup"><span data-stu-id="7d3d8-146"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-147">Veloce!</span><span class="sxs-lookup"><span data-stu-id="7d3d8-147">Fast!</span></span></td>
        <td><span data-ttu-id="7d3d8-148">Più lento</span><span class="sxs-lookup"><span data-stu-id="7d3d8-148">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-149">Impegno minimo (a malapena tutti i movimenti del corpo necessari)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-149">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="7d3d8-150">Può essere faticoso, possibile disagio (ad esempio, Strain Neck)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-150">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-151">Non richiede un cursore, ma è consigliabile un feedback sottile</span><span class="sxs-lookup"><span data-stu-id="7d3d8-151">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="7d3d8-152">Richiede che mostri un cursore</span><span class="sxs-lookup"><span data-stu-id="7d3d8-152">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-153">Nessun movimento degli occhi, ad esempio, non corretto per il disegno</span><span class="sxs-lookup"><span data-stu-id="7d3d8-153">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="7d3d8-154">Maggiore controllo ed esplicito</span><span class="sxs-lookup"><span data-stu-id="7d3d8-154">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-155">Difficile per le destinazioni di piccole dimensioni (ad esempio, piccoli pulsanti o collegamenti weblink)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-155">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="7d3d8-156">Affidabile!</span><span class="sxs-lookup"><span data-stu-id="7d3d8-156">Reliable!</span></span> <span data-ttu-id="7d3d8-157">Ottimo fallback.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-157">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7d3d8-158">...</span><span class="sxs-lookup"><span data-stu-id="7d3d8-158">...</span></span></td>
        <td><span data-ttu-id="7d3d8-159">...</span><span class="sxs-lookup"><span data-stu-id="7d3d8-159">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="7d3d8-160">Indipendentemente dal fatto che si usi il modello di input con sguardo e commit, ognuno di essi viene usato con diversi insiemi di vincoli di progettazione.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-160">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="7d3d8-161">Questi sono trattati separatamente negli articoli sugli sguardi [e sui commit](gaze-and-commit-eyes.md) e sugli sguardi e sui [commit](gaze-and-commit-head.md) .</span><span class="sxs-lookup"><span data-stu-id="7d3d8-161">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="7d3d8-162">Cursore</span><span class="sxs-lookup"><span data-stu-id="7d3d8-162">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7d3d8-163">Per lo sguardo a capo, la maggior parte delle app deve usare un [cursore](cursors.md) o altre indicazioni visive/visive per fornire all'utente la confidenza con cui si sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-163">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="7d3d8-164">In genere, il cursore viene posizionato in tutto il mondo in cui il raggio di sguardo principale interseca un oggetto, che può essere un ologramma o una superficie reale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-164">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="7d3d8-165">Per gli occhi, in genere è consigliabile *non* mostrare un cursore, in quanto questa operazione può diventare rapidamente distrazione e fastidioso per l'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-165">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="7d3d8-166">È invece possibile evidenziare leggermente le destinazioni visive o usare un cursore a occhio debole per fornire informazioni su ciò che l'utente sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-166">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="7d3d8-167">Per altre informazioni, vedere le [linee guida di progettazione per l'input basato su occhi](eye-tracking.md) su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-167">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="7d3d8-168">![Un cursore visivo di esempio per mostrare lo sguardo](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-168">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="7d3d8-169">*Image: un cursore visivo di esempio per mostrare lo sguardo*</span><span class="sxs-lookup"><span data-stu-id="7d3d8-169">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="7d3d8-170">Commit</span><span class="sxs-lookup"><span data-stu-id="7d3d8-170">Commit</span></span>
<span data-ttu-id="7d3d8-171">Quando _si parla di diversi_ modi per esaminare una destinazione, è possibile approfondire la parte relativa al _commit_ nello _sguardo e nel commit_.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-171">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="7d3d8-172">Dopo la destinazione di un oggetto o di un elemento dell'interfaccia utente, l'utente può interagire o fare clic su di esso usando un input secondario.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-172">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="7d3d8-173">Questo processo è noto come passaggio di commit del modello di input.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-173">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="7d3d8-174">Sono supportati i metodi di commit seguenti:</span><span class="sxs-lookup"><span data-stu-id="7d3d8-174">The following commit methods are supported:</span></span>
- <span data-ttu-id="7d3d8-175">Gesto della mano del rubinetto d'aria, ovvero sollevare la mano davanti all'utente e riunire il dito e il pollice dell'indice</span><span class="sxs-lookup"><span data-stu-id="7d3d8-175">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="7d3d8-176">Pronunciare _"Select"_ o uno dei comandi vocali di destinazione</span><span class="sxs-lookup"><span data-stu-id="7d3d8-176">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="7d3d8-177">Premere un solo pulsante su un [clic del HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-177">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="7d3d8-178">Premere il pulsante ' A ' in un gamepad Xbox</span><span class="sxs-lookup"><span data-stu-id="7d3d8-178">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="7d3d8-179">Premere il pulsante "A" in un controller adattivo Xbox</span><span class="sxs-lookup"><span data-stu-id="7d3d8-179">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="7d3d8-180">Gesto dello sguardo e del tocco aereo</span><span class="sxs-lookup"><span data-stu-id="7d3d8-180">Gaze and air tap gesture</span></span>
<span data-ttu-id="7d3d8-181">Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-181">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="7d3d8-182">Per usare un rubinetto aereo, aumentare il dito dell'indice nella posizione pronta, quindi pizzicare il cursore e aumentare il dito dell'indice fino al rilascio.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-182">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="7d3d8-183">In HoloLens (1a generazione), il rubinetto aereo è l'input secondario più comune.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-183">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="7d3d8-184">![Dito nella posizione pronta](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-184">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="7d3d8-185">**Dito nella posizione pronta**</span><span class="sxs-lookup"><span data-stu-id="7d3d8-185">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d3d8-186">![Premere il tasto dito per toccare o fare clic su](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-186">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="7d3d8-187">**Premere il tasto dito per toccare o fare clic su**</span><span class="sxs-lookup"><span data-stu-id="7d3d8-187">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="7d3d8-188">Il rubinetto aereo è disponibile anche in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-188">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="7d3d8-189">È stato rilassato dalla versione originale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-189">It has been relaxed from the original version.</span></span> <span data-ttu-id="7d3d8-190">Quasi tutti i tipi di Pinch sono ora supportati finché la mano è eretta e mantiene ancora.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-190">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="7d3d8-191">In questo modo è molto più semplice per gli utenti apprendere e usare il gesto.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-191">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="7d3d8-192">Questo nuovo tocco sostituisce quello precedente tramite la stessa API, in modo che le applicazioni esistenti avranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-192">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="7d3d8-193">Sguardo e "Select" (comando vocale)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-193">Gaze and "Select" voice command</span></span>
<span data-ttu-id="7d3d8-194">Il comando Voice è uno dei metodi di interazione principali in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-194">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="7d3d8-195">Fornisce un potente meccanismo vivavoce per controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-195">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="7d3d8-196">Esistono diversi tipi di modelli di interazione vocale:</span><span class="sxs-lookup"><span data-stu-id="7d3d8-196">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="7d3d8-197">Comando "Select" generico che usa l'attivazione o il commit di un clic come input secondario.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-197">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="7d3d8-198">I comandi dell'oggetto, ad esempio "close" o "make it Bigger", eseguono ed eseguono il commit in un'azione come input secondario.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-198">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="7d3d8-199">I comandi globali (ad esempio, "Vai a avvio") non richiedono una destinazione.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-199">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="7d3d8-200">Le interfacce utente di conversazione o entità come Cortana hanno una funzionalità del linguaggio di intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-200">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="7d3d8-201">Comandi vocali personalizzati</span><span class="sxs-lookup"><span data-stu-id="7d3d8-201">Custom voice commands</span></span>

<span data-ttu-id="7d3d8-202">Per altre informazioni e per un elenco completo dei comandi vocali disponibili e per informazioni su come usarli, vedere il materiale sussidiario per i comandi [vocali](../out-of-scope/voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="7d3d8-202">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="7d3d8-203">Clicker sguardi e HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d3d8-203">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7d3d8-204">Il HoloLens clic è il primo dispositivo periferico creato in modo specifico per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-204">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="7d3d8-205">È incluso in HoloLens (1st Gen) Development Edition.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-205">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="7d3d8-206">Il clicker HoloLens consente a un utente di fare clic con movimento minimo e di eseguire il commit come input secondario.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-206">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="7d3d8-207">Il HoloLens Clicker si connette a HoloLens (1st Gen) o HoloLens 2 usando Bluetooth Low Energy (BTLE).</span><span class="sxs-lookup"><span data-stu-id="7d3d8-207">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="7d3d8-208">Altre informazioni e istruzioni per associare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d3d8-208">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="7d3d8-209">*Immagine: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="7d3d8-209">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Dispositivo Clicker HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="7d3d8-211">Guarda e controller wireless Xbox</span><span class="sxs-lookup"><span data-stu-id="7d3d8-211">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7d3d8-212">Il controller wireless Xbox esegue l'attivazione tramite clic come input secondario usando il pulsante "A".</span><span class="sxs-lookup"><span data-stu-id="7d3d8-212">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="7d3d8-213">Il dispositivo è mappato a un set predefinito di azioni che facilitano la navigazione e il controllo del sistema.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-213">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="7d3d8-214">Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller wireless Xbox.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-214">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="7d3d8-215">Come associare un controller Xbox al PC</span><span class="sxs-lookup"><span data-stu-id="7d3d8-215">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="7d3d8-216">*Immagine: controller wireless Xbox*</span><span class="sxs-lookup"><span data-stu-id="7d3d8-216">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="7d3d8-218">Sguardo e controller adattivo Xbox</span><span class="sxs-lookup"><span data-stu-id="7d3d8-218">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="7d3d8-219">Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità limitata, il controller adattivo Xbox è un hub unificato per i dispositivi che semplificano l'accessibilità della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-219">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="7d3d8-220">Il controller adattivo Xbox esegue l'attivazione di un clic come input secondario usando il pulsante "A".</span><span class="sxs-lookup"><span data-stu-id="7d3d8-220">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="7d3d8-221">Il dispositivo è mappato a un set predefinito di azioni che facilitano la navigazione e il controllo del sistema.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-221">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="7d3d8-222">Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller adattivo Xbox.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-222">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="7d3d8-223">![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="7d3d8-224">*Controller adattivo Xbox*</span><span class="sxs-lookup"><span data-stu-id="7d3d8-224">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="7d3d8-225">Connetti dispositivi esterni, ad esempio commutatori, pulsanti, montaggi e joystick, per creare un'esperienza di controller personalizzata univoca.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-225">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="7d3d8-226">Gli input Button, levetta e trigger sono controllati con dispositivi per l'accesso facilitato connessi tramite Jack 3,5-mm e porte USB.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-226">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="7d3d8-227">![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d3d8-227">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="7d3d8-228">*Porte del controller adattivo Xbox*</span><span class="sxs-lookup"><span data-stu-id="7d3d8-228">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="7d3d8-229">Istruzioni per associare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d3d8-229">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="7d3d8-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a></span><span class="sxs-lookup"><span data-stu-id="7d3d8-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="7d3d8-231">Movimenti compositi</span><span class="sxs-lookup"><span data-stu-id="7d3d8-231">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="7d3d8-232">Simulazione del tocco</span><span class="sxs-lookup"><span data-stu-id="7d3d8-232">Air tap</span></span>
<span data-ttu-id="7d3d8-233">Il gesto del rubinetto d'aria (e gli altri movimenti seguenti) reagiscono solo a un tocco specifico.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-233">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="7d3d8-234">Per rilevare altri rubinetti, ad esempio menu o afferra, l'applicazione deve usare direttamente le interazioni di livello inferiore descritte nella precedente sezione due movimenti dei componenti principali.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-234">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="7d3d8-235">Tocco e pressione prolungata</span><span class="sxs-lookup"><span data-stu-id="7d3d8-235">Tap and hold</span></span>
<span data-ttu-id="7d3d8-236">La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-236">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="7d3d8-237">La combinazione di tocco aereo e di attesa consente diverse interazioni di tipo "clic e trascinamento" più complesse, in combinazione con lo spostamento ARM, ad esempio la selezione di un oggetto anziché l'attivazione delle interazioni secondarie MouseDown, ad esempio la visualizzazione di un menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-237">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="7d3d8-238">Prestare attenzione quando si progetta per questo movimento, tuttavia, poiché gli utenti possono essere inclini a rilassare le posture della mano durante qualsiasi movimento esteso.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-238">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="7d3d8-239">modifica</span><span class="sxs-lookup"><span data-stu-id="7d3d8-239">Manipulation</span></span>
<span data-ttu-id="7d3d8-240">I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-240">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="7d3d8-241">Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-241">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="7d3d8-242">La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-242">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="7d3d8-243">Una volta avviato il tocco e l'attesa, qualsiasi manipolazione degli oggetti viene gestita da movimenti mano, che consente di liberare l'utente per l'aspetto durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-243">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="7d3d8-244">Spostamento</span><span class="sxs-lookup"><span data-stu-id="7d3d8-244">Navigation</span></span>
<span data-ttu-id="7d3d8-245">I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-245">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="7d3d8-246">Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-246">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="7d3d8-247">È possibile spostare la mano lungo l'asse X, Y o Z da un valore compreso tra-1 e 1, dove 0 è il punto di partenza.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-247">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="7d3d8-248">La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-248">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="7d3d8-249">La navigazione con Rails si riferisce alla capacità di riconoscere i movimenti in determinati assi fino a quando non viene raggiunta una determinata soglia sull'asse.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-249">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="7d3d8-250">Questa operazione è utile solo quando lo sviluppatore sposta in più assi è abilitato in un'applicazione, ad esempio se un'applicazione è configurata in modo da riconoscere i movimenti di navigazione tra l'asse X, l'asse Y ma anche l'asse X specificato con Rails.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-250">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="7d3d8-251">In questo caso, il sistema rileverà i movimenti di mano sull'asse X, purché rimangano all'interno di una guida immaginaria (Guida) sull'asse X, se lo spostamento della mano si verifica anche sull'asse Y.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-251">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="7d3d8-252">Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-252">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="7d3d8-253">In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-253">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="7d3d8-254">Gli utenti possono selezionare quali di queste azioni si verificano alternando gli strumenti sulla barra sopra l'applicazione, selezionando il pulsante o dicendo "<Scroll/drag/zoom> Tool".</span><span class="sxs-lookup"><span data-stu-id="7d3d8-254">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="7d3d8-255">Altre informazioni sui movimenti compositi</span><span class="sxs-lookup"><span data-stu-id="7d3d8-255">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="7d3d8-256">Strumenti di riconoscimento dei movimenti</span><span class="sxs-lookup"><span data-stu-id="7d3d8-256">Gesture recognizers</span></span>

<span data-ttu-id="7d3d8-257">Un vantaggio dell'uso del riconoscimento dei movimenti è che è possibile configurare un riconoscimento di movimento solo per i movimenti che l'ologramma attualmente interessato può accettare.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-257">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="7d3d8-258">La piattaforma esegue solo la risoluzione di ambiguità, se necessario, per distinguere questi movimenti specifici supportati.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-258">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="7d3d8-259">In questo modo, un ologramma che supporta solo il tocco aereo può accettare qualsiasi periodo di tempo tra la pressione e il rilascio, mentre un ologramma che supporta sia tap che tenere premuto può alzare di livello il tocco a una presa dopo la soglia del tempo di attesa.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-259">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="7d3d8-260">Riconoscimento della mano</span><span class="sxs-lookup"><span data-stu-id="7d3d8-260">Hand recognition</span></span>
<span data-ttu-id="7d3d8-261">HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-261">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="7d3d8-262">HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato).</span><span class="sxs-lookup"><span data-stu-id="7d3d8-262">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="7d3d8-263">Quando le mani si trovano in altre pose, HoloLens le ignora.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-263">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="7d3d8-264">Per ogni mano rilevato da HoloLens, è possibile accedere alla propria posizione senza orientamento e lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-264">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="7d3d8-265">Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-265">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="7d3d8-266">Cornice di movimento</span><span class="sxs-lookup"><span data-stu-id="7d3d8-266">Gesture frame</span></span>
<span data-ttu-id="7d3d8-267">Per i movimenti in HoloLens, è necessario che la mano si trovi all'interno di un frame di movimento, in un intervallo che può essere visualizzato in modo appropriato dalle fotocamere con rilevamento dei movimenti, dal naso alla vita e tra le spalle.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-267">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="7d3d8-268">Gli utenti devono essere sottoposti a training in questa area di riconoscimento sia per l'esito positivo dell'azione sia per la loro comodità.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-268">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="7d3d8-269">Molti utenti presumono inizialmente che il frame di movimento debba trovarsi all'interno della propria visualizzazione tramite HoloLens e mantenere le armi insolitamente per interagire.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-269">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="7d3d8-270">Quando si usa il clicker HoloLens, non è necessario che le mani si trovino all'interno del frame di movimento.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-270">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="7d3d8-271">Per i movimenti continui in particolare, c'è il rischio che gli utenti sposti le loro mani al di fuori del frame di movimento mentre si trova a metà movimento quando si trasferisce un oggetto olografico, ad esempio, e si perde il risultato previsto.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-271">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="7d3d8-272">Sono tre gli aspetti da considerare:</span><span class="sxs-lookup"><span data-stu-id="7d3d8-272">There are three things that you should consider:</span></span>

- <span data-ttu-id="7d3d8-273">Formazione dell'utente sull'esistenza e sui limiti approssimativi del frame di movimento.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-273">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="7d3d8-274">Questa operazione viene insegnata durante l'installazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-274">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="7d3d8-275">Notificare agli utenti quando i movimenti si avvicinano o interferiscono con i limiti del frame di movimento all'interno di un'applicazione fino a quando un movimento perso conduce a risultati indesiderati.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-275">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="7d3d8-276">La ricerca ha illustrato le qualità principali di un sistema di notifica.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-276">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="7d3d8-277">La shell HoloLens fornisce un esempio di questo tipo di notifica, ovvero un oggetto visivo, sul cursore centrale, che indica la direzione in cui si verifica l'attraversamento del limite.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-277">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="7d3d8-278">Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-278">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="7d3d8-279">In generale, ciò significa che il risultato di un movimento deve essere interrotto al limite e non invertito.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-279">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="7d3d8-280">Se, ad esempio, un utente sposta un oggetto olografico in una stanza, lo spostamento dovrebbe arrestarsi quando il frame del movimento viene violato e non viene restituito al punto iniziale.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-280">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="7d3d8-281">L'utente può riscontrare qualche frustrazione, ma potrebbe comprendere più rapidamente i limiti e non deve riavviare ogni volta le azioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="7d3d8-281">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="7d3d8-282">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7d3d8-282">See also</span></span>
* [<span data-ttu-id="7d3d8-283">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="7d3d8-283">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="7d3d8-284">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d3d8-284">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="7d3d8-285">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="7d3d8-285">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7d3d8-286">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="7d3d8-286">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d3d8-287">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="7d3d8-287">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7d3d8-288">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="7d3d8-288">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d3d8-289">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="7d3d8-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7d3d8-290">Input vocale</span><span class="sxs-lookup"><span data-stu-id="7d3d8-290">Voice input</span></span>](voice-input.md)