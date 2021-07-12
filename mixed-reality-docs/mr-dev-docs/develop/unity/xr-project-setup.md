---
title: Configurazione della configurazione XR
description: Rimanere aggiornati sulle raccomandazioni di configurazione più recenti di Unity XR per lo HoloLens di applicazioni.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603727"
---
# <a name="setting-up-your-xr-configuration"></a>Configurazione della configurazione XR

Dopo aver scelto una [versione di Unity,](choosing-unity-version.md)il passaggio successivo consiste nel selezionare la configurazione XR che verrà utilizzata per creare l'app di realtà mista:

## <a name="choosing-an-xr-configuration"></a>Scelta di una configurazione XR

Quando si avvia un nuovo progetto Unity, è possibile selezionare diverse configurazioni XR: plug-in **OpenXR** di realtà mista, plug-in **XR Windows** e **XR legacy incorporato.**

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

Il modo più semplice per configurare il progetto Unity per la realtà mista è con l'Toolkit (MRTK).  MRTK per Unity è un kit di sviluppo multipiattaforma open source progettato per semplificare la creazione di straordinarie applicazioni di realtà mista.

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali.  Con MRTK versione 2, è possibile velocizzare lo sviluppo di applicazioni per Microsoft HoloLens, visori vr immersivi Windows Mixed Reality e molti altri dispositivi VR/AR. Il progetto ha lo scopo di ridurre le barriere all'ingresso, consentendo a tutti di creare applicazioni di realtà mista e contribuire alla community con la crescita di tutti.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

Per altre informazioni sul modello di realtà Toolkit, vedere la [documentazione di MRTK.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Anche se Microsoft e la community hanno creato open source strumenti come Il Toolkit di realtà mista [(MRTK)](/windows/mixed-reality/mrtk-unity) che configura automaticamente l'ambiente per la realtà mista, alcuni sviluppatori potrebbero voler creare le proprie esperienze da zero.

[!INCLUDE[](includes/xr/manual-setup.md)]