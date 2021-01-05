---
title: Servizi di Azure per realtà mista
description: USA i servizi di realtà mista di Azure per creare applicazioni 3D, multiutente e a livello di spazio accessibili tra dispositivi HoloLens, iOS e Android.
author: grbury
ms.author: grbury
ms.date: 08/21/2019
ms.topic: overview
keywords: Realtà mista, sviluppo, sviluppo, HoloLens, servizi di Azure, ancoraggi spaziali, sintesi vocale, visione, rendering remoto
ms.openlocfilehash: c25584bd77495ab4e45713d2ad25b1b7b4e526e9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757569"
---
# <a name="azure-mixed-reality-services"></a>Servizi di Azure per realtà mista
Grazie ai servizi di realtà mista di Azure è possibile scoprire le potenzialità del mondo fisico tridimensionale circostante, che ogni essere umano conosce bene. Aiuta gli utenti a creare, apprendere e collaborare in modo più efficace con l'acquisizione di informazioni digitali e l'emersione. Il 3D può essere portato nei dispositivi mobili, nei visori VR e in altri dispositivi senza tethering. L'uso di Azure assicura che le informazioni più sensibili siano protette.

## <a name="multi-user-spatially-aware-applications-using-spatial-anchors"></a>Applicazioni con più utenti e con funzionalità spaziali che usano ancoraggi spaziali

![ Immagine di ancoraggi nello spazio di Azure](../design/images/AzureSpatialAnchors.jpg)

Crea applicazioni di realtà mista a più utenti e in grado di riconoscere lo spazio usando ancoraggi spaziali. Crea app per realtà miste che mappano, designano e richiamano punti di interesse precisi accessibili nei dispositivi HoloLens, iOS e Android. Abilita wayfinding tra gli spazi per aiutare gli utenti a collaborare in modo più efficiente.

[Prova gli ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors)


## <a name="interactive-high-quality-3d-models-using-remote-rendering"></a>Modelli 3D interattivi e di alta qualità che usano il rendering remoto

![ Immagine di Rendering remoto](../design/images/RemoteRendering.jpg)

Negli scenari sono stati rilevati tutti i dettagli, ovvero la gestione di impianti industriali, la revisione della progettazione per asset come motori di autocarri, la pianificazione della chirurgia pre-operativa e altro ancora. Si tratta di un elemento che consente a progettisti, ingegneri, medici e studenti di comprendere informazioni complesse ed effettuare la chiamata giusta.

Se attualmente si eseguono modelli 3D di alta qualità su dispositivi mobili e auricolari reali misti, è necessario semplificare i modelli 3D in modo da poterli eseguire nell'hardware di destinazione. Questa semplificazione può comportare una perdita di dettagli importanti che è necessaria per le decisioni chiave aziendali e di progettazione.

L'anteprima per il rendering remoto di Azure offre modelli 3D interattivi e di alta qualità a dispositivi non collegati con tutti i dettagli intatti e senza compromettere la qualità.

[Altre informazioni sul rendering remoto di Azure](https://azure.microsoft.com/services/remote-rendering)

## <a name="cognitive-services"></a>Servizi cognitivi

:::row:::
    :::column:::
       [![Icona bolla vocale con sfondo grigio vuoto](images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Voce](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
        I servizi Voce consentono l'integrazione delle funzionalità di elaborazione vocale in qualsiasi app o servizio. È possibile convertire la lingua parlata in testo o generare una sintesi vocale naturale da testo usando caratteri voce standard o personalizzabili. È possibile provare gratuitamente qualsiasi servizio e creare velocemente app e servizi abilitati per la sintesi vocale con le funzionalità seguenti.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Rappresentazione grafica degli occhi con sfondo grigio vuoto](images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Visione](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
        È possibile riconoscere, identificare, creare sottotitoli, indicizzare e moderare immagini, video e contenuto input penna digitale. Visione consente ad app e servizi di identificare e analizzare con precisione il contenuto all'interno di immagini, video e input penna digitale.
    :::column-end:::
:::row-end:::


## <a name="see-also"></a>Vedere anche

* Esercitazioni sugli ancoraggi nello spazio di Azure per HoloLens 2: [1 di 3 Introduzione ad Ancoraggi nello spazio di Azure](../mrlearning-asa-ch1.md)
* Esercitazioni sui servizi Voce di Azure per HoloLens 2: [1 di 4 Integrazione e uso del riconoscimento vocale e della trascrizione](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
