---
title: MrTK Figma Bridge per Unity
description: MRTK Figma Bridge per Unity consente di portare il layout da Figma Toolkit in Unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, Sketch, Adobe XD, progettazione, progettazione, file di progettazione, progettazione dell'esperienza utente, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053859"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>MRTK Figma Bridge for Unity (Beta)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge per Unity consente di portare il layout da Figma Toolkit in Unity. Il bridge può importare il layout dell'interfaccia utente creato con MRTK Figma Toolkit, quindi crea un'istanza dei prefab MRTK corrispondenti con la posizione e le dimensioni appropriate. Figma Bridge consente di progettare il processo di integrazione e la collaborazione tra progettisti e sviluppatori.


Per [informazioni su Fig Toolkit ma](figma-toolkit.md) Toolkit che è il file di progettazione con HoloLens 2 di interfaccia utente HoloLens 2 mrtk figma.

## <a name="prerequisites"></a>Prerequisiti
- Vedere [Installare gli strumenti per](/windows/mixed-reality/develop/install-the-tools) il software necessario per lo sviluppo di realtà mista
- Unity 2019 o versione successiva
- [MRTK-Unity 2.7.0 o versione successiva](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Richiede MRTK-Unity 2.7.0 o versione successiva**
> 
> Poiché Figma Toolkit e Figma Bridge sono basati su prefab MRTK 2.7.0, è necessario MRTK 2.7.0 o versione successiva. Se usati con una versione precedente di MRTK, alcuni componenti non verranno tradotti correttamente.

## <a name="how-to-use-mrtk-figma-bridge"></a>Come usare MRTK Figma Bridge

### <a name="1-installation"></a>1. Installazione

Figma Unity Bridge può essere installato tramite [Mixed Reality Feature Tool.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Scaricare ed eseguire Mixed Reality Feature Tool.

Nella **pagina Discover features** (Individua funzionalità) nella sezione Mixed Reality Toolkit (Realtà **mista)** selezionare **MRTK Figma Unity Bridge.** Seguire i passaggi per completare MR Feature Tool e tornare al progetto Unity. Unity importerà il pacchetto per MRTK Figma Bridge.

### <a name="2-open-figma-bridge-window"></a>2. Aprire la finestra Figma Bridge

Al termine del processo di importazione, sarà possibile trovare Figma Bridge nel menu **Mixed Reality > Toolkit > Figma Bridge**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Generare e immettere il token Figma

Nel sito Web Figma fare clic sul menu Figma nell'angolo in alto a sinistra, aprire Guida e account > account. Generare un nuovo token di accesso personale nella sezione "Token di accesso personali".

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Immettere l'ID per un documento Figma
Ogni documento Figma ha un ID univoco nell'URL. Copiare e incollare questo ID in Figma Bridge.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Fare **clic su Get File (Ottieni** file) per scaricare il file Figma. È possibile scaricare altri file Figma immettendo un nuovo ID.

Fare **clic su Carica file** per aprire un file Figma.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. Creare una pagina

Figma Bridge visualizza l'elenco delle pagine nel file Figma. Controllare le pagine da compilare in Unity. Fare clic **sul pulsante Compila** pagine.

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. Aggiornare un documento per le modifiche

È possibile modificare il file Figma sul Web (o usando l'editor desktop) e fare clic su **Aggiorna** per recuperare le modifiche. Fare clic **su Build pages (Compila** pagine) per eseguire la compilazione con gli aggiornamenti. In questo modo è possibile eseguire facilmente l'iterazione della progettazione in Figma e visualizzarla in Unity.



## <a name="see-also"></a>Vedi anche
* [Figma Toolkit](figma-toolkit.md)
* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)
