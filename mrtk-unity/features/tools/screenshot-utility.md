---
title: Utilità screenshot
description: Documentazione sull'hopw per usare lo strumento screenshot in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a0c66969a9058adc790919f0054783b7368da8f6
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647085"
---
# <a name="screenshot-utility"></a><span data-ttu-id="d0ac7-104">Utilità screenshot</span><span class="sxs-lookup"><span data-stu-id="d0ac7-104">Screenshot utility</span></span>

<span data-ttu-id="d0ac7-105">Spesso acquisire screenshot in Unity per la documentazione e le immagini promozionali può essere un'attività gravosa e l'output spesso non è consigliabile.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="d0ac7-106">È qui che entra in gioco la classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).</span><span class="sxs-lookup"><span data-stu-id="d0ac7-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="d0ac7-107">La classe ScreenshotUtility consente di acquisire screenshot tramite voci di menu e API pubbliche all'interno dell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="d0ac7-108">Gli screenshot possono essere acquisiti a varie risoluzioni e con colori chiari trasparenti per l'uso nella semplice composizione post-stampa delle immagini.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="d0ac7-109">La creazione di screenshot da una build autonoma non è supportata da questo strumento.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="d0ac7-110">Screenshot</span><span class="sxs-lookup"><span data-stu-id="d0ac7-110">Taking screenshots</span></span>

<span data-ttu-id="d0ac7-111">Gli screenshot possono essere facilmente acquisite nell'editor selezionando **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Take Screenshot** e quindi selezionando l'opzione desiderata.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-111">Screenshots can be easily capture while in the editor by selecting **Mixed Reality** > **Toolkit** > **Utilities** > **Take Screenshot** and then selecting your desired option.</span></span> <span data-ttu-id="d0ac7-112">Assicurarsi che la scheda della finestra del gioco sia visibile se l'acquisizione non è in esecuzione oppure uno screenshot potrebbe non essere salvato.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="d0ac7-113">Per impostazione predefinita, tutti gli screenshot vengono salvati nel percorso della [cache](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)temporanea. Il percorso dello screenshot verrà visualizzato nella console di Unity.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Voce di menu dell'utilità Screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="d0ac7-115">Screenshot di esempio</span><span class="sxs-lookup"><span data-stu-id="d0ac7-115">Example screenshot capture</span></span>

<span data-ttu-id="d0ac7-116">Lo screenshot seguente è stato acquisito con l'opzione *"Risoluzione 4x (sfondo trasparente)".*</span><span class="sxs-lookup"><span data-stu-id="d0ac7-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="d0ac7-117">In questo modo viene restituita un'immagine ad alta risoluzione con i pixel normalmente rappresentati dal colore non crittografato salvato come pixel trasparenti.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="d0ac7-118">Questa tecnica consente agli sviluppatori di presentare la propria applicazione per lo store o altri media, sovrapponendo questa immagine ad altre immagini.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Esempio di acquisizione di utilità screenshot](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
