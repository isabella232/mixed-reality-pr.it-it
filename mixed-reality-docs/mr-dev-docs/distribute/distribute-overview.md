---
title: Distribuzione delle app
description: Panoramica delle diverse opzioni di distribuzione per diverse piattaforme e archivi di pubblicazione supportati.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realtà mista, cuffie immersive, app, UWP, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, predato, certificazione, pacchetto, appx, merchandising
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215976"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="53c90-104">Distribuzione delle app</span><span class="sxs-lookup"><span data-stu-id="53c90-104">Distributing your apps</span></span>

![Floaty Bird 3D app lancher in WMR Home](images/distribute-hero-image.png)

<span data-ttu-id="53c90-106">La possibilità di ottenere le tue app negli utenti o in tutto il mondo è l'aspetto più importante, a volte accurato, di qualsiasi attività di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="53c90-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="53c90-107">Il processo è stato semplificato in un set di risorse, che dipendono dallo scenario di distribuzione e distribuzione più adatto per l'utente o il team.</span><span class="sxs-lookup"><span data-stu-id="53c90-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="53c90-108">Opzioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="53c90-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="53c90-109">Se si condivide l'app con un'altra parte, è necessario compilare e fornire il file appx.</span><span class="sxs-lookup"><span data-stu-id="53c90-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="53c90-110">Se si usa il programma di installazione delle app, è necessario condividere anche il certificato con l'utente.</span><span class="sxs-lookup"><span data-stu-id="53c90-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="53c90-111">Se si sta condividendo con un'organizzazione, è necessario un account aziendale o dell'Istituto di istruzione e l'accesso all'infrastruttura [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) per le organizzazioni.</span><span class="sxs-lookup"><span data-stu-id="53c90-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="53c90-112">Se si è l'entità di condivisione, è necessario essere un amministratore nel tenant e usare l'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) per rendere disponibile l'app.</span><span class="sxs-lookup"><span data-stu-id="53c90-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="53c90-113">Un'altra opzione consiste nel condividere il file appx e le dipendenze dell'app con l'utente finale.</span><span class="sxs-lookup"><span data-stu-id="53c90-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="53c90-114">Se si è l'utente finale, l'app verrà scaricata automaticamente o sarà disponibile per il download una volta eseguita la registrazione al tenant dell'organizzazione di condivisione.</span><span class="sxs-lookup"><span data-stu-id="53c90-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="53c90-115"><strong>Scenario</strong></span><span class="sxs-lookup"><span data-stu-id="53c90-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="53c90-116"><strong>Installazioni del dispositivo locale</strong></span><span class="sxs-lookup"><span data-stu-id="53c90-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="53c90-117"><strong>Condividi con altri utenti</strong></span><span class="sxs-lookup"><span data-stu-id="53c90-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="53c90-118"><strong>Condividere con un'organizzazione</strong></span><span class="sxs-lookup"><span data-stu-id="53c90-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programma di installazione app</strong></span><span class="sxs-lookup"><span data-stu-id="53c90-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="53c90-120">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-120">✔️</span></span></td>
    <td><span data-ttu-id="53c90-121">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portale aziendale</strong></a></span><span class="sxs-lookup"><span data-stu-id="53c90-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="53c90-123">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-installazione app obbligatoria</strong></a></span><span class="sxs-lookup"><span data-stu-id="53c90-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="53c90-125">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="53c90-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="53c90-127">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-127">✔️</span></span></td>
    <td><span data-ttu-id="53c90-128">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store per le aziende</strong></a></span><span class="sxs-lookup"><span data-stu-id="53c90-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="53c90-130">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Pacchetto di provisioning</strong></a></span><span class="sxs-lookup"><span data-stu-id="53c90-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="53c90-132">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-132">✔️</span></span></td>
    <td><span data-ttu-id="53c90-133">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-133">✔️</span></span></td>
    <td><span data-ttu-id="53c90-134">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="53c90-135"><a href="#other-scenarios"><strong>Distribuzione Win32 personalizzata</strong></a> (non disponibile per i dispositivi HoloLens: vedere di seguito)</span><span class="sxs-lookup"><span data-stu-id="53c90-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="53c90-136">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-136">✔️</span></span></td>
    <td><span data-ttu-id="53c90-137">✔️</span><span class="sxs-lookup"><span data-stu-id="53c90-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="53c90-138">Il programma di installazione dell'app non è attualmente disponibile per i dispositivi gestiti o HoloLens (1a generazione).</span><span class="sxs-lookup"><span data-stu-id="53c90-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="53c90-139">Altri scenari</span><span class="sxs-lookup"><span data-stu-id="53c90-139">Other scenarios</span></span>

* <span data-ttu-id="53c90-140">È possibile generare una Win32. File EXE che usa la destinazione di compilazione autonoma del PC da Unity per la distribuzione di applicazioni Win32, inclusi il gioco di Steam e il pass.</span><span class="sxs-lookup"><span data-stu-id="53c90-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="53c90-141">Una volta ottenuto il. EXE, è possibile inviare le app come di consueto alla piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="53c90-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="53c90-142">Se è necessario installare un'applicazione HoloLens 2 mentre si è offline, fare riferimento alle istruzioni [Secure HoloLens 2 offline](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) oppure installare l'app tramite un pacchetto di provisioning senza abilitare la modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="53c90-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="53c90-143">È anche possibile distribuire le compilazioni nel dispositivo e condividerle con altri sviluppatori che hanno la modalità di sviluppo abilitata tramite la [distribuzione e il debug con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o l' [installazione di un pacchetto dell'applicazione con il portale del dispositivo](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span><span class="sxs-lookup"><span data-stu-id="53c90-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="53c90-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53c90-144">See also</span></span>
* [<span data-ttu-id="53c90-145">Ricerca, installazione e disinstallazione delle applicazioni dal Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="53c90-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

