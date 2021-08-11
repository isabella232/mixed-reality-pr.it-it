---
title: MRTK_Configuration_Dialog
description: Configurare MRTK in Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: ac3dac7e73cca7c600db6aea4bef304870a42e6765dc318854dc1233ee9e8ed5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225351"
---
# <a name="mrtk-project-configuration-dialog"></a>Finestra di dialogo di configurazione del progetto MRTK

La finestra di dialogo di configurazione di MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione hanno bisogno dell'attenzione dello sviluppatore.

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Per applicare le modifiche, fare clic **sul pulsante** Applica. Il **pulsante** Later (Avanti) rinvia le modifiche fino a quando il progetto non viene ricaricato in un secondo momento.

> [!NOTE]
> La finestra di dialogo di configurazione verrà visualizzata di nuovo se una o più impostazioni consigliate non vengono deselezionate. Per evitare questo problema, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite **Mixed Reality Toolkit** Utilities Configure Unity Project (Ignora).  >    >    In questo modo la finestra di dialogo di configurazione non verrà nuovamente visualizzata automaticamente.

## <a name="common-settings"></a>Impostazioni comuni

Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forzare la serializzazione degli asset di testo e abilitare i metadati visibili

Queste impostazioni consentono di semplificare l'uso di progetti Unity e sistemi di controllo del codice sorgente (ad esempio Git).

### <a name="enable-vr-supported"></a>Abilitare la realtà virtuale supportata

**Unity 2018**

Configura le opzioni Virtual Reality Supported (Realtà virtuale supportata) e Virtual Reality SDK in **Player Impostazioni**  >  **XR Impostazioni**.

### <a name="set-single-pass-instanced-rendering-path"></a>Impostare il percorso di rendering con istanze a passaggio singolo

Configura l'oggetto **Player Impostazioni**  >  **XR Impostazioni** rendering stereo  >  **su** Single Pass **Instanced.**

### <a name="set-default-spatial-awareness-layer"></a>Impostare il livello di consapevolezza spaziale predefinito

Registra la consapevolezza spaziale come livello 31 per consentire una configurazione semplice e coerente delle opzioni di raycast e fisica.

### <a name="audio-spatializer"></a>Spazializzatore audio

Gli spazializzatori audio sono i componenti che sbloccano la potenza dell'audio spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà mista.

> [!NOTE]
> L'impostazione dello spazializzatore audio su Nessuno disabilita le funzionalità audio posizionali.

#### <a name="common-spatializers"></a>Spazializzatori comuni

- Spazializzatore Microsoft

Microsoft ha fornito un spazializzatore che supporta l'utilizzo dell'accelerazione hardware HoloLens 2.

Questo spazializzatore è disponibile [tramite NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).

Per altre informazioni su Microsoft Spatializer, vedere la documentazione [relativa al suono spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).

- Spazializzatore MS HRTF

Microsoft Windows spazializzatore fornito da Unity come parte dei pacchetti Windows Mixed Reality e Windows XR Platform.

- Audio di risonazione

Spazializzatore multipiattaforma di Google fornito da Unity.

Altre informazioni sono disponibili nel sito [della documentazione di Resonance Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Impostazioni della Windows universali

![Applicazione UWP Impostazioni](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Funzionalità UWP

Abilita funzionalità specifiche dell'applicazione per l'Windows universali. Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.

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

![Android Impostazioni](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Disabilitare il rendering multi-thread

Disabilita Player **Impostazioni**  >  **altri Impostazioni** rendering  >  **multithreading** come richiesto dal supporto AR di Android.

### <a name="set-minimum-api-level"></a>Impostare il livello API minimo

Imposta il valore di **Player** Impostazioni Other Impostazioni Minimum API Level (Livello API minimo) per applicare i  >    >   requisiti del sistema operativo per le applicazioni AR.

## <a name="ios-settings"></a>Impostazioni iOS

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi iOS.

![Impostazioni iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Impostare la versione del sistema operativo richiesta

Imposta il valore di **Player** Impostazioni Other Impostazioni Target minimum iOS Version (Versione  >    >  **minima iOS** di destinazione) per applicare i requisiti del sistema operativo per le applicazioni AR.

### <a name="set-required-architecture"></a>Impostare l'architettura richiesta

Imposta il valore di **Player** Impostazioni Other Impostazioni Architecture per  >    >   applicare i requisiti della piattaforma per le applicazioni AR.

### <a name="set-camera-usage-descriptions"></a>Impostare le descrizioni di utilizzo della fotocamera

Imposta il valore di **Player Impostazioni** Other Impostazioni Camera Usage Description usato per richiedere  >    >   l'autorizzazione a usare la fotocamera del dispositivo.
