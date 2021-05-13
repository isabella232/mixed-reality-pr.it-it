---
title: UnityArCameraSettings
description: Documentazione per l'uso della fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera AR,
ms.openlocfilehash: 15aacae4cb543a3a94660ef1ab057ad0febcb715
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850417"
---
# <a name="unity-ar-camera-settings-provider"></a>Provider di impostazioni della fotocamera AR unity

Il provider di impostazioni della fotocamera AR unity è un componente sperimentale di MRTK che consente l'esecuzione di applicazioni di realtà mista in dispositivi Android e iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Opzioni del provider di impostazioni della fotocamera AR unity

![Configurazione delle impostazioni della fotocamera AR unity](../images/camera-system/UnityArSettingsConfiguration.png)

Per una guida su come aggiungere il provider alla scena: [Come configurare MRTK per iOS e Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Impostazioni di rilevamento

Il provider di impostazioni della fotocamera AR unity consente le opzioni di configurazione per la modalità di esecuzione del rilevamento. Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera AR unity.

**Origine della posizione**

L'origine della posizione definisce i tipi disponibili di posizioni di rilevamento della realtà aumentata. In generale, questi valori eseguono il mapping a un componente del dispositivo in cui è in esecuzione l'applicazione.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Center | L'occhio centrale di un dispositivo montato con la testa. |
| Fotocamera a colori | Fotocamera a colori di un dispositivo mobile. |
| Head | La testa di un dispositivo montato con la testa, spesso leggermente sopra l'occhio centrale. |
| Occhio sinistro | L'occhio sinistro di un dispositivo montato sulla testa. |
| Pose a sinistra | Posizione del controller a sinistra. |
| Occhio destro | L'occhio destro di un dispositivo montato sulla testa. |
| Posizione a destra | La posizione del controller destro. |

Il valore predefinito per l'origine della posizione è **Fotocamera** a colori , per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.

**Tipo di rilevamento**

Il tipo di rilevamento definisce le parti della posizione che verranno usate per il rilevamento.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Posizione | Posizione del dispositivo. |
| Rotazione | Rotazione del dispositivo. |
| Rotazione e posizione | Posizione e rotazione del dispositivo. |

Il valore predefinito per tipo di rilevamento è **Rotazione e posizione**, per abilitare l'esperienza di rilevamento più completa.

**Tipo di aggiornamento**

Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei frame, verranno campionati i dati di posizione.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Prima del rendering | Subito prima del rendering. |
| Aggiornamento | Durante la fase di aggiornamento del frame. |
| Aggiornamento e prima del rendering | Durante la fase di aggiornamento e subito prima del rendering. |

Il valore predefinito per il tipo di rilevamento è **Aggiorna e prima del rendering** per abilitare la latenza di rilevamento più bassa.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamera](camera-system-overview.md)
- [Creazione di un provider di impostazioni della fotocamera](create-settings-provider.md)
