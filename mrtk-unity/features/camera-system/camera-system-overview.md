---
title: Panoramica del sistema di fotocamera
description: Pagina di destinazione per il sistema di fotocamera in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177046"
---
# <a name="camera-system-overview"></a>Panoramica del sistema di fotocamera

Il sistema di fotocamera consente a Microsoft Mixed Reality Toolkit di configurare e ottimizzare la fotocamera dell'applicazione per l'uso in applicazioni di realtà mista. Usando il sistema di fotocamera, le applicazioni possono essere scritte per supportare sia dispositivi opachi (ad esempio realtà virtuale) che trasparenti (ad esempio Microsoft HoloLens) senza dover scrivere codice per distinguere e supportare ogni tipo di visualizzazione.

## <a name="enabling-the-camera-system"></a>Abilitazione del sistema di fotocamera

Il sistema di fotocamera è gestito dall'oggetto MixedRealityToolkit (o da un altro componente del registrar del servizio).

La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit. I passaggi necessari per altri registrar del servizio possono essere diversi.

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) e verificare che **l'opzione Enable Camera System** (Abilita sistema fotocamera) sia selezionata.

    ![Abilitazione del sistema di fotocamera](../images/camera-system/EnableCameraSystem.png)

3. Selezionare l'implementazione del sistema di fotocamera. L'implementazione predefinita della classe fornita da MRTK è `MixedRealityCameraSystem` .

    ![Selezionare l'implementazione del sistema di fotocamera](../images/camera-system/SelectCameraSystemType.png)

4. Selezionare il profilo di configurazione desiderato

    ![Selezionare il profilo di sistema della fotocamera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configurazione del sistema di fotocamera

### <a name="settings-providers"></a>Impostazioni provider

![Provider di Impostazioni fotocamera](../images/camera-system/CameraSettingsProviders.png)

I provider di impostazioni della fotocamera abilitano la configurazione specifica della piattaforma della fotocamera. Queste impostazioni possono includere passaggi di configurazione personalizzati e/o componenti.

È possibile aggiungere provider facendo clic sul **pulsante Add Camera Impostazioni Provider (Aggiungi Impostazioni provider).** Possono essere rimossi facendo clic **-** sul pulsante a destra del nome del provider.

> [!Note]
> Non tutte le piattaforme richiedono un provider di impostazioni della fotocamera. Se non sono presenti provider compatibili con la piattaforma in cui è in esecuzione l'applicazione, microsoft Mixed Reality Toolkit applica le impostazioni predefinite di base.

### <a name="display-settings"></a>Impostazioni schermo

![Schermo fotocamera Impostazioni](../images/camera-system/CameraDisplaySettings.png)

Le impostazioni di visualizzazione vengono specificate sia per i display opachi (ad esempio, realtà virtuale) che per i display trasparenti (ad esempio, Microsoft HoloLens). La fotocamera viene configurata, in fase di esecuzione, usando queste impostazioni.

**Near Clip**

Il piano di ritaglio vicino è il più vicino, in metri, che un oggetto virtuale può essere alla fotocamera ed essere ancora sottoposto a rendering. Per maggiore comodità dell'utente, è consigliabile impostare questo valore su un valore maggiore di zero. L'immagine precedente contiene valori che si sono trovati a proprio agio in un'ampia gamma di dispositivi.

**Clip lontano**

Il piano di ritaglio lontano è il più lontano, in metri, in cui un oggetto virtuale può essere alla fotocamera ed essere ancora sottoposto a rendering. Per i dispositivi trasparenti, è consigliabile che questo valore sia relativamente vicino per non superare e troppo lo spazio reale e interrompere le qualità immersive dell'applicazione.

**Cancella flag**

Il valore clear flags indica come viene cancellata la visualizzazione mentre viene disegnata. Per le esperienze di realtà virtuale, questo valore è molto spesso impostato su Skybox. Per gli schermi trasparenti, è consigliabile impostare questa opzione su Colore.

**Colore di sfondo**

Se i flag di cancellazione non sono impostati su Skybox, verrà visualizzata la proprietà del colore di sfondo.

**Qualità Impostazioni**

Il valore delle impostazioni di qualità indica la qualità grafica che Unity deve usare quando esegue il rendering della scena. Il livello di qualità è un'impostazione a livello di progetto e non è specifico di alcuna fotocamera. Per altre informazioni, vedere [l'articolo Qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html) nella documentazione di Unity.

## <a name="see-also"></a>Vedere anche

- [Documentazione dell'API Camera System](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Creazione di un provider di Impostazioni fotocamera](create-settings-provider.md)
