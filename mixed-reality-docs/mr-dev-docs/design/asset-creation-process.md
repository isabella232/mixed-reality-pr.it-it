---
title: Processo di creazione degli asset
description: Informazioni su come creare, acquistare e convertire asset per esperienze di realtà mista.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: asset, creazione, processo, budget, poligoni, trame, shader, prestazioni, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, asset
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214110"
---
# <a name="asset-creation-process"></a>Processo di creazione degli asset

Windows Mixed Reality si basa sui decenni di investimenti effettuati da Microsoft in DirectX. Tutta l'esperienza e le competenze degli sviluppatori nella creazione di grafica 3D continuano a essere utili con HoloLens.

Gli asset creati per un progetto sono disponibili in molte forme e forme. Possono essere costituiti da una serie di trame/immagini, audio, video, modelli 3D e animazioni. Non è possibile iniziare a coprire tutti gli strumenti disponibili per creare i diversi tipi di asset usati in un progetto. Per questo articolo verranno descritti i metodi di creazione di asset 3D.

![Concetto, creazione, integrazione e flusso di iterazione](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Concetto, creazione, integrazione e flusso di iterazione*

## <a name="things-to-consider"></a>Aspetti da considerare

Quando si esamina l'esperienza, si sta provando **a** creare un budget che è possibile spendere per provare a creare l'esperienza migliore. Non esistono necessariamente limiti rigidi per il numero **di** poligoni o tipi di materiale che **è** possibile usare negli asset. È più che altro un set di compromessi a budget.

Di seguito è riportato un budget di esempio per l'esperienza. Le prestazioni non sono un singolo punto di guasto, ma un decesso di migliaia di riduzioni.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Asset</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Poligoni</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> Trame</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Shader</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Fisica</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Illuminazione in tempo reale</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Elementi multimediali (audio/video)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Script/logica</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Sovraccarico generale</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Totale</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Numero totale di asset**
* Quanti asset sono attivi nella scena?

**Complessità degli asset**
* Quanti triangoli/poligoni?
* Quanto è complesso lo shader? Quando si usa l'Toolkit realtà mista, è consigliabile usare lo [shader Mixed Reality Toolkit Standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) per ridurre la complessità dello shader.

Sia gli sviluppatori che gli autori devono considerare le funzionalità del dispositivo e del motore di grafica. Microsoft HoloLens contiene tutte le funzionalità di calcolo e grafica incorporate nel dispositivo. Condivide le funzionalità che gli sviluppatori troveranno in una piattaforma per dispositivi mobili.

Il processo di creazione di asset è lo stesso indipendentemente dal fatto che l'esperienza sia destinata a [un dispositivo olografico o a un dispositivo immersive.](../discover/mixed-reality.md#the-mixed-reality-spectrum) L'aspetto principale da notare è la capacità e la scalabilità del dispositivo. È possibile visualizzare il mondo reale nella realtà mista, quindi è necessario mantenere la scalabilità corretta in base all'esperienza.

## <a name="authoring-assets"></a>Creazione di asset

Si inizierà con i modi per ottenere gli asset per il progetto:
1. Creazione di asset (strumenti di creazione e acquisizione di oggetti)
2. Acquisto di asset (acquisto di asset online)
3. Porting di asset (esecuzione di asset esistenti)
4. Outsourcing di asset (importazione di asset da terze parti)

### <a name="creating-assets"></a>Creazione di asset

**Strumenti di creazione**<br>
È prima di tutto possibile creare asset personalizzati in diversi modi. Gli autori 3D usano vari strumenti e applicazioni per creare modelli, costituiti da **mesh,** **trame** e **materiali.** Viene quindi salvato in un formato di file che può essere importato o usato dal motore di grafica usato dall'app, ad esempio **. FBX** o **. OBJ**. Qualsiasi strumento che genera un modello che supporta il motore di grafica scelto funzionerà in **HoloLens**. Tra gli autori 3D, molti scelgono di usare [Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) di Autodesk perché può usare HoloLens per trasformare il modo in cui vengono creati gli asset. Se si vuole ottenere qualcosa in modo rapido, è anche possibile usare 3D Builder [fornito](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) con Windows per esportare . OBJ da usare nell'applicazione.

**Acquisizione di oggetti**<br>
È anche possibile acquisire oggetti in 3D. L'acquisizione di oggetti inanimati in 3D e la loro modifica con software di creazione di contenuti digitali è sempre più diffusa con l'aumento della stampa 3D. Usando il **Kinect 2** e [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) è possibile usare la funzionalità di acquisizione per creare asset da oggetti reali. Si tratta anche di [una suite](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) di strumenti per eseguire la stessa operazione con la **fotogrammetria** elaborando diverse immagini da unire e mesh e trame.

### <a name="purchasing-assets"></a>Acquisto di asset

Un'altra opzione eccellente è l'acquisto di asset per la propria esperienza. Sono disponibili, tra gli altri, molti asset tramite servizi come [Unity Asset Store](https://www.assetstore.unity3d.com/) o [TurboSquid.](https://www.turbosquid.com/)

Quando si acquistano asset da terze parti, è sempre necessario controllare le proprietà seguenti:
* **Qual è il numero di poli?**
  * Rientra nel budget?
* **Esistono livelli di dettaglio (LOD) per il modello?**
  * Un livello di dettaglio del modello consente di ridimensionare i dettagli di un modello per le prestazioni.
* **Il file di origine è disponibile?**
  * Non incluso in [Unity Asset Store,](https://www.assetstore.unity3d.com/) ma sempre incluso con servizi come [TurboSquid.](https://www.turbosquid.com/)
  * Senza il file di origine, non è possibile modificare l'asset.
  * Assicurarsi che il file di origine fornito possa essere importato dagli strumenti 3D.
* **Sapere cosa si sta ricevendo**
  * Vengono fornite animazioni?
  * Assicurarsi di controllare l'elenco dei contenuti dell'asset che si sta acquistando.

### <a name="porting-assets"></a>Porting di asset

In alcuni casi verranno consegnati asset esistenti originariamente creati per altri dispositivi e app diverse. Nella maggior parte dei casi, questi asset possono essere convertiti in formati compatibili con il motore di grafica utilizzato dall'app.

Quando si esegue il porting degli asset da usare nell'applicazione HoloLens, è necessario porre le domande seguenti:
* **È possibile importare direttamente o è necessario convertirlo in un altro formato?** Controllare il formato che si sta importando con il motore di grafica in uso.
* **Se la conversione in un formato compatibile viene persa?** A volte i dettagli possono andare persi o l'importazione può causare la pulizia di elementi che devono essere puliti in uno strumento di creazione 3D.
* **Qual è il numero di triangoli/poligoni per l'asset?** In base al budget per l'applicazione, è possibile usare [Simplygon](https://www.simplygon.com/) o strumenti simili per eliminare (proceduralmente o manualmente il numero di poli) l'asset originale in base al budget delle applicazioni.

### <a name="outsourcing-assets"></a>Esternalizzazione di asset

Un'altra opzione per progetti di dimensioni maggiori che richiedono più asset rispetto a quelli che il team è in grado di creare è l'esternalizzazione della creazione di asset. Il processo di esternalizzazione comporta la ricerca dello studio o dell'agenzia giusto specializzato nell'esternalizzazione di asset. Questa può essere l'opzione più costosa, ma anche la più flessibile in ciò che si ottiene.
* **Definire chiaramente ciò che si sta richiedendo**
  * Fornire il maggior numero possibile di dettagli
  * Immagini concettuali anteriore, laterale e posteriore
  * Immagine di riferimento che mostra l'asset nel contesto
  * Scala dell'oggetto (in genere specificata in centimetri)
* **Specificare un budget**
  * Intervallo di conteggio dei poli
  * Numero di trame
  * Tipo di shader (per Unity e HoloLens è consigliabile impostare sempre per impostazione predefinita gli shader per dispositivi mobili)
* **Comprendere i costi**
  * Quali sono i criteri di outsourcing per le richieste di modifica?

L'outsourcing può funzionare correttamente in base alla sequenza temporale dei progetti, ma richiede una maggiore supervisione per garantire che si otterrà gli asset necessari la prima volta.
