---
title: Esercitazioni audio spaziali-1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 8790c4c62ab4c1b2b9e9f9c5c6fe0583b9e36545
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002506"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Aggiunta di audio spaziale al progetto Unity

Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2. Questa sequenza di esercitazione Mostra:
* Come usare l'offload della funzione di trasferimento delle intestazioni (HRTF) in HoloLens 2 in Unity
* Come abilitare il riverbero quando si usa l'offload HRTF

Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione. 

Per informazioni su ciò che significa spatialize i suoni usando le tecnologie di spazializzazione basate su HRTF e consigli per quando può essere utile, vedere [progettazione di suoni spaziali](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Che cos'è HRTF offload?
L'elaborazione di audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati. HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di sovraccaricare il processore di applicazioni, quindi "offload" dell'elaborazione degli algoritmi basati su HRTF.  Il plug-in Microsoft Spatializer offre un modo semplice per consentire all'applicazione di sfruttare i vantaggi dell'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori di applicazioni per operazioni diverse dall'audio spaziale.

## <a name="objectives"></a>Obiettivi
In questo primo capitolo, verranno illustrate le operazioni seguenti:
* Creare un progetto Unity e importare MRTK
* Importare il plug-in Microsoft Spatializer
* Abilitare il plug-in Microsoft Spatializer
* Abilitare l'audio spaziale nella workstation per sviluppatori

## <a name="create-a-project-and-add-nuget-for-unity"></a>Creare un progetto e aggiungere NuGet per Unity
Iniziare con un progetto Unity vuoto, quindi aggiungere e configurare NuGet per Unity:
1. Scaricare la versione più recente di [NuGetForUnity. file unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. Nella barra dei menu di Unity fare clic su **Asset-> importa pacchetto-> pacchetto personalizzato...** e installare il pacchetto NuGetForUnity:

![Importa pacchetto personalizzato](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Aggiungere il pacchetto di realtà mista di Windows
Il supporto della realtà mista di Windows in Unity 2019 e versioni successive è incluso in un pacchetto facoltativo. Per aggiungerlo al progetto, aprire **Gestione pacchetti di > finestra** dalla barra dei menu di Unity:

![Menu di gestione pacchetti](images/spatial-audio/package-manager-menu.png)

Individuare e installare il pacchetto di **realtà mista di Windows** :

![Finestra di gestione pacchetti](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Installare MRTK e Microsoft Spatializer
Usando NuGet per Unity, installare i plug-in MRTK e Microsoft Spatializer:
1. Nella barra dei menu di Unity fare clic su **NuGet-> Gestisci pacchetti NuGet**.

![Gestisci pacchetti NuGet](images/spatial-audio/manage-nuget-packages.png)

2. Nella casella di **ricerca** immettere "Microsoft. MixedReality. Toolkit" e installare il pacchetto MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**

![Pacchetto NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

Il [pacchetto NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) dispone di contesto e dettagli aggiuntivi.

4. Nella casella di **ricerca** immettere "Microsoft. SpatialAudio" e installare il pacchetto Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**

![Spatializer plug-in NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Configurare MRTK nel progetto

1. Aprire la finestra impostazioni di compilazione passando a **file-> impostazioni di compilazione**.

2. Selezionare il _piattaforma UWP (Universal Windows Platform)_ e fare clic su **Cambia piattaforma**.

3. Fare clic su **Impostazioni lettore** nella **finestra di compilazione** per aprire le proprietà **delle impostazioni del lettore** nel riquadro **controllo** .
    * In **Impostazioni XR** selezionare la casella di controllo **Virtual Reality supported**
    * In **Impostazioni XR**, modificare la **modalità di rendering stereo** in **Single Pass istanza**.
    * In **impostazioni di pubblicazione** selezionare la casella di controllo **percezione spaziale** nella sezione **funzionalità**

4. Sulla barra dei menu fare clic su **Toolkit realtà mista-> Aggiungi a scena e configura..** per aggiungere MRTK alla scena.

Per altre istruzioni, ad esempio su come compilare l'app e distribuirla in un HoloLens 2, vedere [il capitolo 1 del modulo di base per la formazione di Mr Learning](../../../mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Abilitare il plug-in Microsoft Spatializer
Abilitare il plug-in **Microsoft Spatializer** . Aprire **modifica-> impostazioni progetto-> audio** e modificare il **plug** -in Spatializer in "Microsoft Spatializer". La sezione **audio** delle **impostazioni del progetto** sarà ora simile alla seguente:

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Abilitare l'audio spaziale nella workstation
Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita. Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni. Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.

![Impostazioni audio spaziali desktop](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Unità audio spaziale capitolo 2](unity-spatial-audio-ch2.md)

