---
title: UnityArCameraSettings
description: Documentazione per usare la fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, videocamera AR,
ms.openlocfilehash: 5ac4514d3f42e7f4cb67817e022a1ad07d291774
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683864"
---
# <a name="unity-ar-camera-settings-provider"></a>Provider di impostazioni della fotocamera AR Unity

Il provider di impostazioni della fotocamera AR Unity è un componente sperimentale MRTK che consente l'esecuzione di applicazioni di realtà miste in dispositivi Android e iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Opzioni del provider di impostazioni della fotocamera AR Unity

![Configurazione delle impostazioni della fotocamera AR Unity](../images/camera-system/UnityArSettingsConfiguration.png)

Per una guida su come aggiungere il provider alla scena: [come configurare MRTK per iOS e Android](../cross-platform/UsingARFoundation.md)

### <a name="tracking-settings"></a>Impostazioni di rilevamento

Il provider di impostazioni della fotocamera AR Unity consente le opzioni di configurazione per la modalità di esecuzione del rilevamento. Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera AR di Unity.

**Genera origine**

L'origine della definizione definisce i tipi disponibili di pose di rilevamento di realtà aumentata. In generale, questi valori vengono mappati a un componente del dispositivo in cui è in esecuzione l'applicazione.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Center | Occhio centrale di un dispositivo montato a capo. |
| Fotocamera a colori | Fotocamera a colori di un dispositivo mobile. |
| Head | Occhio a capo di un dispositivo montato in testa, spesso leggermente al di sopra dell'occhio centrale. |
| Occhio sinistro | L'occhio sinistro di un dispositivo montato in testa. |
| Pose a sinistra | Il controller della mano sinistra. |
| Occhio a destra | Occhio destro di un dispositivo montato in testa. |
| Pose a destra | Il controller della mano destra. |

Il valore predefinito per l'origine della posa è la **fotocamera a colori**, per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.

**Tipo di rilevamento**

Il tipo di rilevamento definisce le porzioni della funzione che verranno utilizzate per il rilevamento.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Posizione | Posizione del dispositivo. |
| Rotazione | Rotazione del dispositivo. |
| Rotazione e posizione | Posizione e rotazione del dispositivo. |

Il valore predefinito per il tipo di rilevamento è **rotazione e posizione**, per abilitare l'esperienza di rilevamento più avanzata.

**Tipo di aggiornamento**

Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei frame, verranno campionati i dati di post.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Prima del rendering | Appena prima del rendering. |
| Aggiornamento | Durante la fase di aggiornamento del frame. |
| Aggiornare e prima del rendering | Durante la fase di aggiornamento e immediatamente prima del rendering. |

Il valore predefinito per il tipo di rilevamento è **Update e before render** per abilitare la latenza di rilevamento più bassa.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamere](CameraSystemOverview.md)
- [Creazione di un provider di impostazioni della fotocamera](CreateSettingsProvider.md)
