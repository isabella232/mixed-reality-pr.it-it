---
title: Designing Holograms
description: Scopri la realtà mista tramite la nuova applicazione per la progettazione di ologrammi di Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Toolkit per realtà mista, ologrammi, progettazione di ologrammi, apprendimento, app di esempio, auricolare realtà mista, auricolare della realtà virtuale, informazioni sulla realtà virtuale
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757759"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="d3618-104">Creazione della progettazione di ologrammi</span><span class="sxs-lookup"><span data-stu-id="d3618-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="d3618-105">Per tenere conto di tutte le gif interessanti e dei video incorporati in questa pagina, è necessario attendere una piccola finestra di caricamento.</span><span class="sxs-lookup"><span data-stu-id="d3618-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="d3618-106">L'apprendimento della progettazione per la realtà mista può essere difficile perché il supporto non è sempre tradotto correttamente nei processi di progettazione 2D.</span><span class="sxs-lookup"><span data-stu-id="d3618-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="d3618-107">Qui presso Microsoft è stata creata un'app gratuita per HoloLens 2 che consente di apprendere le nozioni di base della progettazione di UX realtà mista in prima persona.</span><span class="sxs-lookup"><span data-stu-id="d3618-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="d3618-108">L'approccio esclusivo dell'app di progettazione degli ologrammi si immerge in comportamenti di realtà misti, suggerimenti e consigli per la creazione di app HoloLens accattivanti e straordinarie.</span><span class="sxs-lookup"><span data-stu-id="d3618-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="d3618-109">Scarica gratuitamente l'app dal Microsoft Store e impara dal team Microsoft Mixed Reality Design.</span><span class="sxs-lookup"><span data-stu-id="d3618-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d3618-110">Scaricare l'app per la progettazione di ologrammi</span><span class="sxs-lookup"><span data-stu-id="d3618-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animata della scena di rilevamento Head nella stanza demo dell'ologramma di progettazione](images/designing-holograms/demo-room.gif)

<span data-ttu-id="d3618-112">*Progettazione dello spazio dimostrativo dell'ologramma (noto anche come casa di bambola)*</span><span class="sxs-lookup"><span data-stu-id="d3618-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="d3618-113">Progettazione per realtà mista</span><span class="sxs-lookup"><span data-stu-id="d3618-113">Designing for mixed reality</span></span>

<span data-ttu-id="d3618-114">Come molti di voi, ho usato per progettare app per dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="d3618-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="d3618-115">Dal punto di vista di un ambiente di progettazione 2D, il passaggio all'intero ambiente di calcolo spaziale, in cui tutto è ora in tutto il mondo, è stato un cambiamento significativo.</span><span class="sxs-lookup"><span data-stu-id="d3618-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="d3618-116">In realtà mista, le app non sono più confinate in una schermata 2D; Infatti, sono quasi gratuite, si trovano nel mondo reale e interagiscono con gli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="d3618-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="d3618-117">Per me, la connessione di esperienze 3D ai processi di progettazione 2D convenzionali è l'aspetto più complesso dello sviluppo di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="d3618-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="d3618-118">Nelle conversazioni con i clienti, mi sento di sapere quali sono le funzionalità da includere e come renderle operativi.</span><span class="sxs-lookup"><span data-stu-id="d3618-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="d3618-119">Si tratta di codice, posso seguire la documentazione e le esercitazioni, ma l'esperienza utente?</span><span class="sxs-lookup"><span data-stu-id="d3618-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="d3618-120">Un numero così elevato di funzionalità, diverse opzioni di input, scenari diversi e ambienti fisici, è molto difficile.</span><span class="sxs-lookup"><span data-stu-id="d3618-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="d3618-121">![Immagine del workshop di progettazione HoloLens 2 nell'immagine di San Francisco del ](images/designing-holograms/workshop.jpeg)
 *workshop di progettazione HoloLens 2 a San Francisco*</span><span class="sxs-lookup"><span data-stu-id="d3618-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="d3618-122">Opportunità di insegnare</span><span class="sxs-lookup"><span data-stu-id="d3618-122">An opportunity to teach</span></span>

