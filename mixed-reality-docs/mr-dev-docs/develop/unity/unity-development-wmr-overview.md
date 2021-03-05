---
title: Sviluppo in Unity per VR
description: Guida introduttiva alla creazione di app di realtà mista in Unity per VR e visori VR immersive di Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realtà mista, sviluppo, guida introduttiva, nuovo progetto, conversione, funzionalità, fotocamera, simulazione, emulazione, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, che cos'è la realtà virtuale, che cos'è la realtà aumentata, MRTK, mixed reality toolkit, input vocale, fotocamera individuabile, emulatore, Azure, esercitazioni
ms.openlocfilehash: 3a1914fc6bc35b2ec4fb7364818a21522e01c6e1
ms.sourcegitcommit: 5694cc472bde67c940204ebe6671b0598501e62a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "102126604"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="3f084-104">Sviluppo in Unity per VR e Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3f084-104">Unity development for VR and Windows Mixed Reality</span></span>

![Logo banner di Unity](../images/unity_logo_banner.png)

<span data-ttu-id="3f084-106">Se si usa Unity per la prima volta, prima di continuare è consigliabile esplorare le [esercitazioni](https://unity3d.com/learn/tutorials) di livello principiante nella piattaforma Unity Learn.</span><span class="sxs-lookup"><span data-stu-id="3f084-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="3f084-107">È anche opportuno visitare i [forum di Unity sulla realtà mista](https://forum.unity3d.com/forums/hololens.102/) per partecipare alla community online impegnata nella creazione di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3f084-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="3f084-108">In questi ambienti si scoprono spesso risorse o soluzioni estremamente interessanti.</span><span class="sxs-lookup"><span data-stu-id="3f084-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="3f084-109">Per iniziare a usare MRTK, passare ai checkpoint di sviluppo illustrati di seguito.</span><span class="sxs-lookup"><span data-stu-id="3f084-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f084-110">Se si ha a disposizione un progetto Unity da trasmettere a un visore VR immersive di Windows Mixed Reality, consultare le **[guide alla conversione](../porting-apps/porting-overview.md)** .</span><span class="sxs-lookup"><span data-stu-id="3f084-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="3f084-111">Checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="3f084-111">Development checkpoints</span></span>

<span data-ttu-id="3f084-112">Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3f084-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="3f084-113">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="3f084-113">1. Getting started</span></span>

<span data-ttu-id="3f084-114">È presente piccolo set di impostazioni di Unity da modificare manualmente per Windows Mixed Reality e lo sviluppo per VR.</span><span class="sxs-lookup"><span data-stu-id="3f084-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="3f084-115">Le impostazioni sono suddivise in due categorie: per progetto e per scena.</span><span class="sxs-lookup"><span data-stu-id="3f084-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="3f084-116">Al termine di questa sezione, saranno disponibili le impostazioni di progetto e gli strumenti necessari per iniziare a creare le app personali.</span><span class="sxs-lookup"><span data-stu-id="3f084-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="3f084-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="3f084-117">Checkpoint</span></span>  |  <span data-ttu-id="3f084-118">Risultato</span><span class="sxs-lookup"><span data-stu-id="3f084-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3f084-119">Installare gli ultimi aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="3f084-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="3f084-120">Scaricare e installare il pacchetto Unity più recente e configurare il progetto per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="3f084-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="3f084-121">Configurazione del progetto per WMR</span><span class="sxs-lookup"><span data-stu-id="3f084-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="3f084-122">Vedere le informazioni su come creare applicazioni che eseguono il rendering di contenuto digitale in dispositivi di visualizzazione olografici e VR</span><span class="sxs-lookup"><span data-stu-id="3f084-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="3f084-123">2. Componenti fondamentali</span><span class="sxs-lookup"><span data-stu-id="3f084-123">2. Core building blocks</span></span>

<span data-ttu-id="3f084-124">Dopo aver avviato un nuovo progetto immersivo, sono necessari alcuni blocchi predefiniti di base per sviluppare app immersive.</span><span class="sxs-lookup"><span data-stu-id="3f084-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="3f084-125">Tutti i componenti di base per le applicazioni di realtà mista sono esposti in modo coerente con altre API di Unity</span><span class="sxs-lookup"><span data-stu-id="3f084-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="3f084-126">Potrebbero non essere tutti necessari nell'immediato, ma è bene esaminarli nella fase iniziale.</span><span class="sxs-lookup"><span data-stu-id="3f084-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="3f084-127">Dopo aver esaminato i blocchi predefiniti fondamentali indicati di seguito, si avrà a disposizione un insieme completo di funzionalità che è possibile integrare nei progetti VR.</span><span class="sxs-lookup"><span data-stu-id="3f084-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="3f084-128">3. Funzionalità avanzate</span><span class="sxs-lookup"><span data-stu-id="3f084-128">3. Advanced features</span></span>

<span data-ttu-id="3f084-129">Altre funzionalità chiave per le applicazioni immersive sono disponibili tramite le API di Unity senza la necessità di ulteriori pacchetti o configurazioni.</span><span class="sxs-lookup"><span data-stu-id="3f084-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="3f084-130">Dopo aver esaminato le funzionalità più avanzate offerte da Unity, sarà possibile creare app VR più complesse.</span><span class="sxs-lookup"><span data-stu-id="3f084-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="3f084-131">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="3f084-131">Feature</span></span>  |  <span data-ttu-id="3f084-132">Capabilities</span><span class="sxs-lookup"><span data-stu-id="3f084-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="3f084-133">Perdita del tracciamento</span><span class="sxs-lookup"><span data-stu-id="3f084-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="3f084-134">Gestire gli scenari in cui il dispositivo non è in grado di individuare la propria posizione nello spazio globale dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="3f084-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="3f084-135">Input da tastiera</span><span class="sxs-lookup"><span data-stu-id="3f084-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="3f084-136">Ottenere input nelle app da tastiere reali e di realtà mista</span><span class="sxs-lookup"><span data-stu-id="3f084-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="3f084-137">4. Distribuzione in un dispositivo o un emulatore</span><span class="sxs-lookup"><span data-stu-id="3f084-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="3f084-138">Non appena il progetto Unity olografico è pronto per il test, il passaggio successivo è quello di esportare e compilare una soluzione Unity di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f084-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="3f084-139">Con questa soluzione di Visual Studio è possibile eseguire l'applicazione in dispositivi reali o simulati.</span><span class="sxs-lookup"><span data-stu-id="3f084-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="3f084-140">Al termine di questa sezione, sarà possibile distribuire l'applicazione in un dispositivo o un emulatore adatto alle specifiche esigenze di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="3f084-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="3f084-141">Visore VR immersive di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3f084-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="3f084-142">Simulatore di visore VR immersive di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3f084-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="3f084-143">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="3f084-143">What's next?</span></span>

<span data-ttu-id="3f084-144">Il lavoro degli sviluppatori non finisce mai, soprattutto per quanto riguarda la conoscenza di nuovi strumenti o SDK.</span><span class="sxs-lookup"><span data-stu-id="3f084-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="3f084-145">Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati.</span><span class="sxs-lookup"><span data-stu-id="3f084-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="3f084-146">Questi argomenti e queste risorse non sono presentati in ordine sequenziale e possono quindi essere esplorati liberamente.</span><span class="sxs-lookup"><span data-stu-id="3f084-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="3f084-147">Conversione</span><span class="sxs-lookup"><span data-stu-id="3f084-147">Porting</span></span>

<span data-ttu-id="3f084-148">Se si hanno a disposizione app di cui si vuole eseguire la conversione, sarà utile consultare gli articoli elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="3f084-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="3f084-149">Conversione di app VR in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3f084-149">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="3f084-150">Aggiornamento di app SteamVR per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3f084-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="3f084-151">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="3f084-151">Additional resources</span></span>

<span data-ttu-id="3f084-152">Prima di entrare nel mondo della realtà mista in totale autonomia, è consigliabile esaminare la documentazione aggiuntiva indicata di seguito.</span><span class="sxs-lookup"><span data-stu-id="3f084-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="3f084-153">Guida per appassionati di VR</span><span class="sxs-lookup"><span data-stu-id="3f084-153">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="3f084-154">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="3f084-154">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="3f084-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f084-155">See also</span></span> 

* [<span data-ttu-id="3f084-156">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="3f084-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="3f084-157">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="3f084-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="3f084-158">Esportazione e creazione di una soluzione di Visual Studio Unity</span><span class="sxs-lookup"><span data-stu-id="3f084-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="3f084-159">Procedure consigliate per l'uso con Unity e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f084-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)