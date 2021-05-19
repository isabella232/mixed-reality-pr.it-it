---
title: Impostazioni della fotocamera unity AR
description: Documentazione per l'uso della fotocamera AR in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera AR,
ms.openlocfilehash: baa54f4a7c6238b136a108cf5adcbddd29c3ee1b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143467"
---
# <a name="unity-ar-camera-settings-provider"></a>Provider di impostazioni della fotocamera Unity AR

Il provider di impostazioni della fotocamera Unity AR è un componente MRTK sperimentale che consente l'esecuzione di applicazioni di realtà mista nei dispositivi Android e iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Opzioni del provider di impostazioni della fotocamera Unity AR

![Configurazione delle impostazioni della fotocamera Unity AR](../images/camera-system/UnityArSettingsConfiguration.png)

Per una guida su come aggiungere il provider alla scena: [Come configurare MRTK per iOS e Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Impostazioni di rilevamento

Il provider di impostazioni della fotocamera Unity AR consente le opzioni di configurazione per l'esecuzione del rilevamento. Queste impostazioni sono specifiche dell'implementazione del provider di impostazioni della fotocamera Unity AR.

**Origine della posizione**

L'origine della posizione definisce i tipi disponibili di pose di rilevamento della realtà aumentata. In generale, questi valori vengono mappati a un componente del dispositivo in cui è in esecuzione l'applicazione.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Center | L'occhio centrale di un dispositivo montato sulla testa. |
| Fotocamera a colori | Fotocamera a colori di un dispositivo mobile. |
| Head | L'occhio della testa di un dispositivo montato sulla testa, spesso leggermente sopra l'occhio centrale. |
| Occhio sinistro | L'occhio sinistro di un dispositivo montato con la testa. |
| Posizione sinistra | Posizione del controller a sinistra. |
| Occhio destro | L'occhio destro di un dispositivo montato con la testa. |
| Posizione destra | Posizione del controller della mano destra. |

Il valore predefinito per l'origine della posizione è **Fotocamera** a colori, per abilitare una visualizzazione trasparente nei dispositivi mobili, ad esempio un telefono o un tablet.

**Tipo di rilevamento**

Il tipo di rilevamento definisce le parti della posizione che verranno usate per il rilevamento.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Posizione | Posizione del dispositivo. |
| Rotazione | Rotazione del dispositivo. |
| Rotazione e posizione | Posizione e rotazione del dispositivo. |

Il valore predefinito per il tipo di rilevamento è **Rotazione e Posizione** per abilitare l'esperienza di rilevamento più completa.

**Tipo di aggiornamento**

Il tipo di aggiornamento definisce in quali punti, durante l'elaborazione dei fotogrammi, verranno campionati i dati di posizione.

Le opzioni disponibili sono descritte nella tabella seguente.

| Opzione | Descrizione |
| --- | --- |
| Prima del rendering | Subito prima del rendering. |
| Aggiornamento | Durante la fase di aggiornamento del frame. |
| Aggiornamento e prima del rendering | Durante la fase di aggiornamento e subito prima del rendering. |

Il valore predefinito per tipo di rilevamento è **Update And Before Render**, per abilitare la latenza di rilevamento più bassa.

## <a name="see-also"></a>Vedi anche

- [Panoramica del sistema di fotocamera](camera-system-overview.md)
- [Creazione di un provider di impostazioni della fotocamera](create-settings-provider.md)