<span data-ttu-id="d3618-123">Inizialmente non era ovvio, ma era stata presentata un'opportunità eccellente per usare la realtà mista come supporto per insegnarlo.</span><span class="sxs-lookup"><span data-stu-id="d3618-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="d3618-124">La progettazione di ologrammi è un'esperienza visiva che illustra i concetti e le raccomandazioni di progettazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d3618-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="d3618-125">Si tratta solo di un insegnante virtuale che illustra concetti di progettazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d3618-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="d3618-126">Tutto dipende dal punto di vista di una terza persona con l'esperienza nello spazio.</span><span class="sxs-lookup"><span data-stu-id="d3618-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="d3618-127">*Video sulla progettazione degli ologrammi trailer*</span><span class="sxs-lookup"><span data-stu-id="d3618-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="d3618-128">Esplorazione della casa di bambola</span><span class="sxs-lookup"><span data-stu-id="d3618-128">Exploring the doll house</span></span>

<span data-ttu-id="d3618-129">La casa Doll è l'ambiente virtuale usato nell'app.</span><span class="sxs-lookup"><span data-stu-id="d3618-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="d3618-130">L'ambiente è una stanza in miniatura di 80 x 60 x 40 cm che contiene gli elementi di base che la maggior parte delle stanze hanno in comune, ad esempio muri, lampade, mobilia, una tabella e una TV.</span><span class="sxs-lookup"><span data-stu-id="d3618-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="d3618-131">La casa Doll è il protagonista principale dell'esperienza dell'app, quindi è necessario assicurarsi che funzioni perfettamente in qualsiasi ambiente.</span><span class="sxs-lookup"><span data-stu-id="d3618-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="d3618-132">Considerarlo come una piccola stanza demo per visualizzare tutti i tipi di concetti di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d3618-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="d3618-133">*Video del comportamento di regolazione della Dollhouse*</span><span class="sxs-lookup"><span data-stu-id="d3618-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="d3618-134">1:1 prototipi di Visual Studio 1:10</span><span class="sxs-lookup"><span data-stu-id="d3618-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="d3618-135">Il presupposto iniziale era che le dimostrazioni di 1:1 sarebbero state sorprendenti, quasi come la ricerca di un insegnante di vita reale.</span><span class="sxs-lookup"><span data-stu-id="d3618-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="d3618-136">L'utente vedrebbe tutti gli elementi che il docente vede a una reale scalabilità.</span><span class="sxs-lookup"><span data-stu-id="d3618-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="d3618-137">Tuttavia, si è capito immediatamente che ci sarebbero alcuni problemi:</span><span class="sxs-lookup"><span data-stu-id="d3618-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="d3618-138">La maggior parte degli sviluppatori eseguirà le proprie app in uffici o in ambienti di dimensioni inferiori rispetto a quelle dimostrative.</span><span class="sxs-lookup"><span data-stu-id="d3618-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="d3618-139">Gli schermi sono additivi, ovvero l'intero ambiente virtuale verrà sovrapposto alla stanza di un utente.</span><span class="sxs-lookup"><span data-stu-id="d3618-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="d3618-140">Questo può creare confusione con due tabelle, forse doppi divani e muri che non si allineano.</span><span class="sxs-lookup"><span data-stu-id="d3618-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="d3618-141">E peggiori di tutto un ambiente virtuale limitato da un campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d3618-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="d3618-142">Quando è stata tentata la scalabilità minima 1:10, il risultato è una fantastica visualizzazione degli uccelli di una stanza realistica.</span><span class="sxs-lookup"><span data-stu-id="d3618-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="d3618-143">È possibile visualizzare tutti gli elementi che stavano procedendo da qualsiasi angolo nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="d3618-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="d3618-144">Ciò che era più sorprendente è che la maggior parte dei tester ritenesse molto più immersiva per visualizzare una versione ridotta, quindi non si è mai attivata la scala 1:1.</span><span class="sxs-lookup"><span data-stu-id="d3618-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="d3618-145">Quindi abbiamo deciso di rimuovere la versione 1:1 ed evitare il lavoro aggiuntivo necessario per adattare l'interfaccia utente e altri aspetti dell'app.</span><span class="sxs-lookup"><span data-stu-id="d3618-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="d3618-146">![Campo di visualizzazione con il ](images/designing-holograms/1-1-scale.png)
 *campo di visualizzazione scalabile 1:1 con scala 1:1*</span><span class="sxs-lookup"><span data-stu-id="d3618-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="d3618-147">![Campo di visualizzazione con il ](images/designing-holograms/1-10-scale.png)
 *campo di visualizzazione scalabile 1:10 con scala 1:10*</span><span class="sxs-lookup"><span data-stu-id="d3618-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="d3618-148">Uso dell'acquisizione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="d3618-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="d3618-149">Una delle funzionalità più caratteristiche di questa app è l'uso dell'acquisizione di realtà mista per insegnare e dimostrare concetti di progettazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d3618-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="d3618-150">Microsoft dispone di uno studio di acquisizione di realtà mista a San Francisco.</span><span class="sxs-lookup"><span data-stu-id="d3618-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="d3618-151">Microsoft concede anche questa tecnologia ad altri studio, tra cui la dimensione avatar a Washington D.C., metastage a Los Angeles, Dimension Studios a Londra, SK Telecom a Seoul e Volucap a Berlino.</span><span class="sxs-lookup"><span data-stu-id="d3618-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="d3618-152">Qui è possibile trovare altre informazioni sugli [studi di acquisizione di realtà miste](https://www.microsoft.com/mixed-reality/capture-studios).</span><span class="sxs-lookup"><span data-stu-id="d3618-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="d3618-153">*Metraggio non elaborato di Daniel Escudero da una delle fotocamere 106 in Mixed Reality Capture Studio a San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="d3618-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="d3618-154">Il processo di acquisizione genera una mesh, normali e una trama con fotogrammi chiave, che possono essere recapitati come file OBJ/PNG per un ulteriore post-produzione o pronti per la riproduzione come file MP4 compresso H. 264.</span><span class="sxs-lookup"><span data-stu-id="d3618-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="d3618-155">Questi file possono essere importati in progetti Unity, Unreal, native e WebXR.</span><span class="sxs-lookup"><span data-stu-id="d3618-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="d3618-156">I file possono essere eseguiti in Windows, iOS, Mac, Android, Magic LEAP e PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="d3618-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="d3618-157">*Il lettore di acquisizione fornito per analizzare mp4s che contengono video con reti audio e mesh incorporate.*</span><span class="sxs-lookup"><span data-stu-id="d3618-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="d3618-158">Manipolazione di acquisizioni e oggetti virtuali</span><span class="sxs-lookup"><span data-stu-id="d3618-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="d3618-159">Le acquisizioni di realtà miste producono rappresentazioni virtuali di persone o animali, ma in alcuni casi potrebbe essere necessario usare tali caratteri per interagire con altri oggetti virtuali.</span><span class="sxs-lookup"><span data-stu-id="d3618-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="d3618-160">I due esempi seguenti illustrano i diversi modi in cui abbiamo modificato le scene per ottenere questo effetto.</span><span class="sxs-lookup"><span data-stu-id="d3618-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="d3618-161">Regolazione dello sguardo Head</span><span class="sxs-lookup"><span data-stu-id="d3618-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="d3618-162">La regolazione Headgaze consente di spostare la testa di una persona acquisita in fase di esecuzione, vale a dire che è possibile avere un volto di acquisizione verso un utente.</span><span class="sxs-lookup"><span data-stu-id="d3618-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="d3618-163">In questo caso, è stato usato per visualizzare il campo di visualizzazione e il campo di interesse.</span><span class="sxs-lookup"><span data-stu-id="d3618-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="d3618-164">Di seguito è riportato un GameObject che funge da destinazione per lo sguardo a capo.</span><span class="sxs-lookup"><span data-stu-id="d3618-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="d3618-165">Quando si sposta la destinazione da Side a Side, l'intestazione dell'acquisizione segue.</span><span class="sxs-lookup"><span data-stu-id="d3618-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="d3618-166">Questo espediente è stato usato per assicurarsi che l'acquisizione inattiva sia sempre rivolta agli ologrammi posizionati in parti diverse della casa di bambola.</span><span class="sxs-lookup"><span data-stu-id="d3618-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![L'intestazione di acquisizione viene spostata in fase di esecuzione dopo un GameObject di destinazione in Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="d3618-168">*L'intestazione dell'acquisizione viene spostata in fase di esecuzione dopo un GameObject di destinazione in Unity.*</span><span class="sxs-lookup"><span data-stu-id="d3618-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="d3618-169">Sincronizzazione di oggetti animati</span><span class="sxs-lookup"><span data-stu-id="d3618-169">Syncing Animated Objects</span></span>

<span data-ttu-id="d3618-170">Il secondo è stato l'animazione degli oggetti da sincronizzare con lo spostamento di un'acquisizione.</span><span class="sxs-lookup"><span data-stu-id="d3618-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="d3618-171">In diverse parti dell'app sono stati importati obj sequenziali di un'acquisizione specifica ogni cinque frame.</span><span class="sxs-lookup"><span data-stu-id="d3618-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="d3618-172">Il obj è stato quindi animato nella scena per verificare che corrispondano al frame corrispondente dell'acquisizione.</span><span class="sxs-lookup"><span data-stu-id="d3618-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="d3618-173">Si tratta di un processo noioso di animazione e di fotogrammi, ma il risultato è eccezionale.</span><span class="sxs-lookup"><span data-stu-id="d3618-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="d3618-174">È ora possibile vedere un'acquisizione di realtà mista che interagisce con oggetti non acquisiti.</span><span class="sxs-lookup"><span data-stu-id="d3618-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animazione sincronizzata tra un'acquisizione di realtà mista e un pannello dell'interfaccia utente](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="d3618-176">*Animazione sincronizzata tra un'acquisizione di realtà mista e un pannello dell'interfaccia utente*</span><span class="sxs-lookup"><span data-stu-id="d3618-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="d3618-177">Processo creativo dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="d3618-177">UI creative process</span></span>

<span data-ttu-id="d3618-178">Quando è stata avviata la progettazione dell'interfaccia utente, abbiamo voluto illustrare alcuni dei Magic e delle possibilità che gli ologrammi offrivano.</span><span class="sxs-lookup"><span data-stu-id="d3618-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="d3618-179">Semplicemente mostrando le finestre 2D statiche e le caselle di testo non si ritengono nel mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="d3618-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="d3618-180">Molte delle possibilità a disposizione non vengono visualizzate, quindi fin dall'inizio abbiamo deciso di allontanarsi da questo e sfruttare completamente lo spazio 3D olografico.</span><span class="sxs-lookup"><span data-stu-id="d3618-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="d3618-181">Inizialmente, abbiamo iniziato ad aggiungere uno spessore ai pannelli, alle icone e alle informazioni di testo.</span><span class="sxs-lookup"><span data-stu-id="d3618-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="d3618-182">Tuttavia, come un utente, viene visualizzata una casella di testo.</span><span class="sxs-lookup"><span data-stu-id="d3618-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="d3618-183">Caselle di testo con immagini, ma non sono presenti.</span><span class="sxs-lookup"><span data-stu-id="d3618-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="d3618-184">Siamo andati oltre usando gli shader MRTK (Mixed Reality Toolkit).</span><span class="sxs-lookup"><span data-stu-id="d3618-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="d3618-185">Gli shader MRTK sono diventati uno strumento potente e sono state usate le funzionalità degli stencil per aggiungere una profondità negativa ai pannelli.</span><span class="sxs-lookup"><span data-stu-id="d3618-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="d3618-186">Ciò significa invece di aggiungere elementi davanti a una casella di testo, le icone vengono ora visualizzate dietro un pannello trasparente.</span><span class="sxs-lookup"><span data-stu-id="d3618-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="d3618-187">Ora, come un utente è qualcosa che non riesco più a replicare nel mondo reale e questo è il punto in cui la magia olografica è iniziata.</span><span class="sxs-lookup"><span data-stu-id="d3618-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="d3618-188">Inoltre, un utente che non mi piace leggere, faccio molto già nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="d3618-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="d3618-189">Ovviamente le icone funzionano in modo molto migliore rispetto al testo semplice, per offrire una guida ancora più potente, ho iniziato a creare un set di oggetti animati e avatar, ognuno dei quali racconta una piccola cosa che viene eseguita nel rispettivo scenario e come viene usata.</span><span class="sxs-lookup"><span data-stu-id="d3618-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animata di un sistema di menu interattivo olografico](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="d3618-191">Concetti di base</span><span class="sxs-lookup"><span data-stu-id="d3618-191">Core concepts</span></span>

<span data-ttu-id="d3618-192">**Frame olografico**</span><span class="sxs-lookup"><span data-stu-id="d3618-192">**Holographic frame**</span></span>

![GIF animata di un utente che si occupa della Dollhouse con il frame olografico evidenziato](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="d3618-194">**Sistemi di coordinate**</span><span class="sxs-lookup"><span data-stu-id="d3618-194">**Coordinate systems**</span></span>

![GIF animata di un utente che sta cercando la Dollhouse con i sistemi di coordinate evidenziati](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="d3618-196">**Tracciamento oculare**</span><span class="sxs-lookup"><span data-stu-id="d3618-196">**Eye tracking**</span></span>

![GIF animato di un utente che esamina gli ologrammi stazionari con il raggio d'occhio evidenziato](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="d3618-198">**Visualizzazione dell'analisi delle chat e mapping spaziale**</span><span class="sxs-lookup"><span data-stu-id="d3618-198">**Room scan visualization and spatial mapping**</span></span>

![GIF animato di tutte le aree all'interno della Dollhouse mappata](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="d3618-200">**Informazioni sulle scene**</span><span class="sxs-lookup"><span data-stu-id="d3618-200">**Scene understanding**</span></span>

![GIF animata di oggetti nella Dollhouse riconosciuta](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="d3618-202">**Punto e commit con raggi mano**</span><span class="sxs-lookup"><span data-stu-id="d3618-202">**Point and commit with hand rays**</span></span>

![GIF animata di un utente che solleva la mano con un raggio di mano evidenziato](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="d3618-204">Minuti di prova</span><span class="sxs-lookup"><span data-stu-id="d3618-204">"Try it out" moments</span></span>

<span data-ttu-id="d3618-205">La progettazione di ologrammi insegna concetti di realtà mista, ma consente anche di provarli nella propria stanza.</span><span class="sxs-lookup"><span data-stu-id="d3618-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="d3618-206">Una volta apportate alcune di queste spiegazioni, viene sospesa la casa di bambola e in un momento interattivo.</span><span class="sxs-lookup"><span data-stu-id="d3618-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="d3618-207">Di seguito sono riportati alcuni esempi di questi momenti interattivi:</span><span class="sxs-lookup"><span data-stu-id="d3618-207">Here are some examples of those interactive moments:</span></span>

![GIF animata del frame di rilevamento mano che mostra quando vengono rilevate mani e quando entrano nel campo della visualizzazione](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="d3618-209">*Frame di rilevamento mano che indica quando vengono rilevate le mani e quando entrano nel campo della visualizzazione.*</span><span class="sxs-lookup"><span data-stu-id="d3618-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animata di interazione con i cristalli in collisione attraverso un'interazione molto più lunga](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="d3618-211">*Interazione con i cristalli in collisione attraverso un'interazione molto più lunga*</span><span class="sxs-lookup"><span data-stu-id="d3618-211">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animata di esplorazione near Interaction affordances](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="d3618-213">*Esplorazione di near Interaction affordances*</span><span class="sxs-lookup"><span data-stu-id="d3618-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="d3618-214">Informazioni sul team</span><span class="sxs-lookup"><span data-stu-id="d3618-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="d3618-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="d3618-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="d3618-216"><i>Progettista tecnico lead</i></span><span class="sxs-lookup"><span data-stu-id="d3618-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="d3618-217">Dan è il direttore creativo sulla progettazione degli ologrammi e attualmente funziona come responsabile della progettazione per la realtà mista di Microsoft a San Francisco ed è stato in precedenza un progettista di uno degli studi di realtà mista di Microsoft a Londra.</span><span class="sxs-lookup"><span data-stu-id="d3618-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="d3618-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="d3618-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="d3618-219"><i>Artista 3D Senior</i></span><span class="sxs-lookup"><span data-stu-id="d3618-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="d3618-220">Martin conduce grafica 3D e progettazione dell'interfaccia utente sulla progettazione degli ologrammi ed era in precedenza un artista 3D Senior presso uno degli studi di realtà mista di Microsoft a Berlino.</span><span class="sxs-lookup"><span data-stu-id="d3618-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="d3618-221">Un enorme ringraziamento al team di progettazione della realtà mista per la condivisione di una conoscenza così elevata e a persone straordinarie con la [teoria degli oggetti](https://objecttheory.com/) per essere i colleghi essenziali a ogni passaggio del progetto.</span><span class="sxs-lookup"><span data-stu-id="d3618-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="d3618-222">Grazie per il talento straordinario, per la passione e per gli occhi eccezionali per la progettazione.</span><span class="sxs-lookup"><span data-stu-id="d3618-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d3618-223">Scaricare l'app per la progettazione di ologrammi</span><span class="sxs-lookup"><span data-stu-id="d3618-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)