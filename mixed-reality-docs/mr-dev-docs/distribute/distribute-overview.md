---
title: Distribuzione delle app
description: Panoramica delle diverse opzioni di distribuzione per diverse piattaforme e archivi di pubblicazione supportati.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realtà mista, cuffie immersive, app, UWP, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, predato, certificazione, pacchetto, appx, merchandising
ms.openlocfilehash: b4b82557ba274852ebb3f97058017fa2e5db1c02
ms.sourcegitcommit: 9e9d58de4513655c7daa71ff4b5b2c2b115ab959
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97034582"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="efe5b-104">Distribuzione delle app</span><span class="sxs-lookup"><span data-stu-id="efe5b-104">Distributing your apps</span></span>

![Floaty Bird 3D app lancher in WMR Home](images/distribute-hero-image.png)

<span data-ttu-id="efe5b-106">La possibilità di ottenere le tue app negli utenti o in tutto il mondo è l'aspetto più importante, a volte accurato, di qualsiasi attività di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="efe5b-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="efe5b-107">Il processo è stato semplificato in un set di risorse elencate di seguito, che dipendono tutti dallo scenario di distribuzione e distribuzione più adatto per l'utente o il team.</span><span class="sxs-lookup"><span data-stu-id="efe5b-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="efe5b-108">Opzioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="efe5b-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="efe5b-109">Se si condivide l'app con un'altra parte, è necessario compilare e fornire il file appx.</span><span class="sxs-lookup"><span data-stu-id="efe5b-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="efe5b-110">Se si usa il programma di installazione delle app, è necessario condividere anche il certificato con l'utente.</span><span class="sxs-lookup"><span data-stu-id="efe5b-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="efe5b-111">Se si sta condividendo con un'organizzazione, è necessario un account aziendale o dell'Istituto di istruzione e l'accesso all'infrastruttura [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) per le organizzazioni.</span><span class="sxs-lookup"><span data-stu-id="efe5b-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="efe5b-112">Se si è l'entità di condivisione, è necessario essere un amministratore nel tenant e usare l'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) per rendere disponibile l'app.</span><span class="sxs-lookup"><span data-stu-id="efe5b-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="efe5b-113">Un'altra opzione consiste nel condividere il file appx e le dipendenze dell'app con l'utente finale.</span><span class="sxs-lookup"><span data-stu-id="efe5b-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="efe5b-114">Se si è l'utente finale, l'app verrà scaricata automaticamente o sarà disponibile per il download una volta eseguita la registrazione al tenant dell'organizzazione di condivisione.</span><span class="sxs-lookup"><span data-stu-id="efe5b-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="efe5b-115"><strong>Scenario</strong></span><span class="sxs-lookup"><span data-stu-id="efe5b-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="efe5b-116"><strong>Installazione del dispositivo locale</strong></span><span class="sxs-lookup"><span data-stu-id="efe5b-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="efe5b-117"><strong>Condividi con altri utenti</strong></span><span class="sxs-lookup"><span data-stu-id="efe5b-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="efe5b-118"><strong>Condividere con un'organizzazione</strong></span><span class="sxs-lookup"><span data-stu-id="efe5b-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programma di installazione app</strong></span><span class="sxs-lookup"><span data-stu-id="efe5b-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="efe5b-120">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-120">✔️</span></span></td>
    <td><span data-ttu-id="efe5b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portale aziendale</strong></a></span><span class="sxs-lookup"><span data-stu-id="efe5b-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="efe5b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-installazione app obbligatoria</strong></a></span><span class="sxs-lookup"><span data-stu-id="efe5b-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="efe5b-125">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="efe5b-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="efe5b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-127">✔️</span></span></td>
    <td><span data-ttu-id="efe5b-128">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-128">✔️</span></span></td><span data-ttu-id="efe5b-129">s</span><span class="sxs-lookup"><span data-stu-id="efe5b-129">s</span></span>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store per le aziende</strong></a></span><span class="sxs-lookup"><span data-stu-id="efe5b-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="efe5b-131">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-131">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Pacchetto di provisioning</strong></a></span><span class="sxs-lookup"><span data-stu-id="efe5b-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="efe5b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-133">✔️</span></span></td>
    <td><span data-ttu-id="efe5b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-134">✔️</span></span></td>
    <td><span data-ttu-id="efe5b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-135">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="efe5b-136"><a href="#additional-scenarios"><strong>Distribuzione Win32 personalizzata</strong></a> (non disponibile per i dispositivi HoloLens: vedere di seguito)</span><span class="sxs-lookup"><span data-stu-id="efe5b-136"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="efe5b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-137">✔️</span></span></td>
    <td><span data-ttu-id="efe5b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="efe5b-138">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="efe5b-139">Il programma di installazione dell'app non è attualmente disponibile per i dispositivi gestiti o HoloLens (1a generazione).</span><span class="sxs-lookup"><span data-stu-id="efe5b-139">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="efe5b-140">Scenari aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="efe5b-140">Additional scenarios</span></span>

* <span data-ttu-id="efe5b-141">Per la distribuzione di applicazioni Win32, inclusi il gioco di Steam e il passaggio del gioco, è possibile creare una Win32. File EXE che usa la destinazione di compilazione autonoma del PC da Unity e invia le app come di consueto alla piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="efe5b-141">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="efe5b-142">Se è necessario installare un'applicazione HoloLens 2 mentre si è offline, fare riferimento alle istruzioni [Secure HoloLens 2 offline](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) oppure installare l'app tramite un pacchetto di provisioning senza abilitare la modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="efe5b-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="efe5b-143">È anche possibile distribuire le compilazioni nel dispositivo e condividerle con altri sviluppatori che hanno la modalità di sviluppo abilitata tramite la [distribuzione e il debug con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o l' [installazione di un pacchetto dell'applicazione con il portale del dispositivo](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="efe5b-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="efe5b-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="efe5b-144">See also</span></span>
* [<span data-ttu-id="efe5b-145">Ricerca, installazione e disinstallazione delle applicazioni dal Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="efe5b-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

