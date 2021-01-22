---
title: Pubblicazione in Microsoft Store
description: Informazioni su come creare pacchetti, certificare e pubblicare le applicazioni di realtà mista Unreal in Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR realtà mista, visore VR di windows mixed reality, visore VR per realtà virtuale, pubblicazione, distribuzione, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583597"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="2b026-104">Pubblicazione in Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2b026-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="2b026-105">Quando l'app Unreal è pronta per essere pubblicata, è necessario aggiornare alcune impostazioni di progetto prima dell'invio a Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="2b026-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="2b026-106">Tutte queste impostazioni hanno valori predefiniti. Per rappresentare l'applicazione in modo ottimale, tuttavia, devono essere modificate per la fase di produzione.</span><span class="sxs-lookup"><span data-stu-id="2b026-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="2b026-107">Impostazioni di progetto per la creazione di pacchetti per lo Store</span><span class="sxs-lookup"><span data-stu-id="2b026-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="2b026-108">Selezionare prima **Project Settings > Description** (Impostazioni progetto > Descrizione) e aggiornare le informazioni sul gioco e sull'editore:</span><span class="sxs-lookup"><span data-stu-id="2b026-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="2b026-109">**Game Name** (Nome gioco) verrà visualizzato nel riquadro dell'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="2b026-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="2b026-110">**Company Distinguished Name** (Nome distinto società) viene usato durante la generazione del certificato di progetto e deve avere il formato seguente:</span><span class="sxs-lookup"><span data-stu-id="2b026-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="2b026-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="2b026-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Screenshot dell'editor di Unreal con la sezione relativa alla descrizione espansa nelle impostazioni di progetto](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="2b026-113">Espandere la sezione **HoloLens** delle impostazioni di progetto e aggiornare le risorse per la creazione di pacchetti.</span><span class="sxs-lookup"><span data-stu-id="2b026-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="2b026-114">Questi nomi di risorse verranno visualizzati nella pagina dell'applicazione nello Store:</span><span class="sxs-lookup"><span data-stu-id="2b026-114">These resource names will be shown on the application’s store page:</span></span>

![Screenshot dell'editor di Unreal con la sezione relativa alla creazione di pacchetti espansa nelle impostazioni di progetto](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="2b026-116">Espandere la sezione **Images** (Immagini) e aggiornare le immagini predefinite dello Store con le trame che rappresentano l'app dello Store.</span><span class="sxs-lookup"><span data-stu-id="2b026-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="2b026-117">Facoltativamente, selezionare la casella di controllo **3D Logo** (Logo 3D) per caricare un file con estensione glb da usare come cubo live 3D all'avvio dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="2b026-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Screenshot dell'editor di Unreal con la sezione relativa alle immagini espansa nelle impostazioni di progetto](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="2b026-119">Infine, selezionare **Generate New** (Genera nuovo) per generare un certificato di firma dal nome del progetto e dal nome distinto della società</span><span class="sxs-lookup"><span data-stu-id="2b026-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="2b026-120">Impostare un valore per **Tile Background Color** (Colore di sfondo riquadro), che verrà visualizzato al posto di eventuali pixel trasparenti nelle immagini dello Store.</span><span class="sxs-lookup"><span data-stu-id="2b026-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="2b026-121">Espandere l'elenco a discesa e abilitare **Use Retail Windows Store Environment** (Usa ambiente Windows Store retail) per l'esecuzione in dispositivi bloccati per utenti retail e non sbloccati per sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="2b026-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Screenshot dell'editor di Unreal con la sezione relativa alla generazione del certificato espansa nelle impostazioni di progetto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="2b026-123">Programma di installazione app facoltativo</span><span class="sxs-lookup"><span data-stu-id="2b026-123">Optional App Installer</span></span>

<span data-ttu-id="2b026-124">È possibile creare un file Programma di installazione app in **Project Settings > HoloLens** (Impostazioni progetto > HoloLens), che può essere usato per distribuire l'applicazione al di fuori dello Store.</span><span class="sxs-lookup"><span data-stu-id="2b026-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="2b026-125">Abilitare la casella di controllo **Should Create App Installer** (Devi creare Programma di installazione app) e impostare un URL o un percorso di rete nella posizione in cui si vuole archiviare il pacchetto appxbundle del gioco.</span><span class="sxs-lookup"><span data-stu-id="2b026-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Screenshot dell'editor di Unreal con la sezione relativa al Programma di installazione app espansa nelle impostazioni di progetto](images/unreal-publishing-img-05.png)

