---
title: Tipi di app di realtà mista
description: Informazioni sulle esperienze supportate dalla piattaforma di realtà mista, da ambienti immersive a livelli di informazioni leggere sull'ambiente di un utente.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, modelli di app, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, HoloLens
ms.openlocfilehash: 13d4f538148b2c6b6f4df422c6c423f2b2710ca1ba2d98fe4f952c14284035f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218928"
---
# <a name="types-of-mixed-reality-apps"></a>Tipi di app di realtà mista

Uno dei vantaggi dello sviluppo di app per Windows Mixed Reality è la gamma di esperienze che la piattaforma può supportare. Da ambienti virtuali completamente immersivi a una sovrapposizione poco invasiva di informazioni all'ambiente corrente di un utente, Windows Mixed Reality offre un set efficace di strumenti per creare qualsiasi tipo di esperienza. È importante che un autore di app comprendi nelle prime fasi del processo di sviluppo la posizione in cui si trova la loro esperienza. Questa decisione in definitiva inciderà sia sulla progettazione delle app che sul percorso tecnologico per lo sviluppo.

## <a name="enhanced-environment-apps-hololens-only"></a>App per ambienti migliorati (solo HoloLens)

Uno dei modi più potenti in cui la realtà mista può dare valore è consentire agli sviluppatori di inserire informazioni o contenuti digitali nell'ambiente corrente di un utente. Questo approccio è molto diffuso per le app in cui il posizionamento contestuale del contenuto digitale nel mondo reale è fondamentale e mantenere "presente" l'ambiente reale dell'utente durante l'esperienza è fondamentale. Gli utenti possono anche spostarsi facilmente tra attività digitali reali. In questo modo si presta ancora di più alla promessa che le app di realtà mista che l'utente vede effettivamente fanno parte del proprio ambiente.

![App per ambienti migliorati](images/enhancedenvironmentapps-640px.jpg)<br>
*App per ambienti migliorati*

**Esempi d'uso**
* Un'app in stile blocco note di realtà mista che consente agli utenti di creare e inserire note nel proprio ambiente
* Un'app tv di realtà mista posizionata in un luogo comodo per la visualizzazione
* Un'app di realtà mista posizionata sopra l'isola della cucina per aiutare un'attività di preparazione
* Un'app di realtà mista che offre agli utenti la impressione di "visione a raggi X", ovvero un ologramma posizionato sopra e simula un oggetto reale, consentendo all'utente di vedere "al suo interno" olograficamente
* Annotazioni di realtà mista posizionate in una factory per fornire le informazioni necessarie al ruolo di lavoro
* Ricerca in modalità di realtà mista in un ufficio
* Esperienze di tablet di realtà mista (ovvero esperienze di stile di gioco da tavolo)
* App di comunicazione di realtà mista come Skype

## <a name="blended-environment-apps"></a>App per ambienti misti

Data Windows Mixed Reality di riconoscere e mappare l'ambiente dell'utente, è in grado di creare un livello digitale che può essere sovrapposto allo spazio dell'utente. Il livello thin rispetta la forma e i limiti dell'ambiente dell'utente, ma l'app può scegliere di trasformare determinati elementi più adatti per coinvolgere l'utente nell'app. Si tratta di un'app di ambiente misto. A differenza di un'app per ambienti ottimizzati, le app per ambienti misti possono avere un'attenzione sufficiente per l'ambiente e usarle al meglio per incoraggiare un comportamento specifico dell'utente (ad esempio incoraggiare lo spostamento o l'esplorazione) o sostituendo gli elementi con modifiche (un contatore della cucina viene ottimizzato per mostrare un modello a sezioni diverso). Questo tipo di esperienza può anche trasformare un elemento in un oggetto completamente diverso, ma mantenere comunque le dimensioni approssimative dell'oggetto come base (un'isola di cucina viene trasformata in un dumpster per un gioco di criminalità).

![App per ambienti misti](images/blendedenvironmentapps-640px.jpg)<br>
*App per ambienti misti*

**Esempi d'uso**
* Un'app di progettazione interna di realtà mista in grado di disegnare pareti, controteni o piani in colori e modelli diversi
* Un'app di realtà mista che consente a un designer automobilistico di creare nuovi livelli di iterazioni di progettazione per un prossimo aggiornamento dell'auto su un'auto esistente
* Un letto è "coperto" e sostituito da uno stand di realtà mista nel gioco per bambini
* Una desk viene "coperta" e sostituita con un dumpster di realtà mista in un gioco di criminalità
* Un'in sospeso viene "coperta" e sostituita con un segnaletica che usa approssimativamente la stessa forma e la stessa dimensione
* Un'app che consente agli utenti di creare buchi nelle pareti del mondo reale o immersive, rivelando un mondo coinvolgente

## <a name="immersive-environment-apps"></a>App dell'ambiente immersive

Le app dell'ambiente immersive sono centrate su un ambiente che cambia completamente il mondo dell'utente e può posizionarle in un tempo e uno spazio diversi. Questi ambienti possono essere reali, creando esperienze coinvolgenti e coinvolgenti limitate solo dall'emozione dell'autore dell'app. A differenza delle app per ambienti misti, una volta che Windows Mixed Reality identifica lo spazio dell'utente, un'app per l'ambiente immersive può ignorare completamente l'ambiente corrente dell'utente e sostituirla con una delle proprie. Queste esperienze possono anche separare il tempo e lo spazio, vale a dire che un utente può percorso le strade di Rome in un'esperienza immersiva, rimanendo relativamente ancora nello spazio reale. Il contesto dell'ambiente reale potrebbe non essere importante per un'app dell'ambiente immersive.

![App dell'ambiente immersive](images/windows-mixed-reality-640px.jpg)<br>
*App dell'ambiente immersive*

**Esempi d'uso**
* Un'app immersiva che consente a un utente di visitare uno spazio separato dal proprio (ovvero, passare attraverso un edificio, una città popolare e popolare)
* Un'app immersiva che orchestra un evento o uno scenario intorno all'utente (ovvero una sfida o una prestazione)

## <a name="see-also"></a>Vedere anche

* [Cenni preliminari sullo sviluppo](../develop/development.md)
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)
