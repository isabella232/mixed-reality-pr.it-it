---
title: Modalità di gioco Unity
description: Informazioni su come usare la modalità di riproduzione nell'editor di Unity per visualizzare in anteprima le modifiche dell'applicazione in un dispositivo senza distribuire un'app.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicazione remota, comunicazione remota olografica, lettore di comunicazione remota olografica, HoloLens, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, modalità di gioco unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392293"
---
# <a name="unity-play-mode"></a><span data-ttu-id="1da1d-104">Modalità di gioco Unity</span><span class="sxs-lookup"><span data-stu-id="1da1d-104">Unity Play Mode</span></span>

<span data-ttu-id="1da1d-105">Un modo rapido per lavorare al progetto Unity è usare la "modalità di riproduzione", che esegue l'app in locale nell'editor di Unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="1da1d-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="1da1d-106">Unity usa Holographic Remoting per offrire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale.</span><span class="sxs-lookup"><span data-stu-id="1da1d-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="1da1d-107">La modalità di riproduzione può essere usata anche con Windows Mixed Reality visore collegato al PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="1da1d-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="1da1d-108">Configurazione della comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="1da1d-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="1da1d-109">Prima di tutto, è [necessario installare l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1da1d-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="1da1d-110">Eseguire l'app Holographic Remoting Player HoloLens 2 e verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi</span><span class="sxs-lookup"><span data-stu-id="1da1d-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="1da1d-111">Per usare il plug-in OpenXR è necessaria la versione 2.4 o successiva</span><span class="sxs-lookup"><span data-stu-id="1da1d-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot di Holographic Remoting Player in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="1da1d-113">Modalità di riproduzione Unity con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1da1d-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="1da1d-114">Con Holographic Remoting è possibile sperimentare l'app in HoloLens mentre viene eseguita nell'editor unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="1da1d-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="1da1d-115">Lo sguardo, il movimento, la voce e l'input di mapping spaziale vengono inviati dal dispositivo HoloLens al PC.</span><span class="sxs-lookup"><span data-stu-id="1da1d-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="1da1d-116">I fotogrammi sottoposti a rendering vengono quindi inviati nuovamente a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1da1d-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="1da1d-117">Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo.</span><span class="sxs-lookup"><span data-stu-id="1da1d-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="1da1d-118">Holographic Remoting richiede un PC veloce e Wi-Fi connessione.</span><span class="sxs-lookup"><span data-stu-id="1da1d-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="1da1d-119">Per altri dettagli, vedere la documentazione [di Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="1da1d-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="1da1d-120">Per ottenere risultati ottimali, assicurarsi che l'app imposta correttamente il [punto di attivazione.](focus-point-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="1da1d-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="1da1d-121">Ciò consente a Holographic Remoting di adattare al meglio la scena alla latenza della connessione wireless.</span><span class="sxs-lookup"><span data-stu-id="1da1d-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1da1d-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1da1d-122">See Also</span></span>

* [<span data-ttu-id="1da1d-123">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="1da1d-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
