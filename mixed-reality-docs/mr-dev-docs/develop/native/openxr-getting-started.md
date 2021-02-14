---
title: Informazioni di base su OpenXR
description: Inizia a usare l'API OpenXR portatile standard in realtà mista di Windows e gli auricolari HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, realtà mista di Windows, OpenXR Strumenti di sviluppo, DirectX, nativo, app nativa, motore personalizzato, middleware, Guida introduttiva, 101, estensioni di anteprima, versione runtime di OpenXR, stato del sistema
ms.openlocfilehash: 99bf2e19c0bd7708f8c2421d7a466e77a6a75d84
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496069"
---
# <a name="getting-started-with-openxr"></a>Informazioni di base su OpenXR

È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introduzione a OpenXR per HoloLens 2

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare una versione recente dell'emulatore di HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Se si usa un'immagine dell'emulatore recente o se il dispositivo ha aggiornato il sistema operativo, è necessario che OpenXR 1,0 sia già pronto per iniziare.
2. Assicurarsi di disporre del runtime di OpenXR più recente con tutte le [estensioni](openxr.md#roadmap) presenti avviando l'app dello **Store** dal dispositivo o dall'emulatore.
    * Aprire il menu in alto a destra, selezionare **download e aggiornamenti** e scegliere **Scarica aggiornamenti**.  

> [!NOTE]
> Se si usa l'emulatore, l'immagine dell'emulatore verrà reimpostata ogni volta che viene avviata, quindi la scommessa migliore consiste nel verificare di disporre [della versione più recente dell'immagine dell'emulatore HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introduzione a OpenXR per le cuffie con la realtà mista di Windows

Per iniziare a sviluppare applicazioni OpenXR per cuffie di realtà miste di Windows Immersive:

1. Assicurarsi che sia in esecuzione almeno l'aggiornamento 2019 di Windows 10 (1903), che è il requisito minimo per gli utenti finali di Windows Mixed Reality per eseguire le applicazioni OpenXR.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento con <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 Update Assistant</a>.
2. Configurare un auricolare di realtà mista di Windows o seguire le istruzioni per [abilitare il simulatore di realtà mista di Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

Questo è tutto.  Il runtime di OpenXR per la realtà mista di Windows viene installato e reso attivo automaticamente per tutti gli utenti della realtà mista di Windows.  Il Microsoft Store mantiene il runtime aggiornato.

Per attivare di nuovo il runtime di OpenXR per la realtà mista di Windows, avviare il portale di realtà mista dal menu Start e selezionare "Correggi" nella parte superiore della finestra.  Se il pulsante non è presente, il runtime di OpenXR è già attivo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Ottenere il Strumenti di sviluppo OpenXR per la realtà mista di Windows

Per provare il runtime di OpenXR per la realtà mista di Windows, è possibile installare il <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">OpenXR strumenti di sviluppo per l'app di realtà mista Windows</a>.  Questa app fornisce una demo delle varie funzionalità di OpenXR, insieme a una pagina di stato del sistema con informazioni chiave sul runtime attivo e sull'auricolare corrente.

Quando si usa l'emulatore HoloLens 2, il modo più semplice per installare la Strumenti di sviluppo OpenXR per la realtà mista di Windows è tramite il [portale del dispositivo Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Passare alla pagina "OpenXR" e quindi fare clic sul pulsante "Installa" in "funzionalità per sviluppatori", che funziona anche su dispositivi HoloLens 2 fisici.

![OpenXR Strumenti di sviluppo per app di realtà mista di Windows](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Assicurarsi di [installare gli strumenti](../install-the-tools.md) necessari per lo sviluppo di OpenXR, se non è già stato fatto.

Il progetto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> Mostra un semplice esempio di OpenXR con i file di progetto Win32 e UWP HoloLens 2 in Visual Studio. Poiché la soluzione contiene un progetto HoloLens UWP, è necessario che il [carico di lavoro di sviluppo piattaforma UWP (Universal Windows Platform)](../install-the-tools.md#installation-checklist) installato in Visual Studio per aprirlo completamente.

Sebbene i file di progetto Win32 e UWP siano separati a causa delle differenze nella creazione di pacchetti e distribuzione, il codice dell'app all'interno di ogni progetto è quasi identico.

Dopo la compilazione di un desktop Win32 OpenXR. EXE, è possibile usarlo con un auricolare VR su qualsiasi piattaforma desktop VR che supporta OpenXR, indipendentemente dal tipo di auricolare.

Dopo aver compilato un pacchetto dell'app OpenXR UWP, è possibile [distribuire il pacchetto](../platform-capabilities-and-apis/using-visual-studio.md) in un dispositivo HoloLens 2 o nell'emulatore HoloLens 2.

## <a name="learning-the-openxr-api"></a>Apprendimento dell'API OpenXR

Per una panoramica dell'API OpenXR, vedere questo video di 60 minuti dell'esempio <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> in Visual Studio.  Il video mostra in che modo ognuno dei principali componenti dell'API OpenXR può essere usato nel proprio motore e illustra anche alcune applicazioni compilate in OpenXR oggi:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrare il caricatore OpenXR in un progetto

Per iniziare a usare OpenXR in un progetto esistente, è necessario includere il caricatore OpenXR.  Il caricatore rileva il runtime OpenXR attivo sul dispositivo e fornisce l'accesso alle funzioni di base e alle funzioni di estensione che implementa.

È possibile [fare riferimento al pacchetto NuGet OpenXR ufficiale](#reference-official-openxr-nuget-package) dal progetto di Visual Studio o [includere l'origine del caricatore OpenXR ufficiale](#include-official-openxr-loader-source) dal repository GitHub Khronos.  Entrambi gli approcci consentono di accedere alle funzionalità di base di OpenXR 1,0, più pubblicate `KHR` `EXT` ed `MSFT` estensioni.

Se si è interessati a provare `MSFT_preview` anche le estensioni, è possibile [copiare le intestazioni OpenXR in anteprima](#using-preview-extensions) dal repository GitHub della realtà mista.

### <a name="reference-official-openxr-nuget-package"></a>Pacchetto NuGet OpenXR ufficiale di riferimento

Il <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">pacchetto NuGet **OpenXR. loader**</a> è il modo più semplice per fare riferimento a un caricatore OpenXR predefinito. DLL nella soluzione Visual Studio C++.  In questo modo sarà possibile accedere alle funzionalità di base di OpenXR 1,0, più pubblicate `KHR` `EXT` ed `MSFT` estensioni.

Per aggiungere un riferimento al pacchetto NuGet OpenXR. loader alla soluzione Visual Studio C++:
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto che userà OpenXR e selezionare **Gestisci pacchetti NuGet...**.
2. Passare alla scheda **Sfoglia** e cercare **OpenXR. loader**.
3. Selezionare il pacchetto **OpenXR. loader** e selezionare installa nel riquadro dei dettagli a destra.
4. Selezionare OK per accettare le modifiche apportate al progetto.
5. Aggiungere `#include <openxr/openxr.h>` a un file di origine per iniziare a usare l'API OpenXR.

Per un esempio dell'API OpenXR in azione, vedere l'app di esempio <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Includi origine del caricatore OpenXR ufficiale

Se si vuole creare il caricatore manualmente, ad esempio per evitare il caricatore aggiuntivo. DLL, è possibile effettuare il pull delle origini ufficiali del caricatore OpenXR di Khronos nel progetto.  In questo modo sarà possibile accedere alle funzionalità di base di OpenXR 1,0, più pubblicate `KHR` `EXT` ed `MSFT` estensioni.

Per iniziare, seguire le istruzioni riportate nel <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repository Khronos OpenXR-SDK su GitHub</a>.  Il progetto è configurato per la compilazione con CMake. Se si usa MSBuild, è necessario copiare il codice nel progetto.

## <a name="using-preview-extensions"></a>Uso delle estensioni di anteprima

Le `MSFT_preview` estensioni elencate nella [Roadmap di estensione](openxr.md#roadmap) sono le estensioni del fornitore sperimentali visualizzate come anteprima per raccogliere commenti e suggerimenti.  Queste estensioni sono destinate solo ai dispositivi per sviluppatori e verranno rimosse quando l'estensione reale viene fornita.

Se si è interessati a provare le estensioni disponibili `MSFT_preview` , seguire questa procedura per aggiornare il progetto:
1. Seguire uno degli approcci precedenti per integrare un caricatore OpenXR nel progetto.
2. Sostituire le intestazioni OpenXR standard nel progetto con le <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">intestazioni di anteprima del repository OpenXR realtà mista su GitHub</a>.

Per attivare il supporto dell'estensione di anteprima nel HoloLens 2 o desktop PC di destinazione:
  1. Per assicurarsi di avere la versione più recente del runtime di OpenXR con tutte le [estensioni](openxr.md#roadmap) presenti, avviare l'app dello **Store** dall'interno del dispositivo o dell'emulatore di destinazione, aprire il menu in alto a destra, selezionare **download e aggiornamenti** e scegliere **Scarica aggiornamenti**.
  2. Installare l' <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">app OpenXR strumenti di sviluppo per la realtà mista di Windows</a> dall'Microsoft Store sul dispositivo di destinazione ed eseguirla.
  3. Passare alla scheda **Impostazioni sviluppatore** e abilitare **Usa ultima versione di anteprima di OpenXR Runtime**.  In questo modo viene abilitato il runtime di anteprima nel dispositivo, in cui sono attivate le estensioni di anteprima.
     ![OpenXR Strumenti di sviluppo per la scheda impostazioni per gli sviluppatori di app di realtà mista di Windows](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Verificare che la **versione del runtime** visualizzata nella scheda stato del **sistema** del [strumenti di sviluppo OpenXR per la realtà mista di Windows](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) corrisponda alla versione richiesta delle estensioni di anteprima che si prevede di provare.  In tal caso, l'estensione verrà visualizzata nell'elenco **estensioni** .  Quando è disponibile un'estensione stabile, la relativa estensione di anteprima verrà rimossa.<br />
     ![OpenXR Strumenti di sviluppo per la scheda stato del sistema app di realtà mista di Windows](images/mixed-reality-openxr-developer-tools-status.png)

Vedere il <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repository di OpenXR per la realtà mista</a> per la documentazione di queste estensioni di anteprima ed esempi su come usarle.

## <a name="troubleshooting"></a>Risoluzione dei problemi

In caso di problemi con lo sviluppo OpenXR, vedere i suggerimenti per la [risoluzione dei problemi](openxr-troubleshooting.md).