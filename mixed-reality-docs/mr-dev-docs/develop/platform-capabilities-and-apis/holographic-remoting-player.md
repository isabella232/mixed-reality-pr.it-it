---
title: Holographic Remoting Player
description: Informazioni su Holographic Remoting Player e sul contenuto olografico in streaming da un PC HoloLens in tempo reale tramite Wi-Fi.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, diagnostica, prestazioni
ms.openlocfilehash: 1e286612035a34c1bac174a620c350a91eb2b0fd59c3e808fe3a99368e03f43c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217147"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

[Informazioni di base su Holographic Remoting.](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>La comunicazione remota olografica HoloLens 2 è una modifica di versione principale. Le applicazioni [remote per HoloLens **(prima generazione)**](add-holographic-remoting.md) devono usare il pacchetto **NuGet versione 1.x.x** e le applicazioni remote per HoloLens 2 devono usare **2.x.x**. [](holographic-remoting-create-remote-wmr.md) Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens (prima generazione) e viceversa.

[Holographic Remoting Player è](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) un'app complementare che si connette ad app per PC e giochi che supportano Holographic Remoting. Il lettore è disponibile sia per HoloLens (prima generazione) che per HoloLens 2.  Le app per PC che supportano Holographic Remoting con HoloLens devono essere aggiornate per supportare Holographic Remoting con HoloLens 2. Per domande sulle versioni supportate, contattare il provider di app.

>[!TIP]
>A partire dalla [versione 2.2.0,](holographic-remoting-version-history.md#v2.2.0) il lettore Holographic Remoting è disponibile anche per i PC Windows che eseguono [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md).

>[!TIP]
>A partire dalla [versione 2.4.0](holographic-remoting-version-history.md#v2.4.0) è possibile creare app remote usando l'API [OpenXR.](../native/openxr.md) Per iniziare, vedere [Writing a Holographic Remoting remote app using OpenXR APIs](holographic-remoting-create-remote-openxr.md)(Scrittura di un'app remota Holographic Remoting con LE API OpenXR).

## <a name="connecting-to-the-holographic-remoting-player"></a>Connessione a Holographic Remoting Player

Seguire le istruzioni dell'app per connettersi a Holographic Remoting Player. È necessario immettere l'indirizzo IP del dispositivo HoloLens, che è possibile visualizzare nella schermata principale di Remoting Player, come indicato di seguito:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Ogni volta che viene visualizzata la schermata principale, si saprà che non è connessa un'app.

La connessione remota olografica **non è crittografata.** È consigliabile usare sempre Holographic Remoting su una connessione Wi-Fi sicura che si considera attendibile.

## <a name="quality-and-performance"></a>Qualità e prestazioni

La qualità e le prestazioni dell'esperienza variano in base a tre fattori:
* **L'esperienza olografica** in esecuzione: le app che eseguono il rendering di contenuti ad alta risoluzione o altamente dettagliati possono richiedere un PC più veloce o una connessione wireless più veloce.
* **Hardware del PC:** il PC deve essere in grado di eseguire e codificare l'esperienza olografica a 60 fotogrammi al secondo. Per una scheda grafica, è in genere consigliabile usare GeForce GTX 970 o AMD Radeon R9 290 o versione migliore. Anche in questo caso, l'esperienza specifica potrebbe richiedere una scheda di fascia alta o inferiore.
* **Connessione Wi-Fi:** l'esperienza olografica viene trasmessa tramite Wi-Fi. Usare una rete veloce con bassa congestione per ottimizzare la qualità. Anche l'uso di un PC connesso tramite un cavo Ethernet, anziché wi-fi, può migliorare la qualità.

## <a name="diagnostics"></a>Diagnostica

Per misurare la qualità della connessione, **pronunciare "abilita** la diagnostica" nella schermata principale di Holographic Remoting Player. Quando la diagnostica è abilitata, **HoloLens (prima generazione)** l'app mostrerà:

* **FPS:** numero medio di fotogrammi sottoposti a rendering che il lettore di comunicazione remota sta ricevendo ed esegue il rendering al secondo. L'ideale è 60 FPS.
* **Latenza:** la quantità media di tempo necessario per un frame per passare dal PC all'HoloLens. Più basso è il valore. Questo dipende in gran parte dalla rete Wi-Fi rete.

In **HoloLens 2** l'app mostrerà:

![Diagnostica del lettore di comunicazione remota olografica](images/holographicremotingplayer-diag.png)

* **Rendering:** numero di fotogrammi di cui viene eseguito il rendering del lettore di comunicazione remota durante l'ultimo secondo. Si noti che questo è indipendente dal numero di fotogrammi, che sono arrivati tramite la rete (vedere **Fotogrammi video**). Viene visualizzato il tempo delta di rendering medio/massimo in millisecondi nell'ultimo secondo tra i fotogrammi sottoposti a rendering.

* **Fotogrammi video:** il primo numero visualizzato viene ignorato, il secondo viene riutilizzato e il terzo viene ricevuto fotogrammi video. Tutti i numeri rappresentano il conteggio nell'ultimo secondo.
    * ```Received frames``` è il numero di fotogrammi video arrivati nell'ultimo secondo. In condizioni normali dovrebbe essere 60, ma se non è questo è un indicatore che i frame vengono eliminati a causa di problemi di rete o il lato remoto/remoto non produce fotogrammi con la frequenza prevista.
    * ```Reused frames``` è il numero di fotogrammi video usati più di una volta nell'ultimo secondo. Ad esempio, se i fotogrammi video arrivano in ritardo, il  ciclo di rendering del lettore esegue comunque il rendering di un fotogramma, ma deve riutilizzare il fotogramma video già usato per il fotogramma precedente.
    * ```Skipped frames``` è il numero di fotogrammi video che non sono stati usati dal ciclo di rendering del lettore. Ad esempio, il jitter di rete può avere l'effetto che i fotogrammi video in arrivo non siano più distribuiti in modo uniforme. Ad esempio, se alcuni sono in ritardo e altri arrivano in tempo con il risultato che non hanno più un delta di 16,66 millisecondi quando vengono eseguiti su 60 Hz. Può verificarsi che più di un fotogramma arrivi tra due tick del ciclo di rendering del lettore. In questo caso, il lettore *ignora* uno o più fotogrammi perché dovrebbe visualizzare sempre il fotogramma video ricevuto più recente.

    >[!NOTE]
    >Quando si verifica un instabilità di rete, i fotogrammi ignorati e riutilizzati sono in genere uguali. Al contrario, se vengono visualizzati solo i fotogrammi ignorati, si tratta di un indicatore che indica che il lettore non ha raggiunto la frequenza dei fotogrammi di destinazione. In questo caso, è consigliabile tenere sotto controllo il tempo massimo di delta di rendering durante la diagnosi dei problemi.

* **Delta dei fotogrammi video:** differenziale minimo/massimo tra i fotogrammi video ricevuti nell'ultimo secondo. Questo numero in genere è correlato ai fotogrammi ignorati/riutilizzati in caso di problemi causati da jitter di rete.
* **Latenza:** il turnaround medio in millisecondi nell'ultimo secondo. Turnaround in questo contesto indica il tempo necessario per inviare i dati di pose/sensore dal HoloLens al lato remoto/remoto fino a visualizzare il fotogramma video per i dati di pose/telemetria sul HoloLens schermo.
* **Fotogrammi video eliminati:** numero di fotogrammi video eliminati nell'ultimo secondo e da quando è stata stabilita una connessione. La causa principale per i fotogrammi video eliminati è quando un fotogramma video non arriva nell'ordine e per questo motivo deve essere eliminato perché ne esiste già uno più recente. Questo è simile ai *frame eliminati,* ma la causa è a un livello inferiore nello stack di comunicazione remota. I fotogrammi video eliminati sono previsti solo in condizioni di rete non ottimali.

Nella schermata principale è possibile pronunciare **"disabilita la diagnostica"** per disattivare la diagnostica.

## <a name="pc-system-requirements"></a>Requisiti di sistema per PC
* Il PC **deve** eseguire l'aggiornamento Windows 10'anniversario o versione più recente.
* È consigliabile usare una scheda grafica GeForce GTX 970 o AMD Radeon R9 290 o versione migliore.
* È consigliabile connettere il PC alla rete tramite ethernet per ridurre il numero di hop wireless.

## <a name="see-also"></a>Vedere anche
* [HoloLens (prima generazione): aggiungere Holographic Remoting](add-holographic-remoting.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)