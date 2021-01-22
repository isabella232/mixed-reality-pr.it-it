---
layout: LandingPage
title: Panoramica dei servizi cloud di realtà mista di Azure
description: Informazioni su tutti i servizi cloud di realtà mista di Azure che è possibile integrare nelle applicazioni Unity o Unreal.
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Realtà mista, sviluppare, sviluppo, HoloLens, servizi cloud, Azure, rendering remoto, ancoraggi nello spazio, servizi cognitivi, cognizione, unity, machine learning, traduzione vocale, visione artificiale, Microsoft Graph
ms.openlocfilehash: 725e41e94923f1738eb11064c772f9138a6be09a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582708"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Panoramica dei servizi cloud di realtà mista di Azure

![ Immagine di ancoraggi nello spazio di Azure](../design/images/AzureSpatialAnchors.jpg)

Grazie ai servizi di realtà mista di Azure è possibile scoprire le potenzialità del mondo fisico tridimensionale circostante, che ogni essere umano conosce bene. È possibile aiutare gli utenti a creare, apprendere e collaborare in modo più efficace mediante l'acquisizione e l'esposizione di informazioni digitali nel contesto del mondo reale, compreso quello lavorativo. Il 3D può essere portato nei dispositivi mobili, nei visori VR e in altri dispositivi senza tethering. L'uso di Azure assicura che le informazioni più sensibili siano protette.

## <a name="mixed-reality-services"></a>Servizi di realtà mista

I servizi cloud di Realtà mista come **Rendering remoto di Azure** e **Ancoraggi nello spazio di Azure** aiutano gli sviluppatori a creare esperienze immersive accattivanti in un'ampia gamma di piattaforme. Questi servizi consentono di integrare il riconoscimento dello spazio nei progetti quando si creano applicazioni per il training 3D, la manutenzione predittiva delle apparecchiature e la revisione della progettazione, tutto nel contesto degli ambienti degli utenti.

### <a name="azure-remote-rendering"></a>Rendering remoto di Azure
Rendering remoto di Azure, o ARR, è un servizio che consente di eseguire il rendering in tempo reale di modelli 3D estremamente complessi e di trasmetterli a un dispositivo. ARR è attualmente disponibile in anteprima pubblica e può essere aggiunto a progetti Unity o C++ nativi destinati a HoloLens 2 o PC desktop Windows.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR è un componente fondamentale di ogni applicazione di realtà mista eseguita in un dispositivo senza tethering, poiché questo tipo di dispositivi ha una potenza di calcolo inferiore per il rendering. Si prenda come esempio il confronto seguente tra i modelli di motore affiancati. Il modello ad alta fedeltà a sinistra ha più di 18 milioni triangoli, mentre il modello ridotto a destra ne ha circa 200.000 soltanto. Negli scenari in cui ogni dettaglio è importante, ad esempio nella gestione di impianti industriali, nella revisione della progettazione di asset come i motori di autocarri, nella pianificazione della chirurgia preoperatoria e altro ancora, la visualizzazione 3D dà vita al dettaglio. In questo modo, progettisti, tecnici, medici e studenti possono comprendere meglio le informazioni complesse ed effettuare la scelta giusta. Questa semplificazione, tuttavia, può comportare la perdita di dettagli importanti necessari per prendere decisioni aziendali e di progettazione fondamentali.

