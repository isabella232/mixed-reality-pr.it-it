---
title: MRTK_Configuration_Dialog
description: Configurare MRTK nel progetto Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: 6b0bad2322f70e0a5adbc0c34c1343d9213bde4c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550741"
---
# <a name="mrtk-project-configuration-dialog"></a>Finestra di dialogo di configurazione del progetto MRTK

La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione richiedono l'attenzione dello sviluppatore.

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Per applicare le modifiche, fare clic sul pulsante **applica** . Il pulsante **più avanti** rinvia le modifiche finché il progetto non viene ricaricato in un momento successivo.

> [!NOTE]
> Se una o più delle impostazioni consigliate non sono state controllate, verrà visualizzata nuovamente la finestra di dialogo di configurazione. Per evitare che ciò accada, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite le utilità del **Toolkit di realtà mista**  >    >  **configurare il progetto Unity** e fare clic su **Ignora**. In questo modo si impedisce la visualizzazione automatica della finestra di dialogo di configurazione.

## <a name="common-settings"></a>Impostazioni comuni

Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forza la serializzazione degli asset di testo e Abilita i metadati visibili

Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio, git).

### <a name="enable-vr-supported"></a>Abilitazione di VR supportata

**Unity 2018**

Configura le opzioni Virtual Reality supported e Virtual Reality SDK in **Impostazioni lettore**  >  **XR impostazioni**.

### <a name="set-single-pass-instanced-rendering-path"></a>Imposta il percorso di rendering con istanza Single Pass

Configura le impostazioni del **lettore impostazioni**  >  **XR**  >  **modalità di rendering stereo** per **singolo passaggio istanza**.

### <a name="set-default-spatial-awareness-layer"></a>Imposta livello di riconoscimento spaziale predefinito

Registra la consapevolezza spaziale come livello 31 per consentire una configurazione semplice e coerente delle opzioni di Raycast e fisica.

### <a name="audio-spatializer"></a>Spatializer audio

Spatializers audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà miste.

> [!NOTE]
> Se si imposta Spatializer audio su None, le funzionalità audio posizionali non vengono disabilitate.

#### <a name="common-spatializers"></a>Spatializers comuni

- Microsoft Spatializer

Microsoft ha fornito Spatializer che supporta l'utilizzo dell'accelerazione hardware in HoloLens 2.

Questo Spatializer è disponibile tramite [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).

Per ulteriori informazioni su Microsoft Spatializer, vedere la [documentazione relativa al suono spaziale](/windows/mixed-reality/spatial-sound-in-unity).

- MS HRTF Spatializer

Microsoft Windows Spatializer fornito da Unity come parte della realtà mista di Windows e dei pacchetti della piattaforma Windows XR.

- Audio risonanza

Spatializer multipiattaforma di Google fornito da Unity.

Altre informazioni sono reperibili nel sito di [documentazione audio risonanza](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .

## <a name="universal-windows-platform-settings"></a>Impostazioni piattaforma UWP (Universal Windows Platform)

![Impostazioni UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Funzionalità UWP

Abilita funzionalità specifiche dell'applicazione per piattaforma UWP (Universal Windows Platform) applicazione. Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.

- Microfono

  Abilita l'acquisizione di suoni tramite il microfono.

- Client Internet

  Abilita il supporto per l'accesso alle risorse su Internet.

- Percezione spaziale

  Abilita il supporto per l'uso dell'ambiente reale.

- Occhio

  **Unity 2019,3 e versioni successive**

  Abilita il supporto per tenere traccia degli sguardi dell'utente.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Evitare l'arresto anomalo di Unity ' PlayerSettings. graphicsJob '

**Unity 2019,3 e versioni successive**

Nella versione più recente di Unity 2019, quando è abilitato "processi grafici", l'app si arresterà in modo anomalo quando viene distribuita in un HoloLens 2.
Questa impostazione è abilitata per impostazione predefinita in Unity. questo bug è disponibile (vedere il [bug Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)). per impostazione predefinita, lo strumento di configurazione imposta i processi grafici su' false ', consentendo così alle app distribuite in HoloLens 2 di non arrestarsi in modo anomalo.

## <a name="android-settings"></a>Impostazioni Android

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi Android.

![Impostazioni Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Disabilitare il rendering multithread

Disabilita **le impostazioni del lettore**  >  **altre impostazioni**  >  di **rendering multithreading** come richiesto dal supporto AR di Android.

### <a name="set-minimum-api-level"></a>Imposta il livello API minimo

Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni**  >  **livello API minimo** per applicare i requisiti del sistema operativo per le applicazioni AR.

## <a name="ios-settings"></a>Impostazioni iOS

Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi con tecnologia iOS.

![Impostazioni iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Imposta la versione richiesta del sistema operativo

Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni** di  >  **destinazione della versione minima di iOS** per applicare i requisiti del sistema operativo per le applicazioni AR.

### <a name="set-required-architecture"></a>Imposta architettura necessaria

Imposta il valore dell'   >  architettura di **altre impostazioni** del lettore  >   per applicare i requisiti di piattaforma per le applicazioni AR.

### <a name="set-camera-usage-descriptions"></a>Imposta descrizioni utilizzo della fotocamera

Imposta il valore di **Impostazioni lettore**  >  **altre impostazioni**  >  **Descrizione utilizzo fotocamera** usato per richiedere l'autorizzazione per l'uso della fotocamera del dispositivo.