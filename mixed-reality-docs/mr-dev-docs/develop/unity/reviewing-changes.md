---
title: Autorizzazione delle modifiche al progetto
description: Informazioni su come autorizzare le modifiche apportate al progetto lo strumento per lo sviluppo HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244586"
---
# <a name="authorizing-project-changes"></a>Autorizzazione delle modifiche al progetto

Prima di modificare il progetto Unity, è necessario rivedere e approvare le modifiche apportate al manifesto e ai file di progetto:

![Richiesta dell'autorizzazione](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>manifesto

Le modifiche al manifesto proposte possono essere visualizzate nella colonna **manifesto** a sinistra. Il contenuto è esattamente ciò che verrà scritto nel manifesto del progetto (**packages/manifest.json**):

![Anteprima manifesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>File da copiare nel progetto

I **file da copiare nella sezione Project** a destra elencano i file specifici del pacchetto di funzionalità che verranno copiati nel progetto Unity:

![Anteprima del manifesto con i file da copiare](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Confronta manifesti

È possibile visualizzare un confronto affiancato dettagliato di tutte le modifiche proposte selezionando **Confronta**:

![Confronta manifesti](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Approvazione delle modifiche

Quando vengono approvate le modifiche proposte, i file elencati verranno copiati nel progetto Unity e il manifesto verrà aggiornato con i riferimenti a questi file.

> [!NOTE]
> I file del pacchetto di funzionalità (*. tgz) devono essere aggiunti al controllo del codice sorgente. Viene fatto riferimento usando un percorso relativo per consentire ai team di sviluppo di condividere facilmente le funzionalità e le modifiche del manifesto.

 Come parte delle modifiche, verrà eseguito il backup del **manifest.jscorrente sul** file.

> [!IMPORTANT]
> Quando si visualizzano i backup del manifesto, il meno recente verrà chiamato **manifest.json. backup**. I backup più recenti verranno annotati con un valore numerico, a partire da zero (0).

## <a name="going-back-to-the-previous-step"></a>Tornando al passaggio precedente

Se è necessario apportare modifiche alle selezioni delle funzionalità, usare **tornare indietro** per tornare al passaggio di [importazione](importing-features.md) .

## <a name="see-also"></a>Vedi anche

- [Strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md)
- [Importazione dei pacchetti selezionati](importing-features.md)
