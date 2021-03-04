---
title: stabilizzazione olografica
description: Prestazioni degli ologrammi in diversi ambienti e condizioni di frequenza dei fotogrammi.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rilevamento dell'ambiente, TMP,
ms.openlocfilehash: a0f0b99cc0d37eb3a3dc4a106aebed389ed5011d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783024"
---
# <a name="hologram-stabilization"></a>Stabilizzazione ologramma

## <a name="performance"></a>Prestazioni

Per ottenere risultati ottimali, è importante che la piattaforma e il dispositivo della realtà mista sottostante ottengano risultati ottimali. Il framerate di destinazione (ad esempio, 60 FPS o 90 FPS) varierà tra le piattaforme e i dispositivi. Tuttavia, le applicazioni di realtà mista che soddisfano la frequenza framerate avranno ologrammi stabili, nonché un rilevamento accurato della testa, il monitoraggio della mano e altro ancora.  

## <a name="environment-tracking"></a>Rilevamento dell'ambiente

Il rendering olografico stabile si basa in modo significativo sul rilevamento della parte principale della piattaforma & dispositivo. Unity eseguirà il rendering della scena per ogni fotogramma dalla fotocamera, che viene stimato e fornito dalla piattaforma sottostante. Se il rilevamento non segue correttamente lo spostamento Head effettivo, gli ologrammi non verranno visualizzati in modo accurato. Questo è particolarmente evidente ed importante per i dispositivi AR come HoloLens, in cui gli utenti possono correlare gli ologrammi virtuali al mondo reale. Le prestazioni sono significative per il rilevamento Head affidabile, ma possono essere presenti anche [altre importanti funzionalità](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens). I tipi di elementi di ambiente che influiscano sull'esperienza utente dipenderanno dalle specifiche della piattaforma di destinazione.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

