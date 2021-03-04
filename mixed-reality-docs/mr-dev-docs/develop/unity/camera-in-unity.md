---
title: Fotocamera in Unity
description: Informazioni su come configurare e usare la fotocamera principale di Unity per lo sviluppo di realtà mista di Windows per eseguire il rendering olografico.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, rendering olografico, olografico, immersivo, punto di messa a fuoco, buffer di profondità, solo orientamento, posizionale, opaco, trasparente, clip, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 865d19482e5f612eab95fa2f74cb2bad59171496
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759767"
---
# <a name="camera-in-unity"></a>Fotocamera in Unity

Quando si usa una cuffia a realtà mista, diventa il centro del mondo olografico. Il componente della [fotocamera](https://docs.unity3d.com/Manual/class-Camera.html) Unity gestirà automaticamente il rendering stereoscopico e seguirà lo spostamento e la rotazione del titolo. Tuttavia, per ottimizzare completamente la qualità visiva e la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md), è necessario impostare le impostazioni della fotocamera descritte di seguito.

## <a name="setup"></a>Configurazione

1. Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**
2. Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity
3. Selezione della **realtà virtuale supportata**

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma le impostazioni non sono state applicate correttamente.

## <a name="holographic-vs-immersive-headsets"></a>Cuffie olografiche rispetto a quelle immersive

Le impostazioni predefinite nel componente della fotocamera Unity sono per le applicazioni 3D tradizionali, che richiedono uno sfondo SKYBOX, perché non hanno un mondo reale.

* Quando si esegue un' **[auricolare immersiva](../../discover/immersive-headset-hardware-details.md)**, si esegue il rendering di tutti gli elementi che l'utente vede, quindi è probabile che si desideri proteggere skybox.
* Tuttavia, quando si esegue un **auricolare olografico** come [HoloLens](/hololens/hololens1-hardware), il mondo reale dovrebbe apparire dietro tutto il rendering della fotocamera. Impostare lo sfondo della fotocamera come trasparente (in HoloLens, il nero viene visualizzato come trasparente) invece di una trama skybox:
    1. Selezionare la fotocamera principale nel pannello gerarchia
    2. Nel pannello Inspector trovare il componente della fotocamera e modificare l'elenco a discesa Clear Flags da skybox a Solid Color.
    3. Selezionare la selezione dei colori di sfondo e modificare i valori di RGBA in (0, 0, 0, 0)

È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).

## <a name="positioning-the-camera"></a>Posizionamento della fotocamera

Il layout dell'app sarà più semplice se si immagina la posizione iniziale dell'utente come (X: 0, Y: 0, Z: 0). Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.

1. Selezionare la fotocamera principale nel pannello gerarchia
2. Nel pannello Inspector trovare il componente Transform e modificare la posizione da (X: 0, Y: 1, Z:-10) a (X: 0, Y: 0, Z: 0)

   ![Fotocamera nel riquadro controllo in Unity](images/maincamera-350px.png)  
   *Fotocamera nel riquadro controllo in Unity*

## <a name="clip-planes"></a>Ritagliare i piani

Il rendering del contenuto troppo vicino all'utente può risultare scomodo in realtà mista. È possibile regolare i [piani di ritaglio vicini e lontani](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) sul componente della fotocamera.

1. Selezionare la fotocamera principale nel pannello gerarchia
2. Nel pannello Inspector trovare i piani di ritaglio dei componenti della fotocamera e modificare la casella di testo near da 0,3 a 0,85. Il rendering del contenuto ancora più vicino può causare disagi da parte dell'utente e deve essere evitato in base alle [linee guida di rendering](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Più fotocamere

Quando nella scena sono presenti più componenti della fotocamera, Unity sa quale fotocamera usare per il rendering stereoscopico e il rilevamento Head in base a quale GameObject ha il tag MainCamera.

## <a name="recentering-a-seated-experience"></a>Ricentrare un'esperienza di seduta

Se si sta creando un' [esperienza a scalabilità verticale](../../design/coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .

