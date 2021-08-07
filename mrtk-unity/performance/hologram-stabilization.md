---
title: Stabilizzazione dell'ologramma
description: Prestazioni degli ologrammi in condizioni di ambiente e frequenza fotogrammi diverse.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rilevamento dell'ambiente, TMP,
ms.openlocfilehash: 48841ee02e5208dcf8363b62c03415797017215c3a52231b3417103978ffc66e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213430"
---
# <a name="hologram-stabilization"></a>Stabilizzazione dell'ologramma

## <a name="performance"></a>Prestazioni

Per consentire alla piattaforma e al dispositivo di realtà mista sottostanti di produrre risultati ottimali, è importante ottenere la frequenza dei fotogrammi. Il framerate di destinazione (ad esempio, 60 FPS o 90 FPS) varia a seconda delle piattaforme e dei dispositivi. Tuttavia, le applicazioni di realtà mista che incornicieranno framerate avranno ologrammi stabili, oltre a un efficiente rilevamento della testa, al tracciamento delle mani e altro ancora.  

## <a name="environment-tracking"></a>Rilevamento dell'ambiente

Il rendering olografico stabile si basa molto sul rilevamento della posizione della testa da parte della piattaforma & dispositivo. Unity eseguirà il rendering della scena di ogni fotogramma dalla posizione della fotocamera stimata e fornita dalla piattaforma sottostante. Se questo rilevamento non segue correttamente lo spostamento effettivo della testa, gli ologrammi appariranno visivamente non accurati. Ciò è particolarmente evidente e importante per i dispositivi ar come HoloLens in cui gli utenti possono correlare gli ologrammi virtuali al mondo reale. Le prestazioni sono significative per il rilevamento head affidabile, ma possono essere presenti [anche](/windows/mixed-reality/environment-considerations-for-hololens)altre importanti funzionalità. I tipi di elementi dell'ambiente che influiscono sull'esperienza utente dipendono dalle specifiche della piattaforma di destinazione.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

La Windows Mixed Reality fornisce un materiale [di riferimento per](/windows/mixed-reality/hologram-stability) la stabilizzazione degli ologrammi nella piattaforma. Esistono tuttavia alcuni strumenti chiave che gli sviluppatori possono usare per migliorare l'esperienza visiva degli ologrammi per gli utenti.

### <a name="depth-buffer-sharing"></a>Condivisione buffer di profondità

Gli sviluppatori unity hanno la possibilità di condividere il buffer di profondità dell'applicazione con la piattaforma. In questo modo vengono fornite informazioni, in cui sono presenti ologrammi per un frame corrente, che la piattaforma può usare per stabilizzare gli ologrammi tramite un processo assistito dall'hardware noto come Late-Stage reproiezione.

#### <a name="late-stage-reprojection"></a>Riprogettazione in fase finale

Al termine del rendering di un frame, la piattaforma Windows Mixed Reality accetta il colore & destinazioni di rendering di profondità prodotte dall'applicazione e trasforma l'output dello schermo finale per conto di qualsiasi leggero spostamento della testa dall'ultima stima della posizione della testa. L'esecuzione del ciclo di gioco di un'applicazione richiede tempo. Ad esempio, a 60 FPS, ciò significa che l'applicazione sta prendendo ~16.667 ms per eseguire il rendering di un frame. Anche se può sembrare una quantità di tempo minima, la posizione e l'orientamento dell'utente della testa cambieranno, determinando nuove matrici di proiezione per la fotocamera nel rendering. La riproiezione in fase tardiva trasforma i pixel nell'immagine finale per conto di questa nuova prospettiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR per pixel rispetto al piano di stabilizzazione

