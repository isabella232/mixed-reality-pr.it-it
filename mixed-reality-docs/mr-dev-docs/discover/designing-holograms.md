---
title: Designing Holograms
description: Informazioni sulla realtà mista tramite la nuova applicazione Microsoft Designing Holograms.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, ologrammi, progettazione di ologrammi, apprendimento, app di esempio, visore per realtà mista, visore per realtà virtuale, che cos'è la realtà virtuale
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143635"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="3ca88-104">Creazione di ologrammi di progettazione</span><span class="sxs-lookup"><span data-stu-id="3ca88-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="3ca88-105">Consentire una piccola finestra di caricamento per tenere conto di tutte le GIF e i video incorporati in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="3ca88-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="3ca88-106">Imparare a progettare per la realtà mista può essere difficile perché il supporto non sempre si traduce bene in processi di progettazione 2D.</span><span class="sxs-lookup"><span data-stu-id="3ca88-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="3ca88-107">In Microsoft è stata creata un'app gratuita per il HoloLens 2 per apprendere in prima persona i concetti fondamentali di UX Design per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="3ca88-108">L'approccio unico dell'app Designing Holograms si insedia in comportamenti, suggerimenti e consigli di realtà mista per creare app HoloLens accattivanti e straordinarie.</span><span class="sxs-lookup"><span data-stu-id="3ca88-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="3ca88-109">Scaricare l'app gratuitamente dal Microsoft Store e apprendere dal team di progettazione di Realtà mista di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3ca88-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ca88-110">Scaricare l'app Designing Holograms</span><span class="sxs-lookup"><span data-stu-id="3ca88-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animata della scena di rilevamento della testa nella sala demo di Designing Hologram](images/designing-holograms/demo-room.gif)

<span data-ttu-id="3ca88-112">*Progettazione della demo room di Hologram (nota anche come casa delle bambole)*</span><span class="sxs-lookup"><span data-stu-id="3ca88-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="3ca88-113">Progettazione per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="3ca88-113">Designing for mixed reality</span></span>

<span data-ttu-id="3ca88-114">Come molti di voi, ho usato per progettare app per dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="3ca88-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="3ca88-115">Proveniente da un mondo di progettazione 2D, il passaggio completo al calcolo spaziale, dove tutto è ora nel mondo, è stato un cambiamento significativo.</span><span class="sxs-lookup"><span data-stu-id="3ca88-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="3ca88-116">In realtà mista, le app non sono più limitate a uno schermo 2D; In realtà, sono quasi gratuiti, inseriti nel mondo reale e interagiscono con oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="3ca88-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="3ca88-117">Per me, connettere esperienze 3D a processi di progettazione 2D convenzionali è l'aspetto più complesso dello sviluppo di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="3ca88-118">Nelle conversazioni con i clienti si udivano elementi come "So quali funzionalità includere e come ottenerle.</span><span class="sxs-lookup"><span data-stu-id="3ca88-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="3ca88-119">È codice, è possibile seguire la documentazione e le esercitazioni, ma l'esperienza utente?</span><span class="sxs-lookup"><span data-stu-id="3ca88-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="3ca88-120">Molte funzionalità, opzioni di input diverse, scenari diversi e ambienti fisici sono molto difficili".</span><span class="sxs-lookup"><span data-stu-id="3ca88-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="3ca88-121">![Immagine del workshop HoloLens 2 design a San Francisco Immagine del ](images/designing-holograms/workshop.jpeg)
 *workshop HoloLens 2 design di San Francisco*</span><span class="sxs-lookup"><span data-stu-id="3ca88-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="3ca88-122">Un'opportunità per insegnare</span><span class="sxs-lookup"><span data-stu-id="3ca88-122">An opportunity to teach</span></span>

<span data-ttu-id="3ca88-123">All'inizio non era ovvio, ma è stata presentata un'ottima opportunità per usare la realtà mista come mezzo per insegnarla.</span><span class="sxs-lookup"><span data-stu-id="3ca88-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="3ca88-124">La progettazione di ologrammi è un'esperienza visiva che illustra i concetti e le raccomandazioni di progettazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="3ca88-125">Si tratta solo dell'utente e di un insegnante virtuale che illustra i concetti di progettazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="3ca88-126">Tutto è da una prospettiva di terza persona con l'esperienza che si trova nel proprio spazio.</span><span class="sxs-lookup"><span data-stu-id="3ca88-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="3ca88-127">*Video sulla progettazione di trailer di ologrammi*</span><span class="sxs-lookup"><span data-stu-id="3ca88-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="3ca88-128">Esplorazione della casa del caseino</span><span class="sxs-lookup"><span data-stu-id="3ca88-128">Exploring the doll house</span></span>

