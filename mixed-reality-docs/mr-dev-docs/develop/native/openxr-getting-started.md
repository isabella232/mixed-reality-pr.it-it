---
title: Informazioni di base su OpenXR
description: Introduzione all'uso dello standard dell'API OpenXR portabile Windows Mixed Reality e HoloLens 2 visori VR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Strumenti di sviluppo, DirectX, app nativa, nativa, motore personalizzato, middleware, introduzione, 101, estensioni di anteprima, versione di runtime OpenXR, stato del sistema
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189156"
---
# <a name="getting-started-with-openxr"></a>Informazioni di base su OpenXR

È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.  Se non si ha accesso a un visore VR, è possibile usare il HoloLens 2 Emulator o il simulatore Windows Mixed Reality dispositivo.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introduzione a OpenXR per HoloLens 2

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare una versione recente dell'emulatore HoloLens 2 .](../platform-capabilities-and-apis/using-the-hololens-emulator.md) OpenXR 1.0 dovrebbe essere già pronto per l'uso se si usa un'immagine dell'emulatore recente o se il dispositivo ha aggiornato il sistema operativo.
2. Assicurarsi di avere la versione più recente del runtime OpenXR con tutte le estensioni [presenti](openxr.md#roadmap) avviando l'app **dello Store** dal dispositivo o dall'emulatore.
    * Aprire il menu in alto a destra, selezionare **Download e aggiornamenti** e scegliere Ottieni **aggiornamenti.**  

> [!NOTE]
> Se si usa l'emulatore, l'immagine dell'emulatore verrà reimpostata a ogni avvio, quindi la soluzione migliore è assicurarsi di avere la versione più recente dell'immagine [dell'emulatore HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introduzione a OpenXR per visori WINDOWS MIXED REALITY visori VR

Per iniziare a sviluppare applicazioni OpenXR per visori VR Windows Mixed Reality immersive:

1. Assicurarsi di eseguire almeno il Aggiornamento di Windows 10 (maggio 2019) (1903), che è il requisito minimo per consentire Windows Mixed Reality utenti finali di eseguire applicazioni OpenXR.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento <a href="https://www.microsoft.com/software-download/windows10" target="_blank">usando l'Windows 10 di aggiornamento.</a>
2. Configurare un visore VR Windows Mixed Reality o seguire le istruzioni per [abilitare il simulatore Windows Mixed Reality .](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

Questo è tutto.  Il runtime Windows Mixed Reality OpenXR viene installato e reso attivo automaticamente per tutti Windows Mixed Reality utenti.  Il Microsoft Store quindi mantiene aggiornato il runtime.

Per attivare di nuovo Windows Mixed Reality OpenXR Runtime, avviare Portale realtà mista dal menu Start e selezionare "Correggi" nella parte superiore della finestra.  Se il pulsante non è presente, il runtime OpenXR è già attivo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Recupero del Strumenti di sviluppo OpenXR per Windows Mixed Reality

Per provare il runtime Windows Mixed Reality OpenXR, è possibile installare <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">openXR Strumenti di sviluppo per l Windows Mixed Reality app</a>.  Questa app offre una demo delle varie funzionalità di OpenXR, insieme a una pagina Stato del sistema con informazioni chiave sul runtime attivo e sul visore VR corrente.

Quando si usa l'emulatore HoloLens 2, il modo più semplice per installare openXR Strumenti di sviluppo per Windows Mixed Reality è tramite il [Windows Portale di dispositivi](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Passare alla pagina "OpenXR" e quindi fare clic sul pulsante "Installa" in "Funzionalità per sviluppatori", che funziona anche nei dispositivi HoloLens 2 fisici.

![OpenXR Strumenti di sviluppo per Windows Mixed Reality app](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Assicurarsi di [installare gli strumenti](../install-the-tools.md) necessari per lo sviluppo OpenXR, se non è già stato fatto.

Il <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">progetto BasicXrApp</a> mostra un semplice esempio OpenXR con file di progetto HoloLens 2 Win32 e UWP in Visual Studio. Poiché la soluzione contiene un progetto UWP HoloLens, è necessario che il carico di lavoro Sviluppo della piattaforma [UWP (Universal Windows Platform)](../install-the-tools.md#installation-checklist) sia installato in Visual Studio per aprirlo completamente.

Anche se i file di progetto Win32 e UWP sono separati a causa delle differenze nella creazione di pacchetti e nella distribuzione, il codice dell'app all'interno di ogni progetto è quasi esattamente lo stesso.

Dopo aver compilato un .EXE desktop OpenXR Win32, puoi usarlo con un visore VR in qualsiasi piattaforma di realtà virtuale desktop che supporta OpenXR, indipendentemente dal tipo di visore VR.

Dopo aver compilato un pacchetto di [](../platform-capabilities-and-apis/using-visual-studio.md) app UWP OpenXR, puoi distribuirvi in un dispositivo HoloLens 2 o nel HoloLens 2 Emulator.

## <a name="learning-the-openxr-api"></a>Learning'API OpenXR

Per una presentazione dell'API OpenXR, vedere questo video di 60 minuti dell'esempio <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> in Visual Studio.  Il video illustra come ognuno dei componenti principali dell'API OpenXR può essere usato nel proprio motore e illustra anche alcune delle applicazioni attualmente compilate su OpenXR:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrare il caricatore OpenXR in un progetto

Per iniziare a usare OpenXR in un progetto esistente, si includerà il caricatore OpenXR.  Il caricatore individua il runtime OpenXR attivo nel dispositivo e fornisce l'accesso alle funzioni di base e alle funzioni di estensione che implementa.

È possibile fare riferimento al pacchetto di NuGet [OpenXR](#reference-official-openxr-nuget-package) ufficiale dal progetto Visual Studio o includere l'origine ufficiale del caricatore [OpenXR](#include-official-openxr-loader-source) dal GitHub Khronos.  Entrambi gli approcci consentono di accedere alle funzionalità principali di OpenXR 1.0, oltre alle estensioni `KHR` `EXT` pubblicate e `MSFT` .

Se si è interessati a sperimentare anche con le estensioni, è possibile copiare in anteprima le intestazioni `MSFT_preview` [OpenXR](#using-preview-extensions) dal GitHub realtà mista.

### <a name="reference-official-openxr-nuget-package"></a>Fare riferimento al pacchetto NuGet OpenXR ufficiale

Il pacchetto di NuGet <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR.Loader**</a> è il modo più semplice per fare riferimento a un caricatore OpenXR predefinito .DLL nella soluzione Visual Studio C++.  In questo modo sarà possibile accedere alle funzionalità principali di OpenXR 1.0, oltre alle estensioni `KHR` `EXT` pubblicate e `MSFT` .

Per aggiungere un riferimento al pacchetto NuGet OpenXR.Loader alla Visual Studio C++:
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto che userà OpenXR e scegliere Gestisci pacchetti **NuGet...**.
2. Passare alla **scheda Sfoglia** e cercare **OpenXR.Loader.**
3. Selezionare il **pacchetto OpenXR.Loader** e selezionare Installa nel riquadro dei dettagli a destra.
4. Selezionare OK per accettare le modifiche apportate al progetto.
5. Aggiungere `#include <openxr/openxr.h>` a un file di origine per iniziare a usare l'API OpenXR.

Per un esempio dell'API OpenXR in azione, vedere l'app <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">di esempio BasicXrApp.</a>

### <a name="include-official-openxr-loader-source"></a>Includere l'origine ufficiale del caricatore OpenXR

Se si vuole compilare il caricatore manualmente, ad esempio per evitare il .DLL aggiuntivo del caricatore, è possibile eseguire il pull delle origini ufficiali del caricatore Khronos OpenXR nel progetto.  In questo modo sarà possibile accedere alle funzionalità principali di OpenXR 1.0, oltre alle estensioni `KHR` `EXT` pubblicate e `MSFT` .

Per iniziare, seguire le istruzioni nel <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repo Khronos OpenXR-SDK in GitHub</a>.  Il progetto è configurato per la compilazione con CMake: se si usa MSBuild, sarà necessario copiare il codice nel proprio progetto.

## <a name="using-preview-extensions"></a>Uso delle estensioni di anteprima

Le `MSFT_preview` estensioni elencate nella guida di [orientamento per le estensioni sono](openxr.md#roadmap) estensioni sperimentali del fornitore in anteprima per raccogliere commenti e suggerimenti.  Queste estensioni sono solo per i dispositivi di sviluppo e verranno rimosse quando viene fornita l'estensione reale.

Se si è interessati a provare le estensioni disponibili, seguire `MSFT_preview` questa procedura per aggiornare il progetto:
1. Seguire uno degli approcci precedenti per integrare un caricatore OpenXR nel progetto.
2. Sostituire le intestazioni OpenXR standard nel progetto con le intestazioni di anteprima del <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">repo OpenXR</a>di Realtà mista GitHub .

Per attivare quindi il supporto dell'estensione di anteprima nel pc HoloLens 2 o desktop di destinazione:
  1. Per assicurarsi di avere la versione più recente [](openxr.md#roadmap) del runtime OpenXR con tutte le estensioni presenti, avviare l'app  **Dello Store** dal dispositivo o dall'emulatore di destinazione, aprire il menu in alto a destra, selezionare Download e aggiornamenti e scegliere Scarica **aggiornamenti.**
  2. Installare <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">l'Strumenti di sviluppo OpenXR Windows Mixed Reality'app</a> dal Microsoft Store nel dispositivo di destinazione ed eseguirla.
  3. Passare alla scheda **Developer Impostazioni** e abilitare Use latest **preview OpenXR runtime (Usa l'anteprima più recente del runtime OpenXR).**  In questo modo viene attivato il runtime di anteprima nel dispositivo, in cui sono attivate le estensioni di anteprima.
     ![OpenXR Strumenti di sviluppo per l Windows Mixed Reality app per sviluppatori Impostazioni scheda](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Verificare che la versione  **del runtime** visualizzata nella scheda Stato sistema del Strumenti di sviluppo [OpenXR](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) per Windows Mixed Reality corrisponda alla versione richiesta delle estensioni di anteprima che si prevede di provare.  In questo caso, l'estensione dovrebbe essere visualizzata **nell'elenco** Estensioni.  Quando un'estensione stabile è disponibile, l'estensione di anteprima verrà rimossa.<br />
     ![OpenXR Strumenti di sviluppo per la Windows Mixed Reality stato del sistema dell'app](images/mixed-reality-openxr-developer-tools-status.png)

Vedere il <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repo Mixed Reality OpenXR per</a> la documentazione di queste estensioni di anteprima ed esempi su come usarle.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi di funzionamento con lo sviluppo OpenXR, consultare i suggerimenti per la [risoluzione dei problemi.](openxr-troubleshooting.md)