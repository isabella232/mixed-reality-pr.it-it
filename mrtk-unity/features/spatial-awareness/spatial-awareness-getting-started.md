---
title: SpatialAwareness
description: descrive la conoscenza spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7a27f5eb63150b2521ea3471f50c2bbdeb886d90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782172"
---
# <a name="spatial-awareness"></a>Consapevolezza spaziale

![Consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Il sistema di riconoscimento spaziale fornisce una reale consapevolezza ambientale nelle applicazioni di realtà mista. Quando introdotta in Microsoft HoloLens, la consapevolezza spaziale ha fornito una raccolta di mesh, che rappresenta la geometria dell'ambiente, che consentiva di interagire in modo interessante tra gli ologrammi e il mondo reale.

> [!NOTE]
> A questo punto, il Toolkit di realtà mista non viene fornito con gli algoritmi di comprensione spaziale come originariamente confezionato in HoloToolkit. La comprensione spaziale comporta in genere la trasformazione dei dati di rete spaziale per creare dati di mesh semplificati e/o raggruppati, ad esempio piani, muri, piani, soffitti e così via.

## <a name="getting-started"></a>Guida introduttiva

L'aggiunta del supporto per la consapevolezza spaziale richiede due componenti chiave del Toolkit di realtà mista: il sistema di riconoscimento spaziale e un provider di piattaforme supportato.

1. [Abilitare](#enable-the-spatial-awareness-system) il sistema di riconoscimento spaziale
2. [Registrare](#register-observers) e [configurare](configuring-spatial-awareness-mesh-observer.md) uno o più osservatori spaziali per fornire dati mesh
3. [Compila e Distribuisci](#build-and-deploy) in una piattaforma che supporta la consapevolezza spaziale

### <a name="enable-the-spatial-awareness-system"></a>Abilitare il sistema di riconoscimento spaziale

Il sistema di riconoscimento spaziale è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ). Attenersi alla procedura seguente per abilitare o disabilitare il *sistema di riconoscimento spaziale* nel profilo *MixedRealityToolkit* .

Il Toolkit di realtà misto viene fornito con alcuni profili preconfigurati predefiniti. Per alcune di queste funzionalità il sistema di riconoscimento spaziale è abilitato o disabilitato per impostazione predefinita. Lo scopo di questa pre-configurazione, in particolare per i casi in cui è disabilitato, è quello di evitare il sovraccarico visivo del calcolo e del rendering dei mesh.

| Profilo | Sistema abilitato per impostazione predefinita |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | Falso |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | Falso |
| `DefaultMixedRealityToolkitConfigurationProfile` (Asset/MRTK/SDK/profili) | Vero |

1. Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena per aprirlo nel pannello di controllo.

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Passare alla sezione *sistema di riconoscimento spaziale* e selezionare *Abilita sistema di riconoscimento spaziale*

    ![Abilita consapevolezza spaziale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Selezionare il tipo di implementazione del sistema di riconoscimento spaziale desiderato. [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)È il valore predefinito specificato.

    ![Selezionare l'implementazione del sistema di riconoscimento spaziale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrare gli osservatori

I servizi nel Toolkit per la realtà mista possono avere [provider di dati Servizi](../../architecture/systems-extensions-providers.md) che integrano il servizio principale con i controlli di implementazione e i dati specifici della piattaforma. Un esempio è il sistema di input della realtà mista che dispone di [più provider di dati](../input/input-providers.md) per ottenere il controller e altre informazioni di input correlate da diverse API specifiche della piattaforma.

Il sistema di riconoscimento spaziale è simile in quanto i provider di dati forniscono al sistema i dati di rete sul mondo reale. Il profilo di riconoscimento spaziale deve avere almeno un osservatore spaziale registrato. Gli osservatori spaziali sono in genere componenti specifici della piattaforma che fungono da provider per l'emersione di diversi tipi di dati mesh da un endpoint specifico della piattaforma (ad esempio HoloLens).

1. Aprire o espandere il *profilo di sistema di riconoscimento spaziale*

    ![Profilo del sistema di riconoscimento spaziale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Fai clic sul pulsante *"Aggiungi osservatore spaziale"*
1. Selezionare il *tipo di implementazione dell'osservatore spaziale* desiderato

    ![Selezionare l'implementazione dell'osservatore spaziale](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modificare le proprietà di configurazione nell'Observer](configuring-spatial-awareness-mesh-observer.md) se necessario

> [!NOTE]
> Gli utenti di `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles) avranno il sistema di riconoscimento spaziale preconfigurato per la piattaforma di realtà mista di Windows che usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe.

### <a name="build-and-deploy"></a>Eseguire la compilazione e la distribuzione

Quando il sistema di riconoscimento spaziale viene configurato con gli osservatori desiderati, il progetto può essere compilato e distribuito nella piattaforma di destinazione.

> [!IMPORTANT]
> Se la destinazione è la piattaforma di realtà mista di Windows (ad esempio, HoloLens), è importante assicurarsi che la [funzionalità di percezione spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) sia abilitata per poter usare il sistema di riconoscimento spaziale sul dispositivo.

> [!WARNING]
> Alcune piattaforme, tra cui Microsoft HoloLens, forniscono supporto per l'esecuzione remota dall'interno di Unity. Questa funzionalità consente lo sviluppo e i test rapidi senza richiedere la fase di compilazione e distribuzione. Assicurarsi di eseguire test di accettazione finali usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver seguito le procedure riportate sopra per abilitare il sistema di riconoscimento spaziale, il sistema può essere configurato e controllato in modo più dettagliato.

Informazioni per la configurazione degli osservatori in Inspector:

- [Configurazione degli Observer per l'utilizzo del dispositivo](configuring-spatial-awareness-mesh-observer.md)
- [Configurazione degli osservatori per l'utilizzo in-Editor](spatial-object-mesh-observer.md)

Informazioni per il controllo e l'estensione degli osservatori tramite codice:

- [Configurazione di osservatori tramite codice](usage-guide.md)
- [Creazione di un Observer personalizzato](create-data-provider.md)

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API di riconoscimento spaziale](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Panoramica del mapping spaziale WMR](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping)
- [Mapping spaziale in Unity WMR](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity)
