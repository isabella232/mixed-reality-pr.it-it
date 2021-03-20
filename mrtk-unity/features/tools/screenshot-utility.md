---
title: ScreenshotUtility
description: Documentazione su Hopw per usare lo strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4fbd5457dd0af502ddedf30a10482690cd8e1a1d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693068"
---
# <a name="screenshot-utility"></a><span data-ttu-id="a212b-104">Utilità screenshot</span><span class="sxs-lookup"><span data-stu-id="a212b-104">Screenshot utility</span></span>

<span data-ttu-id="a212b-105">Spesso le schermate in Unity per la documentazione e le immagini promozionali possono essere gravose e l'output sembra spesso minore di quanto sia auspicabile.</span><span class="sxs-lookup"><span data-stu-id="a212b-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="a212b-106">Qui `ScreenshotUtility` entra in gioco la classe (xrif: Microsoft. MixedReality. Toolkit. Utilities. Editor. ScreenshotUtility).</span><span class="sxs-lookup"><span data-stu-id="a212b-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="a212b-107">La classe ScreenshotUtility aiuta ad acquisire screenshot tramite voci di menu e API pubbliche nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="a212b-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="a212b-108">Le schermate possono essere acquisite con diverse risoluzioni e con colori cancellati trasparenti per l'uso in una semplice composizione post di immagini.</span><span class="sxs-lookup"><span data-stu-id="a212b-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="a212b-109">Lo strumento non supporta l'acquisizione di schermate da una compilazione autonoma.</span><span class="sxs-lookup"><span data-stu-id="a212b-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="a212b-110">Acquisizione di schermate</span><span class="sxs-lookup"><span data-stu-id="a212b-110">Taking screenshots</span></span>

<span data-ttu-id="a212b-111">Le schermate possono essere facilmente acquisite nell'editor selezionando *reality Toolkit->Utilities->acquisire screenshot* e quindi selezionare l'opzione desiderata.</span><span class="sxs-lookup"><span data-stu-id="a212b-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="a212b-112">Assicurarsi che la scheda della finestra di gioco sia visibile se l'acquisizione non viene riprodotta oppure è possibile che non sia stata salvata una schermata.</span><span class="sxs-lookup"><span data-stu-id="a212b-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="a212b-113">Per impostazione predefinita, tutte le schermate vengono salvate nel [percorso della cache temporanea](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), il percorso dello screenshot verrà visualizzato nella console di Unity.</span><span class="sxs-lookup"><span data-stu-id="a212b-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Voce di menu utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="a212b-115">Acquisizione di screenshot di esempio</span><span class="sxs-lookup"><span data-stu-id="a212b-115">Example screenshot capture</span></span>

<span data-ttu-id="a212b-116">La schermata seguente è stata acquisita con l'opzione *"risoluzione 4x (sfondo trasparente)"* .</span><span class="sxs-lookup"><span data-stu-id="a212b-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="a212b-117">Viene così restituita un'immagine ad alta risoluzione con qualsiasi pixel normalmente rappresentato dal colore chiaro salvato come pixel trasparenti.</span><span class="sxs-lookup"><span data-stu-id="a212b-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="a212b-118">Questa tecnica aiuta gli sviluppatori a presentare le proprie applicazioni per lo Store o altri punti di supporto, sovrapponendo questa immagine sopra le altre immagini.</span><span class="sxs-lookup"><span data-stu-id="a212b-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Esempio di acquisizione dell'utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
