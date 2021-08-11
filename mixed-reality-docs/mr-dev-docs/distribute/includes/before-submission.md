---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198788"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

Se si ha un'HoloLens, scegliere l'opzione [di distribuzione](../distribute-overview.md#distribution-options) preferita nella tabella seguente. Se si pubblica nel Microsoft Store, è possibile aggiungere acquisti [in-app](../in-app-purchases.md) per monetizzare il contenuto.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Se si lavora con un'applicazione immersiva destinata a un visore Windows Mixed Reality, creare [](../distribute-overview.md#distribution-options) un'icona di avvio di app 3D, quindi scegliere l'opzione di distribuzione preferita dalla tabella seguente. Se si pubblica nel Microsoft Store, è possibile aggiungere acquisti [in-app](../in-app-purchases.md) per monetizzare il contenuto.

### <a name="designing-3d-app-launchers-for-vr"></a>Progettazione di utilità di avvio di app 3D per la realtà virtuale 

Le utilità di avvio delle app 3D vengono visualizzate come oggetti nell'ambiente Windows Mixed Reality home che viene visualizzato ogni volta che un utente mette un visore immersivo. Questi oggetti possono essere creati e personalizzati come si desidera, ma [](../3d-app-launcher-design-guidance.md) è consigliabile iniziare con l'articolo sulle linee guida per la progettazione per ottenere buone procedure di progettazione, tra cui ridimensionamento, tipo, scelta dei colori, texturing e, soprattutto, per distinguerlo in un ambiente virtuale.

### <a name="modeling-and-exporting-3d-app-launchers"></a>Modellazione ed esportazione di utilità di avvio di app 3D

Dopo aver impostato l'idea per l'icona di avvio delle app 3D, è necessario assicurarsi che soddisfi i requisiti di Microsoft Store, tra cui il formato del file di asset, il numero di triangoli, le dimensioni delle trame, la lunghezza dell'animazione e l'ottimizzazione degli asset. Questo processo può essere altamente tecnico, quindi è consigliabile usare l'articolo sulla creazione di modelli [3D](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per controllare tutte le caselle. Gli asset che non soddisfano questa specifica di creazione non verranno sottoposti a rendering nella Windows Mixed Reality home page.

### <a name="adding-3d-app-launchers-in-your-apps"></a>Aggiunta di utilità di avvio di app 3D nelle app

Dopo aver garantito che l'icona di avvio delle app 3D soddisfi le linee guida per la creazione di Windows Mixed Reality, può essere usata per eseguire l'override dell'utilità di avvio 2D predefinita per l'applicazione nell'ambiente Windows Mixed Reality home. Il processo di integrazione di un'utilità di avvio di app 3D nell'applicazione dipende dal tipo di applicazione che si sta sviluppando:

* [App UWP](../implementing-3d-app-launchers.md)
* [App Win32](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>[Facoltativo] Posizionamento di modelli 3D nella Windows Mixed Reality iniziale

Come ulteriore vantaggio, alcune applicazioni 2D consentono di posizionare i modelli 3D direttamente nella casa Windows Mixed Reality come decori o per un'ispezione completa in 3D. Il protocollo aggiungi modello consente di inviare un modello 3D dal sito Web o dall'applicazione alla home page di Windows Mixed Reality, dove verrà mantenuto come utilità di avvio di app 3D, app 2D e ologrammi. Vedere come [posizionare i modelli 3D](../enable-placement-of-3d-models-in-the-home.md) nella home Windows Mixed Reality per trovare altri dettagli e istruzioni su come creare app personalizzate.