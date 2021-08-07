---
title: Tracciamento mano in Unreal
description: Informazioni su come usare l'input del tracciamento della mano, la posizione, le mesh delle mani e le animazioni con collegamento in tempo reale nelle app di realtà mista Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, tracciamento delle mani, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
ms.openlocfilehash: 4c3b86c842fc875ebedbdf2527bf962fd8afd4d19cef90d168293cc85b664f70
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187265"
---
# <a name="hand-tracking-in-unreal"></a>Tracciamento mano in Unreal

Il sistema di tracciamento delle mani usa le mani e le dita di una persona come input. Sono disponibili i dati sulla posizione e la rotazione di ogni dito, l'intero palmo e i movimenti della mano. A partire da Unreal 4.26, il tracciamento delle mani si basa sul plug-in Unreal HeadMountedDisplay e usa un'API comune in tutte le piattaforme e i dispositivi XR. La funzionalità è la stessa per i Windows Mixed Reality e OpenXR.

## <a name="hand-pose"></a>Posizione della mano

La posizione della mano consente di tenere traccia e usare le mani e le dita degli utenti come input, accessibili sia in Blueprints che in C++. L'API Unreal invia i dati come sistema di coordinate, con tick sincronizzati con Unreal Engine.

![Immagine dello scheletro della mano con giunzioni sovrapposte ](images/hand-tracking-img-02.png)
 ![ a Hand Skeleton](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animazione hand-live link

Le posizioni della mano vengono esposte all'animazione usando il [plug-in Collegamento live.](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)

Se i Windows Mixed Reality e Live Link sono abilitati:
1. Selezionare **Finestra > Collegamento live per** aprire la finestra dell'editor di Live Link.
2. Selezionare **Source (Origine)** e abilitare **Windows Mixed Reality Hand Tracking Source (Origine tracciamento manuale)**

![Origine collegamento in tempo reale](images/unreal/live-link-source.png)

Dopo aver abilitato l'origine e aperto un asset di animazione, espandere la sezione **Animation** (Animazione) nella **scheda Preview Scene** (Anteprima scena) e visualizzare altre opzioni.

![Animazione collegamento in tempo reale](images/unreal/live-link-animation.png)

La gerarchia dell'animazione manuale è la stessa di `EWMRHandKeypoint` . L'animazione può essere ridestinata **usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset:**

![Animazione collegamento in tempo reale 2](images/unreal/live-link-animation2.png)

Può anche essere sottoclassato nell'editor:

![Modifica del mapping dei collegamenti in tempo reale](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Hand Mesh

### <a name="hand-mesh-as-a-tracked-geometry"></a>Mesh mano come geometria tracciata

> [!IMPORTANT]
> Per ottenere mesh mano come geometria tracciata in OpenXR, è necessario chiamare **Set Use Hand Mesh** with Enabled Tracking Geometry (Imposta usa mesh mano con geometria di **tracciamento abilitata).**

Per abilitare tale modalità, è necessario chiamare Set Use Hand Mesh with Enabled Tracking Geometry **(Imposta usa mesh mano** **con geometria di rilevamento abilitata):**

![Progetto dell'evento begin play connesso per impostare l'uso della funzione hand mesh con la modalità geometria di rilevamento abilitata](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Non è possibile che entrambe le modalità siano abilitate contemporaneamente. Se si abilita un'opzione, l'altra viene disabilitata automaticamente.

### <a name="accessing-hand-mesh-data"></a>Accesso ai dati della mesh manuale

![Hand Mesh](images/unreal/hand-mesh.png)

Prima di poter accedere ai dati della mesh manuale, è necessario:
- Selezionare **l'asset ARSessionConfig,** espandere le impostazioni **AR Impostazioni -> World Mapping** e selezionare Generate Mesh Data from Tracked Geometry (Genera dati mesh da geometria **tracciata).**

Di seguito sono riportati i parametri di mesh predefiniti:

1.  Usare i dati mesh per l'occlusione
2.  Generare una collisione per i dati della mesh
3.  Generare la mesh di spostamento per i dati della mesh
4.  Eseguire il rendering dei dati della mesh in wireframe: parametro di debug che mostra la mesh generata

Questi valori di parametro vengono usati come valori predefiniti per mesh di mapping spaziale e mesh manuale. È possibile modificarli in qualsiasi momento in Blueprints o nel codice per qualsiasi mesh.

### <a name="c-api-reference"></a>Informazioni di riferimento sulle API C++
Usare `EEARObjectClassification` per trovare i valori della mesh manuale in tutti gli oggetti tracciabili.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

I delegati seguenti vengono chiamati quando il sistema rileva qualsiasi oggetto tracciabile, inclusa una mesh mano.

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

Assicurarsi che i gestori delegati seguano la firma della funzione seguente:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

È possibile accedere ai dati della mesh tramite  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Informazioni di riferimento sulle API di Blueprint

Per usare hand mesh in Blueprints:
1. Aggiungere un **componente ARTrackableNotify** a un attore blueprint

![ARTrackable Notify](images/unreal/ar-trackable-notify.png)

2. Passare al pannello **Dettagli** ed espandere la **sezione** Eventi.

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)

3. Sovrascrivi in caso di aggiunta/aggiornamento/rimozione della geometria rilevata con i nodi seguenti nell'Graph:

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualizzazione Hand Mesh in OpenXR

Il modo consigliato per visualizzare la mesh manuale è usare il plug-in XRPop di Epic insieme al [plug-in Microsoft OpenXR.](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 

Nell'editor del progetto è quindi necessario usare **la funzione Set Use Hand Mesh** del plug-in Microsoft [OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **Enabled XR Plugin** come parametro:

![Progetto dell'evento begin play connesso per impostare l'uso della funzione hand mesh con la modalità xrvisualizzazione abilitata](images/unreal-hand-tracking-img-05.png)

Per gestire il processo di rendering, è necessario usare **render motion controller** da XRVisual:

![Progetto di funzione get motion controller data connessa per eseguire il rendering della funzione controller del movimento](images/unreal-hand-tracking-img-06.png)

Ecco il risultato:

![Immagine della mano digitale sovrapposta a una mano umana reale](images/unreal-hand-tracking-img-07.png) 

Se è necessario qualcosa di più complicato, ad esempio disegnare una mesh manuale con uno shader personalizzato, è necessario ottenere le mesh come geometria tracciata. 

## <a name="hand-rays"></a>Raggi mano

Ottenere la posizione della mano funziona per interazioni di chiusura, ad esempio afferrare oggetti o premere i pulsanti. Tuttavia, a volte è necessario lavorare con ologrammi molto disacconti dagli utenti. Questa operazione può essere eseguita con i raggi della mano, che possono essere usati come dispositivi di puntamento sia in C++ che in Blueprints. È possibile disegnare un raggio dalla mano fino a un punto lontano e, con l'aiuto di Unreal Ray Tracing, selezionare un ologramma che altrimenti sarebbe fuori portata. 

> [!IMPORTANT]
> Poiché tutti i risultati della funzione cambiano ogni fotogramma, vengono tutti resi chiamabili. Per altre informazioni sulle funzioni pure e impure o chiamabili, vedere il GUID utente di Blueprint sulle [funzioni](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Movimenti

Il HoloLens 2 traccia i movimenti spaziali, il che significa che è possibile acquisire tali movimenti come input. Il rilevamento movimenti si basa su un modello di sottoscrizione. È consigliabile usare la funzione "Configura movimenti" per indicare al dispositivo i movimenti di cui si vuole tenere traccia.  Per altri dettagli sui movimenti, vedere il documento HoloLens 2 [Basic Usage (Uso di](/hololens/hololens2-basic-usage) base).

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Ancoraggi nello spazio locali](unreal-spatial-anchors.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.