<span data-ttu-id="2b026-127">Quando si crea il pacchetto dell'app, vengono generati sia appxbundle sia appinstaller.</span><span class="sxs-lookup"><span data-stu-id="2b026-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="2b026-128">Caricare appxbundle nell'URL di installazione e quindi avviare appinstaller per installare l'app dal percorso di rete.</span><span class="sxs-lookup"><span data-stu-id="2b026-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="2b026-129">Kit di certificazione app Windows</span><span class="sxs-lookup"><span data-stu-id="2b026-129">Windows App Certification Kit</span></span>

<span data-ttu-id="2b026-130">Windows 10 SDK viene fornito con il Kit di certificazione app Windows (WACK) per convalidare problemi comuni che possono influire sul caricamento di un pacchetto nello Store.</span><span class="sxs-lookup"><span data-stu-id="2b026-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="2b026-131">È possibile trovare WACK nella directory Windows Kits, in genere nel percorso seguente:</span><span class="sxs-lookup"><span data-stu-id="2b026-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="2b026-132">Dopo la creazione del pacchetto del file appx per la pubblicazione, eseguire **appcertui.exe** e seguire le istruzioni per eseguire la scansione di appx:</span><span class="sxs-lookup"><span data-stu-id="2b026-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Screenshot dell'app selezionata per la convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="2b026-134">Selezionare **Convalida app di Store**:</span><span class="sxs-lookup"><span data-stu-id="2b026-134">Select **Validate Store App**:</span></span>

![Screenshot della selezione della convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="2b026-136">Individuare appx nella sezione superiore e selezionare **Avanti**:</span><span class="sxs-lookup"><span data-stu-id="2b026-136">Browse for the appx in the top section and select **Next**:</span></span>

![Screenshot della selezione di test nel Kit di certificazione app Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="2b026-138">Selezionare **Avanti** per eseguire i test e creare un report:</span><span class="sxs-lookup"><span data-stu-id="2b026-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="2b026-139">Tutti i test disponibili che possono essere eseguiti nel PC host saranno abilitati per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="2b026-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Screenshot dello stato di avanzamento della convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="2b026-141">Attendere il completamento dei test.</span><span class="sxs-lookup"><span data-stu-id="2b026-141">Wait for the tests to finish.</span></span> <span data-ttu-id="2b026-142">Al termine, nella finestra finale verrà indicato l'esito positivo o negativo, che può essere visualizzato nel report salvato.</span><span class="sxs-lookup"><span data-stu-id="2b026-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Screenshot dei risultati del report finale nel Kit di certificazione app Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="2b026-144">Errore noto di WACK nella versione 4.25</span><span class="sxs-lookup"><span data-stu-id="2b026-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="2b026-145">Il plug-in di Windows Mixed Reality in Unreal 4.25 non riuscirà a eseguire WACK perché vengono inclusi alcuni file binari x64 durante la creazione del pacchetto per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2b026-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="2b026-146">L'errore sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2b026-146">The failure will look like this:</span></span>

![Screenshot dell'errore dovuto all'analizzatore binario e alle API supportate dal Kit di certificazione app Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="2b026-148">Per correggere il problema:</span><span class="sxs-lookup"><span data-stu-id="2b026-148">To fix the issue:</span></span>
1. <span data-ttu-id="2b026-149">Passare alla directory radice di installazione o di origine di Unreal aprendo un progetto di Unreal e facendo clic con il pulsante destro del mouse sull'icona di Unreal nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="2b026-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="2b026-150">Fare clic con il pulsante destro del mouse su UE4Editor, selezionare Properties (Proprietà) e passare al percorso indicato alla voce **Location** (Posizione):</span><span class="sxs-lookup"><span data-stu-id="2b026-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="2b026-151">In **WindowsMixedRealityHMD.Build.cs** modificare la **riga 32** da:</span><span class="sxs-lookup"><span data-stu-id="2b026-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="2b026-152">in:</span><span class="sxs-lookup"><span data-stu-id="2b026-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="2b026-153">Chiudere Unreal, riaprire il progetto e creare nuovamente il pacchetto per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2b026-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="2b026-154">Eseguire nuovamente WACK e l'errore verrà rimosso.</span><span class="sxs-lookup"><span data-stu-id="2b026-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="2b026-155">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2b026-155">See also</span></span>

* [<span data-ttu-id="2b026-156">Invio di un'app a Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2b026-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="2b026-157">Kit di certificazione app Windows</span><span class="sxs-lookup"><span data-stu-id="2b026-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="2b026-158">Creare un file del programma di installazione app manualmente</span><span class="sxs-lookup"><span data-stu-id="2b026-158">Create an App Installer file manually</span></span>](/windows/msix/app-installer/how-to-create-appinstaller-file)