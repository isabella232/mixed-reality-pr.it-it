---
title: Uso di WebVR con la realtà mista di Windows
description: Descrive WebVR e come usarlo con Microsoft Edge negli auricolari per la realtà mista di Windows.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, WebVR, Edge, Microsoft Edge, esplorazione Web
ms.openlocfilehash: 92f1d00c7f635c88a727732fb743996a654ba775
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725602"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Uso di WebVR con la realtà mista di Windows

>[!IMPORTANT]
>La maggior parte dei Web browser moderni ha deprecato il supporto di WebVR a favore di WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR. Installare [il nuovo Microsoft Edge per il](using-microsoft-edge.md) supporto di WebXR.

## <a name="what-is-webvr"></a>Informazioni su WebVR

[WebVR](https://webvr.info) è una specifica aperta che consente di sperimentare direttamente VR da un browser. Se un sito Web implementa il supporto WebVR e fornisce contenuto 3D, può visualizzare contenuti immersivi nell'auricolare, con il consenso dell'utente.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Qual è la differenza tra WebVR e l'esplorazione del Web in VR

WebVR è una tecnologia che consente a un autore di siti Web di aggiungere funzionalità VR a una pagina. L'API WebVR viene usata da una pagina per visualizzare il contenuto 3D, ad esempio un video di 360 gradi o un modello 3D o un gioco 3D, per l'intera cuffia. **Esempio:** Visualizzazione di un video 360 in [CNN.com/VR](http://cnn.com/vr). Se una pagina supporta WebVR, verrà aggiunto un pulsante o un altro elemento dell'interfaccia utente che è possibile selezionare per immettere VR.

Esplorare il Web in VR significa usare il browser Microsoft Edge mentre si sta indossando la cuffia come una lavagna di app 2D all'interno della Cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Tutti i siti Web supportano WebVR

No. Gli autori di siti Web devono acconsentire esplicitamente all'uso di WebVR e possono creare siti ottimizzati per browser, cuffie e controller specifici. Alcuni contenuti di WebVR sono ottimizzati solo per i dispositivi mobili VR. Tenere inoltre presente che i siti Web devono creare e fornire in modo esplicito il contenuto di WebVR. Il numero di siti con contenuto compatibile con WebVR sta crescendo ogni giorno.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Posso usare le mie vive/Oculus e così via per visualizzare il contenuto di WebVR in Microsoft Edge

No. Un headset di realtà mista di Windows è necessario per usare WebVR in Edge. Tuttavia, è possibile accedere al contenuto di WebVR in un altro browser. vedere l'elenco completo dei dispositivi e dei browser compatibili all'indirizzo: [WebVR. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Dove è possibile trovare la documentazione per gli sviluppatori di WebVR

La documentazione per gli sviluppatori è disponibile qui: [documentazione per sviluppatori WebVR](https://docs.microsoft.com/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Ho trovato un sito Web con WebVR che non funziona in realtà mista di Windows. Cosa devo fare

È possibile segnalare i siti interrotti direttamente al team del browser Microsoft Edge in [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o tramite twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

È anche possibile registrare i bug usando l'app hub di feedback di Windows nella categoria:

Microsoft Edge: problemi del sito Web >

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Che cosa è una pagina efficace per verificare se WebVR funziona

Vedere gli [esempi di webvr.info](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Ricerca per categorie configurare WebVR

Per sperimentare il contenuto di WebVR in un auricolare di realtà mista di Windows (usando hardware o simulazione), è necessario:

1. Verificare che l'auricolare sia connesso.
2. Avviare Microsoft Edge sul desktop o in una realtà mista.
3. Passare a una pagina abilitata per WebVR.
4. Selezionare il pulsante ENTER VR nella pagina (la posizione e la rappresentazione visiva di questo pulsante possono variare per sito Web). Potrebbe essere simile a: \
   ![Immagine di occhiali VR](images/75px-enter-vr.png)
5. La prima volta che si tenta di immettere VR in un dominio specifico, il browser richiederà il consenso per l'uso di visualizzazione immersiva, selezionare Sì: ![Interfaccia utente di consenso visualizzata al primo tentativo di immissione di VR in un particolare dominio](images/1053px-Webvr-consent-ui.png)
6. L'auricolare dovrebbe iniziare a visualizzare il contenuto di WebVR.

## <a name="see-also"></a>Vedi anche

* [Risoluzione dei problemi > WebVR](webvr-questions.md)
* [Come accedere alla prima esperienza WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Uso di giochi e app in realtà mista di Windows](using-games-and-apps-in-windows-mixed-reality.md)
* [Home realtà mista](your-mixed-reality-home.md)
* [Sistema di rilevamento](tracking-system.md)
* [Controller di movimento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Commenti sulla presentazione](filing-feedback.md)
