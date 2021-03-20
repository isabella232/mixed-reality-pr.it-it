---
title: Installare gli strumenti
description: MRTK-Unity, installare la pagina della documentazione degli strumenti
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Toolkit per realtà mista, installazione, aggiornamento, strumenti, introduzione, nozioni di base, Unity, Visual Studio, Toolkit, auricolare in realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, installazione, Windows, HoloLens, emulatore
ms.openlocfilehash: a22a032261f3734167b229618f40db112b43c0f7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "102236962"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? È possibile installare l' [emulatore di HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)  per testare alcune funzionalità di app realtà miste senza HoloLens. È anche possibile usare il [simulatore di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)  per testare le app per realtà mista per auricolari immersivi.

Questa pagina consente di installare gli strumenti necessari per usare MRTK con Unity. Se si è interessati a esplorare altre piattaforme di sviluppo di realtà miste, vedere la pagina [Introduzione allo sviluppo di realtà mista](https://docs.microsoft.com/windows/mixed-reality/develop/development?tabs=unity) .

È possibile usare il [Toolkit di realtà mista per](https://github.com/Microsoft/MixedRealityToolkit-Unity)la simulazione di input di Unity per testare vari tipi di interazioni di input, ad esempio il rilevamento manuale e la verifica degli occhi.

|Suggerimento: aggiungere un segnalibro a questa pagina e controllarlo regolarmente per mantenersi aggiornati sulla versione più recente di ogni strumento consigliato per lo sviluppo di realtà miste.|
|---|

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione

| Strumento | Note |
|---------|---------|
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (collegamento per l'installazione manuale)</a><br><br>Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista.  | **Installazione di Windows 10** <br> Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra. <br><br>Vedi le [note sulla versione aggiornate](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10. **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti a livello aziendale**<br>Se il computer è gestito dal reparto IT di un'organizzazione, potrebbe essere necessario contattare il reparto per eseguire l'aggiornamento. <br><br> **Versioni 'N' di Windows**<br> i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Immagine del logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o versione successiva)** (collegamento per l'installazione)</a> <br><br>Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Installazione di Visual Studio 2019** <br> Assicurati di installare i carichi di lavoro seguenti: <br><br>*● Sviluppo per desktop con C++*<br>*● Sviluppo per la piattaforma UWP (Universal Windows Platform)*<br><br>Nel carico di lavoro della piattaforma UWP assicurati di selezionare il componente facoltativo seguente se prevedi di sviluppare per HoloLens:<br><br>*● Connettività dispositivi USB*<br><br>**Nota su Unity**<br>a meno che non si stia intenzionalmente tentando di installare una versione più recente (non LTS) di Unity per uno scopo specifico, è consigliabile *non* installare il carico di lavoro Unity come parte dell'installazione di Visual Studio e installare invece il flusso **Unity 2019 LTS** come indicato di seguito.<br><br>**Problemi noti**<br>esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurarsi di eseguire l'aggiornamento a **Visual Studio 2019 versione 16.8 o successiva**. |
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (collegamento per l'installazione manuale)</a> <br><br>Include le intestazioni, le librerie, i metadati e gli strumenti più recenti per la creazione di app di Windows 10 in HoloLens 2. | **Per creare app HoloLens 2, è necessario installare Windows SDK, build 18362 o versioni successive.**<br> <br> Se si sviluppano solo applicazioni per gli auricolari di realtà mista di Windows desktop o HoloLens (1a generazione), è possibile usare il Windows SDK installato da Visual Studio 2019. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**Emulatore HoloLens 2 (Windows olografico, versione 20H2 aggiornamento 2021 febbraio)** (collegamento di installazione: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore HoloLens (prima generazione)** (collegamento per l'installazione: 10.0.17763.134)</a> <br><br>L'emulatore permette di eseguire le applicazioni in un'immagine di macchina virtuale HoloLens senza un dispositivo HoloLens fisico.<br> <br> | Vedi [Uso dell'emulatore di HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) per altre informazioni su come iniziare a usare l'emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br> <br> **Nota sull'emulatore HoloLens (prima generazione)** <br>. Se si sta installando l'emulatore HoloLens (prima generazione) con Visual Studio 2019, è necessario deselezionare i modelli di Visual Studio e [installarli da Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Ora che si dispone di Windows 10, Visual Studio e Windows 10 SDK pronto per l'uso, si userà Unity come motore per la compilazione.

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile il flusso [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) come versione ottimale per iniziare nuovi progetti, eseguendo l'aggiornamento alla revisione più recente per usufruire delle ultime fix stabili.

* La raccomandazione attuale consiste nell'usare [unity 2019,4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4). È supportata anche Unity 2018,4 LTS.
* Se si vuole usare le funzionalità di anteprima [mista OpenXR](https://docs.microsoft.com/windows/mixed-reality/develop/unity/openxr-getting-started) con MRTK, sarà necessario unity 2020,2 o versione successiva.
* Se per motivi specifici è necessario usare una versione diversa di Unity, è supportata l'installazione side-by-side di versioni diverse di Unity.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. installare lo strumento per la funzionalità di realtà mista

Lo [strumento per la funzionalità di realtà mista](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per gli sviluppatori di individuare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.

È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto Unity scelto.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

È possibile scaricare il pacchetto del Toolkit per la realtà mista seguendo le [istruzioni di installazione e utilizzo](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) e selezionando il pacchetto di base per il Toolkit di realtà misto.

Se si preferisce scaricare manualmente i pacchetti MRTK da GitHub, visitare la pagina relativa alla versione in [realtà mista Toolkit-Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

| Nota: è possibile sviluppare e distribuire le app per HoloLens, cuffie immersive VR o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità. |
|---|

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il computer di sviluppo per lo sviluppo di HoloLens, assicurarsi che soddisfi i requisiti di sistema per [Unity](https://docs.unity3d.com/Manual/system-requirements.html) e Visual Studio. Per eseguire l'app su un dispositivo HoloLens, è necessario seguire le [istruzioni di installazione del Portale di dispositivi di Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). Se si prevede di usare l'[emulatore HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements).

Per iniziare a usare l'emulatore di HoloLens, vedi [Uso dell'emulatore di HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

### <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](https://docs.microsoft.com/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens2-compliance).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerisce che l'amministratore IT/MDM Abilita i [criteri CSP ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) per il dispositivo specifico o per un gruppo di dispositivi dello sviluppatore.
Questo criterio può essere impostato tramite [pacchetti di provisioning](https://docs.microsoft.com/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](https://docs.microsoft.com/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)

| Nota: per altre informazioni sulla gestione dei dispositivi, vedere Panoramica di gestione dei dispositivi HoloLens.|
|---|

Impossibile distribuire tramite USB

Se non si riesce a distribuire un'applicazione direttamente tramite USB, verificare che siano soddisfatti tutti i requisiti di installazione sopra elencati e seguire l'[esercitazione dettagliata](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Requisiti per visori VR immersive

| Nota: le linee guida seguenti sono le specifiche minime e consigliate correnti per il PC per lo sviluppo di auricolari immersivi (VR) e vengono aggiornate regolarmente.|
|---|

| Avviso: non confondere questo valore con le [linee guida per la compatibilità hardware del PC minime](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che delineano le specifiche del PC consumer a cui è necessario destinare l'app o il gioco per cuffie immersive (VR).|
|---|

Se il PC per lo sviluppo di cuffie immersive non ha porte HDMI e/o USB 3,0 di dimensioni complete, è necessario disporre di [Adapter ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)per connettere l'auricolare.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

. | Minima | Implementazione consigliata
--- |--- |---
Processore | Notebook: CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading Desktop: CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading OPPURE equivalente quad-core 4,2 GHz AMD FX4350| Desktop: GPU Intel Desktop i7 6a generazione (6 core) o AMD Ryzen 5 1600 (6 core, 12 thread) | Notebook: GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12Desktop: GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12 | Desktop: GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12
Versione WDDM driver GPU | Driver WDDM 2.2
Potenza termica | Almeno 15 W
Porte per scheda video | 1x porta di visualizzazione grafica disponibile per auricolare (HDMI 1,4 o DisplayPort 1,2 per cuffie 60Hz, HDMI 2,0 o DisplayPort 1,2 per cuffie 90Hz)
Risoluzione dello schermo | Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel
Memory | 8 GB di RAM o superiore | Almeno 16 GB di RAM
Archiviazione: | >10 GB di spazio disponibile aggiuntivo
Porte USB | Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) Nota: USB deve fornire un minimo di 900mA
Bluetooth | Bluetooth 4.0 (per la connettività degli accessori)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Ora che sono stati installati gli strumenti, è consigliabile seguire la serie di esercitazioni MRTK HoloLens 2.
> [!div class="nextstepaction"]
> [Serie di esercitazioni su HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)