---
title: Tracciamento mano in Unreal
description: Spiega come usare il rilevamento manuale in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, Tracking manuale, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia a realtà mista di Windows, headset di realtà virtuale
ms.openlocfilehash: 66ae1994f2bbee3ba4786a7c4eeebfe1cd57ca37
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002659"
---
# <a name="hand-tracking-in-unreal"></a>Tracciamento mano in Unreal

Il sistema di rilevamento manuale usa le palme e le dita di una persona come input. I dati sulla posizione e sulla rotazione di ogni dito, l'intero palmo e i movimenti della mano sono disponibili. A partire da Unreal 4,26, il rilevamento manuale è basato sul plug-in HeadMountedDisplay non reale e usa un'API comune in tutti i dispositivi e le piattaforme XR. La funzionalità è la stessa per i sistemi OpenXR e di realtà mista di Windows.

## <a name="hand-pose"></a>Hand Pose

Hand Pose consente di tenere traccia e di usare le mani e le dita degli utenti come input, a cui è possibile accedere sia nei progetti sia in C++. L'API Unreal invia i dati come sistema di coordinate, con segni di selezione sincronizzati con il motore irreale.

![Scheletro mano](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animazione collegamento dinamico

Le pose della mano vengono esposte all'animazione usando il plug-in [Live link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Se sono abilitati i plug-in della realtà mista di Windows e dei collegamenti dinamici:
1. Selezionare **finestra > collegamento Live** per aprire la finestra dell'editor di collegamento Live.
2. Selezionare l' **origine** e abilitare l' **origine del rilevamento a mano della realtà mista di Windows**

![Origine collegamento dinamico](images/unreal/live-link-source.png)

Dopo aver abilitato l'origine e aperto un asset di animazione, espandere la sezione **animazione** nella scheda della **scena anteprima** . vedere anche opzioni aggiuntive.

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)

La gerarchia di animazione della mano è identica a quella di `EWMRHandKeypoint` . L'animazione può essere ridestinata usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)

Può anche essere sottoclassato nell'Editor:

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Mesh mano

### <a name="hand-mesh-as-a-tracked-geometry"></a>Mesh mano come geometria rilevata

> [!IMPORTANT]
> Per ottenere le mesh della mano come geometria tracciata in OpenXR, è necessario chiamare **set Use Hand mesh** con la **geometria di rilevamento abilitata**.

Per abilitare questa modalità, è necessario chiamare **set Use Hand mesh** con la **geometria di rilevamento abilitata**:

![Progetto di avvio dell'evento Play connesso per impostare Use Hand mesh Function con la modalità di rilevamento Geometry abilitata](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Non è possibile abilitare entrambe le modalità nello stesso momento. Se ne viene abilitato uno, l'altro viene disabilitato automaticamente.

### <a name="accessing-hand-mesh-data"></a>Accesso ai dati della rete a mano

![Mesh mano](images/unreal/hand-mesh.png)

Prima di poter accedere ai dati della mesh a mano, è necessario:
- Selezionare l'asset **ARSessionConfig** , espandere impostazioni **AR-> Impostazioni mapping del mondo** e selezionare **genera dati mesh da geometria rilevata**.

Di seguito sono riportati i parametri di mesh predefiniti:

1.  Usare i dati mesh per l'occlusione
2.  Genera collisione per i dati mesh
3.  Genera la mesh NAV per i dati mesh
4.  Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata

Questi valori di parametro vengono usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano. È possibile modificarli in qualsiasi momento in progetti o codice per qualsiasi mesh.

### <a name="c-api-reference"></a>Informazioni di riferimento sulle API C++
Usare `EEARObjectClassification` per trovare i valori della mesh mano in tutti gli oggetti rilevabili.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

I delegati seguenti vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano.

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Assicurarsi che i gestori del delegato seguano la firma della funzione seguente:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

È possibile accedere ai dati mesh tramite  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Riferimento all'API Blueprint

Per lavorare con le mesh mano nei progetti:
1. Aggiungere un componente **ARTrackableNotify** a un attore del progetto

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)

2. Passare al pannello dei **Dettagli** ed espandere la sezione **eventi** .

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)

3. Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con i nodi seguenti nel grafico eventi:

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualizzazione Mesh mano in OpenXR

Il metodo consigliato per visualizzare la mesh manuale consiste nell'usare il plug-in XRVisualization di Epic insieme al plug-in [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Nell'editor del progetto è quindi consigliabile usare la funzione di **configurazione Use Hand mesh** dal [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **XRVisualization abilitato** come parametro:

![Progetto di avvio dell'evento Play connesso per impostare Use Hand mesh Function con la modalità xrvisualization abilitata](images/unreal-hand-tracking-img-05.png)

Per gestire il processo di rendering, è necessario usare il **controller di movimento di rendering** da XRVisualization:

![Progetto della funzione Get Motion controller data connessa alla funzione di rendering del controller di movimento](images/unreal-hand-tracking-img-06.png)

Ecco il risultato:

![Immagine della mano digitale sovrapposta a una mano umana reale](images/unreal-hand-tracking-img-07.png) 

Se sono necessarie altre operazioni più complesse, ad esempio il disegno di una mesh mano con uno shader personalizzato, è necessario ottenere le mesh come geometria rilevata. 

## <a name="hand-rays"></a>Raggi mano

Il recupero della disposizione è adatto a interazioni di chiusura, ad esempio l'acquisizione di oggetti o la pressione di pulsanti. Tuttavia, a volte è necessario lavorare con ologrammi lontani dagli utenti. Questa operazione può essere eseguita con i raggi mano, che possono essere usati come dispositivi di puntamento sia in C++ che nei progetti. È possibile disegnare un raggio da una mano all'altra e, con alcuni aiuti dalla traccia del raggio non reale, selezionare un ologramma che altrimenti non sarà raggiungibile. 

> [!IMPORTANT]
> Poiché tutti i risultati della funzione cambiano ogni frame, sono tutti resi richiamabili. Per ulteriori informazioni sulle funzioni pure e non pure o chiamabili, vedere il GUID utente del progetto nelle [funzioni](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Movimenti

HoloLens 2 tiene traccia dei movimenti spaziali, il che significa che è possibile acquisire tali movimenti come input. Il rilevamento dei movimenti si basa su un modello di sottoscrizione. Utilizzare la funzione "Configura movimenti" per indicare al dispositivo quali movimenti si desidera rilevare.  Per ulteriori informazioni sui movimenti, vedere il documento [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Ancoraggi nello spazio locali](unreal-spatial-anchors.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.
