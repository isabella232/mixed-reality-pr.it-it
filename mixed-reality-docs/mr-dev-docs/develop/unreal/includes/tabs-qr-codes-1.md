---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443708"
---
# <a name="425"></a>[<span data-ttu-id="a8105-101">4.25</span><span class="sxs-lookup"><span data-stu-id="a8105-101">4.25</span></span>](#tab/425)

<span data-ttu-id="a8105-102">Non sono previsti passaggi di abilitazione aggiuntivi specifici per UE 4.25.</span><span class="sxs-lookup"><span data-stu-id="a8105-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="a8105-103">4.26</span><span class="sxs-lookup"><span data-stu-id="a8105-103">4.26</span></span>](#tab/426)

<span data-ttu-id="a8105-104">Se si usa UE 4.26, è consigliabile adottare la configurazione di progetto seguente per aggiungere un piccolo ritardo, perché il rilevamento del codice a matrice deve essere inizializzato DOPO l'avvio di una sessione AR:</span><span class="sxs-lookup"><span data-stu-id="a8105-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![Progetto della funzione Toggle ARCapture con ritardo](../images/qr-codes-img-01.png)
