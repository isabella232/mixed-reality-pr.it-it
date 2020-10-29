---
title: Streaming in Unreal
description: Guida allo streaming in Unreal per HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, streaming, PC, app remota olografica, holographic remoting player, documentazione
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9c60168b409a10a815313b1254a979244763b9e6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701927"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="e0c78-104">Streaming in Unreal</span><span class="sxs-lookup"><span data-stu-id="e0c78-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="e0c78-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="e0c78-105">Overview</span></span>
<span data-ttu-id="e0c78-106">Lo streaming da un PC a HoloLens offre due vantaggi fondamentali:</span><span class="sxs-lookup"><span data-stu-id="e0c78-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="e0c78-107">Consente all'app di realtà mista di sfruttare la potenza di calcolo del PC.</span><span class="sxs-lookup"><span data-stu-id="e0c78-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="e0c78-108">Consente di accelerare l'iterazione dello sviluppo.</span><span class="sxs-lookup"><span data-stu-id="e0c78-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="e0c78-109">Prima di tutto, devi scaricare [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) nel dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e0c78-109">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="e0c78-110">Questo consente all'app di trasmettere direttamente in streaming al lettore remoto in HoloLens dalle origini seguenti:</span><span class="sxs-lookup"><span data-stu-id="e0c78-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="e0c78-111">Editor Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="e0c78-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="e0c78-112">Un eseguibile Windows in pacchetto</span><span class="sxs-lookup"><span data-stu-id="e0c78-112">A packaged Windows executable</span></span> 

<span data-ttu-id="e0c78-113">Durante lo streaming, hai accesso a quasi tutte le funzionalità di HoloLens che avresti a disposizione durante l'esecuzione di un'applicazione in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e0c78-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="e0c78-114">Questo include [tracciamento mano e articolazioni](unreal-hand-tracking.md) (se usi HoloLens 2), [mapping spaziale](unreal-spatial-mapping.md) e [ancoraggi nello spazio](unreal-spatial-anchors.md), ma esclude le funzionalità riportate in questo [elenco di limitazioni](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="e0c78-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="e0c78-115">La qualità dello streaming dipende in larga misura dalla potenza del segnale Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="e0c78-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="e0c78-116">Tutte le funzionalità vengono abilitate automaticamente per il lettore Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="e0c78-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="e0c78-117">Se si trova una funzionalità che richiede l'autorizzazione dell'utente (ad esempio, il tracciamento oculare) per il funzionamento sul flusso ma non durante l'esecuzione nel dispositivo, verificare di aver abilitato le funzionalità appropriate nelle impostazioni del progetto.</span><span class="sxs-lookup"><span data-stu-id="e0c78-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="e0c78-118">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="e0c78-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e0c78-119"><strong>Origine</strong></span><span class="sxs-lookup"><span data-stu-id="e0c78-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="e0c78-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e0c78-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="e0c78-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e0c78-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="e0c78-122"><strong>Visori VR immersive</strong></span><span class="sxs-lookup"><span data-stu-id="e0c78-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e0c78-123">Editor Unreal</span><span class="sxs-lookup"><span data-stu-id="e0c78-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="e0c78-124">✔️</span><span class="sxs-lookup"><span data-stu-id="e0c78-124">✔️</span></span></td>
        <td><span data-ttu-id="e0c78-125">✔️</span><span class="sxs-lookup"><span data-stu-id="e0c78-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0c78-126">Pacchetto Windows</span><span class="sxs-lookup"><span data-stu-id="e0c78-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="e0c78-127">✔️</span><span class="sxs-lookup"><span data-stu-id="e0c78-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="e0c78-128">Streaming dall'editor Unreal</span><span class="sxs-lookup"><span data-stu-id="e0c78-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="e0c78-129">In qualità di sviluppatore, noterai che lo streaming dall'editor Unreal al dispositivo HoloLens offre grandi vantaggi in fase di test, ovvero non è più necessario attendere che l'app venga compilata e distribuita prima di provare gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="e0c78-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="e0c78-130">Puoi trovare istruzioni dettagliate sullo [streaming dall'editor Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) nell'ultima sezione della serie di esercitazioni di introduzione a Unreal.</span><span class="sxs-lookup"><span data-stu-id="e0c78-130">You can find detailed instructions on [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="e0c78-131">Streaming da un eseguibile Windows in pacchetto</span><span class="sxs-lookup"><span data-stu-id="e0c78-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="e0c78-132">A partire da Unreal 4.25.1, è possibile trasmettere l'app in streaming a un dispositivo HoloLens 2 da un eseguibile Windows in pacchetto seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="e0c78-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="e0c78-133">Passa a **File > Package Project > Windows** (File > Crea pacchetto progetto > Windows) nel menu dell'editor.</span><span class="sxs-lookup"><span data-stu-id="e0c78-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="e0c78-134">Scegli una posizione in cui salvare il pacchetto e fai clic su **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="e0c78-134">Choose a location to save your package and click **Select Folder** .</span></span>

2. <span data-ttu-id="e0c78-135">Terminata la creazione del pacchetto, apri **Holographic Remoting Player** in HoloLens 2 e prendi nota dell'indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="e0c78-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="e0c78-136">Lascia aperto **Holographic Remoting Player** e usa il prompt della riga di comando per:</span><span class="sxs-lookup"><span data-stu-id="e0c78-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="e0c78-137">accedere con cd alla directory locale in cui hai salvato il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="e0c78-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="e0c78-138">Immettere il comando seguente: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="e0c78-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="e0c78-139">Dovrebbe essere usato automaticamente il nome dell'applicazione nelle impostazioni del progetto per creare il pacchetto di Windows.</span><span class="sxs-lookup"><span data-stu-id="e0c78-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="e0c78-140">Se per qualche motivo sono diversi, usa il nome dell'eseguibile di Windows al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="e0c78-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="e0c78-141">Premi INVIO e inizierà lo streaming dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e0c78-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="e0c78-142">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0c78-142">See also</span></span>
* [<span data-ttu-id="e0c78-143">Cronologia delle versioni di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e0c78-143">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="e0c78-144">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="e0c78-144">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="e0c78-145">Stabilire una connessione sicura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e0c78-145">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
