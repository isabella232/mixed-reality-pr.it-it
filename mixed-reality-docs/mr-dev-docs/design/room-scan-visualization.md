---
title: Visualizzazione della scansione dello spazio
description: Le applicazioni che richiedono il mapping spaziale usano il dispositivo per raccogliere dati nel tempo e tra le sessioni.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Modelli di app, progettazione, HoloLens, scansione della stanza, mapping spaziale, mesh, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens
ms.openlocfilehash: 0ebfbd9a1f07ffd0671d36dcc63dbd5303a2cdbceb906839be9736f43de76937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207829"
---
# <a name="room-scan-visualization"></a>Visualizzazione della scansione dello spazio

Le applicazioni che richiedono il mapping spaziale si basano sul dispositivo per raccogliere dati nel tempo e tra le sessioni. La completezza e la qualità dei dati di mapping dipendono da molti fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo passato dall'esplorazione e se oggetti come mobili e porte sono stati spostati dopo la scansione dell'area da parte del dispositivo.

Per garantire dati di mapping spaziale utili, gli sviluppatori di applicazioni hanno diverse opzioni:
* Fare affidamento su ciò che potrebbe essere già stato raccolto. Questi dati potrebbero essere inizialmente incompleti.
* Chiedere all'utente di usare il movimento di fiore per raggiungere la Windows Mixed Reality home e quindi esplorare l'area da usare per l'esperienza. Possono usare il tocco per verificare che tutta l'area necessaria sia nota al dispositivo.
* Creare un'esperienza di esplorazione personalizzata nella propria applicazione.

In tutti questi casi, i dati effettivi raccolti durante l'esplorazione vengono archiviati dal sistema e l'applicazione non deve eseguire questa operazione. Se si desidera vedere la visualizzazione della scansione della stanza in azione, vedere la demo video **Progettazione di Ologrammi - Consapevolezza** spaziale di seguito:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Questo video è stato tratto dall'app "Progettazione Ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Visualizzazione della scansione dello spazio</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>Creazione di un'esperienza di analisi personalizzata

Le applicazioni possono analizzare i dati di mapping spaziale all'inizio dell'esperienza per valutare se vogliono che l'utente eserciti passaggi aggiuntivi per migliorarne la completezza e la qualità. Se l'analisi indica che la qualità deve essere migliorata, gli sviluppatori devono fornire una visualizzazione da sovrapporre al mondo per indicare:
* La quantità del volume totale nelle vicinanze degli utenti deve far parte dell'esperienza
* Dove l'utente deve andare per migliorare i dati

Gli utenti non sanno cosa rende un'analisi "buona". È necessario mostrarne o determinare cosa cercare se viene chiesto di valutare un'analisi: flatness, distanza dalle pareti effettive e così via. Lo sviluppatore deve implementare un ciclo di feedback che includa l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o esplorazione.

In molti casi, è meglio indicare all'utente cosa deve fare per ottenere la qualità di analisi necessaria. Ad esempio, osservare il controsoffitto, guardare dietro le quinte e così via.

## <a name="cached-versus-continuous-spatial-mapping"></a>Mapping spaziale continuo e memorizzato nella cache

I dati di mapping spaziale sono le applicazioni di origine dati con il peso più pesante che possono utilizzare. Per evitare problemi di prestazioni, ad esempio frame eliminati o stuttering, l'utilizzo di questi dati deve essere eseguito con attenzione.

L'analisi attiva durante un'esperienza può essere utile e dannosa, quindi è necessario decidere quale metodo usare in base all'esperienza.

### <a name="cached-spatial-mapping"></a>Mapping spaziale memorizzato nella cache

Se sono presenti dati di mapping spaziale memorizzati nella cache, l'applicazione in genere snapshot dei dati di mapping spaziale e usa questo snapshot durante l'esperienza.

**Vantaggi**
* Riduzione del sovraccarico del sistema durante l'esecuzione dell'esperienza, con un notevole miglioramento delle prestazioni di potenza, termica e CPU.
* Implementazione più semplice dell'esperienza principale perché non viene interrotta dalle modifiche nei dati spaziali.
* Un singolo costo una volta per qualsiasi post-elaborazione dei dati spaziali per la fisica, la grafica e altri scopi.

**Svantaggi**
* Lo spostamento di oggetti o persone reali non viene riflessa dai dati memorizzati nella cache. Ad esempio, l'applicazione potrebbe considerare aperta una porta quando viene chiusa.
* Potenzialmente più memoria dell'applicazione per mantenere la versione dei dati memorizzata nella cache.

Un buon caso per questo metodo è un ambiente controllato o un gioco da tavolo principale.

### <a name="continuous-spatial-mapping"></a>Mapping spaziale continuo

Alcune applicazioni possono basarsi sull'analisi continua per aggiornare i dati di mapping spaziale.

**Vantaggi**
* Non è necessario creare in anticipo un'esperienza di analisi o esplorazione separata nell'applicazione.
* Lo spostamento di oggetti reali può essere riflessa dal gioco, anche se con un certo ritardo.

**Svantaggi**
* Maggiore complessità nell'implementazione dell'esperienza principale.
* Potenziale sovraccarico dovuto all'elaborazione grafica e fisica aggiuntiva, in quanto le modifiche devono essere inserite in modo incrementale da questi sistemi.
* Maggiore impatto su potenza, termica e CPU.

Un buon caso per questo metodo è quello in cui si prevede che gli ologrammi interagiscano con gli oggetti in movimento, ad esempio un'auto olografica che guida sul piano può voler entrare in una porta a seconda che sia aperta o chiusa.

## <a name="see-also"></a>Vedere anche

* [Mapping spaziale](spatial-mapping.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)