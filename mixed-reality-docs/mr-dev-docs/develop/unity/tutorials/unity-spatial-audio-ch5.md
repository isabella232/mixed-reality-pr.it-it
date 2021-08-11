---
title: Esercitazioni sull'audio spaziale - 5. Uso del riverbero per aggiungere distanza all'audio spaziale
description: Aggiungere un effetto di riverbero per migliorare il senso di variazione della distanza all'audio spaziale.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens2, audio spaziale, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, funzione di trasferimento correlata alla testa, riverbero, spazialista Microsoft, mixer audio, riverbero SFX
ms.openlocfilehash: 8adc92eb96cb8ebd2cc5fff14d522bcfe72733cc5748183dd6db59d753e12a3e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192974"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Uso del riverbero per aggiungere distanza all'audio spaziale

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente è stata aggiunta la spazializzazione per i suoni per dare loro un senso di direzione in questa esercitazione si aggiungerà un effetto di riverbero per dare ai suoni un senso di distanza.

## <a name="objectives"></a>Obiettivi

* Migliorare la distanza percepita delle sorgenti audio aggiungendo riverbero.
* Controllare la distanza percepita del suono usando la distanza dell'listener dall'ologramma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Aggiungere un gruppo di mixer e un effetto di riverbero

In [Spatializing button interaction sounds Tutorial (Esercitazione sull'interazione](unity-spatial-audio-ch2.md)con i pulsanti spazializzazione) è stato aggiunto un mixer. Per impostazione predefinita, il **mixer** include un gruppo **denominato Master.** Poiché si vuole applicare solo un effetto di riverbero ad alcuni suoni, si aggiungerà un secondo gruppo per tali suoni. Per aggiungere un gruppo, fare clic con il pulsante  destro del mouse sul gruppo Master **nell'Mixer** scegliere Aggiungi gruppo figlio e assegnare un nome appropriato, ad esempio _Effetto stanza:_

![Aggiungere un gruppo figlio](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Ogni **gruppo** ha un proprio set di effetti. Aggiungere un effetto di riverbero al nuovo gruppo facendo clic su **Aggiungi...** nel nuovo gruppo e scegliendo **SFX Reverb (Riverbero SFX):**

![Aggiungere il riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

Nella terminologia audio, l'audio originale non riverberato viene chiamato percorso dry e l'audio dopo il filtro con il filtro riverbero è denominato percorso _riverbero_.  Entrambi i percorsi vengono inviati all'output audio e i relativi punti di forza in questa combinazione sono detti combinazione _umida/asciutta._ La combinazione umida/asciutta influisce fortemente sul senso della distanza.

Il **riverbero SFX include controlli** per regolare la combinazione riverbero/dry all'interno dell'effetto. Poiché il **plug-in Microsoft Spatializer** gestisce il percorso dry, si usa **il riverbero SFX** solo per il percorso riverbero. Nel riquadro Inspector (Controllo) di **SFX Reverb (Riverbero SFX):**

* Impostare la **proprietà Dry Level** sull'impostazione più bassa (-10000 mB)
* Impostare la **proprietà Room** sull'impostazione più alta (0 mB)

![Proprietà del riverbero SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

Le altre impostazioni controllano l'aspetto della stanza simulata. In particolare, **il tempo di decadimento** è correlato alle dimensioni percepite della stanza.

## <a name="enable-reverb-on-the-video-playback"></a>Abilitare il riverbero nella riproduzione video

Per abilitare il riverbero in un'origine audio, è necessario eseguire due passaggi:

* Instradare **l'origine** audio al gruppo **appropriato**
* Impostare il **plug-in Microsoft Spatializer** per passare l'audio al **gruppo per** l'elaborazione

Nei passaggi seguenti si regola lo script per controllare il routing audio e si collega uno script di controllo fornito con il plug-in **Microsoft Spatializer** per l'alimentazione dei dati nel riverbero.

Con il **quad selezionato** nella gerarchia, fare clic su **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) e aggiungere Room Effect Send **Level (Script) (Livello** di invio effetto stanza - Script):

![Aggiungere lo script del livello di invio](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> A meno che non **si abiliti** la funzionalità Livello di invio effetto stanza del plug-in **Microsoft Spatializer,** non invia audio al motore audio unity per l'elaborazione degli effetti.

Il **componente Livello di invio effetto** stanza include un controllo grafico che imposta il livello dell'audio inviato al motore audio unity per l'elaborazione del riverbero. Per aprire il controllo grafico, fare clic su **Livello di invio effetto stanza**.  Fare clic e trascinare la curva verde verso il basso per impostare il livello su circa -30dB:

![Regolare la curva del riverbero](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

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

Dopo aver aggiunto il commento a queste righe, vengono aggiunte due proprietà al controllo dello **script SpatializeOnOff**. Assegnarli nella finestra Inspector **(Controllo) del componente SpatializeOnOff** del **quad**.

Con l'oggetto Quad ancora selezionato in Hierarchy (Gerarchia), nella finestra Inspector (Controllo) individuare il **componente SpatializeOnOff Script (Script SpatializeOnOff)** e :

* Impostare la **proprietà Room Effect Group (Gruppo** effetto stanza) sul nuovo gruppo di mixer effetto stanza
* Impostare la **proprietà Gruppo** master sul gruppo mixer master

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Lezione completata

Sono stati completati i HoloLens 2 per l'audio spaziale per Unity. Provare l'app in un HoloLens 2 o Unity. Quando si fa clic sul pulsante nell'app per attivare la spazializzazione, lo script instraderà l'audio del video al gruppo di effetti della stanza per aggiungere il riverbero. Quando si passa allo stereo, instraderà l'audio al gruppo Master ed evita di aggiungere riverbero.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
