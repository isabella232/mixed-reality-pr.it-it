---
title: Linee guida per la progettazione di launcher di app 3D
description: Un'icona di avvio di app 3D è un oggetto "fisico" nella realtà mista dell'utente che può scegliere di avviare un'app.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, utilità di avvio di app 3D, visore vr immersivo, cubo live, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, UWP, Win32, illuminazione, colore
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188527"
---
# <a name="3d-app-launcher-design-guidance"></a>Linee guida per la progettazione di launcher di app 3D

Quando si inserisce un visore Windows Mixed Reality vr immersivo, si entra nella Windows Mixed Reality home. La casa viene visualizzato come una casa su una roccia immersa in monti e acqua, ma è possibile scegliere altri ambienti e [persino crearne uno personalizzato.](../design/add-custom-home-environments.md) All'interno dello spazio della casa, un utente è libero di disporre e organizzare gli oggetti e le app 3D che si preoccupano nel modo desiderato. **Un'icona di avvio di app 3D** è un oggetto "fisico" nella realtà mista dell'utente che può scegliere di avviare un'app.

![Esempio: Icona di avvio di app floaty Bird 3D](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio di app Floaty Bird 3D (app fittizia)*

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'icona di avvio delle app 3D

Per creare un'icona di avvio di app 3D, è necessario eseguire tre passaggi:

1. Progettazione e creazione di concetti (questo articolo)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrazione nell'applicazione:
    * [App UWP](implementing-3d-app-launchers.md)
    * [App Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Concetti relativi alla progettazione

### <a name="fantastic-yet-familiar"></a>Fantastico ma familiare

L Windows Mixed Reality ambiente in cui si trova l'utilità di avvio delle app è in parte familiare, in parte fantastico/sci-fi. Le migliori utilità di avvio seguono le regole di questo mondo. Si pensi a come è possibile prendere un oggetto familiare e rappresentativo dall'app, ma modificare alcune regole della realtà effettiva. Verrà restituito Magic.

### <a name="intuitive"></a>intuitivo

Quando si guarda l'icona di avvio delle app, lo scopo, per avviare l'app, deve essere ovvio e non deve causare confusione. Ad esempio, assicurarsi che l'utilità di avvio sia un rappresentante abbastanza ovvio dell'app che non verrà confusa per un'opera di decorazione nel Casa sulla scogliera. L'icona di avvio delle app deve invitare gli utenti a toccarla/selezionarla.

![Esempio: utilità di avvio delle app 3D fresh note](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio di app 3D fresh Note (app fittizia)*

### <a name="home-scale"></a>Scalabilità home

Le utilità di avvio delle app 3D sono Casa sulla scogliera e le relative dimensioni predefinite dovrebbero avere senso con gli altri oggetti "fisici" nello spazio. Se si posiziona il launcher accanto, ad esempio, a una pianta della casa o ad alcuni mobili, dovrebbe essere a casa, per dimensioni. Un buon punto di partenza è vedere come appare a 30 centimetri cubi, ma tenere presente che gli utenti possono ridimensionarlo in alto o in basso, se lo desiderano.

### <a name="own-able"></a>Own-able

L'icona di avvio delle app dovrebbe avere l'aspetto di un oggetto che una persona sarebbe contenta di avere nel proprio spazio. Si circondano virtualmente di queste cose, quindi l'utilità di avvio dovrebbe avere l'aspetto di qualcosa che l'utente ha ritenuto abbastanza desiderabile da cercare e mantenere nelle vicinanze.

![Esempio: utilità di avvio delle app 3D Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio di app 3D Astro Warp (app fittizia)*

### <a name="recognizable"></a>Riconoscibile

L'icona di avvio delle app 3D deve esprimere immediatamente il "marchio dell'app" agli utenti che la vedono. Se nell'app è presente un carattere star o un oggetto particolarmente identificabile, è consigliabile usarlo come parte significativa della progettazione. In un mondo di realtà mista, un oggetto trarrà più interesse dagli utenti rispetto al solo logo. Gli oggetti riconoscibili comunicano il marchio in modo rapido e chiaro.

### <a name="volumetric"></a>Volumetrico

L'app merita di più del semplice inserimento del logo su un piano piano e della chiamata giornaliera. L'utilità di avvio dovrebbe essere un interessante oggetto fisico 3D nello spazio dell'utente. Un buon approccio consiste nell'immaginare che l'app abbia un palloncino nella parata del giorno del giorno del ringraziamento di Macy. Chiedersi cosa sorprenderebbe realmente le persone quando si è visto in fondo alla strada? Che aspetto avrebbe da tutte le angolazioni di visualizzazione?

:::row:::
    :::column:::
        ![Solo ](images/20171016-140436-mixedreality-640px.jpg) *logo Solo logo*
    :::column-end:::
    :::column:::
        ![Più riconoscibile con un carattere ](images/20171016-140557-mixedreality-640px.jpg) *Più riconoscibile con un carattere*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![L'approccio flat, non a caso, si ritiene flat, non ](images/20171016-155101-mixedreality-640px.jpg) *a caso, flat*
    :::column-end:::
    :::column:::
        ![L'approccio volumetrico illustra meglio l'approccio volumetrico dell'app ](images/20171016-161407-mixedreality-640px.jpg) *per presentare meglio l'app*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Suggerimenti per modelli 3D buoni

* Quando si pianificano le dimensioni per l'icona di avvio delle app, è possibile creare un cubo di circa 30 cm. Quindi, un rapporto di dimensioni 1:1:1.
* I modelli devono essere al di sotto di 10.000 poligoni. [Altre informazioni sui conteggi dei triangoli e sui livelli di dettagli (LOD)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Eseguire il test su un visore immersivo.
* Se possibile, compilare i dettagli nella geometria del modello. Non basarsi sulle trame per i dettagli.
* Creare una geometria chiusa "a tenuta d'acqua". Nessun foro modellato.
* Usare materiali naturali nell'oggetto. Imagine crearlo nel mondo reale.
* Assicurarsi che il modello sia letto bene a distanze e dimensioni diverse.
* Quando il modello è pronto per l'esportazione, leggere le linee [guida per l'esportazione degli asset](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modello con dettagli sottili nella trama](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modello con dettagli sottili nella trama*

### <a name="what-to-avoid"></a>Da evitare

* Non usare dettagli a contrasto elevato o modelli e trame piccoli e occupati.
* Non usare la geometria sottile: non funziona bene a distanza e non usa correttamente un alias.
* Non lasciare che parti del modello si estendano troppo oltre il rapporto di dimensioni 1:1:1. Creerà problemi di ridimensionamento.

![Evitare modelli di occupato a contrasto elevato e di piccole dimensioni](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitare modelli a contrasto elevato, piccoli e occupati*

## <a name="how-to-handle-type"></a>Come gestire il tipo

* È consigliabile che il tipo occupa circa 1/3 dell'icona di avvio delle app (o più). Il tipo è la cosa principale che dà agli utenti l'idea che l'utilità di avvio sia, in effetti, un launcher, quindi è interessante se è sostanziale.
* Evitare di rendere il tipo super ampio: provare a mantenerlo entro i limiti delle dimensioni principali delle utilità di avvio delle app (più o meno).
* Il tipo flat può funzionare, ma può essere difficile da visualizzare da determinate angolazioni e in determinati ambienti. Per risolvere questo problema, è possibile considerare la possibilità di creare un oggetto solido o un contesto.
* L'aggiunta di una dimensione al tipo è molto piacevole in 3D. L'ombreggiatura dei lati del tipo con un colore diverso e più scuro può essere utile per migliorare la leggibilità.

:::row:::
    :::column:::
        ![Tipo flat senza sfondo può essere difficile da visualizzare da determinate angolazioni e in determinati ambienti Tipo flat senza sfondo può essere difficile da visualizzare da determinate angolazioni e ](images/flattype-640px.png) *in determinati ambienti*
    :::column-end:::
    :::column:::
        ![Il tipo con un contesto predefinito può funzionare correttamente Il tipo con uno sfondo predefinito ](images/flattypeandbkg-640px.png) *può funzionare correttamente*
    :::column-end:::
    :::column:::
        ![Il tipo estruso può funzionare bene se si ombreggiatura dei lati Tipo estruso può funzionare bene se si ](images/20171016-160221-mixedreality-640px.jpg) *ombreggiatura dei lati*
    :::column-end:::
:::row-end:::

**Tipi di colori che funzionano**

* White
* Nero
* Colore semisaturato chiaro

![Digitare i colori che funzionano.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Tipi di colori che funzionano*

### <a name="colors-to-avoid"></a>Colori da evitare

I colori dei tipi che causano problemi includono:

* Toni medi
* Grigio
* Colori sovrasaturati o colori saturati

![Digitare i colori che causano problemi.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Tipi di colori che causano problemi*

## <a name="lighting"></a>Luce

L'illuminazione per l'icona di avvio delle app proviene dall'Casa sulla scogliera locale. Assicurarsi di testare l'utilità di avvio in diverse posizioni in tutta la casa in modo che sia buona sia in luce che in ombreggiatura. La buona notizia è che, se sono stati seguiti gli altri consigli di progettazione in questo documento, l'utilità di avvio dovrebbe essere in buona forma per la maggior parte dell'illuminazione nel Casa sulla scogliera.

I posti migliori per testare l'aspetto dell'utilità di avvio nelle varie luci dell'ambiente sono lo Studio, la Media Room, ovunque all'esterno e sul backreyy (l'area in concreto con il giardino). Un altro buon test è quello di metterlo in mezza luce e mezza ombreggiatura e vedere come appare.

![Assicurarsi che l'utilità di avvio sia in luce che in ombreggiatura.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Assicurarsi che l'utilità di avvio sia in chiaro che in ombreggiatura*

## <a name="texturing"></a>Texturing

### <a name="authoring-your-textures"></a>Creazione di trame

Il formato finale dell'utilità di avvio delle app 3D sarà un file con estensione glb, che viene creato usando la pipeline PBR (Physically Based Rendering). Questo può essere un processo difficile: è ora un buon momento per impiegare un tecnico, se non è già stato fatto. Se si è un teso diy-er, prendere il tempo per ricercare e apprendere la [terminologia PBR](https://wiki.polycount.com/wiki/PBR) e ciò che accade sotto il cofano prima di iniziare consente di evitare errori comuni. 

![Esempio: app Fresh Note](images/pbr-freshnote1-640px-500px.png)<br>
*Esempio di utilità di avvio di app 3D fresh Note (app fittizia)*

### <a name="recommended-authoring-tool"></a>Strumento di creazione consigliato

Per creare il file [finale,](https://www.allegorithmic.com/products/substance-painter) è consigliabile usare La pittrice di sostanza di Allegorithmic. Se non si ha familiarità con la creazione di shader PBR in Intasato di sostanza, ecco [un'esercitazione.](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)

Se si ha più familiarità con uno di questi strumenti, funziona anche in alternativa [3D-Coat,](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)o Lo strumento Per lo strumento [DioTtotto.](https://www.marmoset.co/toolbag/)

### <a name="best-practices"></a>Procedure consigliate

* Se l'oggetto di avvio delle app è stato creato per PBR, dovrebbe essere semplice convertirlo per l'Casa sulla scogliera ambiente.
* Lo shader prevede un flusso di lavoro Metal/Roughness: lo shader Unreal PBR è un facsimile vicino.
* Quando si esportano le trame, tenere presenti le [dimensioni consigliate](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) per le trame.
* Assicurarsi di creare gli oggetti per l'illuminazione in tempo reale, ovvero:
  * Evitare ombreggiature cotte o ombreggiature disegnate
  * Evitare l'illuminazione al forno nelle trame
  * Usare uno dei pacchetti di creazione di materiali PBR per ottenere le mappe giuste generate per lo shader

## <a name="see-also"></a>Vedi anche

* [Creare modelli 3D da usare nella ambiente iniziale](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementare utilità di avvio per app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare utilità di avvio per app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
