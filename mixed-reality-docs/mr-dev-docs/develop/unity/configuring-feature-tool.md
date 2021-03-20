---
title: Configurazione dello strumento funzionalità per la realtà mista
description: Informazioni su come scaricare e installare i pacchetti Unity per la realtà mista dallo strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244597"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configurazione dello strumento funzionalità per la realtà mista

Quando si usa lo strumento per la funzionalità di realtà mista, è possibile accedere a tre diverse categorie di impostazioni che è possibile personalizzare in:

* [Impostazioni di download](#download-settings)
* [Impostazioni delle funzionalità](#feature-settings)
* [Importare impostazioni](#import-settings)

![Impostazioni](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Impostazioni di download

### <a name="overwrite-existing-package-files"></a>Sovrascrivi file di pacchetto esistenti

L'abilitazione di questa impostazione causa il download dei file del pacchetto ogni volta che vengono acquisiti. 
* **È consigliabile lasciare questa opzione disabilitata per ridurre l'utilizzo della larghezza di banda di rete**
* Per impostazione predefinita, i file dei pacchetti acquisiti in precedenza non vengono scaricati di nuovo

### <a name="package-cache"></a>Cache pacchetti

Modificare questa impostazione per aggiornare il percorso in cui vengono scaricati i pacchetti di funzionalità.

> [!NOTE]
> Questa impostazione è di sola **lettura** in questa versione. Le versioni future possono rendere questa impostazione configurabile.

## <a name="feature-settings"></a>Impostazioni delle funzionalità

### <a name="include-preview-releases"></a>Includi versioni di anteprima

Abilitare questa impostazione per acquisire le versioni di anteprima.
* Per impostazione predefinita, le versioni di anteprima non vengono visualizzate nello strumento funzionalità di realtà mista 

> [!NOTE]
> Una versione di anteprima è definita come contenente la designazione **"-Preview"** nella versione del pacchetto.

## <a name="import-settings"></a>Importare impostazioni

### <a name="replace-existing-package-files"></a>Sostituisci file di pacchetto esistenti

Per impostazione predefinita, lo strumento della funzionalità di realtà mista rimuove le copie precedenti dei pacchetti importati per ridurre le dimensioni del file e i calcoli non necessari. 
* Deselezionare questa impostazione per salvare tutte le versioni

### <a name="project-relative-import-path"></a>Percorso importazione relativa progetto

Modificare questa impostazione in Aggiorna percorso cartella di progetto in cui vengono copiati i pacchetti di funzionalità durante l'importazione. 
* Ad esempio, se la cartella del progetto è **C:\GalaxyExplorer**, il percorso di importazione completo sarà **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Questa impostazione è di sola **lettura** in questa versione. Le versioni future possono rendere questa impostazione configurabile.

## <a name="see-also"></a>Vedi anche

- [Strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md)