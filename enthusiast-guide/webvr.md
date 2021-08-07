---
title: Uso di WebVR con Windows Mixed Reality
description: Informazioni di base su WebVR, su come usarlo con Microsoft Edge su Windows Mixed Reality visori VR e sui problemi comuni di risoluzione dei problemi.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, WebVR, Edge, Microsoft Edge, esplorazione Web
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214125"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Uso di WebVR con Windows Mixed Reality

>[!IMPORTANT]
>La maggior parte dei Web browser moderni ha deprecato il supporto di WebVR a favore di WebXR, il nuovo standard per la creazione di esperienze Web immersive per visori VR. Installare il [nuovo Microsoft Edge](using-microsoft-edge.md) per il supporto WebXR.

## <a name="what-is-webvr"></a>Informazioni su WebVR

[WebVR](https://webvr.info) è una specifica aperta che consente di sperimentare la realtà virtuale direttamente da un browser. Se un sito Web implementa il supporto WebVR e fornisce contenuto 3D, può visualizzare contenuto immersive nel visore VR, con il consenso dell'utente.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Qual è la differenza tra WebVR e l'esplorazione del Web nella realtà virtuale?

WebVR è una tecnologia che consente a un autore di siti Web di aggiungere funzionalità di realtà virtuale a una pagina. L'API WebVR viene usata da una pagina per visualizzare il contenuto 3D (ad esempio video a 360 gradi, un modello 3D o un gioco 3D) per l'intero visore VR. **Esempio:** Visualizzazione di un video 360 [cnn.com/vr](http://cnn.com/vr). Se una pagina supporta WebVR, aggiungerà un pulsante o un altro elemento dell'interfaccia utente che è possibile selezionare per accedere alla realtà virtuale.

Esplorare il Web nella realtà virtuale significa usare il browser Edge mentre si usa il visore VR, come slate di app 2D all'interno diHouse.

## <a name="do-all-websites-support-webvr"></a>Tutti i siti Web supportano WebVR

No. Gli autori di siti Web devono acconsentire esplicitamente all'uso di WebVR e possono creare siti ottimizzati per browser, visori VR e controller specifici. Alcuni contenuti WebVR sono ottimizzati solo per i dispositivi VR per dispositivi mobili. Tenere inoltre presente che i siti Web devono creare e fornire contenuto WebVR in modo esplicito. Il numero di siti con contenuto compatibile con WebVR aumenta ogni giorno.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>È possibile usare Vive/Oculus e così via per visualizzare il contenuto di WebVR in Microsoft Edge

No. È Windows Mixed Reality visore VR per usare WebVR in Edge. Tuttavia, è possibile accedere al contenuto di WebVR in un altro browser. Vedere l'elenco completo dei browser e dei dispositivi compatibili [all'indirizzo WebVR.rocks.](http://webvr.rocks/)

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Dove è possibile trovare la documentazione per sviluppatori WebVR

La documentazione per sviluppatori è disponibile qui: [Documentazione per sviluppatori WebVR.](/microsoft-edge/webvr/)

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>È stato trovato un sito Web con WebVR che non funziona in Windows Mixed Reality. Cosa devo fare?

È possibile segnalare i siti interrotti direttamente al [](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)team Microsoft Edge browser nello strumento di gestione dei problemi o tramite Twitter usando #EdgeBug [hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

È anche possibile registrare bug usando l'app Hub di Windows Feedback sotto categoria:

Microsoft Edge -> problemi del sito Web

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Qual è una pagina utile per testare se WebVR funziona?

Vedere [webvr.info esempi.](http://webvr.info/samples/XX-vr-controllers.html)

## <a name="how-do-i-set-up-webvr"></a>Ricerca per categorie configurare WebVR

Per sperimentare il contenuto di WebVR in un visore WINDOWS MIXED REALITY visore VR (con hardware o simulazione), è necessario:

1. Verificare che il visore VR sia connesso.
2. Avviare Microsoft Edge, sul desktop o all'interno di Realtà mista.
3. Passare a una pagina abilitata per WebVR.
4. Selezionare il pulsante Enter VR (Immetti VR) all'interno della pagina (la posizione e la rappresentazione visiva di questo pulsante possono variare per ogni sito Web). L'aspetto potrebbe essere simile al seguente: \
   ![Immagine di vr Goggles](images/75px-enter-vr.png)
5. La prima volta che si prova ad accedere alla realtà virtuale in un dominio specifico, il browser chiederà il consenso per l'uso della visualizzazione immersiva. Selezionare Sì: ![Interfaccia utente di consenso visualizzata al primo tentativo di accesso alla realtà virtuale in un dominio specifico](images/1053px-Webvr-consent-ui.png)
6. Il visore VR dovrebbe iniziare a visualizzare il contenuto di WebVR.

## <a name="see-also"></a>Vedi anche

* [Risoluzione dei problemi > WebVR](webvr-questions.md)
* [Come ottenere la prima esperienza WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Uso di giochi e app in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Home page della realtà mista](your-mixed-reality-home.md)
* [Sistema di rilevamento](tracking-system.md)
* [Controller del movimento](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Inviare commenti e suggerimenti](filing-feedback.md)