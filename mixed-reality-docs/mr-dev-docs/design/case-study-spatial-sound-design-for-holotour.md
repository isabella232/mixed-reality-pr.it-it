---
title: Case study - Progettazione dell'audio spaziale per HoloTour
description: Per creare un tour virtuale 3D realmente immersivo per Microsoft HoloLens, i video panoramici e lo scenario olografico sono solo una parte della formula.
author: jsyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, suono spaziale, case study, visore di realtà mista, visore windows mixed reality, visore di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit, audio
ms.openlocfilehash: b398ea7b3ddd85db85018da1852ed0c5ae410f625ff88bdda286e750a517d260
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196453"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Case study: Progettazione del suono spaziale per HoloTour

I video panoramici e gli scenari olografici sono solo una parte della formula per un tour Microsoft HoloLens immersiva. Questo articolo descrive come l'audio è stato usato per far sembrare di essere effettivamente in ogni posizione di HoloTour.

## <a name="the-tech"></a>La tecnologia

Le belle immagini e le scene olografiche che si possono vedere in HoloTour sono solo una parte di un'esperienza di realtà mista dispersibile. Anche se gli ologrammi vengono visualizzati solo davanti [](spatial-sound.md) a un utente, HoloLens può offrire un suono spaziale da tutte le direzioni, il che offre un'esperienza sensoriale più completa.

Il suono spaziale fornisce segnali per indicare una direzione in cui l'utente deve svoltare o per indicare all'utente che sono presenti più ologrammi da visualizzare all'interno dello spazio. È anche possibile collegare un suono direttamente a un ologramma e aggiornare continuamente la direzione e la distanza dell'ologramma dall'utente. Questa tecnica fa sembrare che il suono proviene direttamente da tale oggetto.

Per HoloTour si è voluto sfruttare le funzionalità del suono spaziale di HoloLens, quindi è stato creato un ambiente ambientale a 360 gradi sincronizzato con il video per rivelare le evidenziazioni sonore di posizioni specifiche.

## <a name="behind-the-scenes"></a>Dietro le quinte

Sono state create esperienze HoloTour di due località diverse: Rome e Machu Picchu. Per rendere questi tour autentici e accattivanti, abbiamo voluto acquisire l'audio dalle posizioni in cui abbiamo filmato invece di usare suoni generici.

### <a name="capturing-the-audio"></a>Acquisizione dell'audio

