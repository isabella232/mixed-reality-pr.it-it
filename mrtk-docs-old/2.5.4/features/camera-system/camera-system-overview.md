---
title: CameraSystemOverview
description: Pagina di destinazione per il sistema camera in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: e12f37d1536ccbbf315276576c37d9e4130a76d6dcafb98572930c163110a224
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193187"
---
# <a name="camera-system"></a>Sistema di fotocamera

Il sistema di fotocamera consente a Microsoft Mixed Reality Toolkit di configurare e ottimizzare la fotocamera dell'applicazione per l'uso in applicazioni di realtà mista. Usando il sistema di fotocamera, le applicazioni possono essere scritte per supportare dispositivi opachi (ad esempio, la realtà virtuale) e trasparenti (ad esempio, Microsoft HoloLens) senza dover scrivere codice per distinguere e gestire ogni tipo di visualizzazione.

## <a name="enabling-the-camera-system"></a>Abilitazione del sistema di fotocamera

Il sistema di fotocamere è gestito dall'oggetto MixedRealityToolkit (o da un altro componente registrar del servizio).

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata da MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Passare al pannello Inspector (Controllo) alla sezione camera system (Sistema fotocamera) e verificare che **l'opzione Enable Camera System (Abilita** sistema fotocamera) sia selezionata.

    ![Abilitazione del sistema di fotocamera](../images/camera-system/EnableCameraSystem.png)

3. Selezionare l'implementazione del sistema di fotocamera. L'implementazione predefinita della classe fornita da MRTK è `MixedRealityCameraSystem` .

    ![Selezionare l'implementazione del sistema di fotocamera](../images/camera-system/SelectCameraSystemType.png)

4. Selezionare il profilo di configurazione desiderato

    ![Selezionare il profilo del sistema di fotocamera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configurazione del sistema di fotocamera

### <a name="settings-providers"></a>Impostazioni provider

![Provider di Impostazioni fotocamera](../images/camera-system/CameraSettingsProviders.png)

I provider di impostazioni della fotocamera abilitano la configurazione specifica della piattaforma della fotocamera. Queste impostazioni possono includere passaggi di configurazione personalizzati e/o componenti.

I provider possono essere aggiunti facendo clic **sul pulsante Add Camera Impostazioni Provider (Aggiungi camera Impostazioni provider).** Possono essere rimossi facendo clic **-** sul pulsante a destra del nome del provider.

> [!Note]
> Non tutte le piattaforme richiedono un provider di impostazioni della fotocamera. Se non sono presenti provider compatibili con la piattaforma in cui è in esecuzione l'applicazione, microsoft Mixed Reality Toolkit applica le impostazioni predefinite di base.

### <a name="display-settings"></a>Impostazioni schermo

![Impostazioni di visualizzazione della fotocamera Impostazioni](../images/camera-system/CameraDisplaySettings.png)

Le impostazioni di visualizzazione vengono specificate sia per gli schermi opachi (ad esempio, virtual reality) che per i display trasparenti (ad esempio, Microsoft HoloLens). La fotocamera viene configurata, in fase di esecuzione, usando queste impostazioni.

**Near Clip**

Il piano di ritaglio vicino è il più vicino, in metri, che un oggetto virtuale può essere alla fotocamera ed essere ancora sottoposto a rendering. Per il massimo comfort dell'utente, è consigliabile rendere questo valore maggiore di zero. L'immagine precedente contiene valori che si sono trovati a proprio agio in un'ampia gamma di dispositivi.

**Far Clip**

Il piano di ritaglio lontano è il più lontano, in metri, in cui un oggetto virtuale può essere sulla fotocamera ed essere ancora sottoposto a rendering. Per i dispositivi trasparenti, è consigliabile che questo valore sia relativamente vicino per non superare e troppo lo spazio reale e interrompere le qualità immersive dell'applicazione.

**Cancella flag**

Il valore dei flag di cancellazione indica come viene cancellata la visualizzazione mentre viene disegnata. Per le esperienze di realtà virtuale, questo valore è spesso impostato su Skybox. Per gli schermi trasparenti, è consigliabile impostare questa opzione su Colore.

**Colore di sfondo**

Se i flag di cancellazione non sono impostati su Skybox, verrà visualizzata la proprietà del colore di sfondo.

**Qualità Impostazioni**

Il valore delle impostazioni di qualità indica la qualità grafica che Unity deve usare quando esegue il rendering della scena. Il livello di qualità è un'impostazione a livello di progetto e non è specifico di alcuna fotocamera. Per altre informazioni, vedere [l'articolo Sulla](https://docs.unity3d.com/Manual/class-QualitySettings.html) qualità nella documentazione di Unity.

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API Del sistema di fotocamere](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Creazione di un provider di Impostazioni fotocamera](create-settings-provider.md)
