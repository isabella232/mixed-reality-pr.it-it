---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549129"
---
# <a name="performance-recommendations-for-unreal"></a>Consigli sulle prestazioni per Unreal

## <a name="overview"></a>Panoramica

Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine. Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.

## <a name="recommended-unreal-project-settings"></a>Impostazioni consigliate per il progetto Unreal
Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).

1. Uso del renderer VR per dispositivi mobili:
    * Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. Uso del renderer di avanzamento: 
    * Questa funzionalità è molto più efficiente per la realtà mista rispetto alla pipeline predefinita di rendering posticipato. Questo è dovuto principalmente al numero di funzionalità che è possibile disabilitare singolarmente. 
    * Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Rendering di avanzamento](images/unreal/performance-recommendations-img-04.png)

3. Uso delle visualizzazioni multiple dei dispositivi mobili:
    * Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili). L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

4. Verificare che sia selezionato **Default** (Predefinito) o **D3D12** come **Default RHI** (RHI predefinito) quando si usa OpenXR.
    * La selezione di **D3D11** avrà un impatto negativo sulle prestazioni a causa del passaggio di rendering aggiuntivo eseguito dalla piattaforma. **D3D12** dovrebbe offrire miglioramenti delle prestazioni di rendering, oltre a evitare il passaggio di rendering aggiuntivo.

![RHI predefinito](images/unreal/performance-recommendations-img-09.png)

5. Disabilitazione dell'annebbiamento ai vertici: 
    * La funzionalità di annebbiamento ai vertici applica calcoli di annebbiamento a ogni vertice di un poligono e quindi interpola i risultati in tutta la faccia del poligono. Se il gioco non prevede la nebbia, è necessario scegliere questa impostazione per disabilitare la nebbia e aumentare le prestazioni di ombreggiatura.

![Opzioni di annebbiamento ai vertici](images/unreal/performance-recommendations-img-05.png)

6. Disabilitazione del culling delle occlusioni:
    * Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).
        + Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering). Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.
    * Il culling delle occlusioni sulla GPU dei dispositivi mobili è lento. In generale, è auspicabile che la GPU si occupi principalmente di rendering. Se si ha la sensazione che l'occlusione possa aiutare le prestazioni, provare ad abilitare l'occlusione del software. Si noti che l'abilitazione dell'occlusione del software potrebbe peggiorare le prestazioni se si è già vincolati alla CPU da un elevato numero di chiamate di disegno.

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

7. Disabilitazione del passaggio dello stencil di profondità personalizzato:
    * Questa funzionalità richiede un'ulteriore approvazione perché è lenta. Anche la traslucenza è lenta in Unreal. Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Stencil profondità](images/unreal/performance-recommendations-img-06.png)

8. Riduzione delle mappe delle ombreggiature a cascata: 
    * La riduzione del numero di mappe delle ombreggiature determina un miglioramento delle prestazioni. In generale, questo valore deve essere impostato su 1, altrimenti si verifica una visibile perdita di qualità. 

![Mappe delle ombreggiature a cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Impostazioni facoltative

> [!NOTE]
> Le impostazioni seguenti possono migliorare le prestazioni, causando tuttavia la disabilitazione di alcune funzionalità. Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.

1. Riduzione delle permutazioni degli shader per dispositivi mobili
    * Se le luci non si muovono in modo indipendente dalla fotocamera, è possibile impostare questo valore tranquillamente su 0. Il vantaggio principale è che consentirà a Unreal di escludere diverse permutazioni degli shader, accelerando la compilazione degli shader stessi.

![Riduzione delle permutazioni degli shader per dispositivi mobili](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Vedere anche
* [Linee guida sulle prestazioni di Unreal Engine per dispositivi mobili]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)