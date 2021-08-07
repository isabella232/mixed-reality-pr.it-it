---
title: MRTK_Modularization
description: Descrive la componentizzazione in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f0952d8c945d613a8bb14c058c8dd8edfe2b2aa6f15c1f5e86eedd7247e2890f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189537"
---
# <a name="mixed-reality-toolkit-componentization"></a>Componentizzazione Toolkit realtà mista

Una delle nuove funzionalità principali di Mixed Reality Toolkit v2 è la componentizzazione migliorata. Laddove possibile, i singoli componenti sono isolati da tutti i componenti, ad esempio il livello principale della base.

## <a name="minimized-dependencies"></a>Dipendenze ridotte a icona

MRTK v2 è stato intenzionalmente sviluppato per essere modulare e per ridurre al minimo le dipendenze tra i servizi di sistema (ad esempio, la consapevolezza spaziale).

A causa della natura di alcuni servizi di sistema (ad esempio, input e teletrasporto), esiste un numero ridotto di dipendenze.

Anche se è previsto che i servizi necessitino di uno o più componenti provider di dati, non sono presenti collegamenti diretti tra di essi. Lo stesso vale per le funzionalità dell'SDK (ad esempio, Interfaccia utente componenti).

## <a name="component-communication"></a>Comunicazione dei componenti

Per assicurarsi che non siano presenti collegamenti diretti tra i componenti, MRTK v2 usa le interfacce per comunicare tra servizi, provider di dati e codice dell'applicazione. Queste interfacce sono definite in e tutte le comunicazioni vengono instradati tramite il componente di base Toolkit realtà mista.

![Uso del sistema di consapevolezza spaziale tramite interfacce](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Riduzione al minimo del footprint di importazione di MRTK

A questo punto, MRTK viene importato come pacchetto di base singolo(ignorando per un momento l'esistenza del pacchetto di esempi, che è un pacchetto completamente facoltativo). È possibile ridurre questo footprint riducendo manualmente i file importati, anche se si tratta di un processo altamente manuale che non ha una guida ben definita.

È possibile deselezionare elementi arbitrari durante l'importazione del pacchetto Foundation. Tuttavia, non è consigliabile eseguire questa operazione in una fase iniziale dello sviluppo perché potrebbe interrompere la funzionalità. Dopo aver calcolato il set di funzionalità finale di un'app, è possibile eliminare i provider e i servizi non necessari nelle cartelle seguenti:

- MRTK/Services
- MRTK/Providers
- MRTK/SDK/Funzionalità

> [!NOTE]
> MRTK v2.x **_richiede_** il contenuto della cartella Assets/MRTK/Core.

## <a name="upcoming-features"></a>Funzionalità future

### <a name="application-architecture"></a>Architettura dell'applicazione

MRTK includerà il supporto per consentire la costruzione di applicazioni con un'ampia gamma di architetture, tra cui:

- [Localizzatore di servizi MixedRealityToolkit](#mixedrealitytoolkit-service-locator)
- [Singoli servizi](#individual-service-components)
- [Localizzatore di servizi personalizzato](#custom-service-locator)
- [Architettura ibrida](#hybrid-architecture)

Quando si seleziona un'architettura dell'applicazione, è importante considerare la flessibilità di progettazione e le prestazioni dell'applicazione. Le architetture descritte di seguito non sono adatte per ogni applicazione.

#### <a name="mixedrealitytoolkit-service-locator"></a>Localizzatore di servizi MixedRealityToolkit

MRTK abilita (e configura automaticamente) le scene dell'applicazione per l'uso del componente [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) del localizzatore di servizi predefinito. Questo componente include il supporto per la configurazione di sistemi e provider di dati MRTK tramite controlli di configurazione e gestisce la durata dei componenti e i comportamenti di base (ad esempio, quando eseguire l'aggiornamento).

Tutti i sistemi sono rappresentati nel controllo della configurazione principale, indipendentemente dal fatto che siano presenti o abilitati nel progetto. Per altre [informazioni, vedi la Guida alla](../configuration/mixed-reality-configuration-guide.md) configurazione della realtà mista.

#### <a name="individual-service-components"></a>Singoli componenti del servizio

Alcuni sviluppatori hanno espresso il desiderio di includere singoli componenti del servizio nella gerarchia della scena dell'applicazione. Per abilitare questo utilizzo, i servizi dovranno essere incapsulati in un registrar personalizzato o essere autoregistrati/autogestiti.

Un servizio autoregistrato implementa e registra se stesso in modo che il codice dell'applicazione possa individuare l'istanza del servizio [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) tramite un registro.

Un servizio di gestione autonoma può essere implementato come oggetto singleton nella gerarchia della scena. Questo oggetto fornisce e la proprietà dell'istanza che il codice dell'applicazione può usare per accedere direttamente alla funzionalità del servizio.

#### <a name="custom-service-locator"></a>Localizzatore di servizi personalizzato

Alcuni sviluppatori hanno richiesto la possibilità di creare un componente localizzatore di servizi personalizzato. I localizzatori di servizi personalizzati implementano [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) l'interfaccia e gestiscono il ciclo di vita e i comportamenti principali dei servizi attivi.

#### <a name="hybrid-architecture"></a>Architettura ibrida

MRTK supporterà un'architettura ibrida in cui gli sviluppatori possono combinare gli approcci precedenti in base alle esigenze o alle esigenze. Ad esempio, uno sviluppatore può iniziare con il [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizzatore di servizi e aggiungere un servizio di autoregistrazione.

> [!NOTE]
> Quando si sceglie un'architettura ibrida, è importante tenere presente qualsiasi duplicazione del lavoro(ad esempio, l'acquisizione dei dati del controller da più componenti).
