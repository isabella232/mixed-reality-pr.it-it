---
title: Domande frequenti sulle prestazioni
description: Risoluzione avanzata dei problemi di Windows Mixed Reality che va oltre la documentazione standard del supporto clienti.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, prestazioni
appliesto:
- Windows 10
ms.openlocfilehash: 2150d605ecf29bb0bcf88f0f76a0193046f74ed5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685813"
---
# <a name="performance-faqs"></a>Domande frequenti sulle prestazioni

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a>Il rendering delle cuffie con la realtà mista di Windows viene eseguito a 60Hz o 90Hz framerate?

Se si dispone di una GPU discreta con porte HDMI 2,0 e una CPU con quattro o più core fisici, si dovrebbe ottenere 90 Hz. Per confermare, controllare il **portale del dispositivo > scheda prestazioni** . 

Nota: se la GPU dispone solo di un output HDMI 1,4, è possibile usare un adattatore DisplayPort per [hdmi 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) come soluzione alternativa. 

Nota: le impostazioni della qualità visiva in "auricolare display" influiscono solo sul rendering dell'esperienza della Home realtà mista di Windows.

## <a name="my-pc-is-running-slowly"></a>Il PC funziona lentamente.

Il sistema può essere lento per diversi motivi e, nella maggior parte dei casi, questo solo pochi secondi. Se si verifica questo problema in lunghi periodi di tempo:
1. Chiudere l'applicazione inutilizzata sul desktop.
2. Verificare che il computer portatile sia collegato a una fonte di alimentazione.
3. Verificare che il PC non stia scaldando.
4. Abbassare la qualità visiva nella Home realtà mista di Windows.
5. Assicurarsi di disporre dei [driver grafici](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) più recenti per il PC.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Il mio PC si sta scaldando durante l'esecuzione delle esperienze di realtà miste. Ricerca per categorie mantenerlo interessante?

1. Verificare che la batteria sia addebitata e che la fonte di alimentazione sia collegata.
2. Verificare che le ventole del PC non siano bloccate.
3. Usare il PC in un ambiente relativamente sporadico.
4. Verificare che non siano presenti fonti di calore, ad esempio il sole o i sfiati di calore, a cui punta il PC.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Gli oggetti visivi sono irregolari, vengono caricati lentamente o non sembrano corretti.
* Assicurarsi che l'auricolare sia collegato alla scheda grafica corretta nel PC. Alcuni PC hanno schede grafiche sia integrate che discrete. La scheda discreta offre in genere le prestazioni migliori. [Altre informazioni sull'hardware del PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Chiudere le applicazioni inutilizzate sul desktop.
* Verificare che le cuffie si trovino comodamente (spostarle in basso e in alto o a sinistra e a destra per adattarle).
* Modificare le impostazioni visive dell'auricolare in **impostazioni > realtà mista > visualizzazione dell'auricolare** . Quando la "qualità visiva" è impostata su "automatico", l'esperienza di realtà mista per il PC verrà scelta automaticamente. Per altri dettagli visivi, impostare "qualità visiva" su "alta". Se gli oggetti visivi sono increspati, selezionare un'impostazione inferiore.
* Modificare la manopola di calibrazione dell'auricolare per assicurarsi che le lenti siano impostate sulla distanza corretta tra gli alunni (denominato dpi). Se non si conosce il valore di dpi, un optometrista dovrebbe essere in grado di misurarlo o usare un sito web progettato per misurare i dpi. Se la cuffia non ha una manopola di calibrazione, selezionare **impostazioni > realtà mista > visualizzare l'auricolare** e modificare il "controllo di calibrazione".
* Se si usa un adattatore USB-C o DisplayPort per HDMI, provare con un altro. Vedere [Adapter consigliati.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Disconnettere tutti i monitoraggi aggiuntivi che possono essere connessi alla scheda grafica del computer.
* Provare alcune app di realtà miste diverse da Windows Store, altre possono funzionare meglio con la configurazione del computer.
