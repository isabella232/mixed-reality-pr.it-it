---
title: Domande frequenti su WebVR
description: Rimanere aggiornati sulla risoluzione dei problemi di realtà mista per le applicazioni Web che vanno oltre la documentazione di supporto standard per gli utenti.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, WebVR
ms.openlocfilehash: d0f91af9cf14d8019707e504a9f8bc076bbe39db566895f17e1e56d6b906336d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211093"
---
# <a name="webvr-faqs"></a>Domande frequenti su WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Perché non è possibile visualizzare i controller quando si visualizza il contenuto vr da Edge

Non tutto il contenuto di WebVR viene creato per supportare i controller del movimento. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio controller di gioco o controller del movimento. Se i controller non sono visualizzati in un sito, probabilmente non è disponibile il supporto per il controller del movimento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Perché non è possibile usare il mouse in una visualizzazione WebVR immersiva

L'uso di un mouse è una funzionalità facoltativa della specifica WebVR. Non tutti i browser supportano questa funzionalità e non tutto il contenuto WebVR viene creato per supportare l'input del mouse. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio mouse, tastiera, controller di gioco o controller del movimento. Il comportamento di input del mouse varia in base al browser. All'Microsoft Edge, gli autori di siti Web devono assicurarsi di usare "pointerlock" durante la presentazione al visore VR per il funzionamento dell'input del mouse.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Perché non è possibile visualizzare video a 360 gradi da Youtube/Facebook/Vimeo/The Guardian e così via da Edge nella realtà virtuale?

È presente una specifica WebVR che consente ai siti Web di avviare esperienze di realtà virtuale direttamente dal browser. Gli autori di questi siti Web non hanno implementato questa specifica in questo momento. In alcune piattaforme potrebbero essere disponibili app scaricabili che consentono la visualizzazione del contenuto della realtà virtuale da questi fornitori.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Perché non è possibile immettere la realtà virtuale da Firefox o Chrome?

WebVR è attualmente supportato solo Windows Mixed Reality dispositivi in Edge.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Quando si immette VR da un sito Web, perché viene visualizzata una schermata vuota nel visore VR?

Il sito Web potrebbe non avere implementato il supporto per più computer GPU (inclusi i portatili GPU ibridi). Provare a:

* Ricaricare la pagina.
* Nei computer desktop collegare il visore VR alla stessa scheda grafica del monitor visualizzato Microsoft Edge. Collegare entrambi alla scheda grafica con potenza superiore, non alla scheda grafica integrata.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando si esce dalla realtà virtuale quando si guarda un video da Edge, la riproduzione del suono continua ma la finestra edge è disattivata

Si tratta di un problema noto durante l'esecuzione di WebVR da Edge in Mixed Reality Casa sulla scogliera. Per risolvere il problema, premere ESC sulla tastiera anziché sul pulsante windows per uscire dall'esperienza WebVR oppure attivare la finestra di Edge disattivata selezionandola e quindi arrestare il video.

## <a name="can-i-use-webvr-on-the-hololens"></a>È possibile usare WebVR nel HoloLens

Microsoft non ha annunciato nulla su WebVR HoloLens a questo punto.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Perché è la visualizzazione a livello di piano quando si visualizza il contenuto di WebVR da Edge

Il sito Web non supporta correttamente i Windows Mixed Reality visori VR. Per risolvere il problema:

1. Posizionare il visore VR sul fondo dello spazio.
2. Passare alla pagina WebVR usando Microsoft Edge sul desktop (non all'interno della realtà mista).
3. Selezionare "Enter VR" (Immetti VR).
4. Attendere da cinque a 10 secondi che l'esperienza entri completamente in modalità immersive.
5. Inserire il visore VR.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>Lo schermo è a bassa risoluzione in alcune esperienze WebVR

Questi siti Web non supportano correttamente visori VR ad alta risoluzione. Per risolvere il problema:

* Se si avvia WebVR dal desktop (anziché dal Casa sulla scogliera realtà mista), assicurarsi che la finestra sia ingrandita prima di selezionare "Enter VR" (Immetti VR).
* Evitare di ridimensionare la Microsoft Edge dopo aver immesso la realtà virtuale.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Perché la visualizzazione immersive di WebVR si chiude quando si modificano le schede del browser

Si tratta di un comportamento previsto. Per motivi di sicurezza, solo la scheda attiva del browser può accedere ai visori VR connessi.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Perché non è possibile ascoltare l'audio in una particolare esperienza WebVR

Il sito Web potrebbe usare il formato di file audio OGG, che Microsoft Edge attualmente non supporta.

È possibile segnalare i siti interrotti direttamente al [](https://developer.microsoft.com/microsoft-edge/platform/issues/)team del browser Microsoft Edge nella gestione dei problemi o tramite Twitter usando #EdgeBug [hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Perché il feedback attico non funziona in WebVR con i controller del movimento

Microsoft Edge attualmente non supporta gli aptici nelle estensioni API del gamepad WebVR.