La piattaforma di realtà mista di Windows fornisce un [materiale di riferimento](https://docs.microsoft.com/windows/mixed-reality/hologram-stability) per la stabilizzazione di ologrammi sulla piattaforma. Sono disponibili alcuni strumenti chiave che possono essere usati dagli sviluppatori per migliorare l'esperienza visiva degli ologrammi per gli utenti.

### <a name="depth-buffer-sharing"></a>Condivisione buffer di profondità

Gli sviluppatori di Unity hanno la possibilità di condividere il buffer di profondità dell'applicazione con la piattaforma. In questo modo vengono fornite informazioni, in cui sono presenti ologrammi per un frame corrente, che la piattaforma può utilizzare per stabilizzare gli ologrammi tramite un processo assistito da hardware noto come Late-Stage riproiezione.

#### <a name="late-stage-reprojection"></a>Riproiezione in fase ritardata

Al termine del rendering di un frame, la piattaforma per la realtà mista di Windows acquisisce le destinazioni di rendering del colore & profondità generate dall'applicazione e trasforma l'output finale della schermata in modo da tenere conto di eventuali movimenti di lieve entità rispetto alla stima dell'ultima posizione. Il ciclo di gioco di un'applicazione richiede tempo per l'esecuzione. Ad esempio, a 60 FPS, significa che l'applicazione sta prendendo ~ 16.667 MS per eseguire il rendering di un frame. Anche se questo può sembrare una quantità di tempo minuscola, la posizione e l'orientamento dell'utente della testa cambieranno con la conseguente generazione di nuove matrici di proiezione per la fotocamera nel rendering. La riproiezione in fase avanzata trasforma i pixel nell'immagine finale per tenere conto di questa nuova prospettiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR piano di stabilizzazione confronto per pixel

A seconda dell'endpoint del dispositivo e della versione del sistema operativo in esecuzione su un dispositivo di realtà mista Windows, l'algoritmo di riproiezione Late-Stage verrà eseguito per pixel o tramite un [piano di stabilizzazione](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Basato sulla profondità per pixel

La riproiezione basata sulla profondità per pixel comporta l'utilizzo del buffer di profondità per modificare l'output dell'immagine per pixel e quindi stabilizzare gli ologrammi a diverse distanze. Una sfera, ad esempio, può trovarsi davanti a un pilastro che è di 10 metri. I pixel che rappresentano la sfera avranno una trasformazione diversa da quella dei pixel lontani che rappresentano la colonna se l'utente ha inclinato leggermente la testa. La riproiezione per pixel prenderà in considerazione questa differenza di distanza in ogni pixel per una riproiezione più accurata.

##### <a name="stabilization-plane"></a>Piano di stabilizzazione

Se non è possibile creare un buffer di profondità preciso da condividere con la piattaforma, un altro tipo di LSR usa un piano di stabilizzazione. Tutti gli ologrammi in una scena riceveranno una certa stabilizzazione, ma gli ologrammi che si trovano nel piano desiderato riceveranno la massima stabilizzazione hardware. Il punto e il normale per il piano possono essere forniti alla piattaforma tramite l'API *HolographicSettings. SetFocusPointForFrame* [fornita da Unity](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity).

#### <a name="depth-buffer-format"></a>Formato buffer profondità

Se la destinazione è HoloLens per lo sviluppo, è consigliabile utilizzare il formato di buffer di profondità a 16 bit rispetto a 24 bit. Questo può risparmiare notevolmente sulle prestazioni anche se i valori di profondità avranno una minore precisione. Per compensare la precisione inferiore ed evitare il superamento della [z](https://en.wikipedia.org/wiki/Z-fighting), è consigliabile ridurre il [piano di ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) dal valore predefinito di 1000 m impostato da Unity.

> [!NOTE]
> Se si utilizza il *formato di profondità a 16 bit*, gli effetti necessari sul buffer dello stencil non funzioneranno perché [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il *formato di profondità a 24 bit* , in genere viene creato un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html), se applicabile sulla piattaforma grafica dell'endpoint.

#### <a name="depth-buffer-sharing-in-unity"></a>Condivisione del buffer di profondità in Unity

Per usare LSR basati sulla profondità, è necessario eseguire due passaggi importanti.

1. In **modifica**  >  **Impostazioni progetto**  >  **lettore**  >  **XR impostazioni**  >  **SDK realtà virtuale** > Abilita **condivisione buffer di profondità**
    1. Se la destinazione è HoloLens, è consigliabile selezionare anche il **formato di profondità a 16 bit** .
1. Quando si esegue il rendering del colore sullo schermo, viene visualizzato anche il livello di profondità

Il [GameObject opaco](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity verrà in genere scritto in profondità automaticamente. Tuttavia, per impostazione predefinita, gli oggetti di testo Transparent & non vengono in genere scritti in profondità. Se si usa MRTK standard shader o text mesh Pro, questo può essere facilmente risolvibile.

> [!NOTE]
> Per determinare rapidamente quali oggetti di una scena non scrivono visivamente il buffer di profondità, è possibile usare l'utilità di [ *rendering del buffer di profondità*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) sotto le impostazioni dell' *Editor* nel profilo di configurazione MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Shader standard MRTK trasparente

Per i materiali Transparent con lo [shader standard MRTK](../features/rendering/MRTK-standard-shader.md), selezionare il materiale da visualizzare nella finestra di *controllo* . Fare quindi clic sul pulsante *Correggi ora* per convertire il materiale in scrittura in profondità, ad esempio Z-Write on).

Prima

![Buffer di profondità prima della correzione dello shader standard MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

After

![Shader MRTK standard fisso buffer di profondità](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Testo mesh Pro

Per oggetti di rete di testo, selezionare il GameObject TMP da visualizzare nel controllo. Nel componente materiale passare allo shader per il materiale assegnato per usare lo shader TextMeshPro di MRTK.

![Correzione buffer profondità Pro mesh di testo](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Shader personalizzato

Se si scrive uno shader personalizzato, aggiungere il [flag ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) all'inizio della definizione del blocco *pass* per configurare lo shader per la scrittura nel buffer di profondità.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>Backup opachi

Se i metodi precedenti non funzionano per uno scenario specifico, ad esempio usando l'interfaccia utente di Unity, è possibile che un altro oggetto scriva nel buffer di profondità. Un esempio comune è l'uso del testo dell'interfaccia utente di Unity su un pannello mobile in una scena. Rendendo il pannello opaco o almeno scrivendo in profondità, il testo & il pannello verrà stabilizzato dalla piattaforma perché i valori z sono così vicini tra loro.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Oltre a garantire che siano soddisfatte le configurazioni corrette per garantire la stabilità visiva, è importante assicurarsi che gli ologrammi rimangano stabili nei percorsi fisici corretti. Per informare la piattaforma su posizioni importanti in uno spazio fisico, gli sviluppatori possono sfruttare [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) in GameObject che devono rimanere in un'unica posizione. Un [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) è un componente aggiunto a un GameObject che assume il controllo assoluto sulla trasformazione di tale oggetto.

I dispositivi, ad esempio HoloLens, eseguono costantemente l'analisi e l'apprendimento dell'ambiente. Di conseguenza, poiché il HoloLens tiene traccia dello spostamento & posizione nello spazio, le stime verranno aggiornate e il [sistema di coordinate Unity verrà regolato](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity). Ad esempio, se un GameObject viene posizionato 1m dalla fotocamera all'avvio, poiché il HoloLens tiene traccia dell'ambiente, può realizzare il punto fisico in cui si trova la GameObject è effettivamente 1,1 m. Questo comporterebbe la dispersione dell'ologramma. L'applicazione di un WorldAnchor a una GameObject consentirà all'ancoraggio di controllare la trasformazione dell'oggetto in modo che l'oggetto rimanga nella posizione fisica corretta, ad esempio eseguire l'aggiornamento a 1,1 m, anziché 1 milione al runtime. Per salvare in modo permanente [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) tra le sessioni dell'app, gli sviluppatori possono usare il [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) per [salvare e caricare WorldAnchors](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity).

> [!NOTE]
> Una volta aggiunto un componente WorldAnchor a un GameObject, non è possibile modificare la trasformazione di GameObject (ad esempio Transform. Position = x). Uno sviluppatore deve rimuovere WorldAnchor per modificare la trasformazione.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

## <a name="see-also"></a>Vedere anche

- [Prestazioni](../performance/perf-getting-started.md)
- [Considerazioni sull'ambiente per HoloLens](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens)
- [Realtà mista di Windows per la stabilità olografica](https://docs.microsoft.com/windows/mixed-reality/hologram-stability)
- [Punto focale in Unity](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity)
- [Sistemi di coordinate in Unity](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistenza in Unity](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity)
- [Informazioni sulle prestazioni per la realtà mista](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Consigli sulle prestazioni per Unity](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
