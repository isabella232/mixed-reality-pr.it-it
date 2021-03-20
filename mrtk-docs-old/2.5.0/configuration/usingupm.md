---
title: usingupm
description: Uso di MRTK in Unity pakage Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK pakages,
ms.openlocfilehash: bd8b4c3a828a5d5fd89d6a1fb0281c13e8fd9e4a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692188"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="94fa7-104">Toolkit per realtà mista e gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="94fa7-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="94fa7-105">A partire dalla versione 2.5.0, Microsoft Mixed Reality Toolkit è disponibile tramite Gestione pacchetti Unity (UPM), in Unity 2019,4 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="94fa7-105">Starting with version 2.5.0, the Microsoft Mixed Reality Toolkit is available using the Unity Package Manager (UPM), on Unity 2019.4 and newer.</span></span>

## <a name="installing-mixed-reality-features-using-the-unity-package-manager"></a><span data-ttu-id="94fa7-106">Installazione delle funzionalità della realtà mista tramite Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="94fa7-106">Installing Mixed Reality features using the Unity Package Manager</span></span>

<span data-ttu-id="94fa7-107">Gestione pacchetti Unity usa un [file manifesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) per determinare i pacchetti da installare e i registri (Server) da cui possono essere installati.</span><span class="sxs-lookup"><span data-stu-id="94fa7-107">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) from which they can be installed.</span></span>

> [!Note]
> <span data-ttu-id="94fa7-108">A partire dalla versione 2.5.0 di MRTK, la registrazione iniziale del server e dei pacchetti è una procedura manuale per progetto. per istruzioni dettagliate, vedere le sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="94fa7-108">As of version 2.5.0 of the MRTK, initial registration of the server and packages is a per-project, manual procedure, please read the following sections for detailed instructions.</span></span>
>
> <span data-ttu-id="94fa7-109">Questo processo è necessario a causa dell'uso di UPM per la funzionalità di ricerca NPM legacy (/-/All) non supportata da Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="94fa7-109">This process is required due to UPM's use of legacy npm search functionality (/-/all) that is not supported by Azure DevOps.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="94fa7-110">Registrazione del server del componente realtà mista</span><span class="sxs-lookup"><span data-stu-id="94fa7-110">Registering the Mixed Reality component server</span></span>

<span data-ttu-id="94fa7-111">Per ogni progetto che utilizzerà Microsoft Mixed Reality Toolkit, il `manifest.json` file (nella cartella Pacchetti) dovrà aggiungere il registro di sistema con ambito di realtà misto.</span><span class="sxs-lookup"><span data-stu-id="94fa7-111">For each project that will be using the Microsoft Mixed Reality Toolkit, the `manifest.json` file (in the Packages folder) will need to have the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="94fa7-112">Di seguito viene illustrato come modificare correttamente `manifest.json` per supportare la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="94fa7-112">The following illustrate how to properly modify `manifest.json` to support Mixed Reality.</span></span>

