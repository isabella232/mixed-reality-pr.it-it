---
title: Creare modelli 3D per l'uso nello spazio iniziale
description: Requisiti degli asset e linee guida per la creazione di modelli 3D da usare nella home page Windows Mixed Reality su visori HoloLens e vr immersivi.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modellazione, linee guida per la modellazione, requisiti di asset, linee guida per la creazione, utilità di avvio, utilità di avvio 3D, trama, materiali, complessità, triangoli, mesh, poligoni, polycount, limiti, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207681"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Creare modelli 3D per l'uso nello spazio iniziale

La [Windows Mixed Reality home è](../discover/navigating-the-windows-mixed-reality-home.md) il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni. Quando si progetta l'applicazione Windows Mixed Reality visori, usare un modello [3D](implementing-3d-app-launchers.md) come icona di avvio delle app e inserire collegamenti diretti [3D](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)nella Windows Mixed Reality home page. Questo articolo illustra le linee guida per la creazione di modelli 3D compatibili con la Windows Mixed Reality home page.

## <a name="asset-requirements-overview"></a>Panoramica dei requisiti degli asset

Quando si creano modelli 3D per Windows Mixed Reality, tutti gli asset devono soddisfare alcuni requisiti: 
1. [Esportazione:](#exporting-models) gli asset devono essere recapitati nel formato di file con estensione glb (glTF binario)
2. [Modellazione:](#modeling-guidelines) gli asset devono essere inferiori a 10.000 triangoli, non devono avere più di 64 nodi e 32 sottomesi per ogni LOD
3. [Materiali:](#material-guidelines) le trame non possono essere maggiori di 4096 x 4096 e la mappa mip più piccola non deve essere maggiore di 4 in entrambe le dimensioni
4. [Animazione:](#animation-guidelines) le animazioni non possono essere più lunghe di 20 minuti a 30 FPS (36.000 fotogrammi chiave) e devono contenere <= 8192 vertici di destinazione morphing
5. [Ottimizzazione:](#optimizations) gli asset devono essere ottimizzati usando [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). *Obbligatorio Windows versioni del sistema <= 1709** e consigliato Windows versioni del sistema operativo >= 1803

Il resto di questo articolo include una panoramica dettagliata di questi requisiti e linee guida aggiuntive per garantire che i modelli funzionino correttamente con la Windows Mixed Reality home. 

## <a name="detailed-guidance"></a>Indicazioni dettagliate

### <a name="exporting-models"></a>Esportazione di modelli

La Windows Mixed Reality prevede che gli asset 3D siano recapitati usando il formato di file con estensione glb con immagini incorporate e dati binari. Glb è la versione binaria del formato glTF, uno standard aperto gratuito per la distribuzione di asset 3D gestito dal gruppo Khronos. Con l'evolversi di glTF come standard di settore per i contenuti 3D interoperativi, microsoft supporterà il formato tra app ed esperienze Windows di lavoro. Se non è stato creato un asset glTF prima di trovare un elenco di convertitori e esportatori supportati, vedere la pagina github del gruppo di lavoro glTF. [](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)  

### <a name="modeling-guidelines"></a>Linee guida per la modellazione

Windows che gli asset siano generati usando le linee guida di modellazione seguenti per garantire la compatibilità con l'esperienza home di realtà mista. Quando si esegue la modellazione nel programma preferito, tenere presenti le raccomandazioni e le limitazioni seguenti:
1. L'asse Su deve essere impostato su "Y".
2. L'asset deve essere "in avanti" verso l'asse Z positivo.
3. Tutti gli asset devono essere compilati sul piano terra all'origine della scena (0,0,0)
4. Le unità di lavoro devono essere impostate su metri e asset in modo che gli asset possano essere creati su scala globale
5. Non è necessario combinare tutte le mesh, ma è consigliabile scegliere come destinazione i dispositivi con risorse vincolate
6. Tutte le mesh devono condividere un solo materiale, con un solo set di trame usato per l'intero asset
7. Gli UV devono essere disposti in una disposizione quadrata nello spazio 0-1. Evitare trame di affiancamento anche se sono consentite.
8. I multi-UV non sono supportati
9. I materiali a doppio lato non sono supportati

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Conteggi dei triangoli e livelli di dettaglio (LOD)

La Windows Mixed Reality home non supporta modelli con più di 10.000 triangoli. È consigliabile triangolare le mesh prima dell'esportazione per assicurarsi che non superino questo numero. Windows MR supporta anche livelli di dettaglio (LOD) facoltativi per garantire un'esperienza performante e di alta qualità. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) consente di combinare 3 versioni del modello in un singolo modello con estensione glb. Windows determina il lod da visualizzare in base alla quantità di spazio su schermo utilizzato dal modello. Sono supportati solo 3 livelli LOD con i conteggi dei triangoli consigliati seguenti:
<br>

|  Livello LOD  |  Conteggio triangoli consigliato  |  Numero massimo triangoli | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5\.000  |  10,000 | 
|  LOD 2 |  2\.500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Conteggi dei nodi e limiti dei sottomesh

La Windows Mixed Reality home non supporta modelli con più di 64 nodi o 32 sottomesi per loD. I nodi sono un concetto nella [specifica glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) che definisce gli oggetti nella scena. Le sottomeshe sono definite nella matrice di [primitive](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) nella mesh nell'oggetto . 

|  Funzionalità |  Descrizione  |  Numero massimo supportato | Documentazione |
|------|------|------|------|
|  Nodi |  Oggetti nella scena glTF |  64 per loD | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Sottomeshe |  Somma delle primitive in tutte le mesh |  32 per loD | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Linee guida per i materiali

Le trame devono essere preparate usando un flusso di lavoro PBR metal roughness. Per iniziare, creare un set completo di trame, tra cui Albedo, Normal, Occlusion, Metallic e Roughness. Windows Mixed Reality supporta trame con risoluzioni fino a 4096x4096, ma è consigliabile creare 512x512. Le trame devono essere scritte in risoluzioni in multipli di 4. Si tratta di un requisito per il formato di compressione applicato alle trame nei passaggi di esportazione descritti di seguito. Quando si generano mappe mip o una trama, il mip più basso deve essere un massimo di 4x4.
<br>

|  Dimensioni trame consigliate  |  Dimensioni massime trama | Mip più basso
|----|----|----|
|  512x512  |  4096x4096 | max 4x4|

### <a name="albedo-base-color-map"></a>Mappa albedo (colore di base)

Colore non elaborato senza informazioni sull'illuminazione. Questa mappa contiene anche le informazioni di riflessione e diffusione rispettivamente per le superfici di metallo (bianco nella mappa metallica) e isolante (nero nella mappa metallica).

### <a name="normal"></a>Normale

Mappa normale dello spazio tangente

### <a name="roughness-map"></a>Mappa di ruvidità

Descrive il microsurface dell'oggetto . White 1.0 è rough Black 0.0 è smooth. Questa mappa offre all'asset il maggior numero di caratteri, in quanto descrive realmente la superficie. Ad esempio, scratch, impronte digitali, sbavature, morfine e così via.

### <a name="ambient-occlusion-map"></a>Mappa dell'occlusione di ambiente

Mappa della scala dei valori che mostra le aree di luce occlusa, che blocca i riflessi

### <a name="metallic-map"></a>Mappa metallica

Indica allo shader se qualcosa è in metallo o meno. Raw Metal = 1,0 bianco non in metallo = 0,0 nero. Possono essere presenti valori grigi di transizione che indicano qualcosa che copre il metallo non elaborato, ad esempio lo sterrato, ma in generale questa mappa deve essere solo in bianco e nero.

## <a name="optimizations"></a>Ottimizzazioni

Windows Mixed Reality home offre una serie di ottimizzazioni oltre alla specifica glTF di base definita tramite estensioni personalizzate. Queste ottimizzazioni sono necessarie Windows versioni <= 1709 e consigliate nelle versioni più recenti di Windows. È possibile ottimizzare facilmente qualsiasi modello glTF 2.0 usando [Windows Mixed Reality Asset Converter disponibile in GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Questo strumento eseguirà le ottimizzazioni e i packing delle trame corretti, come specificato di seguito. Per l'utilizzo generale, è consigliabile usare WindowsMRAssetConverter, ma se è necessario un maggiore controllo sull'esperienza e si vuole creare una pipeline di ottimizzazione personalizzata, è possibile fare riferimento alla specifica dettagliata riportata di seguito.  

> [!NOTE]
> Per un elenco definitivo delle possibilità per i limiti esatti del modello, vedere l'articolo ottimizzazione del modello [3D](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) per l'uso nelle applicazioni Dynamics 365.

### <a name="materials"></a>Materiali

Per migliorare il tempo di caricamento degli asset negli ambienti di realtà mista Windows MR supporta il rendering di trame DDS compresse compresse in base alla combinazione di trame definita in questa sezione. Le trame DDS vengono referenziati [usando l'MSFT_texture_dds.](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds) La compressione delle trame è altamente consigliata. 

#### <a name="hololens"></a>HoloLens

HoloLens esperienze di realtà mista basate su standard prevedono che le trame siano imballate usando una configurazione a 2 trame usando la specifica di pacchetto seguente:
<br>

|  Proprietà glTF  |  Trama  |  Schema di pacchetto | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), Verde (G), Blu (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normale (RG), Roughness (B), Metallico (A) | 


Quando si comprimono le trame DDS, è prevista la compressione seguente in ogni mappa:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Visori vr immersivi

Le esperienze di Windows Mixed Reality basate su PC per visori VR immersive prevedono la creazione di un pacchetto di trame usando una configurazione a 3 trame usando la specifica di pacchetto seguente:

##### <a name="windows-os--1803"></a>Windows Sistema operativo >= 1803

<br>

|  Proprietà glTF  |  Trama  |  Schema di pacchetto | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), Verde (G), Blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusione (R), Roughness (G), Metal (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprimono le trame DDS, è prevista la compressione seguente in ogni mappa:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows Sistema operativo <= 1709
<br>

|  Proprietà glTF  |  Trama  |  Schema di pacchetto | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), Verde (G), Blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R), Metallic (G), Occlusion (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprimono le trame DDS, è prevista la compressione seguente in ogni mappa:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Aggiunta di LOD mesh

Windows MR usa i LOD dei nodi geometry per eseguire il rendering dei modelli 3D in diversi livelli di dettaglio a seconda della copertura sullo schermo. Sebbene questa funzionalità non sia tecnicamente necessaria, è consigliabile per tutti gli asset. Attualmente Windows supporta 3 livelli di dettaglio. Il lod predefinito è 0, che rappresenta la qualità più elevata. Altri LOD sono numerati in sequenza, ad esempio 1, 2 e ottengono una qualità progressivamente inferiore. Il [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) supporta la generazione di asset che soddisfano questa specifica LOD accettando più modelli glTF e unendoli in un singolo asset con livelli loD validi. La tabella seguente illustra le destinazioni previste per l'ordinamento del lod e il triangolo:
<br>

|  Livello LOD  |  Conteggio triangoli consigliato  |  Numero massimo triangoli | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5\.000  |  10,000 | 
|  LOD 2 |  2\.500  |  10,000 | 

Quando si usano i lod, specificare sempre 3 livelli loD. I LOD mancanti causeranno il rendering imprevisto del modello quando il sistema lod passa al livello lod mancante. glTF 2.0 attualmente non supporta i LOD come parte della specifica core. I LOD devono essere definiti usando [l'estensione MSFT_LOD .](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)

### <a name="screen-coverage"></a>Copertura dello schermo

I LOD vengono visualizzati in Windows Mixed Reality in base a un sistema basato sul valore di copertura dello schermo impostato su ogni LOD. Gli oggetti che attualmente utilizzano una parte più ampia dello spazio dello schermo vengono visualizzati a un livello loD superiore. La copertura dello schermo non fa parte della specifica core glTF 2.0 e deve essere specificata usando MSFT_ScreenCoverage nella sezione "extra" [dell'estensione](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)MSFT_lod .
<br>

|  Livello LOD  |  Intervallo consigliato  |  Intervallo predefinito | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  0,5 | 
|  LOD 1 |  Inferiore al 50% - 20%  |  0,2 | 
|  LOD 2 |  Sotto il 20% - 1%  |  0.01 | 
|  LOD 4  |  Inferiore all'1%  |  - | 

## <a name="animation-guidelines"></a>Linee guida per l'animazione

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte [dell'Windows 10 di aprile 2018.](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) Nelle versioni precedenti di Windows queste animazioni non verranno riprodotte, ma verranno comunque caricate se sono stati creati in base alle linee guida di questo articolo.  

Il ambiente iniziale supporta oggetti glTF animati HoloLens visori VR immersive. Se si vogliono attivare animazioni nel modello, è necessario usare l'estensione Mappa di animazione nel formato glTF. Questa estensione consente di attivare animazioni nel modello glTF in base alla presenza dell'utente nel mondo, ad esempio attivare un'animazione quando l'utente è vicino all'oggetto o mentre lo guarda. Se l'oggetto glTF contiene animazioni, ma non definisce trigger, le animazioni non verranno riprodotte. La sezione seguente descrive un flusso di lavoro per l'aggiunta di questi trigger a qualsiasi oggetto glTF animato.

### <a name="tools"></a>Strumenti

Prima di tutto, scaricare gli strumenti seguenti, se non sono già disponibili. Questi strumenti semplificano l'apertura di qualsiasi modello glTF, l'anteprima, l'applicazione di modifiche e il salvataggio come glTF o glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [GlTF Tools per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Apertura e anteprima del modello

Per iniziare, aprire il modello glTF in VSCode trascinando il file con estensione glTF nella finestra dell'editor. Se si ha un file con estensione glb invece di un file con estensione glTF, è possibile importarlo in VSCode usando il componente aggiuntivo glTF Tools scaricato. Passare a "Visualizza -> riquadro comandi" e quindi iniziare a digitare "glTF" nel riquadro comandi e selezionare "glTF: Import from glb", che aprirà una selezione file con cui importare un file con estensione glb. 

Dopo aver aperto il modello glTF, il codice JSON dovrebbe essere visualizzato nella finestra dell'editor. È anche possibile visualizzare in anteprima il modello in un visualizzatore 3D live usando facendo clic con il pulsante destro del mouse sul nome del file e selezionando il collegamento di comando "glTF: Preview 3D Model" (glTF: Anteprima modello 3D) dal menu di scelta rapida. 

### <a name="adding-the-triggers"></a>Aggiunta dei trigger

I trigger di animazione vengono aggiunti al codice JSON del modello glTF usando l'estensione mappa di animazione. L'estensione della mappa di animazione è documentata pubblicamente qui [GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (NOTA: SI TRATTA DI UN'ESTENSIONE BOZZA). Per aggiungere l'estensione al modello, scorrere fino alla fine del file glTF nell'editor e aggiungere il blocco "extensionsUsed" e "extensions" al file, se non esistono già. Nella sezione "extensionsUsed" si aggiungerà un riferimento all'estensione "EXT_animation_map" e nel blocco "extensions" si aggiungeranno i mapping alle animazioni nel modello.

Come specificato nella specifica, si definisce ciò che attiva l'animazione usando la stringa "semantica" [in](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) un elenco di "animazioni", ovvero una matrice di indici di animazione. Nell'esempio seguente è stata specificata l'animazione da riprodurre mentre l'utente guarda l'oggetto:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
La semantica dei trigger di animazione seguente è supportata dal Windows Mixed Reality home page.  
* "ALWAYS": ciclo continuo di un'animazione
* "HELD": ciclo durante l'intera durata in cui un oggetto viene afferrato.
* "GAZE": ciclo durante la ricerca di un oggetto
* "PROXIMITY": ciclo mentre un visualizzatore è vicino a un oggetto
* "POINTING": ciclo mentre un utente punta a un oggetto

### <a name="saving-and-exporting"></a>Salvataggio ed esportazione

Dopo aver apportato le modifiche al modello glTF, è possibile salvarlo direttamente come glTF. È anche possibile fare clic con il pulsante destro del mouse sul nome del file nell'editor e scegliere "glTF: Export to GLB (binary file)" (glTF: Esporta in GLB (file binario)) per esportare un file con estensione glb. 

### <a name="restrictions"></a>Restrizioni

Le animazioni non possono essere più lunghe di 20 minuti e non possono contenere più di 36.000 fotogrammi chiave (20 minuti a 30 FPS). Inoltre, quando si usano animazioni basate su destinazione morph non superano o meno 8192 vertici di destinazione di morphing. Se si superano questi conteggi, l'asset animato non sarà supportato nella Windows Mixed Reality home. 

|Funzionalità|Massimo|
|-----|-----|
|Durata|20 minuti|
|Fotogrammi chiave|36,000| 
|Morph Target Vertices|8192|

## <a name="gltf-implementation-notes"></a>Note sull'implementazione di glTF

Windows MR non supporta il capovolgimento della geometria usando scale negative. La geometria con scale negative probabilmente avrà come risultato artefatti visivi.

L'asset glTF DEVE puntare alla scena predefinita usando l'attributo della scena di cui eseguire il rendering Windows MR. Inoltre, il Windows mr glTF prima [dell'aggiornamento Windows 10 aprile 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) **richiede funzioni** di accesso:
* Deve avere valori minimo e massimo.
* Il tipo SCALAR deve essere componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* I tipi VEC2 e VEC3 devono essere componentType FLOAT (5126).

Le proprietà materiali seguenti vengono usate dalla specifica core glTF 2.0, ma non obbligatorie:
* baseColorFactor, metalFactor, roughnessFactor
* baseColorTexture: deve puntare a una trama archiviata in dds.
* emissiveTexture: deve puntare a una trama archiviata in dds.
* emissiveFactor
* alphaMode

Le proprietà material seguenti vengono ignorate dalla specifica core:
* Tutti i multi-UV
* metalRoughnessTexture: deve usare invece la creazione di un pacchetto di trame ottimizzato Microsoft definito di seguito
* normalTexture: deve usare invece la creazione di un pacchetto di trame ottimizzato Microsoft definito di seguito
* normalScale
* occlusionTexture: deve usare invece la creazione di un pacchetto di trama ottimizzato Microsoft definito di seguito
* occlusionStrength

Windows MR non supporta linee e punti in modalità primitiva. 

È supportato un solo attributo vertice UV.

## <a name="more-resources"></a>Altre risorse

* [GlTF Exporters and Converters](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [GlTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [Specifica glTF 2.0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Specifica dell'estensione LOD Microsoft glTF](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Specifica delle estensioni per il pacchetto di trame di realtà mista per PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Specifica delle estensioni per il pacchetto di trame di realtà mista](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Specifica delle estensioni glTF di Microsoft DDS Textures](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Vedi anche

* [Implementare utilità di avvio per app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare utilità di avvio per app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)