<span data-ttu-id="3ca88-129">La casa della casa è l'ambiente virtuale che viene utilizzato in tutta l'app.</span><span class="sxs-lookup"><span data-stu-id="3ca88-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="3ca88-130">L'ambiente è una stanza in miniatura di 80 x 60 x 40 cm che contiene gli elementi di base che la maggior parte delle stanze ha in comune, ad esempio pareti, lampioni, mobili, un tavolo e una TV.</span><span class="sxs-lookup"><span data-stu-id="3ca88-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="3ca88-131">La casa della casa è il principale elemento dell'esperienza dell'app, quindi è necessario assicurarsi che funzioni bene in qualsiasi ambiente.</span><span class="sxs-lookup"><span data-stu-id="3ca88-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="3ca88-132">Può essere un piccolo spazio dimostrativo per la visualizzazione di tutti i tipi di concetti di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="3ca88-133">*Video del comportamento di regolazione diHouse*</span><span class="sxs-lookup"><span data-stu-id="3ca88-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="3ca88-134">Prototipi 1:1 e 1:10</span><span class="sxs-lookup"><span data-stu-id="3ca88-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="3ca88-135">Il presupposto iniziale era che le dimostrazioni 1:1 sarebbero state straordinarie, quasi come guardare un insegnante reale.</span><span class="sxs-lookup"><span data-stu-id="3ca88-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="3ca88-136">L'utente dovrebbe vedere tutto ciò che vede il docente su scala reale.</span><span class="sxs-lookup"><span data-stu-id="3ca88-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="3ca88-137">Tuttavia, ci siamo subito resi conto che ci sarebbero stati alcuni problemi:</span><span class="sxs-lookup"><span data-stu-id="3ca88-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="3ca88-138">La maggior parte degli sviluppatori eseguirà le app in uffici o stanze più piccole rispetto alla demo, quindi non è adatta.</span><span class="sxs-lookup"><span data-stu-id="3ca88-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="3ca88-139">Gli schermi sono additivi, ovvero l'intero ambiente virtuale verrà sovrapposto alla stanza di un utente.</span><span class="sxs-lookup"><span data-stu-id="3ca88-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="3ca88-140">Questo può creare confusione con due tabelle, forse doppi divano e pareti che non sono allineate.</span><span class="sxs-lookup"><span data-stu-id="3ca88-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="3ca88-141">E il peggiore di tutti gli ambienti virtuali è fortemente vincolato da un campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3ca88-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="3ca88-142">Quando è stata provata una scala minima di 1:10, il risultato era una vista accattivante di una stanza realistica.</span><span class="sxs-lookup"><span data-stu-id="3ca88-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="3ca88-143">È possibile vedere tutto ciò che succedeva da qualsiasi angolo nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="3ca88-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="3ca88-144">La cosa più sorprendente è che la maggior parte dei tester l'ha trovata molto più immersiva per vedere una versione ridotta, quindi non è mai tornati alla scala 1:1.</span><span class="sxs-lookup"><span data-stu-id="3ca88-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="3ca88-145">Si è quindi deciso di scartare effettivamente la versione 1:1 ed evitare il lavoro aggiuntivo necessario per adattare l'interfaccia utente e altri aspetti dell'app.</span><span class="sxs-lookup"><span data-stu-id="3ca88-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="3ca88-146">![Campo di visualizzazione con scala 1:1 Campo di visualizzazione ](images/designing-holograms/1-1-scale.png)
 *con scala 1:1*</span><span class="sxs-lookup"><span data-stu-id="3ca88-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="3ca88-147">![Campo di visualizzazione con scala 1:10 Campo di visualizzazione ](images/designing-holograms/1-10-scale.png)
 *con scala 1:10*</span><span class="sxs-lookup"><span data-stu-id="3ca88-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="3ca88-148">Uso di Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="3ca88-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="3ca88-149">Una delle funzionalità più caratteristiche di questa app è l'uso di Acquisizione realtà mista per insegnare e illustrare i concetti di progettazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3ca88-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="3ca88-150">Microsoft ha una Acquisizione realtà mista studio a San Francisco.</span><span class="sxs-lookup"><span data-stu-id="3ca88-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="3ca88-151">Microsoft licenzerà questa tecnologia anche in altri studi, tra cui Avatar Dimension a Washington D.C., Metastage a Los Angeles, Dimension Studio a Londra, SK Telecom a Seattle e Volucap a Sydney.</span><span class="sxs-lookup"><span data-stu-id="3ca88-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="3ca88-152">Altre informazioni sui nostri Acquisizione realtà mista [Studio sono disponibili qui.](https://www.microsoft.com/mixed-reality/capture-studios)</span><span class="sxs-lookup"><span data-stu-id="3ca88-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="3ca88-153">*Raw cameras of Daniel Escudero from one of the 106 cameras in the Acquisizione realtà mista Studio in San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="3ca88-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="3ca88-154">Il processo di acquisizione genera una mesh con fotogrammi chiave, normali e trama, che può essere recapitata come file OBJ/PNG per un'ulteriore post-produzione o pronta per la riproduzione come file MP4 compresso H.264.</span><span class="sxs-lookup"><span data-stu-id="3ca88-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="3ca88-155">Questi file possono essere importati in progetti Unity, Unreal, Native e WebXR.</span><span class="sxs-lookup"><span data-stu-id="3ca88-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="3ca88-156">I file possono essere eseguiti in Windows, iOS, Mac, Android, Magic Leap e Playstation VR.</span><span class="sxs-lookup"><span data-stu-id="3ca88-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="3ca88-157">*Capture Player fornito per analizzare i file mp4 contenenti video con mesh incorporate e audio.*</span><span class="sxs-lookup"><span data-stu-id="3ca88-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="3ca88-158">Manipolazione di acquisizioni e oggetti virtuali</span><span class="sxs-lookup"><span data-stu-id="3ca88-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="3ca88-159">Le acquisizioni di realtà mista producono rappresentazioni virtuali di persone o animali, ma a volte potrebbero essere necessari per interagire con altri oggetti virtuali.</span><span class="sxs-lookup"><span data-stu-id="3ca88-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="3ca88-160">I due esempi seguenti illustrano diversi modi in cui le scene sono stati manipolate per ottenere questo effetto.</span><span class="sxs-lookup"><span data-stu-id="3ca88-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="3ca88-161">Regolazione dello sguardo della testa</span><span class="sxs-lookup"><span data-stu-id="3ca88-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="3ca88-162">La regolazione dell'headgaze consente di spostare la testa di una persona acquisita in fase di esecuzione, ovvero si potrebbe avere un viso di acquisizione verso un utente.</span><span class="sxs-lookup"><span data-stu-id="3ca88-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="3ca88-163">In questo caso, è stato usato per visualizzare il campo di visualizzazione e il campo di interesse.</span><span class="sxs-lookup"><span data-stu-id="3ca88-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="3ca88-164">Quello che si vede di seguito è un oggetto di gioco in movimento che funge da destinazione per lo sguardo rivolto verso la testa.</span><span class="sxs-lookup"><span data-stu-id="3ca88-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="3ca88-165">Quando si sposta la destinazione da un lato all'altro, l'intestazione dell'acquisizione segue.</span><span class="sxs-lookup"><span data-stu-id="3ca88-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="3ca88-166">Questo trucco è stato usato per assicurarsi che l'acquisizione inattiva si faccia sempre verso ologrammi posizionati in diverse parti della casa delle bambole.</span><span class="sxs-lookup"><span data-stu-id="3ca88-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![La testa dell'acquisizione viene spostata in fase di esecuzione in seguito a un gameobject di destinazione in Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="3ca88-168">*La testa dell'acquisizione viene spostata in fase di esecuzione in seguito a un gameobject di destinazione in Unity.*</span><span class="sxs-lookup"><span data-stu-id="3ca88-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="3ca88-169">Sincronizzazione di oggetti animati</span><span class="sxs-lookup"><span data-stu-id="3ca88-169">Syncing Animated Objects</span></span>

<span data-ttu-id="3ca88-170">Il secondo, animava gli oggetti per la sincronizzazione con lo spostamento di un'acquisizione.</span><span class="sxs-lookup"><span data-stu-id="3ca88-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="3ca88-171">In parti diverse dell'app sono stati importati OBJ sequenziali di un'acquisizione specifica ogni cinque fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="3ca88-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="3ca88-172">Gli OBJ sono stati quindi animati nella scena per assicurarsi che corrispondano al fotogramma corrispondente dell'acquisizione.</span><span class="sxs-lookup"><span data-stu-id="3ca88-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="3ca88-173">Si tratta di un processo noioso di animazione e keyframing, ma il risultato è ottimo.</span><span class="sxs-lookup"><span data-stu-id="3ca88-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="3ca88-174">È ora possibile visualizzare un Acquisizione realtà mista che interagisce con oggetti non acquisiti.</span><span class="sxs-lookup"><span data-stu-id="3ca88-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animazione sincronizzata tra un Acquisizione realtà mista e il pannello dell'interfaccia utente](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="3ca88-176">*Animazione sincronizzata tra un Acquisizione realtà mista e il pannello dell'interfaccia utente*</span><span class="sxs-lookup"><span data-stu-id="3ca88-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="3ca88-177">Processo di creazione dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="3ca88-177">UI creative process</span></span>

<span data-ttu-id="3ca88-178">Quando è stata avviata la progettazione dell'interfaccia utente, si è voluto mostrare alcuni dei magic e delle possibilità che gli ologrammi hanno da offrire.</span><span class="sxs-lookup"><span data-stu-id="3ca88-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="3ca88-179">La semplice visualizzazione di finestre e caselle di testo 2D statiche non è una scelta giusta nel mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="3ca88-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="3ca88-180">Molte delle possibilità disponibili non vengono mostrate, quindi fin dall'inizio si è deciso di allontanarsi da questa possibilità e di usare completamente lo spazio 3D olografico.</span><span class="sxs-lookup"><span data-stu-id="3ca88-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="3ca88-181">All'inizio è stato aggiunto uno spessore ai pannelli, alle icone e alle informazioni di testo.</span><span class="sxs-lookup"><span data-stu-id="3ca88-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="3ca88-182">Tuttavia, come utente, quello che viene visualizzato è una casella di testo.</span><span class="sxs-lookup"><span data-stu-id="3ca88-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="3ca88-183">Caselle di testo con immagini, ma non sono presenti.</span><span class="sxs-lookup"><span data-stu-id="3ca88-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="3ca88-184">Abbiamo fatto di più usando gli shader di Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="3ca88-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="3ca88-185">Gli shader MRTK sono diventati uno strumento potente ed è stato fatto uso delle funzionalità degli stencil per aggiungere profondità negativa ai pannelli.</span><span class="sxs-lookup"><span data-stu-id="3ca88-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="3ca88-186">Ciò significa che invece di aggiungere elementi davanti a una casella di testo, le icone vengono ora visualizzate dietro un pannello trasparente.</span><span class="sxs-lookup"><span data-stu-id="3ca88-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="3ca88-187">Quello che si vede ora come utente è qualcosa che non è più possibile replicare nel mondo reale ed è qui che inizia a verificarsi il magic olografico.</span><span class="sxs-lookup"><span data-stu-id="3ca88-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="3ca88-188">Inoltre, come utente che non mi piace leggere, posso fare molto già nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="3ca88-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="3ca88-189">Ovviamente le icone funzionano molto meglio del testo semplice. Per fornire indicazioni ancora più potenti, ho quindi iniziato a creare un set di oggetti animati e avatar, ognuno dei quali racconta una piccola storia su ciò che viene fatto nel rispettivo scenario e su come viene usato.</span><span class="sxs-lookup"><span data-stu-id="3ca88-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animata di un sistema di menu olografico interattivo](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="3ca88-191">Concetti di base</span><span class="sxs-lookup"><span data-stu-id="3ca88-191">Core concepts</span></span>

<span data-ttu-id="3ca88-192">**Tracciamento della testa e tracciamento oculare**</span><span class="sxs-lookup"><span data-stu-id="3ca88-192">**Head Tracking and Eye Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="3ca88-193">**Tracciamento delle mani**</span><span class="sxs-lookup"><span data-stu-id="3ca88-193">**Hand Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="3ca88-194">**Consapevolezza spaziale**</span><span class="sxs-lookup"><span data-stu-id="3ca88-194">**Spatial Awareness**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="3ca88-195">**Frame olografico**</span><span class="sxs-lookup"><span data-stu-id="3ca88-195">**Holographic frame**</span></span>

![GIF animata di un utente che guarda intorno al cascinato con la cornice olografica evidenziata](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="3ca88-197">**Sistemi di coordinate**</span><span class="sxs-lookup"><span data-stu-id="3ca88-197">**Coordinate systems**</span></span>

![GIF animata di un utente che guarda intorno alla caserma con i sistemi di coordinate evidenziati](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="3ca88-199">**Tracciamento oculare**</span><span class="sxs-lookup"><span data-stu-id="3ca88-199">**Eye tracking**</span></span>

![GIF animata di un utente che guarda gli ologrammi stazionari con il raggio dello sguardo fisso evidenziato](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="3ca88-201">**Visualizzazione dell'analisi della stanza e mapping spaziale**</span><span class="sxs-lookup"><span data-stu-id="3ca88-201">**Room scan visualization and spatial mapping**</span></span>

![GIF animata di tutte le superfici all'interno dell'cascina da mappare](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="3ca88-203">**Informazioni sulle scene**</span><span class="sxs-lookup"><span data-stu-id="3ca88-203">**Scene understanding**</span></span>

![GIF animata di oggetti nel caseino riconosciuto](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="3ca88-205">**Puntare ed eseguire il commit con i raggi della mano**</span><span class="sxs-lookup"><span data-stu-id="3ca88-205">**Point and commit with hand rays**</span></span>

![GIF animata di un utente che alza la mano con un raggio della mano evidenziato](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="3ca88-207">Momenti di "Prova"</span><span class="sxs-lookup"><span data-stu-id="3ca88-207">"Try it out" moments</span></span>

<span data-ttu-id="3ca88-208">La progettazione di ologrammi insegna concetti di realtà mista, ma consente anche di provarli in camera.</span><span class="sxs-lookup"><span data-stu-id="3ca88-208">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="3ca88-209">Dopo alcune di queste spiegazioni, ci si sospende e si esce dalla casa delle bambole e si entra in un momento interattivo.</span><span class="sxs-lookup"><span data-stu-id="3ca88-209">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="3ca88-210">Ecco alcuni esempi di questi momenti interattivi:</span><span class="sxs-lookup"><span data-stu-id="3ca88-210">Here are some examples of those interactive moments:</span></span>

![GIF animata del frame di rilevamento della mano che mostra quando vengono rilevate le mani e quando entrano nel campo di visualizzazione](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="3ca88-212">*Frame di rilevamento della mano che mostra quando vengono rilevate le mani e quando entrano nel campo di visualizzazione.*</span><span class="sxs-lookup"><span data-stu-id="3ca88-212">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animata dell'interazione con i cristallo in collisione tramite l'interazione da lontano](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="3ca88-214">*Interazione con i cristallo in collisione attraverso l'interazione da lontano*</span><span class="sxs-lookup"><span data-stu-id="3ca88-214">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animata dell'esplorazione delle interazioni near affordances](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="3ca88-216">*Esplorazione degli affordance di interazione vicina*</span><span class="sxs-lookup"><span data-stu-id="3ca88-216">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="3ca88-217">Informazioni sul team</span><span class="sxs-lookup"><span data-stu-id="3ca88-217">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="3ca88-218"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="3ca88-218"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="3ca88-219"><i>Lead Technical Designer</i></span><span class="sxs-lookup"><span data-stu-id="3ca88-219"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="3ca88-220">Dan è creative director per la progettazione di ologrammi e attualmente lavora come Responsabile della progettazione per la Mixed Reality Academy di Microsoft a San Francisco e in precedenza è stato designer in uno dei Mixed Reality Studios di Microsoft a Londra.</span><span class="sxs-lookup"><span data-stu-id="3ca88-220">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="3ca88-221"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="3ca88-221"><b>Martin Wettig</b></span></span><br><span data-ttu-id="3ca88-222"><i>Senior 3D Artist</i></span><span class="sxs-lookup"><span data-stu-id="3ca88-222"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="3ca88-223">Martin è a capo di 3D Art and UI Design on Designing Holograms e in precedenza è stato Senior 3D Artist in uno dei Mixed Reality Studios di Microsoft a Berlino.</span><span class="sxs-lookup"><span data-stu-id="3ca88-223">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="3ca88-224">Un grazie enorme al team di progettazione di realtà mista per la condivisione di così tante conoscenze e agli straordinari colleghi di [Object Theory](https://objecttheory.com/) per essere membri essenziali del team in ogni passaggio del progetto.</span><span class="sxs-lookup"><span data-stu-id="3ca88-224">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="3ca88-225">Grazie a tutti per il tuo straordinario speaker, per la tua passione e la tua grande attenzione per la progettazione.</span><span class="sxs-lookup"><span data-stu-id="3ca88-225">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ca88-226">Scaricare l'app Designing Holograms (Progettazione di ologrammi)</span><span class="sxs-lookup"><span data-stu-id="3ca88-226">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)