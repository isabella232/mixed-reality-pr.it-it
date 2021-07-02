---
title: Finestra di dialogo di configurazione di MRTK
description: Configurare MRTK in Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: 50a0f40723c05e96f79eefab933942044afb22f1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177331"
---
# <a name="mrtk-configuration-dialog"></a>Finestra di dialogo di configurazione di MRTK

La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione devono essere attenzioni dello sviluppatore.

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Per applicare le modifiche, fare clic **sul pulsante** Applica. Il **pulsante** In seguito posticiperà le modifiche fino a quando il progetto non verrà ricaricato in un momento futuro.

> [!NOTE]
> La finestra di dialogo di configurazione verrà visualizzata di nuovo se una o più impostazioni consigliate non vengono deselezionate. Per evitare questo problema, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite **Mixed Reality Toolkit**  >  **Utilities** Configure  >  **Unity Project** e fare clic su **Ignora**. In questo modo la finestra di dialogo di configurazione non verrà visualizzata automaticamente.

## <a name="common-settings"></a>Impostazioni comuni

Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forzare la serializzazione degli asset di testo e abilitare i metafile visibili

Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio Git).

### <a name="enable-vr-supported"></a>Abilitare la realtà virtuale supportata

**Unity 2018**

Configura le opzioni Virtual Reality Supported e Virtual Reality SDK in **Player Impostazioni**  >  **XR Impostazioni**.

### <a name="set-single-pass-instanced-rendering-path"></a>Impostare il percorso di rendering con istanza a passaggio singolo

Configura il **lettore Impostazioni**  >  **XR Impostazioni** modalità di rendering  >  **stereo** in istanza a passaggio **singolo**.

### <a name="set-default-spatial-awareness-layer"></a>Impostare il livello di consapevolezza spaziale predefinito

Registra La consapevolezza spaziale come livello 31 per abilitare la configurazione semplice e coerente delle opzioni di raycast e fisica.

### <a name="audio-spatializer"></a>Spazializzatore audio

Gli spazializzatori audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere le esperienze di realtà mista realmente immersive.

> [!NOTE]
> L'impostazione dello spazializzatore audio su Nessuno disabilita le funzionalità audio posizionali.

#### <a name="common-spatializers"></a>Spazializzatori comuni

- Microsoft Spatializer

Microsoft ha fornito un spazializzatore che supporta l'utilizzo dell'accelerazione hardware HoloLens 2.

Questo spazializzatore è [disponibile](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) tramite NuGet e [GitHub](https://github.com/microsoft/spatialaudio-unity).

Altre informazioni su Microsoft Spatializer sono disponibili nella documentazione [relativa al suono spaziale](/windows/mixed-reality/spatial-sound-in-unity).

- Spazializzatore MS HRTF

Microsoft Windows spazializzatore fornito da Unity come parte dei pacchetti Windows Mixed Reality e Windows XR Platform.

- Audio di risonazione

Uno spazializzatore multipiattaforma di Google fornito da Unity.

Altre informazioni sono disponibili nel sito [della documentazione di Resonance Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Impostazioni della Windows universali

![Impostazioni UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Funzionalità UWP

Abilita funzionalità specifiche dell'applicazione per l'applicazione Universal Windows Platform. Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.

- Microfono

  Abilita l'acquisizione di audio tramite il microfono.

- Internet Client

  Abilita il supporto per l'accesso alle risorse su Internet.

- Percezione spaziale

  Abilita il supporto per l'uso dell'ambiente reale.

- Sguardo fisso

  **Unity 2019.3 e versione più recente**

  Abilita il supporto per il rilevamento dello sguardo dell'utente.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Evitare l'arresto anomalo di Unity 'PlayerSettings.graphicsJob'

**Unity 2019.3 e versione più recente**

Nella versione più recente di Unity 2019, quando è abilitato "Processi di grafica", l'app si arresta in modo anomalo quando viene distribuita in un HoloLens 2.
Questa impostazione è abilitata per impostazione predefinita in Unity: mentre questo bug esiste (vedere [Il bug di Unity),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)il configuratore imposta per impostazione predefinita Processi grafici su "false" (consentendo così alle app distribuite di HoloLens 2 di non bloccarsi).

## <a name="android-settings"></a>Impostazioni Android

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi android.

![Android Impostazioni](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Disabilitare il rendering multi-thread

Disabilita **player Impostazioni**  >  **altri Impostazioni** rendering  >  **multithreading** come richiesto dal supporto ar di Android.

### <a name="set-minimum-api-level"></a>Impostare il livello API minimo

Imposta il valore di **Player** Impostazioni altri Impostazioni livello API minimo per applicare i  >    >   requisiti del sistema operativo per le applicazioni ar.

## <a name="ios-settings"></a>Impostazioni iOS

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi basati su iOS.

![iOS Impostazioni](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Impostare la versione del sistema operativo necessaria

Imposta il valore di **Player Impostazioni**  >  **altri Impostazioni** versione minima di iOS di destinazione per applicare i requisiti del  >   sistema operativo per le applicazioni AR.

### <a name="set-required-architecture"></a>Impostare l'architettura richiesta

Imposta il valore di **Player Impostazioni** Other Impostazioni Architecture per applicare i requisiti  >    >  della piattaforma per le applicazioni AR.

### <a name="set-camera-usage-descriptions"></a>Impostare le descrizioni di utilizzo della fotocamera

Imposta il valore di **Player Impostazioni** la Impostazioni di utilizzo della fotocamera usata per richiedere l'autorizzazione per  >    >   l'uso della fotocamera del dispositivo.
