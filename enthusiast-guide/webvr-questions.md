---
title: Domande frequenti su WebVR
description: Risoluzione dei problemi di realtà mista Web che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, WebVR
ms.openlocfilehash: fd9906ca36c71b1bf959466d90c57e07be0eca5e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725632"
---
# <a name="webvr-faqs"></a>Domande frequenti su WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Perché non è possibile visualizzare i controller quando si visualizzano i contenuti VR da Edge

Non tutto il contenuto di WebVR viene creato per supportare i controller di movimento. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio controller di gioco o controller di movimento. Se non vengono visualizzati i controller in un sito, probabilmente non è supportato il controller di movimento.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Perché non è possibile usare il mouse in una visualizzazione WebVR immersiva

L'uso di un mouse è una funzionalità facoltativa della specifica WebVR. Non tutti i browser supportano questa funzionalità e non tutto il contenuto di WebVR viene creato per supportare l'input del mouse. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio mouse, tastiera, controller di gioco o controller di movimento. Il comportamento di input del mouse varia a seconda del browser. In Microsoft Edge gli autori di siti Web devono assicurarsi di usare "pointerlock" per la presentazione all'auricolare per il funzionamento dell'input del mouse.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Perché non è possibile visualizzare video di 360 gradi da YouTube/Facebook/Vimeo/The Guardian e così via da Microsoft Edge in VR

È disponibile una specifica WebVR che consente ai siti Web di avviare esperienze VR direttamente dal browser. Gli autori di questi siti Web non hanno implementato questa specifica in questo momento. In alcune piattaforme possono essere disponibili app scaricabili che consentono la visualizzazione di contenuto VR da tali fornitori.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Perché non è possibile immettere VR da Firefox o Chrome

WebVR è attualmente supportato solo da dispositivi di realtà mista Windows in Microsoft Edge.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Quando si immette VR da un sito Web, perché viene visualizzata una schermata vuota nell'auricolare

Il sito Web potrebbe non aver implementato il supporto per i computer con più GPU (inclusi i portatili GPU ibridi). Provare a:

* Ricaricare la pagina.
* Nei computer desktop collegare l'auricolare alla stessa scheda grafica del monitor che visualizza Microsoft Edge. Inserire entrambi i valori nella scheda grafica più elevata, non nella scheda grafica integrata.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando si esce da VR quando si guarda un video da Edge, il suono continua a riprodurre, ma la finestra perimetrale è disabilitata

Si tratta di un problema noto quando si esegue WebVR da Edge nella realtà mista Cliff House. Per risolverlo, premere Escape sulla tastiera anziché il pulsante Windows per uscire dall'esperienza WebVR oppure attivare la finestra bordo grigio selezionando il pulsante e quindi arrestare il video.

## <a name="can-i-use-webvr-on-the-hololens"></a>È possibile usare WebVR in HoloLens

A questo punto, Microsoft non ha annunciato alcuna cosa su WebVR in HoloLens.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Perché la visualizzazione è a livello di piano quando si Visualizza il contenuto di WebVR da Edge

Il sito Web non supporta correttamente le cuffie per la realtà mista di Windows. Per risolvere il problema:

1. Posizionare l'auricolare sul pavimento dello spazio.
2. Passare alla pagina WebVR usando Microsoft Edge sul desktop (non all'interno di realtà mista).
3. Selezionare "Enter VR".
4. Attendere da cinque a 10 secondi perché l'esperienza entri completamente in modalità immersiva.
5. Inserire l'auricolare.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>La visualizzazione è a bassa risoluzione in alcune esperienze di WebVR

Questi siti Web non supportano correttamente le cuffie ad alta risoluzione. Per risolvere il problema:

* Se si avvia WebVR dal desktop, invece della realtà mista Cliff House, assicurarsi che la finestra sia ingrandita prima di selezionare "Enter VR".
* Evitare di ridimensionare la finestra Microsoft Edge dopo aver immesso VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Perché la visualizzazione immersiva WebVR viene chiusa quando si modificano le schede del browser

Si tratta di un comportamento previsto. Per motivi di sicurezza, solo la scheda Active browser può accedere alle cuffie connesse.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Perché non è possibile ascoltare l'audio in una particolare esperienza WebVR

Il sito Web può usare il formato di file audio OGG, che attualmente non è supportato da Microsoft Edge.

È possibile segnalare i siti interrotti direttamente al team del browser Microsoft Edge in [Issue Tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/)o tramite twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Perché i commenti tattili non funzionano in WebVR con i controller di movimento

Microsoft Edge attualmente non supporta haptics nelle estensioni dell'API di WebVR Gamepad.