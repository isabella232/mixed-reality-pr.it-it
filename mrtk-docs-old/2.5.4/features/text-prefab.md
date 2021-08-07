---
title: TextPrefab
description: Panoramica di TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, TMP,
ms.openlocfilehash: 9e51c296d897e6bb494f3c9fc23a7af269a8d9b8bbd2d18006721acdbe2d9ea3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188353"
---
# <a name="text-prefab"></a>Prefab di testo

Questi prefab sono ottimizzati per la qualità di rendering in Windows Mixed Reality. Per altre informazioni, leggere le linee guida Text in Unity on Microsoft Windows Dev Center [(Testo in Unity](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) in Microsoft Windows Dev Center).

## <a name="prefabs"></a>Prefab

### <a name="3dtextprefab"></a>3DTextPrefab

Prefab 3D Text Mesh (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con fattore di scala ottimizzato a 2 metri di distanza. (Leggere le istruzioni seguenti)

### <a name="uitextprefab"></a>UITextPrefab

Prefab ui Text Mesh (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con fattore di scala ottimizzato a 2 metri di distanza. (Leggere le istruzioni seguenti)

## <a name="fonts"></a>Tipi di carattere

Tipi di carattere open source (Assets/MRTK/Core/StandardAssets/Fonts) inclusi in Mixed Reality Toolkit.

> [!IMPORTANT]
> Text Prefab usa il open source carattere "Selawik". Per usare Il prefab di testo con un tipo di carattere diverso, importare il file del tipo di carattere e seguire le istruzioni riportate di seguito. L'esempio seguente illustra come usare il tipo di Segoe UI con il prefab di testo.

![Importazione di Segoe UI file dei tipi di carattere](images/text-prefab/TextPrefabInstructions01.png)

1. Assegnare la trama del carattere al materiale 3DTextSegoeUI.mat.

    ![Assegnazione della trama del tipo di carattere](images/text-prefab/TextPrefabInstructions02.png)

1. Nel materiale 3DTextSegoeUI.mat selezionare lo shader Custom/3DTextShader.shader.

    ![Assegnazione di shader](images/text-prefab/TextPrefabInstructions03.png)

1. Assegnare Segoe UI tipo di carattere e materiale 3DTextSegoeUI ai componenti di testo nei prefab.

    ![Assegnazione di file e materiale dei tipi di carattere](images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Uso dei tipi di carattere in Unity

Quando si aggiunge un nuovo textmesh 3D a una scena in Unity, esistono due problemi visivamente evidenti. Uno, il tipo di carattere appare molto grande e due, il tipo di carattere appare molto sfocato. È anche interessante notare che il valore predefinito dimensioni carattere è impostato su zero nel controllo. La sostituzione di questo valore zero con 13 non mostrerà alcuna differenza nelle dimensioni, perché 13 è effettivamente il valore predefinito.

Unity presuppone che tutti i nuovi elementi aggiunti a una scena siano di dimensioni di 1 unità Unity o una scala di trasformazione al 100%, che si traduce in circa 1 metro nella HoloLens. Nel caso dei tipi di carattere, viene visualizzato il rettangolo di selezione per un oggetto TextMesh 3D, per impostazione predefinita a circa 1 metro di altezza.

### <a name="font-scale-and-font-sizes"></a>Scala dei caratteri e dimensioni dei caratteri

La maggior parte delle finestre di progettazione visiva usa Points per definire le dimensioni dei caratteri nel mondo reale, nonché i relativi programmi di progettazione. Sono presenti circa 2835 punti (2.834.645666399962) in 1 contatore. In base alla conversione del sistema di punti in 1 contatore e alle dimensioni del carattere TextMesh predefinite di Unity pari a 13, la semplice matematica di 13 divisa per 2835 equivale a 0,0046 (0,004586111116 per l'esattezza) offre una scala standard adatta per iniziare, anche se alcuni potrebbero voler arrotondare a 0,005.

In entrambi i casi, il ridimensionamento dell'oggetto o del contenitore Text a questi valori non solo consentirà la conversione 1:1 delle dimensioni dei caratteri da un programma di progettazione, ma fornisce anche uno standard per mantenere la coerenza in tutta l'applicazione o nel gioco.

### <a name="ui-text"></a>Testo interfaccia utente 

Quando si aggiunge un elemento Text basato su interfaccia utente o area di disegno a una scena, la disparità di dimensioni è ancora maggiore. Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0,000458611116 per l'esatto) o 0,0005 per il valore arrotondato.

**Dichiarazione di non responsabilità:** il valore predefinito di qualsiasi tipo di carattere può essere effetto della dimensione della trama del tipo di carattere o della modalità di importazione del tipo di carattere in Unity. Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity e a un altro tipo di carattere importato.

![Dimensioni del carattere con fattori di ridimensionamento](images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Materials/)

Materiale per 3DTextPrefab con supporto dell'occlusione. Richiede 3DTextShader.shader

![Materiale del tipo di carattere predefinito e materiale 3DTextSegoeUI](images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/StandardAssets/Shaders)

Shader per 3DTextPrefab con supporto dell'occlusione.
