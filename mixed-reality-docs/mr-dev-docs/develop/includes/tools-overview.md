---
ms.openlocfilehash: e8eb162b1d2d1e416ba90530f41d2724a960ca11
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101882259"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Banner con logo di Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile il flusso [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) come versione ottimale per iniziare nuovi progetti, eseguendo l'aggiornamento alla revisione più recente per usufruire delle ultime fix stabili.
* La raccomandazione attuale consiste nell'usare **[unity 2019,4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**, ovvero la build LTS necessaria per MRTK V2.
* Se per motivi specifici è necessario usare una versione diversa di Unity, è supportata l'installazione side-by-side di versioni diverse di Unity.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. installare lo strumento per la funzionalità di realtà mista

Lo [strumento per la funzionalità di realtà mista](../unity/welcome-to-mr-feature-tool.md) è un nuovo modo per gli sviluppatori di individuare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity. 

È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

![MRTK](../../design/images/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. 

* Installare il pacchetto del Toolkit per la realtà mista seguendo le [istruzioni di installazione e utilizzo](../unity/welcome-to-mr-feature-tool.md#system-requirements) e selezionando il pacchetto di **mixed reality Toolkit Foundation** .

Si consiglia di completare la sezione introduttiva nei percorsi di sviluppo [HoloLens](../unity/unity-development-overview.md#1-getting-started) o [VR](../unity/unity-development-wmr-overview.md#1-getting-started) . Se si sta già seguendo il percorso di sviluppo con Unity per HoloLens, completare i rimanenti passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](../unity/tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Si noti che le istruzioni di installazione sono destinate alla più recente combinazione stabile di versioni di MRTK e Unity, che sono **MRTK 2.5.1** e **Unity 2019,4 LTS**.

> [!NOTE]
> Se non si vuole usare MRTK per Unity, è necessario [creare script per tutte le interazioni e i comportamenti](../unity/configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner di Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>Altri strumenti [facoltativo]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bit di codice e componenti che non possono essere eseguiti direttamente in HoloLens o nei visori VR immersive, ma che si aggiungono a questi strumenti per creare esperienze per Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a>: raccolta di script e componenti condivisi.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando configuri il computer di sviluppo per lo sviluppo per HoloLens, assicurati che soddisfi i requisiti di sistema sia di <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> che di <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Per eseguire l'app su un dispositivo HoloLens, è necessario seguire le [istruzioni di installazione del Portale di dispositivi di Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Se si prevede di usare l'[emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Per iniziare a usare l'emulatore di HoloLens, vedi [Uso dell'emulatore di HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

#### <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](/hololens/security-adminless-os#device-owner).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerire all'amministratore IT/MDM di abilitare il [criterio ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) del CSP per il dispositivo specifico o per un gruppo di dispositivi dello sviluppatore. 
    * Questo criterio può essere impostato tramite [pacchetti di provisioning](/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Per altre informazioni sulla gestione dei dispositivi, vedere la panoramica sulla **[gestione dei dispositivi HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Impossibile distribuire tramite USB

Se non si riesce a distribuire un'applicazione direttamente tramite USB, verificare che siano soddisfatti tutti i requisiti di installazione sopra elencati e seguire l'[esercitazione dettagliata](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
</tr><tr>
<td> Processore</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading <b>Desktop:</b> CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading <b>OPPURE</b> equivalente quad-core 4,2 GHz AMD FX4350</td><td> <b>Desktop:</b> Intel Desktop i7 sesta generazione (6 core) <b>OPPURE</b> AMD Ryzen 5 1600 (6 core, 12 thread)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12<b>Desktop:</b> GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12</td><td><b>Desktop:</b> GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12</td>
</tr><tr>
<td> Versione WDDM driver GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potenza termica</td><td colspan="2"> Almeno 15 W</td>
</tr><tr>
<td> Porte per scheda video</td><td colspan="2"> Porta per scheda video disponibile 1x per&#160;visore VR (HDMI 1.4 o DisplayPort 1.2 per visori VR 60 Hz, HDMI 2.0 o DisplayPort 1.2 per visori VR 90 Hz)</td>
</tr><tr>
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

Se non si ha familiarità con lo sviluppo di MRTK con Unity, è consigliabile seguire il nostro percorso di sviluppo con Unity:

> [!div class="nextstepaction"]
> [Inizia il percorso in Unity per HoloLens](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [Inizia il percorso in Unity per VR](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo con Unity per HoloLens delineato, l'attività successiva consiste nel seguire la serie di esercitazioni su HoloLens 2.

> [!div class="nextstepaction"]
> [Serie di esercitazioni su HoloLens 2](../unity/tutorials/mr-learning-base-01.md)

Se si segue il percorso in Unity per VR, l'attività successiva consiste nel configurare il progetto.

> [!div class="nextstepaction"]
> [Configurazione del progetto per WMR](../unity/configure-unity-project.md)

È sempre possibile tornare ai checkpoint di sviluppo con Unity per [HoloLens](../unity/unity-development-overview.md#1-getting-started) e [VR](../unity/unity-development-wmr-overview.md#1-getting-started) in qualsiasi momento.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile installare [Unreal Engine versione 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o versione successiva per sfruttare appieno il supporto di HoloLens incorporato.

Passare alla scheda **libreria** dell'utilità di avvio Epic Games, selezionare la freccia a discesa accanto a **Avvia** e fare clic su **Opzioni**. In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).
![MRTK](../../develop/images/Unreal_Install_Option_HoloLens2.png)

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importare Mixed Reality Toolkit (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.

Per l'installazione, è consigliabile completare la [sezione introduttiva](../unreal/unreal-development-overview.md#1-getting-started) del nostro [percorso di sviluppo con Unreal](../unreal/unreal-development-overview.md). Se si sta già seguendo il percorso di sviluppo con Unreal, completare il resto dei passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Immagine del logo di Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se non si vuole usare MRTK per Unreal, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.

#### <a name="other-tools-optional"></a>Altri strumenti [facoltativo]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bit di codice e componenti che non possono essere eseguiti direttamente in HoloLens o nei visori VR immersive, ma che si aggiungono a questi strumenti per creare esperienze per Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a>: raccolta di script e componenti condivisi.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il PC per lo sviluppo per HoloLens, verificare che vengano soddisfatti i requisiti di sistema sia di [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) sia di <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Per eseguire l'app su un dispositivo HoloLens, è necessario seguire le [istruzioni di installazione del Portale di dispositivi di Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Se si prevede di usare l'[emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

#### <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](/hololens/security-adminless-os#device-owner).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerire all'amministratore IT/MDM di abilitare il [criterio ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) del CSP per il dispositivo specifico o per un gruppo di dispositivi dello sviluppatore. 
    * Questo criterio può essere impostato tramite [pacchetti di provisioning](/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Per altre informazioni sulla gestione dei dispositivi, vedere la panoramica sulla **[gestione dei dispositivi HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Impossibile distribuire tramite USB

Se non si riesce a distribuire un'applicazione direttamente tramite USB, verificare che siano soddisfatti tutti i requisiti di installazione sopra elencati e seguire l'[esercitazione dettagliata](../unreal/tutorials/unreal-uxt-ch6.md).

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
</tr><tr>
<td> Processore</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading <b>Desktop:</b> CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading <b>OPPURE</b> equivalente quad-core 4,2 GHz AMD FX4350</td><td> <b>Desktop:</b> Intel Desktop i7 sesta generazione (6 core) <b>OPPURE</b> AMD Ryzen 5 1600 (6 core, 12 thread)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12<b>Desktop:</b> GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12</td><td><b>Desktop:</b> GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12</td>
</tr><tr>
<td> Versione WDDM driver GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potenza termica</td><td colspan="2"> Almeno 15 W</td>
</tr><tr>
<td> Porte per scheda video</td><td colspan="2"> Porta per scheda video disponibile 1x per&#160;visore VR (HDMI 1.4 o DisplayPort 1.2 per visori VR 60 Hz, HDMI 2.0 o DisplayPort 1.2 per visori VR 90 Hz)</td>
</tr><tr>
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

Se non si ha familiarità con lo sviluppo di MRTK con Unreal, è consigliabile seguire il nostro percorso di sviluppo con Unreal:

> [!div class="nextstepaction"]
> [Iniziare il percorso Unreal](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, l'attività successiva consiste nel seguire la serie di esercitazioni su HoloLens 2.

> [!div class="nextstepaction"]
> [Serie di esercitazioni su HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](../unreal/unreal-development-overview.md#1-getting-started) in qualsiasi momento.

# <a name="native-openxr"></a>[Nativo (OpenXR)](#tab/native)

 ![Sviluppo di app native](../images/native_logo_banner.png)

Per lo sviluppo di app OpenXR native non è disponibile un motore da scaricare. È possibile trovare tutti gli elementi necessari per iniziare lo sviluppo nel documento [Informazioni di base su OpenXR](../native/openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il PC per lo sviluppo per HoloLens, verificare che vengano soddisfatti i requisiti di sistema di <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Per eseguire l'app su un dispositivo HoloLens, è necessario seguire le [istruzioni di installazione del Portale di dispositivi di Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Se si prevede di usare l'[emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](/hololens/security-adminless-os#device-owner).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerire all'amministratore IT/MDM di abilitare il [criterio ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) del CSP per il dispositivo specifico o per un gruppo di dispositivi dello sviluppatore. 
    * Questo criterio può essere impostato tramite [pacchetti di provisioning](/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Per altre informazioni sulla gestione dei dispositivi, vedere la panoramica sulla **[gestione dei dispositivi HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
</tr><tr>
<td> Processore</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading <b>Desktop:</b> CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading <b>OPPURE</b> equivalente quad-core 4,2 GHz AMD FX4350</td><td> <b>Desktop:</b> Intel Desktop i7 sesta generazione (6 core) <b>OPPURE</b> AMD Ryzen 5 1600 (6 core, 12 thread)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12<b>Desktop:</b> GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12</td><td><b>Desktop:</b> GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12</td>
</tr><tr>
<td> Versione WDDM driver GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potenza termica</td><td colspan="2"> Almeno 15 W</td>
</tr><tr>
<td> Porte per scheda video</td><td colspan="2"> Porta per scheda video disponibile 1x per&#160;visore VR (HDMI 1.4 o DisplayPort 1.2 per visori VR 60 Hz, HDMI 2.0 o DisplayPort 1.2 per visori VR 90 Hz)</td>
</tr><tr>
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

Se non si ha familiarità con lo sviluppo nativo con MRTK, è consigliabile seguire il nostro percorso di sviluppo nativo:

> [!div class="nextstepaction"]
> [Iniziare il percorso Nativo](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo nativo che abbiamo delineato, l'attività successiva consiste nel configurare l'ambiente di sviluppo per HoloLens 2.

> [!div class="nextstepaction"]
> [Configurazione per HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

È sempre possibile tornare ai [checkpoint per lo sviluppo nativo](../native/directx-development-overview.md#1-getting-started) in qualsiasi momento.