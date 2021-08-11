---
title: Introduzione alla consapevolezza spaziale
description: descrive la consapevolezza spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204329"
---
# <a name="spatial-awareness-getting-started"></a>Introduzione alla consapevolezza spaziale

![Consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Il sistema di consapevolezza spaziale offre consapevolezza ambientale reale nelle applicazioni di realtà mista. Se introdotta in Microsoft HoloLens, la consapevolezza spaziale ha fornito una raccolta di mesh, che rappresentano la geometria dell'ambiente, che ha consentito interazioni accattivanti tra ologrammi e il mondo reale.

> [!NOTE]
> In questo momento, l'Toolkit realtà mista non è disponibile con algoritmi di comprensione spaziale come originariamente in pacchetto in HoloToolkit. La comprensione spaziale comporta in genere la trasformazione dei dati della mesh spaziale per creare dati mesh semplificati e/o raggruppati, ad esempio piani, pareti, piani, controsoffi e così via.

## <a name="getting-started"></a>Guida introduttiva

L'aggiunta del supporto per la consapevolezza spaziale richiede due componenti chiave del Toolkit realtà mista: il sistema di consapevolezza spaziale e un provider di piattaforma supportato.

1. [Abilitare](#enable-the-spatial-awareness-system) il sistema di consapevolezza spaziale
2. [Registrare](#register-observers) [e configurare](configuring-spatial-awareness-mesh-observer.md) uno o più osservatori spaziali per fornire dati mesh
3. [Compilare e distribuire](#build-and-deploy) in una piattaforma che supporta la consapevolezza spaziale

### <a name="enable-the-spatial-awareness-system"></a>Abilitare il sistema di consapevolezza spaziale

Il sistema di consapevolezza spaziale è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente registrar del](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servizio). Seguire questa procedura per abilitare o disabilitare il *sistema di* consapevolezza spaziale nel *profilo MixedRealityToolkit.*

L'Toolkit realtà mista viene fornito con alcuni profili preconfigurati predefiniti. Per alcuni di questi il sistema di consapevolezza spaziale è abilitato o disabilitato per impostazione predefinita. Lo scopo di questa pre-configurazione, in particolare per quando è disabilitato, è evitare il sovraccarico visivo dovuto al calcolo e al rendering delle mesh.

| Profilo | Sistema abilitato per impostazione predefinita |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | Falso |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | Falso |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) | Vero |

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena per aprirlo nel pannello inspector.

    ![Gerarchia della scena configurata di MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Passare alla sezione *Spatial Awareness System (Sistema di consapevolezza* spaziale) e *selezionare Enable Spatial Awareness System (Abilita sistema di consapevolezza spaziale)*

    ![Abilitare la consapevolezza spaziale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Selezionare il tipo di implementazione del sistema di consapevolezza spaziale desiderato. è [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) il valore predefinito fornito.

    ![Selezionare l'implementazione del sistema di consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrare gli osservatori

I servizi nel modello di [](../../architecture/systems-extensions-providers.md) realtà Toolkit possono avere provider di dati che integrano il servizio principale con dati specifici della piattaforma e controlli di implementazione. Un esempio è il sistema di [](../input/input-providers.md) input di realtà mista che ha più provider di dati per ottenere il controller e altre informazioni di input correlate da varie API specifiche della piattaforma.

Il sistema di consapevolezza spaziale è simile perché i provider di dati forniscono al sistema dati mesh sul mondo reale. Il profilo di consapevolezza spaziale deve avere almeno un osservatore spaziale registrato. Gli osservatori spaziali sono in genere componenti specifici della piattaforma che fungono da provider per l'eserzione di vari tipi di dati mesh da un endpoint specifico della piattaforma (ad esempio HoloLens).

1. Aprire o espandere il *profilo Spatial Awareness System (Sistema di consapevolezza spaziale)*

    ![Profilo del sistema di consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Fare clic sul *pulsante "Add Spatial Observer" (Aggiungi osservatore* spaziale)
1. Selezionare il tipo di *implementazione osservatore spaziale desiderato*

    ![Selezionare l'implementazione dell'osservatore spaziale](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modificare le proprietà di configurazione nell'osservatore in](configuring-spatial-awareness-mesh-observer.md) base alle esigenze

> [!NOTE]
> Gli utenti di `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) avranno il sistema di consapevolezza spaziale preconfigurato per la piattaforma Windows Mixed Reality che usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe .

### <a name="build-and-deploy"></a>Eseguire la compilazione e la distribuzione

Dopo aver configurato il sistema di consapevolezza spaziale con gli osservatori desiderati, il progetto può essere compilato e distribuito nella piattaforma di destinazione.

> [!IMPORTANT]
> Se la destinazione è Windows Mixed Reality piattaforma (ad esempio, HoloLens), è importante assicurarsi che la funzionalità [Percezione](/windows/mixed-reality/spatial-mapping-in-unity) spaziale sia abilitata per usare il sistema di consapevolezza spaziale nel dispositivo.

> [!WARNING]
> Alcune piattaforme, tra cui Microsoft HoloLens, forniscono il supporto per l'esecuzione remota dall'interno di Unity. Questa funzionalità consente lo sviluppo e il test rapidi senza richiedere il passaggio di compilazione e distribuzione. Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver seguito le procedure descritte in precedenza per abilitare il sistema di consapevolezza spaziale, il sistema può essere configurato e controllato in modo più dettagliato.

Informazioni per la configurazione degli osservatori nel controllo:

- [Configurazione degli osservatori per sull'utilizzo del dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurazione degli osservatori per l'utilizzo nell'editor](spatial-object-mesh-observer.md)

Informazioni per il controllo e l'estensione degli osservatori tramite codice:

- [Configurazione degli osservatori tramite codice](usage-guide.md)
- [Creazione di un osservatore personalizzato](create-data-provider.md)

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API di consapevolezza spaziale](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Panoramica del mapping spaziale WMR](/windows/mixed-reality/spatial-mapping)
- [Mapping spaziale in Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)
