---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443708"
---
# <a name="425"></a>[4.25](#tab/425)

Non sono previsti passaggi di abilitazione aggiuntivi specifici per UE 4.25.

# <a name="426"></a>[4.26](#tab/426)

Se si usa UE 4.26, è consigliabile adottare la configurazione di progetto seguente per aggiungere un piccolo ritardo, perché il rilevamento del codice a matrice deve essere inizializzato DOPO l'avvio di una sessione AR:

![Progetto della funzione Toggle ARCapture con ritardo](../images/qr-codes-img-01.png)
