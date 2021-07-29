---
title: Introduzione a Mixed Reality Feature Tool
description: Informazioni di base sullo strumento di funzionalità MR per lo sviluppo HoloLens vr.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 1244f9cd4da0d6ae0b5c6f92698f87f0edd812e2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757094"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Introduzione a Mixed Reality Feature Tool

![Immagine del banner dello strumento di funzionalità di realtà mista](images/feature-tool-banner.jpg)

> [!IMPORTANT]
> Lo strumento funzionalità realtà mista è attualmente disponibile solo per Unity. Se si sviluppa in Unreal, vedere la documentazione di [installazione degli](../install-the-tools.md) strumenti.

Lo strumento funzionalità realtà mista è un nuovo modo per consentire agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Se non si è mai usato un file manifesto prima, si tratta di un file JSON contenente tutti i pacchetti di progetti. Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.

## <a name="system-requirements"></a>Requisiti di sistema

Prima di poter eseguire lo strumento di funzionalità di realtà mista, sono necessari:

* [Runtime di .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Lo strumento funzionalità realtà mista attualmente viene eseguito solo Windows, ma il supporto macOS sarà presto disponibile.

## <a name="download"></a>Scarica

Dopo aver configurato l'ambiente:

* [Scaricare la versione più recente di Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) dall'Area download Microsoft.
* Al termine del download, decomprimere il file e salvarlo sul desktop
    * È consigliabile creare un collegamento al file eseguibile per un accesso più rapido

> [!NOTE]
> Se non si ha la novità di usare unity Gestione pacchetti, seguire le [istruzioni upm](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).

## <a name="changes-in-this-release"></a>Modifiche in questa versione

La versione 1.0.2103 Beta include le correzioni seguenti:

* Miglioramenti per scaricare il rilevamento degli errori.
* Aggiornamenti sulla modalità di scrittura dei manifesti per evitare errori di aggiornamento corretto.
* L'escpaing è stato rimosso dai percorsi di file nel manifesto del progetto.

In questa versione sono state aggiunte le funzionalità seguenti:

* Il catalogo di funzionalità è ora memorizzato nella cache. Per verificare la presenza di nuove funzionalità e aggiornamenti, usare il pulsante aggiorna in Individuazione.
* Spostare la selezione del progetto dal passaggio Importa a prima dell'individuazione.
* I pacchetti disponibili vengono filtrati in base alla versione di Unity specificata del progetto.
* La vista di individuazione visualizza ora i pacchetti attualmente installati.

## <a name="1-getting-started"></a>1. Guida introduttiva

Avviare Mixed Reality Feature Tool dal file eseguibile, che visualizza la pagina iniziale al primo avvio:

![Guida introduttiva](images/FeatureToolStart.png)

Nella pagina iniziale è possibile:

* [Configurare le](configuring-feature-tool.md) impostazioni dello strumento usando il **pulsante icona a forma di** ingranaggio
* Usare il **pulsante punto** interrogativo per avviare il Web browser predefinito e visualizzare la documentazione
* Selezionare **Avvia per** iniziare a individuare i pacchetti di funzionalità

## <a name="2-selecting-your-unity-project"></a>2. Selezione del progetto Unity

Per assicurarsi che tutte le funzionalità individuate siano supportate nella versione del progetto di Unity, il  passaggio precedente consiste nel puntare lo strumento funzionalità realtà mista al progetto usando il pulsante con i puntini di sospensione (a destra del campo del percorso del progetto).

![Selezionare il progetto Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file. Per consentire la selezione della cartella, deve essere presente un valore per il nome file.

Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista.

> [!IMPORTANT]
> Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity. La cartella deve `Assets` contenere `Packages` le cartelle e `Project Settings` .

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. Individuazione e acquisizione di pacchetti di funzionalità

> [!NOTE]
> La versione 1.0.2103 Beta ora memorizza nella cache il contenuto del catalogo di funzionalità ogni volta che si accede al server. Questa modifica consente l'accesso rapido alle funzionalità disponibili, a scapito della visualizzazione dei dati più recenti assoluti. Per aggiornare il catalogo, usare il **pulsante** Aggiorna.

Le funzionalità sono raggruppate per categoria per semplificare la ricerca. Ad esempio, la **categoria Toolkit** realtà mista include diverse funzionalità tra cui scegliere:

![Individuazione e acquisizione](images/FeatureToolDiscovery.png)

Quando lo strumento di funzionalità realtà mista riconosce le funzionalità importate in precedenza, visualizza un messaggio di notifica da parte di ognuna.

![Notifica della funzionalità importata](images/feature-tool-imported-note.png)


Dopo aver effettuato le scelte, selezionare **Recupera funzionalità** per recuperare tutti i pacchetti necessari dal catalogo. Per altre informazioni, vedere Individuazione e [acquisizione di funzionalità](discovering-features.md).

## <a name="4-importing-feature-packages"></a>4. Importazione di pacchetti di funzionalità

Dopo l'acquisizione, viene presentato il set completo di pacchetti, insieme a un elenco di dipendenze necessarie. Se è necessario modificare le selezioni di funzionalità o pacchetti, questo è il momento seguente:

![Importazione di pacchetti](images/FeatureToolImport.png)

È consigliabile usare il **pulsante Convalida** per assicurarsi che il progetto Unity possa importare correttamente le funzionalità selezionate. Dopo la convalida, verrà visualizzata una finestra di dialogo popup con un messaggio di esito positivo o un elenco di problemi identificati.

Selezionare **Importa** per continuare.

> [!NOTE]
> Dopo aver fatto **clic sul** pulsante Importa, se rimangono problemi verrà visualizzato un messaggio semplice. È consigliabile fare clic su No e usare il **pulsante Convalida** per visualizzare e risolvere i problemi.

Per altre informazioni, vedere Importazione [di funzionalità](importing-features.md).

## <a name="5-reviewing-and-approving-project-changes"></a>5. Revisione e approvazione delle modifiche al progetto

Il passaggio finale consiste nell'esaminare e approvare le modifiche proposte ai file manifesto e di progetto:

* Le modifiche proposte al manifesto vengono visualizzate a sinistra
* I file da aggiungere al progetto sono elencati a destra
* Il **pulsante** Confronta consente la visualizzazione affiancata del manifesto corrente e delle modifiche proposte

![Autorizzazione](images/FeatureToolApprovalRequest.png)

Per altre informazioni, vedere [Revisione e approvazione delle modifiche del progetto.](reviewing-changes.md)

## <a name="6-project-updated"></a>6. Project aggiornato

Quando le modifiche proposte vengono approvate, il progetto Unity di destinazione viene aggiornato per fare riferimento alle funzionalità di realtà mista selezionate.

![Project aggiornato](images/FeatureToolProjectUpdated.png)

La cartella Packages del progetto **Unity** include ora una sottocartella **MixedReality** con i file del pacchetto di funzionalità e il manifesto conterrà i riferimenti appropriati.

Tornare a Unity, attendere il caricamento delle nuove funzionalità selezionate e iniziare a compilare.

## <a name="see-also"></a>Vedere anche

- [Configurazione dello strumento di funzionalità](configuring-feature-tool.md)
- [Individuazione e acquisizione](discovering-features.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Importazione di pacchetti selezionati](importing-features.md)
- [Revisione e approvazione delle modifiche al progetto](reviewing-changes.md)