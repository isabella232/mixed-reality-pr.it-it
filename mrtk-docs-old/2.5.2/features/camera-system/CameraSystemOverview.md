---
title: CameraSystemOverview
description: Pagina di destinazione per il sistema della fotocamera in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: d2c5a0a806d3f6fd6844eca716ca70ec233d1146
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702217"
---
# <a name="camera-system"></a>Sistema fotocamera

Il sistema della fotocamera consente a Microsoft Mixed Reality Toolkit di configurare e ottimizzare la fotocamera dell'applicazione per l'uso in applicazioni con realtà mista. Utilizzando il sistema di fotocamera, le applicazioni possono essere scritte in modo da supportare sia i dispositivi opachi (ad esempio, la realtà virtuale) che quelli trasparenti (ad esempio, Microsoft HoloLens) senza dover scrivere codice per distinguere tra e adattarsi a ogni tipo di visualizzazione.

## <a name="enabling-the-camera-system"></a>Abilitazione del sistema della fotocamera

Il sistema della fotocamera è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di registrazione del servizio).

I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar di servizi potrebbero essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Passare al pannello di controllo nella sezione sistema della fotocamera e verificare che sia selezionata l'opzione **Abilita sistema fotocamera** .

    ![Abilitazione del sistema della fotocamera](../images/camera-system/EnableCameraSystem.png)

3. Selezionare l'implementazione del sistema della fotocamera. L'implementazione della classe predefinita fornita da MRTK è `MixedRealityCameraSystem` .

    ![Selezionare l'implementazione del sistema della fotocamera](../images/camera-system/SelectCameraSystemType.png)

4. Selezionare il profilo di configurazione desiderato

    ![Seleziona profilo di sistema della fotocamera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configurazione del sistema della fotocamera

### <a name="settings-providers"></a>Provider di impostazioni

![Provider di impostazioni della fotocamera](../images/camera-system/CameraSettingsProviders.png)

I provider di impostazioni della fotocamera abilitano la configurazione specifica della piattaforma della fotocamera. Queste impostazioni possono includere passaggi di configurazione personalizzati e/o componenti.

È possibile aggiungere i provider facendo clic sul pulsante **Aggiungi provider impostazioni fotocamera** . È possibile rimuoverli facendo clic sul **-** pulsante a destra del nome del provider.

> [!Note]
> Non tutte le piattaforme richiedono un provider di impostazioni della fotocamera. Se non sono presenti provider compatibili con la piattaforma in cui è in esecuzione l'applicazione, Microsoft Mixed Reality Toolkit applica le impostazioni predefinite di base.

### <a name="display-settings"></a>Impostazioni schermo

![Impostazioni di visualizzazione della fotocamera](../images/camera-system/CameraDisplaySettings.png)

Le impostazioni di visualizzazione vengono specificate per le visualizzazioni opache (ad esempio, realtà virtuale) e trasparenti (ad esempio: Microsoft HoloLens). La fotocamera viene configurata, in fase di esecuzione, usando queste impostazioni.

**Near clip**

Il piano di ritaglio vicino è il più vicino, in metri, che un oggetto virtuale può essere alla fotocamera ed è ancora sottoposto a rendering. Per ottenere la massima comodità per gli utenti, è consigliabile fare in modo che questo valore sia maggiore di zero. Nell'immagine precedente sono contenuti i valori che sono stati rilevati per essere comodi in un'ampia gamma di dispositivi.

**Clip lontano**

Il piano di ritaglio è il più lontano, in metri, che un oggetto virtuale può essere alla fotocamera ed è ancora sottoposto a rendering. Per i dispositivi trasparenti, è consigliabile che questo valore sia relativamente vicino a non superare eccessivamente lo spazio reale e suddividere le qualità immersive dell'applicazione.

**Cancella flag**

Il valore Clear Flags indica il modo in cui la visualizzazione viene cancellata mentre viene disegnata. Per le esperienze di realtà virtuale, questo valore viene spesso impostato su skybox. Per le visualizzazioni trasparenti, è consigliabile impostare questa proprietà su Color.

**Colore di sfondo**

Se i flag Clear non sono impostati su SKYBOX, verrà visualizzata la proprietà del colore di sfondo.

**Impostazioni qualità**

Il valore delle impostazioni di qualità indica la qualità grafica che Unity deve usare quando esegue il rendering della scena. Il livello di qualità è un'impostazione a livello di progetto e non è specifico di una fotocamera. Per altre informazioni, vedere l'articolo relativo alla [qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html) nella documentazione di Unity.

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API di sistema per fotocamere](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Creazione di un provider di impostazioni della fotocamera](CreateSettingsProvider.md)