A seconda dell'endpoint del dispositivo e della versione del sistema operativo in esecuzione in un dispositivo Windows Mixed Reality, l'algoritmo Late-Stage Reprojection verrà eseguito per pixel o tramite un piano [di stabilizzazione](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Basata sulla profondità per pixel

La riproiezione basata sulla profondità per pixel comporta l'uso del buffer di profondità per modificare l'output dell'immagine per pixel e quindi stabilizzare gli ologrammi a varie distanze. Ad esempio, una sfera a 1 m di distanza può essere davanti a un pilastro a 10 metri di distanza. I pixel che rappresentano la sfera avranno una trasformazione diversa rispetto ai pixel più lontani che rappresentano il pilastro se l'utente ha leggermente inclinato la testa. La riproiezione per pixel prenderà in considerazione questa differenza di distanza in ogni pixel per una riprogettazione più accurata.

##### <a name="stabilization-plane"></a>Piano di stabilizzazione

Se non è possibile creare un buffer di profondità accurato da condividere con la piattaforma, un'altra forma di LSR usa un piano di stabilizzazione. Tutti gli ologrammi in una scena riceveranno una certa stabilizzazione, ma gli ologrammi che si trovano nel piano desiderato riceveranno la stabilizzazione hardware massima. Il punto e la normale per il piano possono essere forniti alla piattaforma tramite l'API *HolographicSettings.SetFocusPointForFrame* [fornita da Unity.](/windows/mixed-reality/focus-point-in-unity)

#### <a name="depth-buffer-format"></a>Formato del buffer di profondità

Se la destinazione HoloLens per lo sviluppo, è consigliabile usare il formato buffer di profondità a 16 bit rispetto a 24 bit. Ciò consente di risparmiare molto sulle prestazioni, anche se i valori di profondità avranno una precisione inferiore. Per compensare la precisione inferiore ed evitare [lo z-fighting,](https://en.wikipedia.org/wiki/Z-fighting)è consigliabile ridurre il piano di [ritaglio](https://docs.unity3d.com/Manual/class-Camera.html) lontano dal valore predefinito di 1000 metri impostato da Unity.

> [!NOTE]
> Se si usa un formato di profondità a *16 bit,* gli effetti necessari per il buffer di stencil non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html)se applicabile nella piattaforma grafica dell'endpoint.

#### <a name="depth-buffer-sharing-in-unity"></a>Condivisione del buffer di profondità in Unity

Per usare l'LSR basato sulla profondità, gli sviluppatori devono eseguire due passaggi importanti.

1. In **Edit**  >  **Project Impostazioni**  >  **Player**  >  **XR Impostazioni** Virtual Reality  >  **SDK** > Enable Depth Buffer **Sharing**
    1. Se la destinazione HoloLens, è consigliabile selezionare anche il formato di profondità **a 16 bit.**
1. Quando si esegue il rendering del colore sullo schermo, anche la profondità di rendering

[Gli oggetti GameObject opachi](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity in genere scrivono automaticamente in profondità. Tuttavia, per impostazione & gli oggetti di testo trasparenti non scrivono in profondità per impostazione predefinita. Se si usa lo shader standard MRTK o la mesh Pro testo, è possibile risolvere questo problema facilmente.

> [!NOTE]
> Per determinare rapidamente gli oggetti di una scena che non scrivono visivamente nel  buffer di profondità, è possibile usare l'utilità Buffer di profondità di rendering nel Impostazioni Editor nel profilo di configurazione MRTK. [  ](../configuration/mixed-reality-configuration-guide.md#editor-utilities)

##### <a name="transparent-mrtk-standard-shader"></a>Shader MRTK Standard trasparente

Per i materiali trasparenti che [usano lo shader MRTK Standard,](../features/rendering/MRTK-standard-shader.md)selezionare il materiale per visualizzarlo nella *finestra Inspector (Controllo).* Fare quindi clic *sul pulsante Correggi* ora per convertire il materiale in modo da scrivere in profondità,ad esempio Z-Write On).

Prima

![Buffer di profondità prima di correggere lo shader standard MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

After

![Buffer di profondità fisso MRTK Standard Shader](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Mesh di testo Pro

Per Text Mesh Pro oggetti, selezionare TMP GameObject per visualizzarlo nel controllo. Nel componente materiale, cambiare lo shader per il materiale assegnato per usare lo shader TextMeshPro MRTK.

![Correzione del buffer Pro mesh di testo](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Shader personalizzato

Se si scrive uno shader personalizzato, aggiungere il [flag ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) all'inizio della definizione del blocco *Pass* per configurare lo shader per la scrittura nel buffer di profondità.

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

Se i metodi precedenti non funzionano per un determinato scenario ,ad esempio usando l'interfaccia utente di Unity, è possibile fare in modo che un altro oggetto scrivo nel buffer di profondità. Un esempio comune è l'uso del testo dell'interfaccia utente di Unity in un pannello mobile in una scena. Rendendo il pannello opaco o almeno scrivendo in profondità, entrambi i valori del testo & il pannello verranno stabilizzati dalla piattaforma perché i valori z sono così vicini l'uno all'altro.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Oltre a garantire che siano soddisfatte le configurazioni corrette per garantire la stabilità visiva, è importante assicurarsi che gli ologrammi rimangano stabili nelle posizioni fisiche corrette. Per informare la piattaforma su posizioni importanti in uno spazio fisico, gli sviluppatori possono sfruttare [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) su GameObject che devono rimanere in un'unica posizione. [WorldAnchor è](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) un componente aggiunto a un GameObject che assume il controllo assoluto sulla trasformazione dell'oggetto.

I dispositivi come HoloLens vengono costantemente a conoscenza dell'ambiente. Di conseguenza, man HoloLens tiene traccia & posizione nello spazio, le stime verranno aggiornate e il sistema [di coordinate Unity regolato](/windows/mixed-reality/coordinate-systems-in-unity). Ad esempio, se un GameObject viene posizionato a 1 m dalla fotocamera all'inizio, poiché il HoloLens tiene traccia dell'ambiente, può rendersi conto che il punto fisico in cui si trova GameObject è effettivamente a 1,1 m di distanza. Ciò comporta la deriva dell'ologramma. L'applicazione di un oggetto WorldAnchor a un GameObject consentirà all'ancoraggio di controllare la trasformazione dell'oggetto in modo che rimanga nella posizione fisica corretta , ad esempio eseguire l'aggiornamento a 1,1 m anziché a 1 m in fase di esecuzione. Per salvare [in modo permanente WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) tra le sessioni dell'app, gli sviluppatori possono usare [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) per salvare e caricare [WorldAnchors.](/windows/mixed-reality/persistence-in-unity)

> [!NOTE]
> Dopo l'aggiunta di un componente WorldAnchor a un GameObject, non è possibile modificare la trasformazione di tale GameObject(ad esempio, transform.position = x). Uno sviluppatore deve rimuovere WorldAnchor per modificare la trasformazione.

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

Se si vuole un'alternativa all'uso manuale degli ancoraggi, vedere Microsoft World Locking Tools. 

> [!div class="nextstepaction"]
> [Eseguire l'installazione con lo strumento di funzionalità MR](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Vedere anche

- [Prestazioni](../performance/perf-getting-started.md)
- [Considerazioni sull'ambiente per HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Ologramma Stability Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Punto focale in Unity](/windows/mixed-reality/focus-point-in-unity)
- [Sistemi di coordinate in Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistenza in Unity](/windows/mixed-reality/persistence-in-unity)
- [Informazioni sulle prestazioni per la realtà mista](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Consigli sulle prestazioni per Unity](/windows/mixed-reality/performance-recommendations-for-unity)
