---
title: Configurazione dello strumento di funzionalità di realtà mista
description: Informazioni su come scaricare e installare pacchetti Unity di Realtà mista dallo strumento di funzionalità MR per lo HoloLens e la realtà virtuale.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 419f26f79ca8bdd1998955a2bdf72dfabf73976c89b1abce175ef2cf60c9597b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210909"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configurazione dello strumento di funzionalità di realtà mista

Quando si usa lo strumento di funzionalità di realtà mista, è possibile accedere a tre diverse categorie di impostazioni che è possibile personalizzare:

* [Impostazioni di download](#download-settings)
* [Impostazioni delle funzionalità](#feature-settings)
* [Importare le impostazioni](#import-settings)

## <a name="download-settings"></a>Impostazioni di download

![Impostazioni di download](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Sovrascrivi file di pacchetto esistenti

Se si abilita questa impostazione, i file del pacchetto vengono scaricati ogni volta che vengono acquisiti. 

* **È consigliabile lasciare questa opzione disabilitata per ridurre l'utilizzo della larghezza di banda di rete**
* Per impostazione predefinita, i file del pacchetto acquisiti in precedenza non vengono scaricati nuovamente

### <a name="package-cache"></a>Cache dei pacchetti

Modificare questa impostazione per aggiornare il percorso in cui vengono scaricati i pacchetti di funzionalità.

> [!NOTE]
> Questa impostazione è **di sola lettura** in questa versione. Le versioni future possono rendere configurabile questa impostazione.

## <a name="feature-settings"></a>Impostazioni delle funzionalità

![Impostazioni delle funzionalità](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Mostra versioni di anteprima

Abilitare questa impostazione per acquisire le versioni di anteprima.
* Per impostazione predefinita, le versioni di anteprima non vengono visualizzate nello strumento di funzionalità di realtà mista 

> [!NOTE]
> Una versione di anteprima è definita come contenente la designazione **"-preview"** nella versione del pacchetto.

### <a name="show-early-access-program-features"></a>Visualizzare le funzionalità del programma ad accesso anticipato

Abilitare questa impostazione per acquisire funzionalità dalle versioni dei programmi registrati ad accesso anticipato.

* Per impostazione predefinita, le funzionalità di accesso anticipato non vengono visualizzate nello strumento di funzionalità di realtà mista 

> [!NOTE]
> L'abilitazione di senza può comportare la visualizzazione dei pacchetti di `Show early access program features` `Show preview releases` accesso eary nell'individuazione.

## <a name="import-settings"></a>Importare impostazioni

![Importare impostazioni](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Sostituire i file di pacchetto esistenti

Per impostazione predefinita, lo strumento di funzionalità di realtà mista rimuove le copie precedenti dei pacchetti importati per ridurre le dimensioni del file e i calcoli non necessari. 

* Deselezionare questa impostazione per mantenere tutte le versioni

### <a name="project-relative-import-path"></a>Project percorso di importazione relativo

Modificare questa impostazione per aggiornare il percorso della cartella del progetto in cui vengono copiati i pacchetti di funzionalità durante l'importazione. 

* Ad esempio, se la cartella del progetto è **C:\GalaxyExplorer**, il percorso di importazione completo sarà **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Questa impostazione è **di sola lettura** in questa versione. Le versioni future possono rendere configurabile questa impostazione.

## <a name="early-access-settings"></a>Impostazioni di accesso anticipato

![Impostazioni di accesso anticipato](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Chiedere conferma prima di rimuovere un programma ad accesso anticipato

Questa impostazione determina se verrà visualizzata una richiesta ogni volta che viene rimosso un programma ad accesso anticipato.

### <a name="my-previews"></a>Anteprime

Elenco di programmi registrati ad accesso anticipato. Usare `Add` , `Edit` e per gestire la raccolta di programmi `Remove` registrati.

## <a name="diagnostic-settings"></a>Impostazioni di diagnostica

![Impostazioni di diagnostica](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>File di registro

Visualizza il percorso del file di log di diagnostica.

## <a name="see-also"></a>Vedi anche

- [Introduzione a Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)