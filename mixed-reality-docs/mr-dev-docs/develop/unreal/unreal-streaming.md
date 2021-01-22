---
title: Streaming in Unreal
description: Informazioni su come trasmettere le app Unreal a HoloLens 2, incluse le limitazioni di streaming e le opzioni della riga di comando.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, streaming, PC, app holographic remoting, holographic remoting player, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: bbae1170850ec4bbb41bc9274223d19102adddae
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580337"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="a05a1-104">Streaming in Unreal</span><span class="sxs-lookup"><span data-stu-id="a05a1-104">Streaming in Unreal</span></span>

<span data-ttu-id="a05a1-105">Lo streaming da un PC a HoloLens offre due vantaggi fondamentali:</span><span class="sxs-lookup"><span data-stu-id="a05a1-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="a05a1-106">Consente all'app di realtà mista di sfruttare la potenza di calcolo del PC.</span><span class="sxs-lookup"><span data-stu-id="a05a1-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="a05a1-107">Consente di accelerare l'iterazione dello sviluppo.</span><span class="sxs-lookup"><span data-stu-id="a05a1-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="a05a1-108">Prima di tutto, devi scaricare [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) nel dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a05a1-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="a05a1-109">Holographic Remoting Player consente all'app di trasmettere in streaming direttamente al lettore remoto di HoloLens dalle origini seguenti:</span><span class="sxs-lookup"><span data-stu-id="a05a1-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="a05a1-110">Editor Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="a05a1-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="a05a1-111">Un eseguibile Windows in pacchetto</span><span class="sxs-lookup"><span data-stu-id="a05a1-111">A packaged Windows executable</span></span> 

<span data-ttu-id="a05a1-112">Durante lo streaming, hai accesso a quasi tutte le funzionalità di HoloLens che avresti a disposizione durante l'esecuzione di un'applicazione in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a05a1-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="a05a1-113">Questo include [tracciamento mano e articolazioni](unreal-hand-tracking.md) se si usa HoloLens 2, [mapping spaziale](unreal-spatial-mapping.md) e [ancoraggi nello spazio](unreal-spatial-anchors.md), ma esclude le funzionalità riportate in questo [elenco](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="a05a1-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="a05a1-114">La qualità dello streaming dipende in larga misura dalla potenza del segnale Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="a05a1-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="a05a1-115">Tutte le funzionalità vengono abilitate automaticamente per il lettore Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="a05a1-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="a05a1-116">Se si trova una funzionalità che richiede l'autorizzazione dell'utente (ad esempio, il tracciamento oculare) per il funzionamento sul flusso ma non durante l'esecuzione nel dispositivo, verificare di aver abilitato le funzionalità appropriate nelle impostazioni del progetto.</span><span class="sxs-lookup"><span data-stu-id="a05a1-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="a05a1-117">Limitazioni dello streaming</span><span class="sxs-lookup"><span data-stu-id="a05a1-117">Streaming limitations</span></span>

<span data-ttu-id="a05a1-118">Le mesh della mano, la fotocamera HoloLens e la tastiera di sistema non sono disponibili in streaming.</span><span class="sxs-lookup"><span data-stu-id="a05a1-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="a05a1-119">Si noti che l'input vocale per le app trasmesse in streaming può essere acquisito tramite il microfono del PC da cui viene eseguito lo streaming.</span><span class="sxs-lookup"><span data-stu-id="a05a1-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="a05a1-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a05a1-120">OpenXR</span></span>

<span data-ttu-id="a05a1-121">Unreal 4.26 in esecuzione in OpenXR supporta lo streaming nelle versioni 2.4.0 e successive di Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="a05a1-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="a05a1-122">A OpenXR che esegue lo streaming nella versione 2.4.0 manca il supporto per il mapping spaziale e gli ancoraggi nello spazio.</span><span class="sxs-lookup"><span data-stu-id="a05a1-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="a05a1-123">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a05a1-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a05a1-124"><strong>Origine</strong></span><span class="sxs-lookup"><span data-stu-id="a05a1-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="a05a1-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens 1a generazione</strong></a></span><span class="sxs-lookup"><span data-stu-id="a05a1-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="a05a1-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="a05a1-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="a05a1-127"><strong>Visori VR immersive</strong></span><span class="sxs-lookup"><span data-stu-id="a05a1-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a05a1-128">Editor Unreal</span><span class="sxs-lookup"><span data-stu-id="a05a1-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="a05a1-129">✔️</span><span class="sxs-lookup"><span data-stu-id="a05a1-129">✔️</span></span></td>
        <td><span data-ttu-id="a05a1-130">✔️</span><span class="sxs-lookup"><span data-stu-id="a05a1-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="a05a1-131">Pacchetto Windows</span><span class="sxs-lookup"><span data-stu-id="a05a1-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a05a1-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a05a1-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="a05a1-133">Streaming dall'editor Unreal</span><span class="sxs-lookup"><span data-stu-id="a05a1-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="a05a1-134">In qualità di sviluppatore, si noterà che lo streaming dall'editor Unreal al dispositivo HoloLens offre vantaggi significativi in fase di test, soprattutto perché non è più necessario attendere che l'app venga compilata e distribuita prima di provare gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="a05a1-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="a05a1-135">È possibile trovare istruzioni dettagliate per lo [streaming dall'editor Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) nella serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="a05a1-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="a05a1-136">Streaming da un eseguibile Windows in pacchetto</span><span class="sxs-lookup"><span data-stu-id="a05a1-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="a05a1-137">In Unreal 4.25.1 e versioni successive, è possibile trasmettere l'app in streaming a un dispositivo HoloLens 2 da un eseguibile Windows in pacchetto:</span><span class="sxs-lookup"><span data-stu-id="a05a1-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="a05a1-138">Passa a **File > Package Project > Windows** (File > Crea pacchetto progetto > Windows) nel menu dell'editor.</span><span class="sxs-lookup"><span data-stu-id="a05a1-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="a05a1-139">Scegliere una posizione in cui salvare il pacchetto e selezionare **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="a05a1-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="a05a1-140">Terminata la creazione del pacchetto, apri **Holographic Remoting Player** in HoloLens 2 e prendi nota dell'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="a05a1-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="a05a1-141">Lascia aperto **Holographic Remoting Player** e usa il prompt della riga di comando per:</span><span class="sxs-lookup"><span data-stu-id="a05a1-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="a05a1-142">accedere con cd alla directory locale in cui hai salvato il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="a05a1-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="a05a1-143">Immettere il comando seguente: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="a05a1-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="a05a1-144">Dovrebbe essere usato automaticamente il nome dell'applicazione nelle impostazioni del progetto per creare il pacchetto di Windows.</span><span class="sxs-lookup"><span data-stu-id="a05a1-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="a05a1-145">Se per qualche motivo sono diversi, usa il nome dell'eseguibile di Windows al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="a05a1-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="a05a1-146">Premi INVIO e inizierà lo streaming dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a05a1-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="a05a1-147">Opzioni della riga di comando</span><span class="sxs-lookup"><span data-stu-id="a05a1-147">Command line options</span></span>

<span data-ttu-id="a05a1-148">Altre opzioni della riga di comando per lo streaming da ogni piattaforma in Unreal Engine 4.26 e versioni successive sono disponibili nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="a05a1-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="a05a1-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a05a1-149">See also</span></span>

* [<span data-ttu-id="a05a1-150">Cronologia delle versioni di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a05a1-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="a05a1-151">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="a05a1-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="a05a1-152">Stabilire una connessione sicura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a05a1-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)