## <a name="reprojection-modes"></a>Modalità di riproiezione

Sia HoloLens che le cuffie immersive riproiettano ogni frame di cui l'app esegue il rendering per adattarsi a qualsiasi stima errata della posizione effettiva dell'utente quando vengono emessi i fotoni.

Per impostazione predefinita:

* Gli **auricolari immersivi** si occupano della riproiezione posizionale se l'app fornisce un buffer di profondità per un determinato frame. Gli auricolari immersivi configureranno anche gli ologrammi in modo da ottenere una stima errata nella posizione e nell'orientamento. Se non viene fornito un buffer di profondità, il sistema correggerà solo le stime errate all'orientamento.
* Gli **auricolari olografici** come HoloLens si occuperà della riproiezione posizionale, indipendentemente dal fatto che l'app fornisca il buffer di profondità.  La riproiezione posizionale è possibile senza buffer di profondità su HoloLens perché il rendering è spesso di tipo sparse con uno sfondo stabile fornito dal mondo reale.

Se si è certi che si sta compilando un' [esperienza di solo orientamento](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato dal corpo (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione su orientamento solo impostando [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) su [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Condivisione dei buffer di profondità con Windows

La condivisione del buffer di profondità dell'app in Windows ogni frame offrirà all'app uno dei due aumenti di stabilità dell'ologramma, in base al tipo di auricolare per cui si esegue il rendering:

* Gli **auricolari immersivi** possono gestire la riproiezione posizionale quando viene fornito un buffer di profondità, regolando gli ologrammi per la stima errata nella posizione e nell'orientamento.
* Per gli **auricolari olografici** sono disponibili alcuni metodi diversi. HoloLens 1 seleziona automaticamente un [punto di interesse](focus-point-in-unity.md) quando viene fornito un buffer di profondità, ottimizzando la stabilità dell'ologramma lungo il piano che interseca la maggior parte del contenuto. HoloLens 2 stabilizza il contenuto usando [LSR di profondità (vedere la sezione Osservazioni)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

Per specificare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **Edit**  >  **Project Settings**  >  **Player**  >  **piattaforma UWP (Universal Windows Platform) Tab**  >  **XR Settings**.
2. Espandere l'elemento **SDK di realtà mista di Windows** .
3. Selezionare o deselezionare la casella di controllo **Abilita condivisione buffer di profondità** .  Per impostazione predefinita, l'opzione Abilita condivisione buffer di profondità è selezionata nei nuovi progetti, poiché questa funzionalità è stata aggiunta a Unity e verrà deselezionata per impostazione predefinita per i progetti meno recenti aggiornati.

Un buffer di profondità può migliorare la qualità visiva, purché Windows possa mappare accuratamente i valori di profondità per pixel normalizzati nel buffer di profondità a distanza in metri, usando i piani vicini e lontani impostati in Unity sulla fotocamera principale.  Se il rendering passa i valori di profondità di gestione in modi tipici, in genere è opportuno eseguire questa procedura, sebbene i passaggi di rendering traslucidi che scrivono nel buffer di profondità durante la visualizzazione dei pixel di colore esistenti possano confondere la riproiezione.  Se si è certi che i passaggi di rendering lasceranno molti dei pixel di profondità finali con valori di profondità non corretti, è probabile che si ottenga una qualità visiva migliore deselezionando "Abilita condivisione buffer di profondità".

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a>Configurazione automatica della scena e della fotocamera con il Toolkit di realtà misto 

Seguire la Guida [dettagliata](tutorials/mr-learning-base-01.md) per aggiungere il Toolkit di reality misto al progetto Unity e il progetto verrà configurato automaticamente. È anche possibile configurare manualmente il progetto senza MRTK con la guida nella sezione seguente.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Sguardo fisso](gaze-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Stabilità degli ologrammi](../platform-capabilities-and-apis/hologram-stability.md)
* [MixedRealityToolkit fotocamera principale. prefabbricata](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)