Nella nostra [case study sull'acquisizione del contenuto visivo per HoloTour,](../out-of-scope/case-study-capturing-and-creating-content-for-holotour.md)si parla della progettazione del rig di fotocamera. Era costituito da 14 fotocamere GoPro in un alloggiamento stampato in 3D progettato per adattarsi al treppiede. Per acquisire l'audio, è stata aggiunta una matrice di quattro microfoni sotto le fotocamere. Il suono si nutre di un'unità di registrazione compatta a quattro canali alla base del treppiede. Sono stati scelti microfoni che erano abbastanza piccoli da evitare interferenze con le fotocamere.

![Dispositivo di fotocamera e microfono personalizzato](images/camera-rig-microphones-300px.png)<br>
*Dispositivo di fotocamera e microfono personalizzato*

Questa configurazione acquisisce il suono in quattro direzioni. Sono stati registrati dati sufficienti per creare di nuovo un panorama urale 3D del suono spaziale, che è possibile sincronizzare successivamente con il video a 360 gradi.

Una sfida dell'audio dell'array di fotocamere è che ci si trova alla mercé di suoni fuori dalla fotocamera, ad esempio sollilli, aerei o venti elevati. Per assicurarsi di avere tutti gli elementi sonori necessari, sono stati usati registratori per dispositivi mobili stereo e mono per acquisire un suono ambientale asincrono in punti specifici di interesse in ogni posizione. Queste registrazioni offrono al sound designer un contenuto pulito per aggiungere interesse e migliorare la direzionalità nella post-produzione.

Ogni giorno di acquisizione genera molti file. Era quindi importante sviluppare un sistema per tenere traccia dei file che corrispondono a una posizione specifica o a una ripresa della fotocamera. L'unità di registrazione è stata impostata per assegnare automaticamente un nome ai file in base alla data e al numero "take". Alla fine di ogni giorno è stato eseguito il backup dei file in unità esterne. È anche importante eseguire lo slate verbale all'inizio delle registrazioni audio. Questa precauzione consente una facile identificazione contestuale del contenuto nel caso in cui si verifichino problemi di nome file. Era anche importante eseguire visivamente l'ardesia dell'acquisizione del rig della fotocamera, perché il video e l'audio venivano registrati come supporti separati e dovevano essere sincronizzati durante la post-produzione.

### <a name="editing-the-audio"></a>Modifica dell'audio

Tornando allo studio dopo il viaggio di acquisizione, il primo passaggio per assemblare un'esperienza aurale direzionale e immersiva consiste nel rivedere tutto l'audio acquisito per una posizione. Vengono scelte le migliori scelte e vengono identificate le evidenziazioni che possono essere applicate durante l'integrazione. L'audio viene quindi modificato e pulito. Ad esempio, una tromba d'auto che dura un secondo o così e si ripete alcune volte potrebbe essere sostituita con audio ambientale più silenzioso della stessa sessione di acquisizione.

Dopo aver impostato la modifica video per una posizione, la finestra di progettazione del suono può sincronizzare l'audio corrispondente. A questo punto, vengono valutate sia le acquisizioni audio per camera-rig che per dispositivi mobili per decidere quali elementi creare la migliore scena audio immersiva. È stato utile inserire tutti gli elementi audio in un editor audio e creare simulazioni lineari rapide per sperimentare diverse idee di combinazione. Questo passaggio ha fornito idee più dettagliate per la creazione delle scene di HoloTour effettive.

### <a name="assembling-the-scene"></a>Assemblaggio della scena

Il primo passaggio per la creazione di una scena di ambiente 3D consiste nel creare un letto di suoni di ciclo ambientale di sfondo generale che supportino altre funzionalità e elementi sonori interattivi in una scena. Si adottare un approccio olistico all'implementazione come determinato dai criteri di progettazione per qualsiasi scena specifica. Alcune scene potrebbero essere indicizzate in base all'uso dell'acquisizione della fotocamera sincronizzata. Momenti più "cinematografici" potrebbero richiedere un approccio curato che si basa su suoni posizionati in modo discreto, elementi interattivi e musica.

Quando è stato effettuato l'indicizzazione sull'audio di acquisizione della fotocamera, sono stati inseriti emettitori audio ambientali abilitati per il suono spaziale che corrispondevano all'orientamento direzionale delle fotocamere. La visualizzazione della fotocamera a nord riproduce l'audio dal microfono nord e allo stesso modo per le altre direzioni cardinali. Questi emettitori sono bloccati in tutto il mondo, il che significa che il suono cambia quando gli utenti girano la testa. Questa tecnica modella in modo efficace il suono di in piedi in quella posizione. Per esempi di scene che usano una buona combinazione di audio acquisito dalla fotocamera, è possibile ascoltare Il Pantheon o La Navona.

In un approccio diverso, talvolta si riproduce l'ambiente stereo a ciclo continuo con gli emettitori di suoni spaziali posizionati intorno alla scena. Questi emettitori emettono suoni una-off di volume casuale, passo e frequenza di trigger. Questa tecnica crea un ambiente con un maggiore senso di direzionalità. In Aguas Alienates, ad esempio, è possibile ascoltare come ogni quadrante del panorama abbia emettitori specifici che evidenziano aree specifiche della geografia, ma che lavorano insieme per creare un ambiente immersivo complessivo.

## <a name="tips-and-tricks"></a>Suggerimenti e consigli

Esistono altri modi per evidenziare la direzionalità e migliorare l'immersione per usare al massimo le funzionalità del suono spaziale HoloLens. È stato fornito un elenco qui. Restare in ascolto di questi effetti al successivo tentativo di HoloTour.
* **Cerca destinazioni:** Questi suoni vengono attivati quando si osserva un oggetto o un'area specifica del frame olografico. Ad esempio, guardare verso il caffè sul lato strada in Via Navona a Roma per attivare i suoni dei ristoranti occupati.
* **Visione locale:** Il percorso di HoloTour contiene alcuni "battiti" in cui la guida, aiutata da ologrammi, esplora in modo approfondito un argomento. Ad esempio, quando la facciata del Pantheon si dissolve per rivelare l'oculus, l'audio riverberante posizionato come emettitore 3D dall'interno del Pantheon invita l'utente a esplorare l'interno.
* **Direzionalità migliorata:** In molte scene, i suoni sono stati inseriti in vari modi per aggiungere alla direzionalità. Nella scena Pantheon, ad esempio, il suono della stilografia è stato posizionato come un emettitore separato abbastanza vicino all'utente da poter ottenere un senso di "parallasse sonora" mentre si aggirano nello spazio di gioco. Nella scena Salinas de Maras del Perù, i suoni dei singoli piccoli flussi sono stati posizionati come emettitori separati per creare un ambiente ambientale più coinvolgente, circondando l'utente con i suoni autentici di tale posizione.
* **Emettitore spline:** Questi emettitori si spostano nello spazio 3D in base alla posizione visiva dell'oggetto a cui sono collegati. Un esempio è il training in Machu Picchu, in cui è stato usato un emettitore spline per dare un senso distinto di direzionalità e movimento.
* **Musica e SFX:** Alcuni aspetti di HoloTour che rappresentano un approccio più stilizzato o cinematografico usano la musica e gli effetti sonori per aumentare l'impatto emotivo. Ad esempio, la lotta per il dissalvamento alla fine del tour di Roma usa effetti speciali come whooshes e stinger per rafforzare l'effetto delle etichette che compaiono nelle scene.

## <a name="see-also"></a>Vedi anche

* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](../develop/unity/spatial-sound-in-unity.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
