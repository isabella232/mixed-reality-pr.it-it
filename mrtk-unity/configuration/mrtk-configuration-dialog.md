---
title: Finestra di dialogo di configurazione MRTK
description: Configurare MRTK nel progetto Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144838"
---
# <a name="mrtk-project-configuration-dialog"></a>Finestra di dialogo di configurazione del progetto MRTK

La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione devono essere attenzioni dello sviluppatore.

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Per applicare le modifiche, fare clic **sul pulsante** Applica. Il **pulsante** In seguito posticiperà le modifiche fino a quando il progetto non verrà ricaricato in un momento futuro.

> [!NOTE]
> La finestra di dialogo di configurazione verrà visualizzata di nuovo se una o più impostazioni consigliate non vengono deselezionate. Per evitare questo problema, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite **Mixed Reality Toolkit** Utilities Configure Unity Project e  >    >   fare clic su **Ignora**. In questo modo la finestra di dialogo di configurazione non verrà visualizzata automaticamente.

## <a name="common-settings"></a>Impostazioni comuni

Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forzare la serializzazione degli asset di testo e abilitare i metafile visibili

Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio Git).

### <a name="enable-vr-supported"></a>Abilitare la realtà virtuale supportata

**Unity 2018**

Configura le opzioni Virtual Reality Supported e Virtual Reality SDK in **Player Settings**  >  XR Settings (Impostazioni **lettore XR Settings XR).**

### <a name="set-single-pass-instanced-rendering-path"></a>Impostare il percorso di rendering con istanza a passaggio singolo

Configura le impostazioni **del lettore**  >  **XR Settings** Stereo Rendering  >  **Mode** su Single Pass **Instanced**.

### <a name="set-default-spatial-awareness-layer"></a>Impostare il livello di consapevolezza spaziale predefinito

Registra la consapevolezza spaziale come livello 31 per consentire la configurazione semplice e coerente delle opzioni di raycast e fisica.

### <a name="audio-spatializer"></a>Spazializzatore audio

Gli spazializzatori audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà mista.

> [!NOTE]
> L'impostazione dello spazializzatore audio su Nessuno disabilita le funzionalità audio posizionali.

#### <a name="common-spatializers"></a>Spazializzatori comuni

- Spazializzatore Microsoft

Microsoft ha fornito un spazializzatore che supporta l'utilizzo dell'accelerazione hardware HoloLens 2.

Questo spazializzatore è disponibile tramite [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub.](https://github.com/microsoft/spatialaudio-unity)

Per altre informazioni su Microsoft Spatializer, vedere la documentazione [relativa al suono spaziale](/windows/mixed-reality/spatial-sound-in-unity).

- Spazializzatore MS HRTF

Spazializzatore di Microsoft Windows fornito da Unity come parte dei pacchetti Windows Mixed Reality e della piattaforma Windows XR.

- Audio di risonazione

Spazializzatore multipiattaforma di Google fornito da Unity.

Altre informazioni sono disponibili nel sito [della documentazione di Resonance Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>piattaforma UWP (Universal Windows Platform) impostazioni

![Impostazioni UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Funzionalità UWP

Abilita funzionalità specifiche dell'applicazione per piattaforma UWP (Universal Windows Platform)appalta. Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.

- Microfono

  Abilita l'acquisizione dell'audio tramite il microfono.

- Internet Client

  Abilita il supporto per l'accesso alle risorse su Internet.

- Percezione spaziale

  Abilita il supporto per l'uso dell'ambiente reale.

- Sguardo fisso

  **Unity 2019.3 e versione più recente**

  Abilita il supporto per tenere traccia dello sguardo fisso dell'utente.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Evitare l'arresto anomalo di 'PlayerSettings.graphicsJob' di Unity

**Unity 2019.3 e versione più recente**

Nella versione più recente di Unity 2019, quando è abilitato "Processi di grafica", l'app si arresta in modo anomalo quando viene distribuita in un HoloLens 2.
Questa impostazione è abilitata per impostazione predefinita in Unity. Anche se questo bug esiste (vedere il bug di [Unity),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)lo configuratore imposta per impostazione predefinita Processi grafici su "false", consentendo così alle app distribuite di HoloLens 2 di non bloccarsi.

## <a name="android-settings"></a>Impostazioni Android

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi Android.

![Impostazioni Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Disabilitare il rendering multi-thread

Disabilita le impostazioni **del**  >  **lettore Altre impostazioni** Rendering  >  **multithreading** come richiesto dal supporto AR di Android.

### <a name="set-minimum-api-level"></a>Impostare il livello API minimo

Imposta il valore di **Player Settings Other Settings** Minimum API Level per applicare i requisiti del sistema operativo per le applicazioni  >    >   AR.

## <a name="ios-settings"></a>Impostazioni iOS

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi iOS.

![Impostazioni iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Impostare la versione del sistema operativo richiesta

Imposta il valore di **Player Settings Other Settings** Target minimum iOS Version per applicare i requisiti del sistema operativo per le applicazioni  >    >   AR.

### <a name="set-required-architecture"></a>Impostare l'architettura richiesta

Imposta il valore di **Impostazioni lettore Altre**  >  **impostazioni**  >  **Architettura per** applicare i requisiti della piattaforma per le applicazioni ar.

### <a name="set-camera-usage-descriptions"></a>Impostare le descrizioni di utilizzo della fotocamera

Imposta il valore di **Impostazioni lettore Altre impostazioni** Descrizione utilizzo fotocamera usata per richiedere  >    >   l'autorizzazione per l'uso della fotocamera del dispositivo.