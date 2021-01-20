---
title: Holographic Remoting Player
description: Informazioni sul lettore di comunicazione remota olografica e sulla trasmissione di contenuto olografico da un PC alla HoloLens in tempo reale tramite Wi-Fi.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale, diagnostica, prestazioni
ms.openlocfilehash: 7a7c7762f079dcc4ec05bacec8bd7ab0d3625e0e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583162"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

>[!IMPORTANT]
>La comunicazione remota olografica per HoloLens 2 è una modifica di versione principale. [Le applicazioni remote per **HoloLens (1st Gen)**](add-holographic-remoting.md) devono usare il pacchetto NuGet versione **1. x.** x e [le applicazioni remote per **HoloLens 2**](holographic-remoting-create-remote-wmr.md) devono usare **2. x. x**. Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens (1a generazione) e viceversa.

Il [lettore di comunicazione remota olografico](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) è un'app complementare che si connette a app e giochi per PC che supportano la comunicazione remota olografica. La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.

Il lettore di servizi remoti olografici può essere usato solo con le app PC progettate per supportare la comunicazione remota olografica.

Il lettore di comunicazione remota olografico è disponibile sia per HoloLens (First Gen) che per HoloLens 2.  È necessario aggiornare le app PC che supportano la comunicazione remota olografica con HoloLens per supportare la comunicazione remota olografica con HoloLens 2. Per domande sulle versioni supportate, contattare il provider di app.

