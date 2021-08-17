---
title: Configurazione del progetto Unreal
description: Informazioni su come configurare il progetto con la versione più recente di Unreal Engine e dello strumento di funzionalità di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realtà mista, sviluppo, funzionalità, nuovo progetto, emulatore, documentazione, guide, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, aggiornato, strumenti, introduzione, nozioni di base, unreal, toolkit, hub, installazione, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905589"
---
# <a name="setting-up-your-unreal-project"></a>Configurazione del progetto Unreal

È consigliabile installare [Unreal Engine versione 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o versione successiva per sfruttare appieno il supporto di HoloLens incorporato.

Passare alla scheda **Library (Libreria)** nell'utilità di avvio di Epic Games, selezionare la freccia a discesa accanto **a Launch (Avvia)** e fare clic su **Options (Opzioni).** In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).
![Opzione di installazione unreal HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importare Toolkit realtà mista per Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.

Se non si ha già un progetto di realtà mista, seguire le prime [tre](tutorials/unreal-uxt-ch1.md) sezioni delle esercitazioni HoloLens 2 Attività iniziali per ottenere un progetto pronto per MRTK.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>Introduzione all'hub MRTK per Unreal

È consigliabile usare l'hub MRTK per acquisire i plug-in MRTK. È un nuovo modo per gli sviluppatori di individuare e aggiornare i plug-in di Microsoft Mixed Reality e aggiungerli ai progetti Unreal. È possibile visualizzare i plug-in, visualizzarne le dipendenze e installarli nel progetto senza uscire dall'editor unreal.

- Scopri i nuovi plug-in di Microsoft Mixed Reality e installali e le relative dipendenze nel progetto Unreal.
- Mantenere aggiornati i plug-in di Microsoft Mixed Reality.
- Rimuovere i plug-in di Microsoft Mixed Reality dal progetto se non sono più necessari.

> [!NOTE]
> L'hub MRTK per Unreal è disponibile solo per Unreal Engine versione 4.26 o successiva. Per Unreal Engine versione 4.25, è possibile ottenere i plug-in MRTK da Unreal Engine Marketplace o GitHub come descritto nella sezione Attività iniziali [.](unreal-development-overview.md#1-getting-started)

#### <a name="installing-the-mrtk-hub"></a>Installazione dell'hub MRTK

Scaricare il plug-in [da Unreal Engine Marketplace,](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub)aprire il progetto e quindi abilitare il plug-in dalla sezione _Realtà_ mista del menu _Plugins (Plug-in)._ Quando richiesto, riavviare l'editor.

![Abilitare il plug-in dell'hub MRTK](images/hub-enable-plugin.png)

Dopo aver abilitato il plug-in per il progetto, è possibile accedere all'hub dal pulsante della barra degli strumenti.

![Aprire la finestra dell'hub MRTK](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>Installazione di plug-in di realtà mista

Per installare un plug-in usando l'hub, selezionare il plug-in che si vuole aggiungere al progetto e quindi fare clic _sul pulsante_ Installa. Per scaricare il plug-in, verificare che non siano presenti conflitti nella _casella Problemi_ e premere _Conferma._ Dopo aver scaricato il plug-in, verrà richiesto di riavviare l'editor. Sfortunatamente non è possibile riavviare automaticamente l'editor. talvolta la nuova istanza dell'editor verrà avviata prima del completamento dell'installazione.

![Installare un plug-in usando l'hub MRTK](images/hub-download.png)

Dopo aver chiuso l'editor, verrà visualizzato un prompt dei comandi con un indicatore di stato per decomprimere il plug-in scaricato. Verrà visualizzato un prompt dei comandi per ogni plug-in installato. Al termine della decompressione, è possibile ria aprire nuovamente l'editor e continuare con il percorso di sviluppo [della realtà mista.](unreal-quickstart.md)

![Decompressione di un plug-in nell'hub MRTK tramite il prompt dei comandi](images/hub-unpack.png)

> [!IMPORTANT]
> Dopo l'installazione, il plug-in deve essere archiviato nel controllo del codice sorgente come qualsiasi altro plug-in a livello di progetto.

#### <a name="updating-mixed-reality-plugins"></a>Aggiornamento dei plug-in di realtà mista

Per aggiornare un plug-in usando l'hub, selezionare il plug-in che si vuole aggiornare dall'elenco e fare clic sul _pulsante_ Installa. Per scaricare il plug-in aggiornato, verificare che non siano presenti conflitti nella _casella Problemi_ e premere _Conferma._ Verrà richiesto di riavviare l'editor per completare l'aggiornamento. Gli aggiornamenti del plug-in vengono e completati durante l'avvio dell'editor, quindi non è necessario attendere il completamento della decompressione prima di ria aprire nuovamente l'editor.

![Aggiornamento di un plug-in tramite l'hub MRTK](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>Rimozione dei plug-in di realtà mista

Per disinstallare un plug-in usando l'hub, selezionare il plug-in da rimuovere e quindi selezionare la versione installata dall'elenco a discesa. Per rimuovere il plug-in, verificare che non siano presenti conflitti nella _casella Problemi_ e premere _Conferma._ Verrà richiesto di riavviare l'editor per completare la rimozione.

![Rimozione di un plug-in tramite l'hub MRTK](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>Revisione delle modifiche e rilevamento delle incompatibilità

È possibile visualizzare le modifiche esatte che verranno apportate al progetto nella sezione inferiore della finestra dell'hub. Da qui è possibile visualizzare i plug-in che verranno aggiunti o rimossi dal progetto insieme a eventuali potenziali incompatibilità che potrebbero causare problemi quando sono state apportate le modifiche.

> [!NOTE]
> _L'elenco_ Problemi presenterà incompatibilità nella versione del motore Unreal e nelle versioni delle dipendenze del plug-in, ma non correggerà o suggerirà automaticamente le correzioni ai problemi.

![Tentativo di installare un plug-in incompatibile](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Immagine del logo Unreal](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se non si vuole usare MRTK per Unreal, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.