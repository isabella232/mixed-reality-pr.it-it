---
title: Processo di creazione degli asset
description: Informazioni su come creare, acquistare e trasferire asset per esperienze di realtà miste.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, creazione, processo, Budget, poligoni, trame, shader, prestazioni, cuffie per realtà mista, cuffie per la realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, asset
ms.openlocfilehash: a5f4271de522111b0ef994869b9ecf4910582562
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009620"
---
# <a name="asset-creation-process"></a>Processo di creazione degli asset

La realtà mista di Windows si basa su decenni di investimenti effettuati da Microsoft in DirectX. Tutta l'esperienza e le competenze degli sviluppatori con la creazione di grafica 3D continuano a essere utili con HoloLens.

Gli asset creati per un progetto sono disponibili in molte forme e form. Possono essere costituiti da una serie di trame/immagini, audio, video, modelli 3D e animazioni. Non è possibile iniziare a coprire tutti gli strumenti disponibili per creare i diversi tipi di asset usati in un progetto. Per questo articolo, ci concentreremo sui metodi di creazione di asset 3D.

![Concetto, creazione, integrazione e flusso di iterazione](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Concetto, creazione, integrazione e flusso di iterazione*

## <a name="things-to-consider"></a>Aspetti da considerare

Quando si esamina l'esperienza, si sta provando a crearla come un **budget** che è possibile spendere per provare a creare l'esperienza migliore. Non sono necessariamente presenti limiti rigidi per il numero di **poligoni** o **tipi di materiale** che è possibile usare negli asset. Considerarlo più come un set di compromessi con budget.

Di seguito è riportato un budget di esempio per la propria esperienza. Le prestazioni non sono un singolo punto di errore, ma sono morte di mille tagli.
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
<td> Supporti (audio/video)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Script/logica</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Overhead generale</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Totale</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Numero totale di asset**
* Quanti asset sono attivi nella scena?

**Complessità degli asset**
* Quanti triangoli/poligoni?
* Quanto è complesso lo shader? Quando si usa il Toolkit di realtà mista, è consigliabile usare lo [shader standard di Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) per ridurre la complessità dello shader.

Gli sviluppatori e gli artisti devono prendere in considerazione le funzionalità del dispositivo e del motore di grafica. Microsoft HoloLens ha tutto il calcolo e la grafica integrati nel dispositivo. Condivide le funzionalità che gli sviluppatori troveranno in una piattaforma mobile.

Il processo di creazione dell'asset è identico se l'esperienza è destinata a un dispositivo [olografico o](../discover/mixed-reality.md#the-mixed-reality-spectrum)a un dispositivo immersivo. La cosa principale da notare è la capacità e la scalabilità del dispositivo. È possibile vedere il mondo reale in realtà mista, quindi è opportuno mantenere la scalabilità corretta in base all'esperienza.

## <a name="authoring-assets"></a>Creazione di asset

Si inizierà con i modi per ottenere gli asset per il progetto:
1. Creazione di asset (strumenti di creazione e acquisizione di oggetti)
2. Acquisti di risorse (acquisto di asset online)
3. Porting degli asset (prendendo gli asset esistenti)
4. Risorse di outsourcing (importazione di asset da terze parti)

### <a name="creating-assets"></a>Creazione di asset

**Strumenti di creazione**<br>
Per prima cosa è possibile creare asset personalizzati in diversi modi. gli artisti 3D utilizzano varie applicazioni e strumenti per creare modelli, che sono costituiti da **mesh**, **trame** e **materiali**. Questa operazione viene quindi salvata in un formato di file che può essere importato o usato dal motore di grafica usato dall'app, ad esempio **. FBX** o **. OBJ**. Tutti gli strumenti che generano un modello supportato dal motore di grafica scelto funzioneranno in **HoloLens**. Tra gli artisti 3D, molti scelgono di usare [Maya di Autodesk perché può usare HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono create le risorse. Se si vuole ottenere un risultato rapido, è anche possibile usare il [Generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) incluso in Windows per l'esportazione. OBJ da usare nell'applicazione.

**Acquisizione oggetti**<br>
È anche possibile acquisire oggetti in 3D. L'acquisizione di oggetti inanimati in 3D e la relativa modifica con il software di creazione di contenuti digitali è sempre più diffusa con la crescita della stampa 3D. Utilizzando il sensore **Kinect 2** e il [Generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) è possibile utilizzare la funzionalità di acquisizione per creare asset da oggetti reali. Si tratta di una [suite di strumenti](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) che consentono di eseguire la stessa operazione con **fotogrammetria** elaborando varie immagini per unire e mesh e trame.

### <a name="purchasing-assets"></a>Acquisti di asset

Un'altra opzione eccellente è quella di acquistare asset per la propria esperienza. Sono disponibili moltissime risorse tramite servizi, ad esempio [Unity Asset Store](https://www.assetstore.unity3d.com/) o [TurboSquid](https://www.turbosquid.com/) , tra gli altri.

Quando si acquistano asset da terze parti, è sempre necessario controllare le proprietà seguenti:
* **Qual è il numero di Poly?**
  * Rientra nel budget?
* **Sono disponibili livelli di dettaglio (LODs) per il modello?**
  * Un livello di dettaglio dei modelli consente di ridimensionare i dettagli di un modello in modo da ottenere prestazioni ottimali.
* **Il file di origine è disponibile?**
  * Non incluso in [Archivio asset Unity](https://www.assetstore.unity3d.com/) ma sempre incluso con servizi come [TurboSquid](https://www.turbosquid.com/).
  * Senza il file di origine, non è possibile modificare l'asset.
  * Verificare che il file di origine fornito possa essere importato dagli strumenti 3D.
* **Scopri cosa stai ricevendo**
  * Sono disponibili animazioni?
  * Assicurarsi di controllare l'elenco dei contenuti dell'asset che si sta acquistando.

### <a name="porting-assets"></a>Porting degli asset

In alcuni casi verranno gestite risorse esistenti originariamente create per altri dispositivi e app diverse. Nella maggior parte dei casi, questi asset possono essere convertiti in formati compatibili con il motore di grafica usato dall'app.

Quando si trasferiscono asset da usare nell'applicazione HoloLens, è necessario porre le domande seguenti:
* **È possibile importare direttamente o è necessario convertirli in un altro formato?** Controllare il formato che si sta importando con il motore grafico in uso.
* **Se la conversione in un formato compatibile è qualcosa di perduto,** Talvolta è possibile che i dettagli vengano persi o che l'importazione possa causare la pulizia degli artefatti in uno strumento di creazione 3D.
* **Qual è il numero di triangolo/poligono per l'asset?** A seconda del budget per l'applicazione, è possibile usare [Simplygon](https://www.simplygon.com/) o strumenti simili per decimare (in modo procedurale o ridurre manualmente il numero di Poly) l'asset originale per adattarsi al budget per le applicazioni.

### <a name="outsourcing-assets"></a>Asset di outsourcing

Un'altra opzione per progetti più grandi che richiedono più risorse rispetto al team è attrezzata per la creazione di asset di origine. Il processo di outsourcing implica la ricerca del giusto studio o agenzia specializzato nell'esternalizzazione degli asset. Questa è l'opzione più costosa, ma è anche la più flessibile per quanto possibile.
* **Definire chiaramente ciò che si sta richiedendo**
  * Fornire il maggior dettaglio possibile
  * Immagini del concetto front, Side e back
  * Arte di riferimento che mostra asset nel contesto
  * Scala dell'oggetto (in genere specificato in centimetri)
* **Fornire un budget**
  * Intervallo conteggio Poly
  * Numero di trame
  * Tipo di shader (per Unity e HoloLens è sempre necessario default per i dispositivi mobili shader)
* **Informazioni sui costi**
  * Quali sono i criteri di outsourcing per le richieste di modifica?

L'outsourcing può funzionare correttamente in base alla sequenza temporale dei progetti, ma richiede una supervisione per garantire che si ottengano le risorse appropriate per la prima volta.
