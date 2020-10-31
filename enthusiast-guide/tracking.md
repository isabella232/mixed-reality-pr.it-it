---
title: Domande frequenti sul rilevamento
description: Rilevamento della risoluzione dei problemi di realtà mista di Windows che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, monitoraggio
ms.openlocfilehash: 7a7e6add79af5917749ba241347d6cf719f6ed90
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132095"
---
# <a name="tracking-faqs"></a><span data-ttu-id="a2978-104">Domande frequenti sul rilevamento</span><span class="sxs-lookup"><span data-stu-id="a2978-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="a2978-105">Il rilevamento dell'auricolare è stato interrotto</span><span class="sxs-lookup"><span data-stu-id="a2978-105">My headset has stopped tracking</span></span>

<span data-ttu-id="a2978-106">Assicurarsi che le spie siano accese e che non sia presente alcun ostacolo alle fotocamere di rilevamento interne all'interno dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="a2978-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="a2978-107">Se il rilevamento viene perso, la ripresa potrebbe richiedere alcuni secondi.</span><span class="sxs-lookup"><span data-stu-id="a2978-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="a2978-108">Se non riprende, riavviare il portale di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a2978-108">If it doesn't resume, restart the Windows Mixed Reality Portal.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="a2978-109">Posso esaminare ma non riesco a tradurre (sono bloccato in 3DOF)</span><span class="sxs-lookup"><span data-stu-id="a2978-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="a2978-110">Ciò significa che il sistema di rilevamento non è in grado di generare la richiesta o che l'applicazione ha interrotto l'uso dei nuovi dati di post per il rendering.</span><span class="sxs-lookup"><span data-stu-id="a2978-110">This means that the tracking system cannot generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="a2978-111">Verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a2978-111">Check the following:</span></span>

* <span data-ttu-id="a2978-112">Assicurarsi che la stanza abbia una luce sufficiente.</span><span class="sxs-lookup"><span data-stu-id="a2978-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="a2978-113">Assicurarsi che la chat room disponga di informazioni sufficienti per la traccia.</span><span class="sxs-lookup"><span data-stu-id="a2978-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="a2978-114">Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a2978-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="a2978-115">Se il messaggio viene mantenuto, contattare il [supporto](https://support.microsoft.com/) tecnico</span><span class="sxs-lookup"><span data-stu-id="a2978-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-completely-frozen"></a><span data-ttu-id="a2978-116">La visualizzazione in HMD è completamente bloccata</span><span class="sxs-lookup"><span data-stu-id="a2978-116">The view in the HMD is completely frozen</span></span>

<span data-ttu-id="a2978-117">Ciò significa in genere che l'applicazione o un componente a livello di sistema non è riuscito.</span><span class="sxs-lookup"><span data-stu-id="a2978-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="a2978-118">Provare a:</span><span class="sxs-lookup"><span data-stu-id="a2978-118">Try to:</span></span>

1. <span data-ttu-id="a2978-119">Per uscire dall'applicazione, fare clic sul pulsante "Home".</span><span class="sxs-lookup"><span data-stu-id="a2978-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="a2978-120">Scollegare il dispositivo, chiudere MRP e collegare di nuovo il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a2978-120">Unplug the device, close MRP and plug the device back in.</span></span>
3. <span data-ttu-id="a2978-121">Riavvia il PC.</span><span class="sxs-lookup"><span data-stu-id="a2978-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="a2978-122">Il mondo si è bloccato brevemente e potrebbe essere inclinato o capovolto prima di tornare al normale</span><span class="sxs-lookup"><span data-stu-id="a2978-122">The world briefly froze and perhaps tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="a2978-123">Il problema potrebbe essere causato da un'applicazione o da un componente a livello di sistema che raggiunge un errore irreversibile o da una mancanza temporanea di memoria o risorse della CPU.</span><span class="sxs-lookup"><span data-stu-id="a2978-123">This could be caused by an application or system level component hitting a fatal error, or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="a2978-124">Per verificare:</span><span class="sxs-lookup"><span data-stu-id="a2978-124">To check:</span></span>

1. <span data-ttu-id="a2978-125">Aprire Task Manager e assicurarsi che almeno il 20% della CPU sia disponibile, che il 400MB di memoria sia disponibile e che i/o del disco siano inferiori al 80%.</span><span class="sxs-lookup"><span data-stu-id="a2978-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="a2978-126">Passare a **Visualizzatore eventi > registri di Windows > applicazione** per individuare eventuali errori che si sono verificati a partire dall'ora del blocco.</span><span class="sxs-lookup"><span data-stu-id="a2978-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="a2978-127">Cercare qualsiasi elemento che si riferisca ai sensori HoloLens, alla realtà mista o all'applicazione in esecuzione in quel momento.</span><span class="sxs-lookup"><span data-stu-id="a2978-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="a2978-128">Questi log potrebbero spiegare la causa dell'errore.</span><span class="sxs-lookup"><span data-stu-id="a2978-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="a2978-129">Riavviare il computer se il problema persiste.</span><span class="sxs-lookup"><span data-stu-id="a2978-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="a2978-130">Il mondo è stato capovolto momentaneamente e restituito al normale</span><span class="sxs-lookup"><span data-stu-id="a2978-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="a2978-131">Questa situazione è in genere causata da errori durante il recupero dei dati dei sensori dall'auricolare per informare gli algoritmi di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="a2978-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="a2978-132">Se il problema si verifica di frequente:</span><span class="sxs-lookup"><span data-stu-id="a2978-132">If this happens frequently:</span></span>

1. <span data-ttu-id="a2978-133">Collegare la cuffia a una porta USB 3,0 diversa.</span><span class="sxs-lookup"><span data-stu-id="a2978-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="a2978-134">Collegare la cuffia direttamente al PC anziché in un hub USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="a2978-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="a2978-135">Se il problema persiste, contattare il [supporto](https://support.microsoft.com/)tecnico.</span><span class="sxs-lookup"><span data-stu-id="a2978-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="a2978-136">Il mondo è inclinato, ma è possibile spostarsi e aggirare la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="a2978-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="a2978-137">Se i dati del sensore vengono registrati nei dati dell'ambiente nel PC, è possibile che la realtà mista di Windows appaia inclinata, a volte in modo permanente.</span><span class="sxs-lookup"><span data-stu-id="a2978-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="a2978-138">Per risolvere il problema:</span><span class="sxs-lookup"><span data-stu-id="a2978-138">To fix this:</span></span>

1. <span data-ttu-id="a2978-139">Scollegare l'auricolare, chiudere la realtà mista di Windows e collegare di nuovo l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="a2978-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="a2978-140">Riavvia il PC.</span><span class="sxs-lookup"><span data-stu-id="a2978-140">Restart the PC.</span></span>
3. <span data-ttu-id="a2978-141">Cancellare i dati dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="a2978-141">Clear your environment data.</span></span>