>[!TIP]
>A partire dalla versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) , il lettore di comunicazione remota olografico è disponibile anche per i PC Windows che eseguono la [realtà mista Windows](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>A partire dalla versione [2.4.0](holographic-remoting-version-history.md#v2.4.0) è possibile creare app Remote con l' [API OpenXR](../native/openxr.md) . Per iniziare, vedere [scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR](holographic-remoting-create-remote-openxr.md).

## <a name="connecting-to-the-holographic-remoting-player"></a>Connessione al lettore di comunicazione remota olografica

Seguire le istruzioni dell'app per connettersi al lettore di comunicazione remota olografica. È necessario immettere l'indirizzo IP del dispositivo HoloLens, che è possibile visualizzare nella schermata principale del lettore remoto, come indicato di seguito:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Quando viene visualizzata la schermata principale, si saprà che non è stata connessa un'app.

La connessione remota olografica **non è crittografata**. È consigliabile usare sempre la comunicazione remota olografica su una connessione Wi-Fi protetta attendibile.

## <a name="quality-and-performance"></a>Qualità e prestazioni

La qualità e le prestazioni dell'esperienza variano in base a tre fattori:
* **L'esperienza olografica che si sta eseguendo: le** app che eseguono il rendering di contenuto ad alta risoluzione o molto dettagliato possono richiedere un PC più veloce o una connessione wireless più veloce.
* **Hardware del PC** : il PC deve essere in grado di eseguire e codificare l'esperienza olografica a 60 fotogrammi al secondo. Per una scheda grafica, è in genere consigliabile usare GeForce GTX 970 o AMD Radeon R9 290 o una soluzione migliore. Anche in questo caso, la tua esperienza specifica potrebbe richiedere una scheda di fascia superiore o inferiore.
* **La connessione Wi-Fi** : l'esperienza olografica viene trasmessa tramite Wi-Fi. Usa una rete veloce con congestione ridotta per massimizzare la qualità. L'uso di un PC connesso tramite un cavo Ethernet, anziché di un Wi-Fi, può migliorare anche la qualità.

## <a name="diagnostics"></a>Diagnostica

Per misurare la qualità della connessione, pronunciare **"Abilita diagnostica"** mentre è presente nella schermata principale del lettore di comunicazione remota olografica. Quando la diagnostica è abilitata, in **HoloLens (prima generazione)** l'app visualizzerà:

* **Fps** : numero medio di frame di cui è stato eseguito il rendering il lettore remoto riceve e il rendering al secondo. La soluzione ideale è 60 FPS.
* **Latenza** : la quantità media di tempo necessaria per il passaggio di un frame dal PC alla HoloLens. Più basso è il migliore. Questo dipende in gran parte dalla rete Wi-Fi.

In **HoloLens 2** l'app visualizzerà:

![Diagnostica del lettore di comunicazione remota olografica](images/holographicremotingplayer-diag.png)

* **Render** : numero di frame di cui il lettore remoto ha eseguito il rendering durante l'ultimo secondo. Si noti che questo è indipendente dal numero di frame, che è arrivato tramite la rete (vedere i **fotogrammi video**). Viene visualizzato il tempo delta di rendering medio/massimo in millisecondi nell'ultimo secondo tra i frame sottoposti a rendering.

* **Fotogrammi video** : il primo numero visualizzato è quello dei fotogrammi video ignorati, il secondo viene riusato per i fotogrammi video e la terza riceve i fotogrammi video. Tutti i numeri rappresentano il conteggio nell'ultimo secondo.
    * ```Received frames``` numero di fotogrammi video, che è arrivato nell'ultimo secondo. In condizioni normali, deve essere 60, ma se non si tratta di un indicatore, i frame vengono eliminati a causa di problemi di rete o il lato remoto/remoto non produce frame con la frequenza prevista.
    * ```Reused frames``` numero di fotogrammi video utilizzati più di una volta nell'ultimo secondo. Ad esempio, se i fotogrammi video arrivano in ritardo, il ciclo di rendering del lettore esegue comunque il rendering di un frame, ma deve *riutilizzare* il fotogramma video già usato per il frame precedente.
    * ```Skipped frames``` numero di fotogrammi video che non sono stati utilizzati dal ciclo di rendering del lettore. Ad esempio, l'instabilità della rete può avere l'effetto che i fotogrammi video in arrivo non sono più distribuiti in modo uniforme. Ad esempio, se alcune sono in ritardo e altre arrivano nel tempo con il risultato che non hanno più un Delta di 16,66 millisecondi quando vengono eseguite su 60 Hz. Può verificarsi che più di un frame arrivi tra due cicli del ciclo di rendering del lettore. In questo caso, il giocatore *Ignora* uno o più frame perché dovrebbe visualizzare sempre il frame video ricevuto più di recente.

    >[!NOTE]
    >Quando viene rilevata un'instabilità della rete, i frame ignorati e riutilizzati sono in genere uguali. Al contrario, se vengono visualizzati solo i frame ignorati, questo indica che il lettore non raggiunge la frequenza dei fotogrammi di destinazione. In questo caso, è necessario tenere sotto controllo il tempo delta massimo di rendering durante la diagnosi dei problemi.

* **Delta dei frame video** : Delta minimo/massimo tra i fotogrammi video ricevuti nell'ultimo secondo. Questo numero è in genere correlato ai frame ignorati/riutilizzati in caso di problemi causati da jitter di rete.
* **Latenza** : il turnaround medio in millisecondi nell'ultimo secondo. Il turnaround in questo contesto indica il tempo necessario per inviare i dati di post/sensore dal HoloLens al lato remoto o remoto fino a visualizzare il frame video per i dati di post/telemetria nella visualizzazione HoloLens.
* **Fotogrammi video scartati** : il numero di fotogrammi video scartati nell'ultimo secondo e dopo che è stata stabilita una connessione. La causa principale per i fotogrammi video scartati è quando un frame video non arriva nell'ordine e per questo motivo deve essere ignorato perché ne esiste già uno più recente. Questa operazione è simile ai *frame eliminati* , ma la relativa origine è a un livello inferiore nello stack di comunicazione remota. I fotogrammi video scartati sono previsti solo in condizioni di rete errate.

Nella schermata principale è possibile **disabilitare** la diagnostica per disattivare la diagnostica.

## <a name="pc-system-requirements"></a>Requisiti di sistema del PC
* Il PC **deve** eseguire l'aggiornamento dell'anniversario di Windows 10 o versione successiva.
* Si consiglia di usare una scheda grafica GeForce GTX 970 o AMD Radeon R9 290 o superiore.
* Si consiglia di connettere il PC alla rete tramite Ethernet per ridurre il numero di hop wireless.

## <a name="see-also"></a>Vedere anche
* [HoloLens (First Gen): aggiungere la comunicazione remota olografica](add-holographic-remoting.md)
* [Scrittura di un'app remota olografica remota usando le API di realtà mista di Windows](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR](holographic-remoting-create-remote-openxr.md)
* [Condizioni di licenza software per Holographic Remoting](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)