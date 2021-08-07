---
title: Autorizzazione delle modifiche al progetto
description: Informazioni su come autorizzare le modifiche al progetto con MR Feature Tool per lo HoloLens e la realtà virtuale.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 67c3b0cd5dbfcc2d0858a098aa3c80f4a8105c5637d26b4e33268d4b830b218e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211755"
---
# <a name="authorizing-project-changes"></a>Autorizzazione delle modifiche al progetto

Prima di modificare il progetto Unity, le modifiche apportate ai file manifesto e di progetto devono essere esaminate e approvate:

![Richiesta di autorizzazione](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>manifesto

Le modifiche proposte al manifesto possono essere visualizzate nella **colonna Manifesto** a sinistra. Il contenuto è esattamente ciò che verrà scritto nel manifesto del progetto (**Packages/manifest.jsin**):

![Anteprima del manifesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>File da copiare nel progetto

La **sezione File da copiare nella sezione del** progetto a destra elenca i file del pacchetto di funzionalità specifici che verranno copiati nel progetto Unity:

![Anteprima del manifesto con i file da copiare](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Confrontare i manifesti

È possibile visualizzare un confronto dettagliato affiancato di tutte le modifiche proposte selezionando **Confronta:**

![Confrontare i manifesti](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Approvazione delle modifiche

Quando le modifiche proposte vengono approvate, i file elencati verranno copiati nel progetto Unity e il manifesto verrà aggiornato con riferimenti a questi file.

> [!NOTE]
> I file del pacchetto di funzionalità (*.tgz) devono essere aggiunti al controllo del codice sorgente. Si fa riferimento a questi elementi usando un percorso relativo per consentire ai team di sviluppo di condividere facilmente le funzionalità e le modifiche del manifesto.

 Come parte delle modifiche, verrà eseguito **il backupmanifest.jscorrente nel** file.

> [!IMPORTANT]
> Quando si visualizzano i backup del manifesto, il meno recente verrà chiamato **manifest.json.backup**. I backup più nuovi verranno annotati con un valore numerico, a partire da zero (0).

## <a name="going-back-to-the-previous-step"></a>Tornare al passaggio precedente

Se è necessario apportare modifiche alle selezioni delle funzionalità, usare **Torna** indietro per tornare al passaggio [di](importing-features.md) importazione.

## <a name="see-also"></a>Vedi anche

- [Introduzione a Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Importazione dei pacchetti selezionati](importing-features.md)
