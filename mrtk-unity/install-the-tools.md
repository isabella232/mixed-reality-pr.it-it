---
title: Installare gli strumenti
description: MRTK-Unity, installare la pagina della documentazione degli strumenti
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, mixed reality toolkit, installare, aggiornato, strumenti, iniziare, nozioni di base, unity, visual studio, toolkit, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, installazione, Windows, HoloLens, emulatore
ms.openlocfilehash: 402693ca06e00a4c6c4ad7f2a81b38d443c4346f
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772404"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? Puoi installare [l'emulatore HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)  per testare alcune funzionalità delle app di realtà mista senza HoloLens. È anche possibile usare il [simulatore](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)  di Windows Mixed Reality per testare le app di realtà mista per visori VR immersive.

Questa pagina consente di installare gli strumenti necessari per usare MRTK con Unity. Se si è interessati a esplorare altre piattaforme di sviluppo di realtà mista, vedere la pagina Introduzione allo sviluppo [di realtà mista.](/windows/mixed-reality/develop/development?tabs=unity)

Puoi usare [Mixed Reality Toolkit per](https://github.com/Microsoft/MixedRealityToolkit-Unity)la simulazione di input di Unity per testare vari tipi di interazioni di input, ad esempio il tracciamento delle mani e il tracciamento oculare.

|SUGGERIMENTO: aggiungere un segnalibro a questa pagina e controllarla regolarmente per rimanere aggiornati sulla versione più recente di ogni strumento consigliato per lo sviluppo di realtà mista.|
|---|

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione

| Strumento | Note |
|---------|---------|
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (collegamento per l'installazione manuale)</a><br><br>Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista.  | **Installazione di Windows 10** <br> Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra. <br><br>Vedi le [note sulla versione aggiornate](/windows/mixed-reality/enthusiast-guide/mixed-reality-software) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10. **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti a livello aziendale**<br>Se il computer è gestito dal reparto IT di un'organizzazione, potrebbe essere necessario contattare il reparto per eseguire l'aggiornamento. <br><br> **Versioni 'N' di Windows**<br> i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Immagine del logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o versione successiva)** (collegamento per l'installazione)</a> <br><br>Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Installazione di Visual Studio 2019** <br> Assicurati di installare i carichi di lavoro seguenti: <br><br>*● Sviluppo per desktop con C++*<br>*● Sviluppo per la piattaforma UWP (Universal Windows Platform)*<br><br>Nel carico di lavoro della piattaforma UWP assicurati di selezionare il componente facoltativo seguente se prevedi di sviluppare per HoloLens:<br><br>*● Connettività dispositivi USB*<br><br>**Nota su Unity**<br>a meno che non si stia intenzionalmente tentando di installare una versione più recente (non LTS) di Unity per uno scopo specifico, è consigliabile *non* installare il carico di lavoro Unity come parte dell'installazione di Visual Studio e installare invece il flusso **Unity 2019 LTS** come indicato di seguito.<br><br>**Problemi noti**<br>esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurarsi di eseguire l'aggiornamento a **Visual Studio 2019 versione 16.8 o successiva**. |
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (collegamento per l'installazione manuale)</a> <br><br>Include le intestazioni, le librerie, i metadati e gli strumenti più recenti per la creazione di app di Windows 10 in HoloLens 2. | **Per creare app HoloLens 2, è necessario installare Windows SDK, build 18362 o versioni successive.**<br> <br> Se si sviluppano solo applicazioni per visori VR Windows Mixed Reality desktop o HoloLens (prima generazione), è possibile usare il Windows SDK installato da Visual Studio 2019. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**emulatore HoloLens 2 (Windows Holographic, versione 20H2 Aggiornamento di febbraio 2021)** (collegamento di installazione: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore HoloLens (prima generazione)** (collegamento per l'installazione: 10.0.17763.134)</a> <br><br>L'emulatore permette di eseguire le applicazioni in un'immagine di macchina virtuale HoloLens senza un dispositivo HoloLens fisico.<br> <br> | Vedi [Uso dell'emulatore di HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) per altre informazioni su come iniziare a usare l'emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br> <br> **Nota sull'emulatore HoloLens (prima generazione)** <br>. Se si sta installando l'emulatore HoloLens (prima generazione) con Visual Studio 2019, è necessario deselezionare i modelli di Visual Studio e [installarli da Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Ora che l'SDK Windows 10, Visual Studio e Windows 10 è pronto per l'uso, si userà Unity come motore su cui basarsi.

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile il flusso [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) come versione ottimale per iniziare nuovi progetti, eseguendo l'aggiornamento alla revisione più recente per usufruire delle ultime fix stabili.

* La raccomandazione corrente è di usare [Unity 2019.4 LTS.](https://unity3d.com/unity/qa/lts-releases?version=2019.4) È supportato anche Unity 2018.4 LTS.
* Per usare le funzionalità di anteprima di [Mixed Reality OpenXR](/windows/mixed-reality/develop/unity/openxr-getting-started) con MRTK, è necessario Unity 2020.2 o versione successiva.
* Se per motivi specifici è necessario usare una versione diversa di Unity, è supportata l'installazione side-by-side di versioni diverse di Unity.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Installare lo strumento di funzionalità di realtà mista

Lo [strumento di funzionalità di realtà mista](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per gli sviluppatori di individuare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity.

È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Dopo aver convalidato i pacchetti desiderati, lo strumento Funzionalità di realtà mista li scarierà nel progetto Unity preferito.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

È possibile scaricare il pacchetto Mixed Reality Toolkit seguendo le [istruzioni](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) di installazione e utilizzo e selezionando il pacchetto Mixed Reality Toolkit Foundation.

Se si preferisce scaricare manualmente i pacchetti MRTK da GitHub, visitare la pagina release all'indirizzo [Mixed Reality Toolkit-Unity (GitHub).](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

| Nota: è possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità. |
|---|

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il PC di sviluppo per lo sviluppo HoloLens, assicurarsi che soddisfi i requisiti di sistema per [Unity](https://docs.unity3d.com/Manual/system-requirements.html) e Visual Studio. Per eseguire l'app su un dispositivo HoloLens, è necessario seguire le [istruzioni di installazione del Portale di dispositivi di Windows](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). Se si prevede di usare l'[emulatore HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements).

Per iniziare a usare l'emulatore di HoloLens, vedi [Uso dell'emulatore di HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

### <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](/hololens/hololens2-compliance).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerendo che l'amministratore IT/MDM abilita [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) dei criteri CSP per il dispositivo specifico o un gruppo di dispositivi per sviluppatori.
Questo criterio può essere impostato tramite [pacchetti di provisioning](/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

| Nota: per altre informazioni sulla gestione dei dispositivi, vedere Panoramica della gestione dei dispositivi HoloLens.|
|---|

Impossibile distribuire tramite USB

Se non si riesce a distribuire un'applicazione direttamente tramite USB, verificare che siano soddisfatti tutti i requisiti di installazione sopra elencati e seguire l'[esercitazione dettagliata](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Requisiti per visori VR immersive

| Nota: le linee guida seguenti sono le specifiche minime e consigliate correnti per il PC di sviluppo di visori VR immersive e vengono aggiornate regolarmente.|
|---|

| Avviso: non confondere questo comportamento con le linee guida minime per la compatibilità hardware del [PC,](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)che delineano le specifiche del PC consumer a cui è consigliabile scegliere come destinazione l'app o il gioco per visori VR immersive.|
|---|

Se il PC di sviluppo di visori VR immersive non ha porte HDMI e/o USB 3.0 di dimensioni complete, sono necessarie schede per connettere il visore VR. [ ](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)

Esistono attualmente [problemi noti](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

. | Minima | Implementazione consigliata
--- |--- |---
Processore | Notebook: CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading Desktop: CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading OPPURE equivalente quad-core 4,2 GHz AMD FX4350| Desktop: GPU Intel Desktop i7 di 6a generazione (6 Core) O AMD Ryzen 5 1600 (6 Core, 12 thread) | Notebook: GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12Desktop: GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12 | Desktop: GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12
Versione WDDM driver GPU | Driver WDDM 2.2
Potenza termica | Almeno 15 W
Porte per scheda video | Porta di visualizzazione grafica 1x disponibile per visori (HDMI 1.4 o DisplayPort 1.2 per visori a 60 Hz, HDMI 2.0 o DisplayPort 1.2 per visori a 90 Hz)
Risoluzione dello schermo | Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel
Memory | 8 GB di RAM o superiore | Almeno 16 GB di RAM
Archiviazione: | >10 GB di spazio disponibile aggiuntivo
Porte USB | Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) Nota: USB deve fornire un minimo di 900mA
Bluetooth | Bluetooth 4.0 (per la connettività degli accessori)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Dopo aver installato gli strumenti, è consigliabile seguire la serie di esercitazioni HoloLens 2 MRTK.
> [!div class="nextstepaction"]
> [HoloLens 2 Tutorial Series](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)
