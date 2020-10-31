---
title: Uso di WebVR con la realtà mista di Windows
description: Descrive WebVR e come usarlo con Microsoft Edge negli auricolari per la realtà mista di Windows.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, WebVR, Edge, Microsoft Edge, esplorazione Web
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131855"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="13969-104">Uso di WebVR con la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="13969-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="13969-105">La maggior parte dei Web browser moderni ha deprecato il supporto di WebVR a favore di WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR.</span><span class="sxs-lookup"><span data-stu-id="13969-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="13969-106">Installare [il nuovo Microsoft Edge per il](using-microsoft-edge.md) supporto di WebXR.</span><span class="sxs-lookup"><span data-stu-id="13969-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="13969-107">Informazioni su WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-107">What is WebVR</span></span>

<span data-ttu-id="13969-108">[WebVR](https://webvr.info) è una specifica aperta che consente di sperimentare VR nel browser.</span><span class="sxs-lookup"><span data-stu-id="13969-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="13969-109">Se un sito Web implementa il supporto WebVR e fornisce contenuto 3D, può visualizzare contenuti immersivi nell'auricolare, con il consenso dell'utente.</span><span class="sxs-lookup"><span data-stu-id="13969-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="13969-110">Qual è la differenza tra WebVR e l'esplorazione del Web in VR</span><span class="sxs-lookup"><span data-stu-id="13969-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="13969-111">WebVR è una tecnologia che consente a un autore di siti Web di aggiungere funzionalità VR a una pagina.</span><span class="sxs-lookup"><span data-stu-id="13969-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="13969-112">L'API WebVR viene usata da una pagina per visualizzare il contenuto 3D (ad esempio, un video di 360 gradi o un modello 3D o un gioco 3D) per l'intero auricolare.</span><span class="sxs-lookup"><span data-stu-id="13969-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="13969-113">**Esempio:** Visualizzazione di un video 360 in [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="13969-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="13969-114">Se una pagina supporta WebVR, verrà aggiunto un pulsante o un altro elemento dell'interfaccia utente su cui è possibile fare clic per immettere VR.</span><span class="sxs-lookup"><span data-stu-id="13969-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="13969-115">Esplorare il Web in VR significa usare il browser Microsoft Edge mentre si indossa la cuffia, come una lavagna di app 2D all'interno della Cliffhouse.</span><span class="sxs-lookup"><span data-stu-id="13969-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="13969-116">Tutti i siti Web supportano WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-116">Do all websites support WebVR</span></span>

<span data-ttu-id="13969-117">No.</span><span class="sxs-lookup"><span data-stu-id="13969-117">No.</span></span> <span data-ttu-id="13969-118">Gli autori di siti Web devono acconsentire esplicitamente all'uso di WebVR e possono inoltre creare siti ottimizzati per browser, cuffie e controller specifici.</span><span class="sxs-lookup"><span data-stu-id="13969-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="13969-119">Ad esempio, alcuni contenuti di WebVR sono ottimizzati solo per i dispositivi mobili VR.</span><span class="sxs-lookup"><span data-stu-id="13969-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="13969-120">Tenere inoltre presente che i siti Web devono creare e fornire in modo esplicito il contenuto di WebVR.</span><span class="sxs-lookup"><span data-stu-id="13969-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="13969-121">Il numero di siti con contenuto compatibile con WebVR sta crescendo ogni giorno.</span><span class="sxs-lookup"><span data-stu-id="13969-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="13969-122">Posso usare le mie vive/Oculus e così via per visualizzare il contenuto di WebVR in Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="13969-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="13969-123">No.</span><span class="sxs-lookup"><span data-stu-id="13969-123">No.</span></span> <span data-ttu-id="13969-124">Per usare WebVR in Edge, è necessario usare un auricolare di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="13969-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="13969-125">Tuttavia, potrebbe essere possibile accedere al contenuto di WebVR in un altro browser. vedere l'elenco completo dei dispositivi e dei browser compatibili all'indirizzo: [WebVR. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="13969-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="13969-126">Dove è possibile trovare la documentazione per gli sviluppatori di WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="13969-127">La documentazione per gli sviluppatori è disponibile qui: [documentazione per sviluppatori WebVR](https://docs.microsoft.com/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="13969-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="13969-128">Ho trovato un sito Web con WebVR che non funziona in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="13969-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="13969-129">Cosa devo fare</span><span class="sxs-lookup"><span data-stu-id="13969-129">What do I do</span></span>

<span data-ttu-id="13969-130">È possibile segnalare i siti interrotti direttamente al team del browser Microsoft Edge in [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o tramite twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span><span class="sxs-lookup"><span data-stu-id="13969-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="13969-131">È anche possibile registrare i bug usando l'app hub di feedback di Windows nella categoria:</span><span class="sxs-lookup"><span data-stu-id="13969-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="13969-132">Microsoft Edge: problemi del sito Web ></span><span class="sxs-lookup"><span data-stu-id="13969-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="13969-133">Che cosa è una pagina efficace per verificare se WebVR funziona</span><span class="sxs-lookup"><span data-stu-id="13969-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="13969-134">Vedere gli [esempi di webvr.info](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="13969-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="13969-135">Ricerca per categorie configurare WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-135">How do I set up WebVR</span></span>

<span data-ttu-id="13969-136">Per sperimentare il contenuto di WebVR in un auricolare di realtà mista di Windows (usando l'hardware o la simulazione), è necessario:</span><span class="sxs-lookup"><span data-stu-id="13969-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>

1. <span data-ttu-id="13969-137">Verificare che l'auricolare sia connesso.</span><span class="sxs-lookup"><span data-stu-id="13969-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="13969-138">Avviare Microsoft Edge sul desktop o in una realtà mista.</span><span class="sxs-lookup"><span data-stu-id="13969-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="13969-139">Passare a una pagina abilitata per WebVR.</span><span class="sxs-lookup"><span data-stu-id="13969-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="13969-140">Fare clic sul pulsante ENTER VR nella pagina (la posizione e la rappresentazione visiva di questo pulsante possono variare per sito Web).</span><span class="sxs-lookup"><span data-stu-id="13969-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="13969-141">Potrebbe essere simile a: </span><span class="sxs-lookup"><span data-stu-id="13969-141">It may look similar to:</span></span>\
   ![Immagine di occhiali VR](images/75px-enter-vr.png)
5. <span data-ttu-id="13969-143">La prima volta che si tenta di immettere VR in un dominio specifico, il browser richiederà il consenso per l'utilizzo della visualizzazione immersiva, quindi fare clic su Sì:</span><span class="sxs-lookup"><span data-stu-id="13969-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![Interfaccia utente di consenso visualizzata al primo tentativo di immissione di VR in un particolare dominio](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="13969-145">L'auricolare dovrebbe iniziare a visualizzare il contenuto di WebVR.</span><span class="sxs-lookup"><span data-stu-id="13969-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="13969-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="13969-146">See also</span></span>

* [<span data-ttu-id="13969-147">Risoluzione dei problemi > WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="13969-148">Come accedere alla prima esperienza WebVR</span><span class="sxs-lookup"><span data-stu-id="13969-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="13969-149">Uso di giochi e app in realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="13969-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="13969-150">Home realtà mista</span><span class="sxs-lookup"><span data-stu-id="13969-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="13969-151">Sistema di rilevamento</span><span class="sxs-lookup"><span data-stu-id="13969-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="13969-152">Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="13969-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="13969-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="13969-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="13969-154">Commenti sulla presentazione</span><span class="sxs-lookup"><span data-stu-id="13969-154">Filing feedback</span></span>](filing-feedback.md)
