---
title: Visualizzazione dello stato
description: Informazioni sul modo in cui i controlli di stato forniscono all'utente feedback sull'esecuzione di un'operazione di lunga durata nelle app per realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX, indicatore di stato, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 489f4bd9fea31126f936673db7acafeab27d9cd9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009461"
---
# <a name="progress-indicator"></a>Indicatore di stato

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un controllo progress fornisce il feedback che è in corso un'operazione a esecuzione prolungata. Quando un indicatore di stato è visibile, gli utenti possono visualizzare il tempo di attesa e non possono interagire con l'app.

<br>

---

## <a name="types-of-progress"></a>Tipi di stato

È importante fornire le informazioni sull'utente su ciò che accade. In realtà mista, gli utenti possono essere facilmente distratti dall'ambiente fisico o dagli oggetti se l'app non ha un feedback visivo valido. Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile mostrare un indicatore visivo. Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra di stato<br>
        Un indicatore di stato Mostra la percentuale di completamento di un'attività. Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non dovrebbe bloccare l'interazione dell'utente con l'app.<br>
        <br>
        *Image: esempio di indicatore di stato in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Esempio di indicatore di stato in HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Anello di stato<br>
        Un anello di avanzamento ha uno stato indeterminato e deve essere usato quando l'interazione dell'utente viene bloccata fino al completamento dell'operazione.<br>
        <br>
        *Immagine: esempio di anello di stato in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Esempio di anello di stato nel dispositivo HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Stato di avanzamento con un oggetto personalizzato<br>
        È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.<br>
        <br>
        *Immagine: esempio di avanzamento con mesh personalizzato in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Esempio di avanzamento con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedure consigliate
* È strettamente correlato alla visualizzazione dello stato di avanzamento [, in quanto](billboarding-and-tag-along.md) l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto. È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento. Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.
* È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente. Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows. È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Indicatore di stato in MRTK (Mixed Reality Toolkit) per Unity

* [MRTK-prefabbricati indicatore di stato](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-servizio di transizione della scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a>Vedere anche

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
