---
title: README_TextPrefab
description: Panoramica di TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, TMP,
ms.openlocfilehash: f77f654e9be98aeb86bdc4c75e9aaeb464dc5b18
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694848"
---
# <a name="text-prefab"></a>Prefabbricato di testo

Questi prefabbricati sono ottimizzati per la qualità di rendering in realtà mista di Windows. Per ulteriori informazioni, leggere il testo della Guida [in Unity in](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) Microsoft Windows Dev Center.

## <a name="prefabs"></a>Prefabbricati

### <a name="3dtextprefab"></a>3DTextPrefab

prefabbricato mesh di testo 3D (assets/MRTK/SDK/StandardAssets/prefabrics/Text) con fattore di scala ottimizzato a distanza di 2 metri. (Leggere le istruzioni riportate di seguito)

### <a name="uitextprefab"></a>UITextPrefab

Prefabbricato mesh del testo dell'interfaccia utente (assets/MRTK/SDK/StandardAssets/prefabrics/Text) con fattore di scalabilità ottimizzato a distanza di 2 metri. (Leggere le istruzioni riportate di seguito)

## <a name="fonts"></a>Tipi di carattere

Tipi di carattere Open Source (assets/MRTK/Core/StandardAssets/fonts) inclusi nel Toolkit per realtà mista.

> [!IMPORTANT]
> Il prefabbricato di testo usa il tipo di carattere Open Source ' Selawik '. Per usare il testo prefabbricato con un tipo di carattere diverso, importare il file del tipo di carattere e seguire le istruzioni seguenti. Nell'esempio seguente viene illustrato come utilizzare il tipo di carattere ' Segoe UI ' con il prefabbricato di testo.

![Importazione del file del tipo di carattere Segoe UI](Images/TextPrefab/TextPrefabInstructions01.png)

1. Assegnare la trama del carattere al materiale 3DTextSegoeUI. mat.

    ![Assegnazione della trama del tipo di carattere](Images/TextPrefab/TextPrefabInstructions02.png)

1. In 3DTextSegoeUI. Mat Material selezionare lo shader Custom/3DTextShader. shader.

    ![Assegnazione dello shader](Images/TextPrefab/TextPrefabInstructions03.png)

1. Assegnare Segoe UI tipo di carattere e il materiale 3DTextSegoeUI ai componenti di testo nei prefabbricati.

    ![Assegnazione del file e del materiale del tipo di carattere](Images/TextPrefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Uso dei tipi di carattere in Unity

Quando si aggiunge un nuovo TextMesh 3D a una scena in Unity, sono presenti due problemi visivi evidenti. Uno, il tipo di carattere è molto grande e due, il tipo di carattere appare molto sfocato. È anche interessante notare che il valore predefinito per le dimensioni del carattere è impostato su zero nel controllo. Se si sostituisce questo valore zero con 13, non verrà visualizzata alcuna differenza di dimensione, perché 13 è effettivamente il valore predefinito.

Unity presuppone che tutti i nuovi elementi aggiunti a una scena corrispondano a 1 unità Unity o alla scala di trasformazione 100%, che si traduce in circa 1 misuratore nella HoloLens. Nel caso dei tipi di carattere, il rettangolo di delimitazione di un TextMesh 3D viene visualizzato per impostazione predefinita a circa 1 metro in altezza.

### <a name="font-scale-and-font-sizes"></a>Scala dei tipi di carattere e dimensioni del carattere

La maggior parte delle finestre di progettazione visiva utilizza punti per definire le dimensioni dei tipi di carattere nel mondo reale, nonché i relativi programmi di progettazione. Sono presenti circa 2835 (834.645666399962) punti in 1 contatore. In base alla conversione del sistema del punto in 1 misuratore e le dimensioni predefinite del tipo di carattere TextMesh di Unity di 13, la matematica semplice di 13 divisa per 2835 è uguale a 0,0046 (0.004586111116 Exact) fornisce una scala standard adeguata per iniziare con, anche se alcune potrebbero voler arrotondare a 0,005.

In entrambi i casi, il ridimensionamento dell'oggetto o del contenitore di testo a questi valori non consentirà solo la conversione 1:1 delle dimensioni dei tipi di carattere da un programma di progettazione, ma fornisce anche uno standard per garantire la coerenza nell'intera applicazione o gioco.

### <a name="ui-text"></a>Testo interfaccia utente 

Quando si aggiunge un'interfaccia utente o un elemento di testo basato su Canvas a una scena, la disparità delle dimensioni è ancora maggiore. Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0.0004586111116) o 0,0005 per il valore arrotondato.

**Dichiarazione** di non responsabilità: il valore predefinito di qualsiasi tipo di carattere può essere applicato dalla dimensione della trama del tipo di carattere o dalla modalità di importazione del tipo di carattere in Unity. Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity, oltre a un altro tipo di carattere importato.

![Dimensioni del carattere con fattori di scala](Images/TextPrefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik. Mat](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Materials)

Materiale per 3DTextPrefab con supporto occlusione. Richiede 3DTextShader. shader

![Materiale carattere predefinito rispetto al materiale 3DTextSegoeUI](Images/TextPrefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader. shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Shaders)

Shader per 3DTextPrefab con supporto occlusione.