1. <span data-ttu-id="94fa7-113">Aprire `<projectRoot>/Packages/manifest.json` in un editor di testo, ad esempio [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="94fa7-113">Open `<projectRoot>/Packages/manifest.json` in a text editor, such as [Visual Studio Code](https://code.visualstudio.com/).</span></span>
1. <span data-ttu-id="94fa7-114">Nella parte superiore del file manifesto aggiungere il server di realtà misto alla sezione del registro di sistema con ambito e salvare il file.</span><span class="sxs-lookup"><span data-stu-id="94fa7-114">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span>

```
{
  "scopedRegistries": [
    {
      "name": "Microsoft Mixed Reality",
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/",
      "scopes": [
        "com.microsoft.mixedreality",
        "com.microsoft.spatialaudio"
      ]
    }
  ],
```

### <a name="adding-mrtk-packages"></a><span data-ttu-id="94fa7-115">Aggiunta di pacchetti MRTK</span><span class="sxs-lookup"><span data-stu-id="94fa7-115">Adding MRTK packages</span></span>

<span data-ttu-id="94fa7-116">Quando il registro con ambito Microsoft Mixed Reality è stato aggiunto al manifesto, è possibile specificare i pacchetti MRTK.</span><span class="sxs-lookup"><span data-stu-id="94fa7-116">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the MRTK packages can be specified.</span></span>

<span data-ttu-id="94fa7-117">La sezione relativa a [Gestione pacchetti Unity](../packages-releases/MRTK_Packages.md#unity-package-manager) dell'articolo relativo al [pacchetto del Toolkit di realtà mista](../packages-releases/MRTK_Packages.md) descrive i pacchetti MRTK disponibili, il relativo contenuto e gli scenari per l'uso.</span><span class="sxs-lookup"><span data-stu-id="94fa7-117">The [Unity Package Manager](../packages-releases/MRTK_Packages.md#unity-package-manager) section of the [Mixed Reality Toolkit package](../packages-releases/MRTK_Packages.md) article describes the available MRTK packages, their contents and the scenarios for their use.</span></span>

<span data-ttu-id="94fa7-118">Per aggiungere un pacchetto MRTK, modificare la sezione dipendenze del `Packages/manifest.json` file.</span><span class="sxs-lookup"><span data-stu-id="94fa7-118">To add an MRTK package, modify the dependencies section of the `Packages/manifest.json` file.</span></span> <span data-ttu-id="94fa7-119">Nell'esempio seguente viene illustrato come aggiungere i pacchetti Foundation, Tools ed examples, il pacchetto di asset standard verrà aggiunto automaticamente come dipendenza della base.</span><span class="sxs-lookup"><span data-stu-id="94fa7-119">The following example illustrates adding the foundation, tools and examples packages, the standard assets package will be added automatically as a dependency of the foundation.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.0",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.0",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.0",
```

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="94fa7-120">Gestione delle funzionalità della realtà mista con gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="94fa7-120">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="94fa7-121">Una volta aggiunto al manifesto del pacchetto, un pacchetto del Toolkit di realtà mista può essere gestito tramite l'interfaccia utente di gestione pacchetti Unity.</span><span class="sxs-lookup"><span data-stu-id="94fa7-121">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Pacchetto UPM MRTK Foundation](../features/Images/Packaging/MRTK_FoundationUPM.png)

> [!Note]
> <span data-ttu-id="94fa7-123">Se un pacchetto del Toolkit di realtà mista viene rimosso tramite Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i [passaggi descritti in precedenza](#adding-mrtk-packages).</span><span class="sxs-lookup"><span data-stu-id="94fa7-123">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#adding-mrtk-packages).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="94fa7-124">Esempi di utilizzo del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="94fa7-124">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="94fa7-125">Diversamente da quando si usano i file di pacchetto asset (con estensione file unitypackage Tools), `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` non vengono importati automaticamente gli asset e le scene di esempio.</span><span class="sxs-lookup"><span data-stu-id="94fa7-125">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="94fa7-126">Per usare uno o più degli esempi, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="94fa7-126">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="94fa7-127">Nell'editor di Unity passare a `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="94fa7-127">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="94fa7-128">Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="94fa7-128">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="94fa7-129">Individuare gli esempi desiderati nell' `Samples` elenco</span><span class="sxs-lookup"><span data-stu-id="94fa7-129">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="94fa7-130">Fare clic su`Import into Project`.</span><span class="sxs-lookup"><span data-stu-id="94fa7-130">Click `Import into Project`</span></span>

![Importazione di esempi](../features/Images/Packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="94fa7-132">Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="94fa7-132">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!Note]
> <span data-ttu-id="94fa7-133">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="94fa7-133">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="94fa7-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="94fa7-134">See Also</span></span>

- [<span data-ttu-id="94fa7-135">Pacchetti Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="94fa7-135">Mixed Reality Toolkit packages</span></span>](../packages-releases/MRTK_Packages.md)
