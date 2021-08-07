---
title: Raccomandazioni sui materiali in Unreal
description: Panoramica dei materiali nel motore Unreal.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, materiali, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
ms.openlocfilehash: d5ce702495c95e8ca6d07a0209a4bc7d02f5d4d682415b028d63995e8910a7e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187736"
---
# <a name="material-recommendations-in-unreal"></a>Raccomandazioni sui materiali in Unreal

I materiali usati possono influire direttamente sull'esecuzione dei progetti in Unreal Engine. Questa pagina funge da guida introduttiva per le impostazioni di base da usare per ottenere prestazioni ottimali dalle applicazioni di realtà mista.

## <a name="using-customizeduvs"></a>Uso di DV personalizzati

Se è necessario fornire la affiancamento UV sul materiale, usare CustomizedUVs invece di modificare direttamente l'UV del nodo della trama. Le UV personalizzate consentono di modificare le UV nei vertex shader anziché nel pixel shader.

![Impostazioni dei materiali in Unreal](images/unreal-materials-img-01c.png)

È possibile trovare informazioni dettagliate sul materiale nella [documentazione di Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) ed esempi di procedure consigliate negli screenshot seguenti:

Impostazioni dei materiali consigliate nella configurazione del materiale consigliato di [ ![ Unreal ](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox) 
 

Impostazioni dei materiali non consigliate nella configurazione del materiale non consigliato di [ ![ Unreal ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 

## <a name="changing-blend-mode"></a>Modifica della modalità blend

È consigliabile impostare la modalità di blend su opaca, a meno che non vi sia un motivo sicuro per farlo diversamente. I materiali mascherati e traslucidi sono lenti. Per altre informazioni sui materiali, vedere la documentazione [di Unreal Engine.](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)

![Modifica della modalità blend](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Aggiornamento dell'illuminazione per dispositivi mobili

La precisione completa deve essere disattivata. L'illuminazione della mappa di luce può essere chiamata verso il basso ruotando le informazioni direzionali. Se disabilitata, l'illuminazione dalle mappe delle luci sarà piana ma più economica.

![Impostazioni dei materiali per dispositivi mobili in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Regolazione dell'ombreggiatura in avanti

Queste opzioni migliorano la fedeltà visiva a s costo delle prestazioni. Devono essere disattivate per le massime prestazioni.

![Inoltrare le impostazioni del materiale ombreggiatura in Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Impostazione della traslucenza dei materiali

Indica che il materiale traslucido non deve essere influenzato da fiore o dof. Poiché entrambi questi effetti sono rari in MR, questa impostazione deve essere attivata per impostazione predefinita.

![Impostazione di traslucidità separata per dispositivi mobili in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Impostazioni facoltative

Le impostazioni seguenti possono migliorare le prestazioni, ma si noti che disabilitano determinate funzionalità. Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.

![Impostazioni dei materiali facoltative in Unreal](images/unreal-materials-img-06.jpg)

Se il materiale non richiede riflessi o riflessi, l'impostazione di questa opzione può offrire un enorme miglioramento delle prestazioni. Nei test interni è veloce quanto "non illuminato" fornendo al tempo stesso informazioni sull'illuminazione.

## <a name="best-practices"></a>Procedure consigliate

Di seguito non sono riportate le "impostazioni" quanto le procedure consigliate correlate ai materiali.

Quando si creano parametri, preferire l'uso di "Parametri statici" laddove possibile. I commutatori statici possono essere usati per rimuovere un intero ramo di un materiale senza costi di runtime. Le istanze possono avere valori diversi, rendendo possibile la configurazione di uno shader con modello senza perdita di prestazioni. Lo svantaggio è che vengono create diverse permutazioni che causeranno la ricompilazione dello shader. Provare a ridurre al minimo il numero di parametri statici nel materiale e il numero di permutazioni dei parametri statici usati. Per altri dettagli sul rendering dei parametri dei materiali, vedere la [documentazione di Unreal Engine.](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)

![Procedure consigliate per le impostazioni dei materiali](images/unreal-materials-img-07.jpg)

Quando si creano istanze di materiale, è necessario dare la preferenza a **Material Instance Constant (Costante istanza materiale)** rispetto a Material Instance Dynamic (Dinamica istanza materiale). **Material Instance Constant è** un oggetto Material con istanze che viene calcolato una sola volta prima del runtime.

L'istanza material creata tramite Content Browser (fare clic con il pulsante destro del mouse >**Crea istanza** di materiale) è una costante dell'istanza material. L'istanza material dynamic viene creata tramite codice. Per altre informazioni sulle istanze dei materiali, vedere la documentazione [di Unreal Engine.](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)

![Creazione di istanze di materiale in Unreal](images/unreal-materials-img-08.png)

Tenere sotto controllo la complessità dei materiali/shader. È possibile visualizzare il costo del materiale su varie piattaforme facendo clic sull'icona Platform Stats (Statistiche piattaforma). È anche possibile trovare altri dettagli sui materiali nella documentazione [di Unreal Engine.](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)

![Creazione di impostazioni dinamiche dell'istanza di materiale in Unreal](images/unreal-materials-img-09.png)

È possibile ottenere un'idea rapida della complessità relativa dello shader tramite la modalità visualizzazione Complessità [shader](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).

* Tasto di scelta rapida modalità di visualizzazione: ALT+8
* Comando console: viewmode shadercomplexity

![Complessità dei materiali in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Vedi anche
* [Materiali per dispositivi mobili](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modalità di visualizzazione](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Istanze material](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
