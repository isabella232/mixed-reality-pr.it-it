---
title: Esercitazioni audio spaziali-5. Uso del riverbero per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso della variazione della distanza nell'audio spaziale.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento correlato alla testa, riverbero, Microsoft Spatializer, mixer audio, riverbero SFX
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578382"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Uso del riverbero per aggiungere distanza all'audio spaziale

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente è stata aggiunta la spazializzazione per i suoni, per dare loro un senso di direzione in questa esercitazione, si aggiungerà un effetto di riverbero per dare un senso di distanza ai suoni.

## <a name="objectives"></a>Obiettivi

* Migliorare la distanza percepita delle origini audio aggiungendo Reverb.
* Controllare la distanza percepita del suono usando la distanza del listener con l'ologramma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Aggiungere un gruppo di mixer e un effetto di riverbero

Nell' [esercitazione sull'interazione con il pulsante Spatializing](unity-spatial-audio-ch2.md)è stato aggiunto un mixer. Il mixer include un **gruppo** per impostazione predefinita denominato **Master**. Poiché si vuole applicare un effetto di riverbero solo ad alcuni suoni, aggiungere un secondo gruppo per i suoni. Per aggiungere un gruppo, fare clic con il pulsante destro del mouse sul gruppo master nel **mixer audio** scegliere **Aggiungi gruppo figlio** e assegnare un nome appropriato per l' _effetto spazio_ di esempio:

![Aggiungi gruppo figlio](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

Ogni **gruppo** ha un proprio set di effetti. Aggiungere un effetto del riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo il **riverbero SFX**:

![Aggiungi Riverb SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

Nella terminologia audio, l'audio originale, non riverberato, viene chiamato _percorso asciutto_ e l'audio dopo l'applicazione di filtri con il filtro del riverbero viene chiamato _percorso bagnato_. Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza relativi in questa combinazione sono detti _mix bagnato/secco_. La combinazione Wet/Dry influiscono fortemente sul senso della distanza.

Il **riverbero SFX** include i controlli per regolare la combinazione di Wet/Dry nell'effetto. Poiché il plug-in **Microsoft Spatializer** gestisce il percorso asciutto, verrà usato il **riverbero SFX** solo per il percorso bagnato. Nel riquadro Inspector del **riverbero SFX**:

* Impostare la proprietà **livello secco** sull'impostazione più bassa (-10000 MB)
* Imposta la **Proprietà room** sull'impostazione massima (0 MB)

![Proprietà del riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

Le altre impostazioni controllano l'aspetto della stanza simulata. In particolare, il **tempo di decadimento** è correlato alla dimensione della stanza percepita.

## <a name="enable-reverb-on-the-video-playback"></a>Abilitare il riverbero per la riproduzione video

Per abilitare il riverbero in un'origine audio sono necessari due passaggi:

* Indirizzare l' **origine audio** al **gruppo** appropriato
* Impostare il plug-in **Microsoft Spatializer** per passare l'audio al **gruppo** per l'elaborazione

Nei passaggi seguenti si modificherà lo script per controllare il routing audio e si collegherà uno script di controllo fornito con il plug-in **Microsoft Spatializer** per inserire i dati nel Reverbo.

Con il **Quad** selezionato nella gerarchia fare clic su **Aggiungi componente** nella finestra di controllo e aggiungere il **livello di invio dell'effetto spazio (script)**:

![Aggiungi script del livello di trasmissione](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> A meno che non si abiliti la funzionalità di **trasmissione dell'effetto spazio** del plug-in **Microsoft Spatializer** , non viene inviato alcun audio al motore audio Unity per l'elaborazione degli effetti.

Il componente del **livello di invio dell'effetto chat** include un controllo grafico che imposta il livello dell'audio inviato al motore audio di Unity per l'elaborazione dei verbi. Per aprire il controllo grafico, fare clic sul **livello di invio dell'effetto chat room**.  Fare clic e trascinare la curva verde verso il basso per impostare il livello su about-30dB:

![Modificare la curva del riverbero](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

Rimuovere quindi il commento dalle 4 righe commentate nello script **SpatializeOnOff** . Lo script sarà ora simile al seguente:

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

Una volta che queste righe sono state annullate, vengono aggiunte due proprietà al controllo dello **script SpatializeOnOff**. assegnare questi elementi nella finestra di controllo del componente **SpatializeOnOff** del **Quad**.

Con l'oggetto Quad ancora selezionato nella gerarchia, nella finestra di controllo individuare il componente **script SpatializeOnOff** e:

* Impostare la proprietà **gruppo effetti Room** sul nuovo gruppo di mixer effetti della stanza
* Impostare la proprietà **gruppo Master** sul gruppo di mixer Master

![Spatialize su off esteso](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>Lezione completata

Sono state completate le esercitazioni audio spaziali HoloLens 2 per Unity. Provare l'app in un HoloLens 2 o Unity. Quando si fa clic sul pulsante nell'app per attivare la spazializzazione, lo script instrada l'audio del video al gruppo di effetti della stanza per aggiungere Reverb. Quando si passa a stereo, l'audio viene indirizzato al gruppo Master ed è possibile evitare di aggiungere Reverb.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
