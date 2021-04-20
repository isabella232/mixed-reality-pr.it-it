---
title: Individuazione e acquisizione di funzionalità
description: Scoprire e scaricare le funzionalità di realtà mista.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732009"
---
# <a name="discovering-and-acquiring-features"></a>Individuazione e acquisizione di funzionalità

Le sezioni di questo articolo descrivono come trovare i pacchetti di funzionalità nello strumento di funzionalità di realtà mista. Fare riferimento alla schermata seguente se è necessario un riferimento per una determinata sezione:

![Individuazione delle funzionalità](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Funzionalità disponibili

### <a name="category"></a>Categoria

Lo strumento funzionalità realtà mista visualizza una raccolta di categorie di funzionalità per semplificare l'individuazione di ciò che si vuole. Espandere una delle categorie per visualizzare la raccolta di funzionalità disponibili.

> [!NOTE]
> Se non è possibile trovare la funzionalità che si sta cercando, selezionare **Altre funzionalità**.

![Categoria funzionalità](images/FeatureCategory.png)

L'intestazione della categoria nello screenshot precedente contiene le proprietà seguenti, da sinistra a destra:

- Pulsante Espandi e comprimi
- Nome della categoria (ad esempio: Mixed Reality Toolkit)
- Conteggio delle funzionalità selezionate
- Conteggio delle funzionalità disponibili
- Pulsanti di sezione

> [!NOTE]
> I pulsanti di selezione sono sensibili al contesto. In base allo stato di selezione delle funzionalità all'interno della categoria, verranno visualizzati uno o più pulsanti `Select All` `Select None` e .

### <a name="feature"></a>Funzionalità

![Voce di funzionalità](images/FeatureEntry.png)

Le funzionalità sono elencate nella categoria appropriata. Da sinistra a destra nello screenshot precedente, le voci di funzionalità contengono:

- Casella di controllo Di selezione
- Nome della funzionalità (ad esempio Mixed Reality Toolkit Foundation)
- Elenco delle versioni disponibili
- Collegamento ai dettagli [del pacchetto di funzionalità](viewing-package-details.md)

> [!NOTE]
> Se una funzionalità viene fornita da un programma di accesso anticipato (detto anche anteprima privata), verrà visualizzata un'icona indicatore di ![ ](images/EarlyAccess.png) accesso anticipato.

## <a name="refresh-the-feature-catalog"></a>Aggiornare il catalogo delle funzionalità

Per verificare la presenza di funzionalità nuove e aggiornate, fare clic sull'aggiornamento ![pulsante di aggiornamento](images/RefreshButton.png) . Questa operazione si connetterà al sito del catalogo e recupererà le informazioni più recenti. Dopo aver letto il catalogo, verranno visualizzate la data e l'ora dell'ultimo aggiornamento.

## <a name="select-features"></a>Selezione delle funzionalità

Le funzionalità vengono selezionate espandendo una categoria, selezionando una versione e facendo clic sulla casella di controllo:

![Funzionalità selezionate](images/SelectedFeatures.png)

Per selezionare ogni pacchetto all'interno di una categoria, viene `Select All` fornito un pulsante. `Select None` deseleziona tutti i pacchetti selezionati. 

Ogni categoria con una o più funzionalità selezionate verrà aggiornato per visualizzare il conteggio.

## <a name="acquiring-features"></a>Acquisizione di funzionalità

Dopo aver scelto le funzionalità, selezionare **Ottieni** funzionalità per avviare il download dei file del pacchetto di funzionalità selezionato.

> [!NOTE]
> Per impostazione predefinita, i file dei pacchetti di funzionalità acquisiti in precedenza non verranno scaricati nuovamente. Per modificare questo comportamento, vedere configurazione [dello strumento di funzionalità](configuring-feature-tool.md).

Al termine del download, lo strumento per le funzionalità di realtà mista passa al passaggio [di importazione delle](importing-features.md) funzionalità.

## <a name="going-back-to-the-previous-step"></a>Tornare al passaggio precedente

Da **Individua funzionalità,** lo strumento funzionalità realtà mista consente di tornare alla selezione del progetto. Selezionare **Torna indietro** per iniziare di nuovo.

## <a name="see-also"></a>Vedi anche

- [Introduzione a Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Configurazione dello strumento di funzionalità](configuring-feature-tool.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Importazione di pacchetti selezionati](importing-features.md)
