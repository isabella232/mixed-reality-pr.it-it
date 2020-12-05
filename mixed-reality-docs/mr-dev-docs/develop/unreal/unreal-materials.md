---
title: Raccomandazioni sui materiali in Unreal
description: Panoramica dei materiali in Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, materiali, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609572"
---
# <a name="material-recommendations-in-unreal"></a>Raccomandazioni sui materiali in Unreal

I materiali usati possono influenzare direttamente il modo in cui i progetti vengono eseguiti in Unreal Engine. Questa pagina funge da avvio rapido per le impostazioni di base che è necessario usare per ottenere prestazioni ottimali dalle applicazioni di realtà mista.

## <a name="using-customizeduvs"></a>Uso di CustomizedUVs

Se è necessario fornire il rivestimento UV sul materiale, usare CustomizedUVs invece di modificare direttamente l'UV del nodo di trama. CustomizedUVs consentono di modificare le UV nei vertex shader invece che nel pixel shader.

![Impostazioni del materiale in Unreal](images/unreal-materials-img-01c.png)

È possibile trovare i dettagli relativi al materiale nella [documentazione di Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) ed esempi di procedure consigliate negli screenshot seguenti:

[ ![ Impostazioni del materiale consigliate nella ](images/unreal-materials-img-01.png) configurazione del ](images/unreal-materials-img-01.png#lightbox) 
 *materiale sconsigliato*

[ ![ Impostazioni del materiale non consigliate in ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)un' 
 *installazione non consigliata di materiali*

## <a name="changing-blend-mode"></a>Modifica della modalità di Blend

È consigliabile impostare la modalità di Blend su opaca a meno che non esista un motivo sicuro per eseguire altre operazioni. I materiali mascherati e traslucidi sono lenti. Per ulteriori informazioni sui materiali, vedere la [documentazione relativa a Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Modifica della modalità di Blend](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Aggiornamento dell'illuminazione per dispositivi mobili

La precisione completa deve essere disattivata. L'illuminazione lightmap può essere disattivata trasformando le informazioni direzionali. Se disabilitata, l'illuminazione da lightmaps sarà piatta, ma più economica.

![Impostazioni del materiale mobile in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Regolazione dell'ombreggiatura diretta

Queste opzioni migliorano la fedeltà visiva a scapito delle prestazioni. Devono essere disattivate per ottenere prestazioni ottimali.

![Impostazioni del materiale ombreggiatura di avanzamento in Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Impostazione della traslucidità del materiale

Indica che il materiale traslucido non deve essere influenzato da Bloom o DOF. Poiché entrambi gli effetti sono rari in MR, questa impostazione deve essere attiva per impostazione predefinita.

![Impostazione della traslucidità separata per dispositivi mobili in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Impostazioni facoltative

Le impostazioni seguenti possono migliorare le prestazioni, ma si noti che disabilitano alcune funzionalità. Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.

![Impostazioni del materiale facoltativo in Unreal](images/unreal-materials-img-06.jpg)

Se il materiale non richiede riflessi o lucentezza, l'impostazione di questa opzione può offrire un notevole miglioramento delle prestazioni. Nel test interno, è veloce come "spento" e fornisce informazioni sull'illuminazione.

## <a name="best-practices"></a>Procedure consigliate

Di seguito sono illustrate le procedure consigliate relative ai materiali.

Quando si creano parametri, è preferibile usare "parametri statici" laddove possibile. È possibile utilizzare le opzioni statiche per rimuovere un intero ramo di un materiale senza costi di Runtime. Le istanze possono avere valori diversi, rendendo possibile la configurazione di uno shader basato su modelli senza perdita delle prestazioni. Lo svantaggio è che vengono create diverse permutazioni che comporteranno la ricompilazione dello shader. Provare a ridurre al minimo il numero di parametri statici nel materiale e il numero di permutazioni dei parametri statici utilizzati. Per ulteriori informazioni sui parametri del materiale di rendering, vedere la [documentazione di Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Procedure consigliate per le impostazioni del materiale](images/unreal-materials-img-07.jpg)

Quando si creano istanze di materiale, è necessario assegnare una preferenza alla **costante dell'istanza Material** su un'istanza del materiale dinamica. La **costante dell'istanza Material** è un materiale di istanza che viene calcolato solo una volta prima del runtime.

L'istanza del materiale creata tramite il browser del contenuto (**fare clic con il pulsante destro del mouse > Crea istanza del materiale**) è una costante dell'istanza del materiale. L'istanza del materiale dinamica viene creata tramite codice. Per ulteriori informazioni sulle istanze di materiale, vedere la [documentazione di Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Creazione di istanze di materiale in Unreal](images/unreal-materials-img-08.png)

Tenere sotto controllo la complessità dei materiali e degli shader. È possibile visualizzare il costo del materiale su diverse piattaforme facendo clic sull'icona Statistiche piattaforma. Per ulteriori informazioni sui materiali, vedere la documentazione di [Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Creazione di impostazioni dinamiche dell'istanza Material in Unreal](images/unreal-materials-img-09.png)

È possibile ottenere una rapida idea della complessità relativa dello shader tramite la [modalità di visualizzazione](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)complessità dello shader.

* Tasto di scelta rapida modalità di visualizzazione: Alt + 8
* Comando della console: ViewMode shadercomplexity

![Complessità del materiale in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Vedere anche
* [Materiali mobili](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modalità di visualizzazione](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Istanze del materiale](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
