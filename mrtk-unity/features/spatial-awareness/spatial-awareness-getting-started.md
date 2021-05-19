---
title: Consapevolezza spaziale
description: descrive la consapevolezza spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144467"
---
# <a name="spatial-awareness"></a>Consapevolezza spaziale

![Consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Il sistema di consapevolezza spaziale offre consapevolezza ambientale reale nelle applicazioni di realtà mista. Se introdotta in Microsoft HoloLens, la consapevolezza spaziale ha fornito una raccolta di mesh, che rappresentano la geometria dell'ambiente, che ha consentito interazioni accattivanti tra ologrammi e il mondo reale.

> [!NOTE]
> Al momento, Mixed Reality Toolkit non include algoritmi spatial understanding come originariamente in pacchetto in HoloToolkit. La comprensione spaziale comporta in genere la trasformazione dei dati della mesh spaziale per creare dati mesh semplificati e/o raggruppati, ad esempio piani, pareti, piani, controsoffi e così via.

## <a name="getting-started"></a>Per iniziare

L'aggiunta del supporto per la consapevolezza spaziale richiede due componenti chiave di Mixed Reality Toolkit: il sistema di consapevolezza spaziale e un provider di piattaforma supportato.

1. [Abilitare](#enable-the-spatial-awareness-system) il sistema di consapevolezza spaziale
2. [Registrare](#register-observers) [e configurare](configuring-spatial-awareness-mesh-observer.md) uno o più osservatori spaziali per fornire dati mesh
3. [Compilare e distribuire](#build-and-deploy) in una piattaforma che supporta la consapevolezza spaziale

### <a name="enable-the-spatial-awareness-system"></a>Abilitare il sistema di consapevolezza spaziale

Il sistema di consapevolezza spaziale è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio). Seguire questa procedura per abilitare o disabilitare il *sistema di* consapevolezza spaziale nel *profilo MixedRealityToolkit.*

Mixed Reality Toolkit viene fornito con alcuni profili preconfigurati predefiniti. Per alcuni di questi il sistema di consapevolezza spaziale è abilitato o disabilitato per impostazione predefinita. Lo scopo di questa pre-configurazione, in particolare per quando è disabilitato, è evitare il sovraccarico visivo dovuto al calcolo e al rendering delle mesh.

| Profilo | Sistema abilitato per impostazione predefinita |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | Falso |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | Falso |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) | Vero |

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena da aprire nel pannello inspector.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Passare alla sezione *Sistema di consapevolezza spaziale* e selezionare Abilita sistema di *consapevolezza spaziale*

    ![Abilitare la consapevolezza spaziale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Selezionare il tipo di implementazione del sistema Spatial Awareness desiderato. è [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) il valore predefinito fornito.

    ![Selezionare l'implementazione del sistema di consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrare gli osservatori

I servizi in Mixed Reality Toolkit possono avere provider di dati [che](../../architecture/systems-extensions-providers.md) integrano il servizio principale con dati specifici della piattaforma e controlli di implementazione. Un esempio è il sistema di [](../input/input-providers.md) input di realtà mista che dispone di più provider di dati per ottenere il controller e altre informazioni di input correlate da varie API specifiche della piattaforma.

Il sistema di consapevolezza spaziale è simile perché i provider di dati forniscono al sistema dati mesh sul mondo reale. Nel profilo Di consapevolezza spaziale deve essere registrato almeno un osservatore spaziale. Gli osservatori spaziali sono in genere componenti specifici della piattaforma che fungono da provider per la visualizzazione di vari tipi di dati mesh da un endpoint specifico della piattaforma (ad esempio HoloLens).

1. Aprire o espandere il profilo *Sistema di consapevolezza spaziale*

    ![Profilo di sistema per la consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Fare clic sul *pulsante "Aggiungi osservatore spaziale"*
1. Selezionare il tipo di *implementazione osservatore spaziale desiderato*

    ![Selezionare l'implementazione dell'osservatore spaziale](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modificare le proprietà di configurazione nell'osservatore](configuring-spatial-awareness-mesh-observer.md) in base alle esigenze

> [!NOTE]
> Gli utenti di `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) avranno il sistema spatial awareness preconfigurato per la piattaforma Windows Mixed Reality che usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe .

### <a name="build-and-deploy"></a>Eseguire la compilazione e la distribuzione

Dopo aver configurato il sistema di riconoscimento spaziale con gli osservatori desiderati, il progetto può essere compilato e distribuito nella piattaforma di destinazione.

> [!IMPORTANT]
> Se la piattaforma Windows Mixed Reality destinazione (ad esempio, HoloLens), è importante assicurarsi che la funzionalità [Percezione](/windows/mixed-reality/spatial-mapping-in-unity) spaziale sia abilitata per usare il sistema di consapevolezza spaziale nel dispositivo.

> [!WARNING]
> Alcune piattaforme, tra cui Microsoft HoloLens, forniscono il supporto per l'esecuzione remota dall'interno di Unity. Questa funzionalità consente di sviluppare e testare rapidamente senza richiedere il passaggio di compilazione e distribuzione. Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver seguito le procedure precedenti per abilitare il sistema di riconoscimento spaziale, il sistema può essere configurato e controllato in modo più dettagliato.

Informazioni per la configurazione degli osservatori in Inspector:

- [Configurazione di Observers per l'utilizzo del dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurazione di Observers per l'utilizzo nell'editor](spatial-object-mesh-observer.md)

Informazioni per il controllo e l'estensione degli osservatori tramite codice:

- [Configurazione degli osservatori tramite codice](usage-guide.md)
- [Creazione di un osservatore personalizzato](create-data-provider.md)

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API Spatial Awareness](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Panoramica del mapping spaziale WMR](/windows/mixed-reality/spatial-mapping)
- [Mapping spaziale in Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)