![Esempio di Rendering remoto di Azure in un'app di presentazione Unity](images/arr-engine.png)

ARR risolve questo problema spostando il carico di lavoro di rendering in GPU di fascia alta nel cloud. Un motore di grafica ospitato nel cloud acquisisce l'immagine e ne esegue il rendering, codifica quest'ultimo come flusso video e trasmette il modello direttamente al dispositivo di destinazione. 

* Per i modelli complessi per gestire i quali non è sufficiente una GPU di fascia alta, ARR distribuisce il carico di lavoro a più GPU e unisce il risultato in un'unica immagine, rendendo il processo completamente trasparente per l'utente. 

Come ulteriore vantaggio, ARR non limita il tipo di interfaccia utente che è possibile usare nell'app. Alla fine di un frame, il contenuto di cui è stato eseguito il rendering in locale viene automaticamente combinato con l'immagine remota come illustrato di seguito:

![Esempio di Rendering remoto di Azure in un'app di presentazione Unity](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure
Ancoraggi nello spazio di Azure, o ASA, è un servizio multipiattaforma che consente di creare applicazioni di realtà mista con riconoscimento dello spazio. Con gli ancoraggi nello spazio di Azure è possibile eseguire il mapping, mantenere in modo permanente e condividere contenuto olografico tra più dispositivi in scala reale. 

ASA è una soluzione personalizzata in modo esclusivo per casi d'uso comuni in realtà mista, tra cui:
* **Way-finding**: due o più ancoraggi nello spazio possono essere collegati per creare un elenco di attività o punti di interesse con cui un utente può interagire.
* **Esperienze multiutente**: gli utenti possono effettuare spostamenti avanti e indietro interagendo con oggetti nello stesso spazio virtuale.
* **Contenuto virtuale permanente nel mondo reale**: gli utenti possono posizionare nel mondo reale oggetti virtuali visualizzabili da altri dispositivi supportati.

![Esempio di Ancoraggi nello spazio di Azure](images/persistence.gif)

Il servizio può essere sviluppato in numerosi ambienti e distribuito a una vasta gamma di dispositivi e piattaforme. In questo modo ottengono una dispensa speciale per il loro elenco di piattaforme disponibili:
* Unity per HoloLens
* Unity per iOS
* Unity per Android
* iOS nativo
* Android nativo
* C++/WinRT e DirectX per HoloLens
* Xamarin per iOS
* Xamarin per Android

## <a name="cognitive-services"></a>Servizi cognitivi

:::row:::
    :::column:::
       [![Riconoscimento vocale](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Voce](/azure/cognitive-services/speech-service/)
        I servizi Voce consentono l'integrazione delle funzionalità di elaborazione vocale in qualsiasi app o servizio. È possibile convertire la lingua parlata in testo o generare una sintesi vocale naturale da testo usando caratteri voce standard o personalizzabili. È possibile provare gratuitamente qualsiasi servizio e creare velocemente app e servizi abilitati per la sintesi vocale con le funzionalità seguenti.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Visione](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Visione](/azure/cognitive-services/computer-vision/)
        È possibile riconoscere, identificare, creare sottotitoli, indicizzare e moderare immagini, video e contenuto input penna digitale. Visione consente ad app e servizi di identificare e analizzare con precisione il contenuto all'interno di immagini, video e input penna digitale.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>Servizi Unity autonomi

I servizi autonomi elencati di seguito non sono applicabili alla realtà mista, ma possono essere utili in un'ampia gamma di contesti di sviluppo. Se si eseguono attività di sviluppo in Unity, ognuno di questi servizi può essere integrato in progetti nuovi o esistenti.

### <a name="device-support"></a>Supporto di dispositivi
<table>
    <tr>
        <td><strong>Servizio cloud di Azure</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">Lingua e traduzione</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Visione artificiale</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Visione personalizzata</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">Notifiche tra più dispositivi</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">Riconoscimento volto</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Funzioni e Archiviazione</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">Video in streaming</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Machine Learning</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Funzioni e Archiviazione</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">Rilevamento oggetti</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Integrazione di bot</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>Vedere anche

* Esercitazioni sugli ancoraggi nello spazio di Azure per HoloLens 2: [1 di 3 Introduzione ad Ancoraggi nello spazio di Azure](./unity/tutorials/mr-learning-asa-02.md)
* Esercitazioni sui servizi Voce di Azure per HoloLens 2: [1 di 4 Integrazione e uso del riconoscimento vocale e della trascrizione](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)