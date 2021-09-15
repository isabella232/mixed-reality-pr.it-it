---
title: Spectator View
description: Visualizzare ologrammi da un dispositivo esterno per mostrare o registrare un'esperienza di realtà mista in uno schermo esterno.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Camera, ARKit, HoloLens, Realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: f30c745154056cda6b5ccf052efbbd0bb7f094ea
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779465"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator View per HoloLens e HoloLens 2

> [!WARNING]
> Microsoft deprecerà l'esempio Disastabili View a causa di incompatibilità con la versione del pacchetto SDK di Ancoraggi nello stato di Azure su cui si basa l'esempio. Inoltre, l'esempio potrebbe smettere di funzionare a causa di altre modifiche nell'ambiente Unity quando i clienti passano alle build LTS 2019 supportate.
>
> Anche se Microsoft attualmente non sta investendo risorse per risolvere i problemi precedenti, potrebbe essere possibile rimuovere la funzionalità di Ancoraggi nello spazio di Azure dall'esempio e basarsi su una tecnologia come i codici a codici a barre per l'allineamento.   Se i membri della community inviano richieste di richiesta per risolvere questi problemi, microsoft li rivedrà e accetterà per il momento.

![Marcatore](images/SpecViewPhoneHero.jpg)

Quando si indossa un dispositivo HoloLens, è facile dimenticare che una persona non dotata di tale dispositivo non può sperimentare le stesse meraviglie visive. Spectator View consente ad altri utenti di visualizzare gli stessi elementi che un utente HoloLens vede in uno schermo 2D. Si tratta inoltre di un approccio rapido e conveniente per registrare ologrammi in HD con dispositivi mobili e ottenere registrazioni di ologrammi di ottima qualità con l'uso di videocamere.

## <a name="key-resources"></a>Risorse principali

* [**Spectator View su GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentazione di Spectator View**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Esempi di Spectator View**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casi d'uso

* Puoi registrare un'esperienza di realtà mista usando un iPhone o un dispositivo Android. Per acquisire video di ologrammi in modo rapido e conveniente, registrare in Full HD e applicare l'anti-aliasing agli ologrammi e all'ombreggiatura.
* Trasmetti in streaming le esperienze di realtà mista a un dispositivo Apple TV direttamente dal tuo iPhone o iPad, in tempo reale.
* Condividi l'esperienza con i tuoi ospiti: consenti alle persone che non hanno HoloLens di visualizzare gli ologrammi direttamente dai loro telefoni o tablet.

## <a name="current-features"></a>Funzionalità attualmente disponibili

* Sincronizzazione spaziale degli ologrammi, in modo che tutti possano visualizzare gli ologrammi esattamente nella stessa posizione.
* Supporto per iOS (dispositivi abilitati per ARKit) e Android (dispositivi abilitati per ARCore).
Più utenti guest iOS.
Registrazione di video + ologrammi + audio dell'ambiente + audio dell'ologramma.
Strumento di condivisione per poter salvare video, inviare un messaggio e-mail o condividere l'esperienza con altre app supportate.

![Marcatore](images/SpecViewPhoneDemo.jpg)
![Marcatore](images/hololensspectatorview-500px.jpg) ![Marcatore](images/spectatorview-300px.png)

La tabella seguente illustra le diverse funzionalità di Spectator View e le opzioni supportate. Scegli l'opzione più adatta alle tue esigenze di registrazione video:

|      Funzionalità                                | Mobile                  |                    Videocamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualità HD                           |         Full HD         |        Registrazioni di qualità professionale (in base alla videocamera)      |
| Facilità di spostamento della videocamera                 |            ✔            |                      ✔                      |
| Visualizzazione di altre persone                    |            ✔            |                      ✔                      |
| Trasmissione in streaming su uno schermo           |            ✔            |                      ✔                      |
| Portabile                             |            ✔            |                                             |
| Wireless                             |            ✔            |                                             |
| Altri requisiti hardware         |     Telefono Android, iPhone    | HoloLens + attrezzatura + treppiede + videocamera + PC + Unity |
| Investimento hardware                  |           Basso            |                     Alto                    |
| Multipiattaforma                       |           Android, iOS   |                                             |
| Contenuto sincronizzato                 |            ✔            |                      ✔                      |
| Durata di configurazione del runtime               |         Adesso          |                     Lente                    |
## <a name="see-also"></a>Vedere anche

* [Acquisizione in realtà mista (MRC, Mixed Reality Capture)](/hololens/holographic-photos-and-videos) 
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)