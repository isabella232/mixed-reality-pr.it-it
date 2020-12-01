---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443520"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Se si dispone di un'applicazione HoloLens, scegliere l' [opzione di distribuzione](../distribute-overview.md#distribution-options) preferita nella tabella seguente. Se si esegue la pubblicazione nel Microsoft Store, è possibile aggiungere [acquisti in-app](../in-app-purchases.md) per monetizzare il contenuto.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Se si usa un'applicazione immersiva destinata a un headset di realtà mista di Windows, creare un utilità di avvio delle app 3D, quindi scegliere l' [opzione di distribuzione](../distribute-overview.md#distribution-options) preferita nella tabella seguente. Se si esegue la pubblicazione nel Microsoft Store, è possibile aggiungere [acquisti in-app](../in-app-purchases.md) per monetizzare il contenuto.

### <a name="designing-3d-app-launchers-for-vr"></a>Progettazione di lanci di app 3D per VR 

i lanci di app 3D vengono visualizzati come oggetti nell'ambiente principale della realtà mista di Windows che viene visualizzato ogni volta che un utente inserisce un auricolare immersivo. Questi oggetti sono personalizzati per la creazione e la personalizzazione, ma è consigliabile iniziare con l'articolo delle [linee guida di progettazione](../3d-app-launcher-design-guidance.md) per ottenere il blocco di procedure di progettazione ottimali, tra cui scalabilità, tipo, scelta dei colori, texturing e, soprattutto, rendendola in un ambiente virtuale.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modellazione ed esportazione di lanci di app 3D

Una volta impostato l'idea per l'utilità di avvio delle app 3D, è necessario verificare che soddisfi i requisiti di Microsoft Store, inclusi il formato di file di asset, il numero di triangolo, le dimensioni della trama, la lunghezza dell'animazione e l'ottimizzazione degli asset. Questo processo può essere altamente tecnico, quindi è consigliabile usare l'articolo [creazione di modelli 3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per verificare tutte le caselle. Gli asset che non soddisfano questa specifica di authoring non verranno visualizzati nella Home realtà mista di Windows.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Aggiunta di lanci di app 3D nelle app

Dopo aver verificato che l'utilità di avvio delle app 3D soddisfi le linee guida per la creazione di realtà miste di Windows, può essere usata per eseguire l'override dell'utilità di avvio 2D predefinita per l'applicazione nell'ambiente principale della realtà mista di Windows. Il processo per l'integrazione di un Launcher di app 3D nell'applicazione dipende dal tipo di applicazione che si sta sviluppando:

* [App UWP](../implementing-3d-app-launchers.md)
* [App Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>Opzionale Inserimento di modelli 3D nella Home realtà mista di Windows

Come ulteriore vantaggio, alcune applicazioni 2D consentono di inserire modelli 3D direttamente nella Home realtà mista di Windows come decorazioni o per un ulteriore controllo in 3D completo. Il protocollo Aggiungi modello consente di inviare un modello 3D dal sito Web o dall'applicazione alla Home realtà mista di Windows, in cui verranno mantenuti come i lanci di app 3D, le app 2D e gli ologrammi. Scopri [come inserire modelli 3D nella Home realtà mista di Windows](../enable-placement-of-3d-models-in-the-home.md) per trovare altre informazioni e istruzioni su come vivacizzare le tue app.