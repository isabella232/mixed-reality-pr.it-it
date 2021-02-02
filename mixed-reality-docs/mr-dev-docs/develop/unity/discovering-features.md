---
title: Individuazione e acquisizione di funzionalità
description: Scopri e Scarica le funzionalità della realtà mista.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 4da6b6fdfc0205d4fa7fb5bf4ae9e48993d7c1e6
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244599"
---
# <a name="discovering-and-acquiring-features"></a>Individuazione e acquisizione di funzionalità

Le sezioni di questo articolo descrivono come trovare i pacchetti di funzionalità nello strumento per le funzionalità di realtà mista. Se è necessario un riferimento per una sezione specifica, fare riferimento alla schermata seguente:

![Individuazione delle funzionalità](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Funzionalità disponibili

### <a name="category"></a>Category

Lo strumento per la funzionalità di realtà mista Visualizza una raccolta di categorie di funzionalità che semplificano l'individuazione delle informazioni desiderate. Espandere una delle categorie per visualizzare la raccolta delle funzionalità disponibili.

> [!NOTE]
> Se non si riesce a trovare la funzionalità cercata, controllare **altre funzionalità**.

![Categoria funzionalità](images/FeatureCategory.png)

L'intestazione Category dello screenshot precedente contiene le proprietà seguenti, da sinistra a destra:

- Pulsante Espandi e Comprimi
- Nome della categoria (ad esempio, Toolkit di realtà mista)
- Numero di funzionalità selezionate
- Numero di funzionalità disponibili

### <a name="feature"></a>Funzionalità

![Voce della funzionalità](images/FeatureEntry.png)

Le funzionalità sono elencate nella categoria appropriata. Da sinistra a destra nella schermata precedente, le voci di funzionalità contengono:

- Casella di controllo selezione
- Nome della funzionalità (ad esempio, Mixed Reality Toolkit Foundation)
- Elenco delle versioni disponibili
- Collegamento ai [Dettagli del pacchetto di funzionalità](viewing-package-details.md)

## <a name="refresh-the-feature-catalog"></a>Aggiornare il catalogo delle funzionalità

Per verificare la presenza di funzionalità nuove e aggiornate, fare clic sull'aggiornamento ![pulsante Aggiorna](images/RefreshButton.png) . Questa operazione si connetterà al sito del catalogo e recupererà le informazioni più recenti.
* Una volta che il catalogo è stato letto, verranno visualizzate la data e l'ora dell'ultimo aggiornamento.

## <a name="select-features"></a>Selezione delle funzionalità

Le funzionalità vengono selezionate espandendo una categoria, selezionando una versione e facendo clic sulla casella di controllo:

![Funzionalità selezionate](images/SelectedFeatures.png)

Ogni categoria con una o più funzionalità selezionate viene aggiornata per visualizzare il conteggio.

## <a name="acquiring-features"></a>Acquisizione di funzionalità

Dopo aver scelto le funzionalità, selezionare **Ottieni funzionalità** per avviare il download dei file del pacchetto di funzionalità selezionato.

> [!NOTE]
> Per impostazione predefinita, i file del pacchetto di funzionalità acquisiti in precedenza non verranno scaricati di nuovo. Per modificare questo comportamento, vedere [configurazione dello strumento per le funzionalità](configuring-feature-tool.md).

Al termine del download, lo strumento per la funzionalità di realtà mista passerà al passaggio delle [funzionalità di importazione](importing-features.md) .

## <a name="going-back-to-the-previous-step"></a>Tornando al passaggio precedente

Dalle **funzionalità di individuazione**, lo strumento della funzionalità di realtà mista consente di tornare all'inizio. Selezionare torna **indietro** per avviare di nuovo.

## <a name="see-also"></a>Vedi anche

- [Strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md)
- [Configurazione dello strumento funzionalità](configuring-feature-tool.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Importazione dei pacchetti selezionati](importing-features.md)
