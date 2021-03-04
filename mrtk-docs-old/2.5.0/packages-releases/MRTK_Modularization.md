---
title: MRTK_Modularization
description: Descrive la componentizzazione in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a8cfe81714de1cc3916b89134c40252feb88adc2
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782823"
---
# <a name="mixed-reality-toolkit-componentization"></a>Componentizzazione del Toolkit di realtà mista

Una delle nuove eccezionali funzionalità di Mixed Reality toolkit V2 è il miglioramento della componentizzazione. Laddove possibile, i singoli componenti sono isolati da tutti i livelli di base della base.

## <a name="minimized-dependencies"></a>Dipendenze minime

MRTK V2 è stato intenzionalmente sviluppato per essere modulare e per ridurre al minimo le dipendenze tra i servizi di sistema (ad esempio, la consapevolezza spaziale).

A causa della natura di alcuni servizi di sistema (ad esempio, input e Teleportation), esiste un numero ridotto di dipendenze.

Sebbene sia previsto che i servizi necessitino di uno o più componenti del provider di dati, non vi sono collegamenti diretti tra di essi. Lo stesso vale per le funzionalità SDK (ad esempio, i componenti dell'interfaccia utente).

## <a name="component-communication"></a>Comunicazione componenti

Per assicurarsi che non vi siano collegamenti diretti tra i componenti, MRTK V2 usa le interfacce per la comunicazione tra servizi, provider di dati e codice dell'applicazione. Queste interfacce sono definite in e tutte le comunicazioni vengono instradate tramite il componente principale del Toolkit di realtà mista.

![Uso del sistema di riconoscimento spaziale tramite le interfacce](../features/Images/Packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Riduzione del footprint di importazione MRTK

A questo punto, il MRTK viene importato come singolo pacchetto di base (ignorando per un momento l'esistenza del pacchetto di esempi, che è un pacchetto completamente facoltativo). È possibile ridurre questo footprint riducendo manualmente i file importati, anche se si tratta di un processo estremamente manuale senza una guida ben definita.

È possibile deselezionare gli elementi arbitrari durante l'importazione del pacchetto di base. Tuttavia, non è consigliabile eseguire questa operazione in una fase iniziale dello sviluppo perché potrebbe interrompere la funzionalità. Dopo aver individuato il set di funzionalità finali di un'app, è possibile eliminare i provider e i servizi non necessari nelle cartelle seguenti:

- MRTK/servizi
- MRTK/provider
- MRTK/SDK/funzionalità

> [!NOTE]
> MRTK V2. x **_richiede_** il contenuto della cartella assets/MRTK/core.

## <a name="upcoming-features"></a>Funzionalità future

### <a name="application-architecture"></a>Architettura dell'applicazione

MRTK avrà il supporto per consentire la compilazione di applicazioni con un'ampia gamma di architetture, tra cui:

- [Localizzatore del servizio MixedRealityToolkit](#mixedrealitytoolkit-service-locator)
- [Singoli servizi](#individual-service-components)
- [Localizzatore servizio personalizzato](#custom-service-locator)
- [Architettura ibrida](#hybrid-architecture)

Quando si seleziona un'architettura di applicazione, è importante considerare la flessibilità di progettazione e le prestazioni dell'applicazione. Le architetture descritte di seguito non sono adatte per ogni applicazione.

#### <a name="mixedrealitytoolkit-service-locator"></a>Localizzatore del servizio MixedRealityToolkit

Il MRTK Abilita (e configura automaticamente) le scene dell'applicazione per usare il [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) componente di localizzazione del servizio predefinito. Questo componente include il supporto per la configurazione di sistemi e provider di dati MRTK tramite i controlli di configurazione e gestisce le durate dei componenti e i comportamenti principali (ad esempio, quando aggiornare).

Tutti i sistemi sono rappresentati nel controllo configurazione principale, indipendentemente dal fatto che siano presenti o non siano abilitati nel progetto. Per ulteriori informazioni, vedere la [Guida alla configurazione della realtà mista](../out-of-scope/MixedRealityConfigurationGuide.md) .

#### <a name="individual-service-components"></a>Singoli componenti del servizio

Alcuni sviluppatori hanno espresso il desiderio di includere singoli componenti del servizio nella gerarchia della scena dell'applicazione. Per abilitare questo utilizzo, i servizi dovranno essere incapsulati in un registrar personalizzato o essere autofirmati o autogestiti.

Un servizio di registrazione automatica implementa [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) e registra se stesso in modo che il codice dell'applicazione possa individuare l'istanza del servizio tramite un registro di sistema.

Un servizio di gestione automatica può essere implementato come un oggetto singleton nella gerarchia della scena. Questo oggetto fornisce una proprietà di istanza che può essere utilizzata dal codice dell'applicazione per accedere direttamente alle funzionalità del servizio.

#### <a name="custom-service-locator"></a>Localizzatore servizio personalizzato

Alcuni sviluppatori hanno richiesto la possibilità di creare un componente del localizzatore di servizi personalizzato. I localizzatori di servizi personalizzati implementano l' [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interfaccia e gestiscono il ciclo di vita e i comportamenti principali dei servizi attivi.

#### <a name="hybrid-architecture"></a>Architettura ibrida

MRTK supporterà un'architettura ibrida in cui gli sviluppatori possono combinare gli approcci precedenti in base alle esigenze o alle esigenze. Ad esempio, uno sviluppatore può iniziare con il [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizzatore del servizio e aggiungere un servizio di registrazione automatica.

> [!NOTE]
> Quando si opta per un'architettura ibrida, è importante tenere presente qualsiasi duplicazione del lavoro (ad esempio, l'acquisizione dei dati del controller da più componenti).
