---
title: Visualizzazione dello stato
description: Informazioni su come i controlli di stato forniscono un feedback all'utente che è in corso un'operazione a esecuzione lunga nelle app di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, controlli, interfaccia utente, ux, indicatore di stato, visore di realtà mista, visore windows di realtà mista, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600550"
---
# <a name="progress-indicator"></a>Indicatore di stato

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un controllo di stato fornisce il feedback che un'operazione a esecuzione lunga è in corso. Quando un indicatore di stato è visibile, gli utenti possono visualizzare il tempo di attesa e non possono interagire con l'app.

<br>

---

## <a name="types-of-progress"></a>Tipi di stato

È importante fornire all'utente informazioni su ciò che accade. In realtà mista, gli utenti possono essere facilmente distratti dall'ambiente fisico o dagli oggetti se l'app non ha un buon feedback visivo. In situazioni che possono richiedere alcuni secondi, ad esempio durante il caricamento dei dati o l'aggiornamento di una scena, è buona idea visualizzare un indicatore visivo. Sono disponibili due opzioni per mostrare all'utente che è in corso un'operazione: un indicatore **di** stato o un **anello di stato**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra di stato<br>
        Un indicatore di stato mostra la percentuale di completamento di un'attività. Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.<br>
        <br>
        *Immagine: Esempio di indicatore di stato in HoloLens*
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
        Un anello Di stato ha solo uno stato indeterminato e deve essere usato quando l'interazione dell'utente viene bloccata fino al completamento dell'operazione.<br>
        <br>
        *Immagine: Esempio di anello di stato in HoloLens*
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
        ### <a name="progress-with-a-custom-objectbr"></a>Avanzamento con un oggetto personalizzato<br>
        È possibile aggiungere alla personalità e all'identità del marchio dell'app personalizzando il controllo Stato con i propri oggetti 2D/3D personalizzati.<br>
        <br>
        *Immagine: Stato dell'esempio di mesh personalizzata in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Avanzamento con l'esempio di mesh personalizzata in HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedure consigliate

* Coppia stretta di [manifesti o tag-along](billboarding-and-tag-along.md) per la visualizzazione di Progress poiché l'utente può spostare facilmente la testa nello spazio vuoto e perdere il contesto. L'app potrebbe sembrare che si sia verificata in modo anomalo se l'utente non riesce a visualizzare alcun elemento. I tag e i tag sono incorporati nel prefab Stato di avanzamento.
* È sempre bene fornire informazioni sullo stato di ciò che accade all'utente. Il prefab Stato fornisce vari stili di visualizzazione, tra cui lo stato di avanzamento del tipo di anello standard di Windows per fornire lo stato. È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Indicatore di stato in MRTK (Mixed Reality Toolkit) per Unity

* [MRTK - Prefab indicatore di stato](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK - Servizio di transizione della scena](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a>Vedi anche

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