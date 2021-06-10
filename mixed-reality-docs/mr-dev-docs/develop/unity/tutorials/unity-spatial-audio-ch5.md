---
title: Esercitazioni sull'audio spaziale - 5. Uso del riverbero per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso di variazione della distanza nell'audio spaziale.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, audio mixer, SFX reverb
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712688"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Uso del riverbero per aggiungere distanza all'audio spaziale

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente è stata aggiunta la spazializzazione per i suoni per dare loro un senso di direzione in questa esercitazione si aggiungerà un effetto riverbero per dare ai suoni un senso di distanza.

## <a name="objectives"></a>Obiettivi

* Migliorare la distanza percepita delle origini sonore aggiungendo il riverbero.
* Controllare la distanza percepita del suono usando la distanza dell'ascoltatore dall'ologramma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Aggiungere un gruppo di mixer e un effetto di riverbero

In [Spatializing button interaction sounds Tutorial (Esercitazione)](unity-spatial-audio-ch2.md)è stato aggiunto un mixer. Il mixer include un **gruppo per** impostazione predefinita denominato **Master.** Poiché si vuole applicare solo un effetto riverbero ad alcuni suoni, si aggiungerà un secondo gruppo per tali suoni. Per aggiungere un gruppo, fare clic con il  pulsante destro del mouse sul gruppo Master nel **mixer audio** e scegliere Aggiungi gruppo figlio e assegnare un nome appropriato, ad esempio _Effetto stanza:_

![Aggiungere un gruppo figlio](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Ogni **gruppo** ha un proprio set di effetti. Aggiungere un effetto di riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo **SFX Reverb**:

![Aggiungere il riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

Nella terminologia audio, l'audio originale non riverberato viene chiamato percorso arido e l'audio dopo il filtro con il filtro riverbero viene chiamato _percorso umido._  Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza in questa combinazione sono denominati _combinazione umida/asciutta._ La combinazione umida/asciutta influisce fortemente sul senso della distanza.

Il **riverbero SFX include** controlli per regolare la combinazione umida/asciutta all'interno dell'effetto. Poiché il **plug-in Microsoft Spatializer** gestisce il percorso secco, si usa **il riverbero SFX** solo per il percorso umido. Nel riquadro Inspector (Controllo) del **riverbero SFX**:

* Impostare la **proprietà Dry Level** sull'impostazione più bassa (-10000 mB)
* Impostare la **proprietà Room** sull'impostazione più alta (0 mB)

![Proprietà del riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

Le altre impostazioni controllano l'aspetto della stanza simulata. In particolare, **il tempo di decadimento** è correlato alle dimensioni percepite della stanza.

## <a name="enable-reverb-on-the-video-playback"></a>Abilitare il riverbero nella riproduzione video

Esistono due passaggi per abilitare il riverbero in un'origine audio:

* Instradare **l'origine** audio al gruppo **appropriato**
* Impostare il **plug-in Microsoft Spatializer** per passare l'audio al **gruppo per** l'elaborazione

Nei passaggi seguenti si regola lo script per controllare il routing audio e si allega uno script di controllo fornito con il plug-in **Microsoft Spatializer** per alimentare i dati nel riverbero.

Con il **quad selezionato** nella gerarchia fare clic su **Aggiungi componente** nella finestra Inspector (Controllo) e aggiungere Room Effect Send Level (Script) (Livello di invio **dell'effetto stanza(Script)**:

![Aggiungere uno script a livello di invio](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> A meno che non **si abiliti** la funzionalità Livello di invio effetto stanza del plug-in **Microsoft Spatializer,** non invia audio al motore audio Unity per l'elaborazione degli effetti.

Il **componente Livello di invio effetto** stanza include un controllo grafico che imposta il livello dell'audio inviato al motore audio Unity per l'elaborazione del riverbero. Per aprire il controllo grafico, fare clic su **Livello di invio effetto stanza**.  Fare clic e trascinare la curva verde verso il basso per impostare il livello su circa -30dB:

![Regolare la curva di riverbero](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

Rimuovere quindi il commento delle 4 righe commentate nello script **SpatializeOnOff.** Lo script avrà ora un aspetto simile al seguente:

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

Dopo aver decommentato queste righe, vengono aggiunte due proprietà al controllo dello **script SpatializeOnOff.** assegnarli nella finestra Inspector del **componente SpatializeOnOff** del **quad**.

Con l'oggetto Quad ancora selezionato nella gerarchia , nella finestra Inspector individuare il **componente SpatializeOnOff Script** e :

* Impostare la **proprietà Gruppo effetti stanza** sul nuovo gruppo di mixer effetto stanza
* Impostare la **proprietà Gruppo master** sul gruppo mixer master

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Lezione completata

Sono stati completati i HoloLens 2 di audio spaziale per Unity. Provare l'app in un HoloLens 2 o Unity. Quando si fa clic sul pulsante nell'app per attivare la spazializzazione, lo script instraderà l'audio del video al gruppo di effetti della stanza per aggiungere il riverbero. Quando si passa allo stereo, instraderà l'audio al gruppo Master ed eviterà di aggiungere riverbero.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
