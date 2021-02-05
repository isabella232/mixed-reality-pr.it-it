---
title: Strumento per la funzionalità di realtà mista
description: Informazioni sulle nozioni di base dello strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570254"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Strumento per la funzionalità di realtà mista

![Immagine del banner dello strumento della funzionalità di realtà mista](images/feature-tool-banner.png)

> [!IMPORTANT]
> Lo strumento per la funzionalità di realtà mista è disponibile solo per Unity al momento. Se si sta sviluppando in Unreal, fare riferimento alla documentazione di [installazione degli strumenti](../install-the-tools.md) .

Lo strumento per la funzionalità di realtà mista è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Se non si è mai usato un file manifesto prima, si tratta di un file JSON contenente tutti i pacchetti di progetti. Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.

## <a name="system-requirements"></a>Requisiti di sistema

Prima di poter eseguire lo strumento per la funzionalità di realtà mista, è necessario:

* [Runtime .NET 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Lo strumento per le funzionalità di realtà mista attualmente viene eseguito solo in Windows, ma il supporto MacOS sarà presto disponibile.

## <a name="download"></a>Scarica 

Dopo aver configurato l'ambiente:

* [Scaricare la versione più recente dello strumento per le funzionalità di realtà mista](https://aka.ms/MRFeatureTool) dall'area download Microsoft.
* Al termine del download, decomprimere il file e salvarlo sul desktop
    * Si consiglia di creare un collegamento al file eseguibile per un accesso più rapido

## <a name="1-getting-started"></a>1. Guida introduttiva

Avviare lo strumento della funzionalità di realtà mista dal file eseguibile, che visualizza la pagina iniziale al primo avvio:

![Guida introduttiva](images/FeatureToolStart.png)

Dalla pagina iniziale è possibile:

* [Configurare](configuring-feature-tool.md) le impostazioni dello strumento usando il pulsante dell' **icona dell'ingranaggio**
* Usare il pulsante **punto interrogativo** per avviare il Web browser predefinito e visualizzare la documentazione
* Selezionare **inizia** per iniziare a individuare i pacchetti di funzionalità

## <a name="2-discovering-and-acquiring-feature-packages"></a>2. individuazione e acquisizione dei pacchetti di funzionalità

Il catalogo dei pacchetti di funzionalità viene recuperato non appena si preme Avvia. Le funzionalità sono raggruppate per categoria per semplificare la ricerca. Ad esempio, la categoria del **Toolkit di realtà mista** offre diverse funzionalità per scegliere:

![Individuazione e acquisizione](images/FeatureToolDiscovery.png)

Una volta effettuate le scelte, selezionare **Recupera funzionalità** per recuperare tutti i pacchetti necessari dal catalogo. Per ulteriori informazioni, vedere [individuazione e acquisizione di funzionalità](discovering-features.md).

## <a name="3-importing-feature-packages"></a>3. importazione di pacchetti di funzionalità

Dopo l'acquisizione viene presentato il set completo di pacchetti, insieme a un elenco di dipendenze obbligatorie. Se è necessario modificare le selezioni delle funzionalità o dei pacchetti, questo è il momento:

![Importazione di pacchetti](images/FeatureToolImport.png)

Si consiglia vivamente di usare il pulsante **Validate** per assicurarsi che il progetto Unity possa importare correttamente le funzionalità selezionate. Dopo la convalida, verrà visualizzata una finestra di dialogo popup con un messaggio di operazione completata o un elenco di problemi identificati.

Prima di importare, è anche necessario impostare il percorso del progetto Unity di destinazione. Utilizzare il pulsante con i **puntini** di sospensione a sinistra del campo percorso progetto per sfogliare. Al termine dell'esplorazione della file system, aprire la cartella che contiene il progetto Unity di destinazione.

> [!NOTE]
> La finestra di dialogo visualizzata quando si Esplora la cartella del progetto Unity contiene ' _' come nome file. Per abilitare la selezione della cartella, è necessario specificare un valore per il nome del file.

Selezionare **Importa** per continuare.

> [!NOTE]
> Dopo aver fatto clic sul pulsante **Importa** , se eventuali problemi rimangono, verrà visualizzato un messaggio semplice. È consigliabile fare clic su No e utilizzare il pulsante **Validate** per visualizzare e risolvere i problemi.

Per ulteriori informazioni, vedere [importazione di funzionalità](importing-features.md).

## <a name="4-reviewing-and-approving-project-changes"></a>4. Revisione e approvazione delle modifiche del progetto

Il passaggio finale consiste nell'esaminare e approvare le modifiche proposte al manifesto e ai file di progetto:

* Le modifiche proposte al manifesto vengono visualizzate a sinistra
* I file da aggiungere al progetto sono elencati a destra
* Il pulsante **Confronta** consente di visualizzare side-by-side del manifesto corrente e delle modifiche proposte

![Autorizzazione](images/FeatureToolApprovalRequest.png)

Per ulteriori informazioni, vedere [revisione e approvazione delle modifiche del progetto](reviewing-changes.md).

## <a name="5-project-updated"></a>5. progetto aggiornato

Quando vengono approvate le modifiche proposte, il progetto Unity di destinazione viene aggiornato in modo da fare riferimento alle funzionalità di realtà mista selezionate:

![Progetto aggiornato](images/FeatureToolProjectUpdated.png)

La cartella **packages** del progetto Unity dispone ora di una sottocartella **MixedReality** con i file del pacchetto di funzionalità e il manifesto conterrà i riferimenti appropriati.

Tornare a Unity, attendere il caricamento delle nuove funzionalità selezionate e iniziare la compilazione.

## <a name="see-also"></a>Vedi anche

- [Configurazione dello strumento funzionalità](configuring-feature-tool.md)
- [Individuazione e acquisizione](discovering-features.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Importazione dei pacchetti selezionati](importing-features.md)
- [Revisione e approvazione delle modifiche del progetto](reviewing-changes.md)
