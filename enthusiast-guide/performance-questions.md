---
title: Domande frequenti sulle prestazioni
description: La risoluzione Windows Mixed Reality delle prestazioni va oltre la documentazione di supporto consumer standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Prestazioni
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219417"
---
# <a name="performance-faqs"></a>Domande frequenti sulle prestazioni

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>Il mio Windows Mixed Reality visore VR a 60 Hz o a 90 Hz

Se si dispone di una GPU discreta con porte HDMI 2.0 e di una CPU con quattro o più core fisici, si dovrebbe ottenere 90 Hz. Per confermare, selezionare la **Portale di dispositivi > Prestazioni.**

Nota: se la GPU ha solo un output HDMI 1.4, è possibile usare un adattatore DisplayPort per [HDMI 2.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) come soluzione alternativa.

Nota: le impostazioni di qualità visiva nel "visore VR" influiscono solo sul rendering dell Windows Mixed Reality'esperienza iniziale.

## <a name="my-pc-is-running-slowly"></a>L'esecuzione del PC è lenta

Il sistema può essere lento per molti motivi, in genere di pochi secondi. Se si verifica questo problema per lunghi periodi di tempo:

1. Chiudere tutte le applicazioni inutilizzate sul desktop.
2. Assicurarsi che il portatile sia collegato a una fonte di alimentazione.
3. Assicurarsi che il PC non si sta riscaldamento.
4. Ridurre la qualità dell'oggetto visivo nella Windows Mixed Reality home page.
5. Assicurarsi di avere i driver di [grafica più recenti](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) per il PC.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Il PC si sta riscaldamento durante l'esecuzione delle esperienze di realtà mista. Ricerca per categorie mantenere l'raffreddamento

1. Verificare che la batteria sia carica e che la fonte di alimentazione sia collegata.
2. Assicurarsi che le ventole del PC non siano bloccate.
3. Usare il PC in un ambiente relativamente interessante.
4. Assicurarsi che non siano presenti fonti di calore (ad esempio, il sole o i fori di calore) puntati al PC.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Gli oggetti visivi sono insoddettanti, si caricano lentamente o non hanno un aspetto positivo

* Assicurarsi che il visore VR sia collegato alla scheda grafica corretta nel PC. Alcuni PC hanno schede grafiche integrate e discrete. La scheda discreta offre in genere prestazioni ottimali. [Altre informazioni sull'hardware del PC.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Chiudere le applicazioni inutilizzate sul desktop.
* Assicurarsi che il visore VR si adatti perfettamente (spostarlo in basso e in alto o a sinistra e a destra per regolarlo).
* Modificare le impostazioni visive del visore VR in Impostazioni > **realtà mista > visore VR.** Quando "Qualità visiva" è impostato su "Automatico", l'esperienza di realtà mista per il PC verrà scelta automaticamente. Per altri dettagli visivi, impostare "Qualità visiva" su "Alta". Se gli oggetti visivi sono molto visivi, selezionare un'impostazione inferiore.
* Regolare la manopola di calibrazione del visore VR per assicurarsi che le lenti siano impostate sulla distanza corretta tra le tue lenti (chiamata IPD). Se non si conosce l'IPD, un optometrista può misurarlo automaticamente o usare un sito Web progettato per misurare l'IPD. Se il visore VR non ha una manopola di calibrazione, selezionare Impostazioni > realtà mista > **visore VR** e modificare il "Controllo calibrazione".
* Se si usa un adattatore USB-C o DisplayPort per HDMI, provarne uno diverso. Vedere [schede consigliate.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Disconnettere eventuali monitor aggiuntivi che potrebbero essere connessi alla scheda grafica del PC.
* Provare alcune app di realtà mista diverse da Windows Store. Alcune potrebbero funzionare meglio con la configurazione del computer.
