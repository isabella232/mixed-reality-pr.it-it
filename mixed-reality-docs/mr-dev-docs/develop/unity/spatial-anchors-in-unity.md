---
title: Blocco del mondo e ancoraggi nello spaziale in Unity
description: Informazioni su come usare gli strumenti di blocco del mondo e gli ancoraggi nello spaziale nelle applicazioni di realtà mista Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, ancoraggi nello spazio, archivio di ancoraggi, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, strumenti di blocco del mondo, ologrammi
ms.openlocfilehash: 34ef74ab968bff04188b1010eb4c863fd73d76ee6b1dd8a0bd89c7d4232a2be9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208848"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Blocco del mondo e ancoraggi nello spaziale in Unity

![Immagine hero degli strumenti di blocco del mondo](images/wlt-img-01.jpeg)

La creazione di applicazioni di realtà mista è fondamentale perché gli ologrammi rimangano sul posto, si spostino con l'utente o in alcuni casi si posizionino in relazione ad altri ologrammi. Questo articolo illustra la soluzione consigliata usando world locking tools, ma verrà illustrata anche la configurazione manuale degli ancoraggi nello spazio nei progetti Unity. Prima di passare a qualsiasi codice, è importante comprendere in che modo Unity gestisce lo spazio delle coordinate e gli ancoraggi nel proprio motore.

## <a name="world-scale-coordinate-systems"></a>Sistemi di coordinate su scala globale

Attualmente, quando si scrivono giochi, app per la visualizzazione dei dati o app di realtà virtuale, l'approccio tipico consiste nel definire un sistema di **coordinate** globale assoluto a cui tutte le altre coordinate possono eseguire il mapping in modo affidabile. In tale ambiente è sempre possibile trovare una trasformazione stabile che definisce una relazione tra due oggetti qualsiasi in tale mondo. Se questi oggetti non sono stati spostati, le relative trasformazioni rimarranno sempre invariate. Questo tipo di sistema di coordinate globale è facile da ottenere quando si esegue il rendering di un mondo puramente virtuale in cui si conosce in anticipo tutta la geometria. Le app per la realtà virtuale a livello di stanza oggi stabiliscono in genere questo tipo di sistema di coordinate assoluto a livello di stanza con l'origine sul piano.

Al contrario, un dispositivo di realtà mista senzatethering, ad esempio HoloLens, ha una comprensione dinamica basata sui sensori del mondo, adattando continuamente le proprie conoscenze nel corso del tempo all'ambiente circostante dell'utente mentre attraversa molti metri su un intero piano di un edificio. In un'esperienza su scala globale, se tutti gli ologrammi sono stati posizionati in un sistema di coordinate rigidi naive, questi ologrammi finirebbero per deviare nel tempo, in base al mondo o l'uno rispetto all'altro.

Ad esempio, il visore VR potrebbe attualmente ritiene che due posizioni nel mondo siano distanti 4 metri e quindi perfezionare tale comprensione, apprendendo che le posizioni sono di fatto a 3,9 metri di distanza. Se questi ologrammi si trovavano inizialmente a 4 metri di distanza in un unico sistema di coordinate rigido, uno di essi apparirebbe sempre a 0,1 metri di distanza dal mondo reale.

È possibile posizionare manualmente gli ancoraggi nello spazio **in** Unity per mantenere la posizione di un ologramma nel mondo fisico quando l'utente è mobile, ma ciò non consente l'auto-coerenza all'interno del mondo virtuale. Ancoraggi diversi si spostano costantemente l'uno rispetto all'altro e si spostano anche nello spazio delle coordinate globale. In questo scenario, attività semplici come il layout diventano difficili e la simulazione fisica risulta problematica.

**World Locking Tools** consente di ottenere il meglio di entrambi i ambienti, stabilendo un singolo sistema di coordinate rigido usando una fornitura interna di ancoraggi nello spazio distribuiti in tutta la scena virtuale mentre l'utente si sposta. Gli strumenti analizzano le coordinate della fotocamera e gli ancoraggi nello stato di ogni fotogramma. Invece di modificare le coordinate di tutti gli elementi del mondo per compensare le correzioni nelle coordinate della testa dell'utente, gli strumenti consentono invece di correggere le coordinate della testa.

## <a name="choosing-your-world-locking-approach"></a>Scelta dell'approccio di blocco globale

* **È consigliabile** usare **world locking tools per tutte** le esigenze di posizionamento degli ologrammi. 
    * World Locking Tools offre un sistema di coordinate stabile che riduce al minimo le incoerenze visibili tra marcatori virtuali e reali. In altre parole, blocca l'intera scena con un pool condiviso di ancoraggi, anziché bloccare ogni gruppo di oggetti con il singolo ancoraggio del gruppo.
* **Per Unity 2019/2020 con OpenXR o il plug-in Windows XR,** è necessario usare **ARAnchorManager**
* Per le versioni precedenti di Unity o **i progetti WSA,** è necessario usare **WorldAnchor**

## <a name="setting-up-world-locking"></a>Configurazione del blocco del mondo 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Blocco permanente del mondo

Gli ancoraggi nello spazio salvano gli ologrammi nello spazio reale tra le sessioni dell'applicazione. Dopo essere stati salvati nell'HoloLens di ancoraggio, possono essere trovati e caricati in sessioni diverse e sono un fallback ideale quando non è disponibile connettività Internet.

> [!IMPORTANT]
> Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud. Se si vuole usare i servizi cloud di Azure per archiviare gli ancoraggi, è disponibile un documento che fornisce informazioni dettagliate sull'integrazione di [Ancoraggi nello spazio di Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors). Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Condivisione degli spazi delle coordinate 

Se si vuole condividere uno spazio di coordinate globale bloccato, vedere la documentazione completa [dell'esperienza condivisa.](shared-experiences-in-unity.md)

Si noti che Ancoraggi nello spazio di Azure non è ancora supportato direttamente in World Locking Tools, quindi le esperienze condivise richiedono la creazione manuale di ancoraggi nello spazio.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se stai seguendo il percorso di checkpoint per lo sviluppo unity che abbiamo stabilito, stai esplorando i blocchi predefiniti principali della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Mapping spaziale](spatial-mapping-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Introduzione agli strumenti di blocco del mondo](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [Guide di avvio rapido](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [Esercitazioni](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [Esempi](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [Persistenza dell'ancoraggio nello spaziale](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
* [Scale dell'esperienza](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Perdita del rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
