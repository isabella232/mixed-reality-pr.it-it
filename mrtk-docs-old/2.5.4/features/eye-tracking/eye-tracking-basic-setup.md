---
title: EyeTracking_BasicSetup
description: Come configurare il tracciamento oculare in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tracciamento oculare,
ms.openlocfilehash: 891f4c7b96ba7bc26ee1afa4e28189a581eadedbda75f4dd714e894da49ed284
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228729"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Introduzione al tracciamento oculare in MRTK

Questa pagina illustra come configurare la scena di Unity MRTK per l'uso del tracciamento oculare nell'app.
Di seguito si presuppone che si inizi con una nuova scena.
In alternativa, è possibile consultare gli esempi di tracciamento oculare [di MRTK](eye-tracking-examples-overview.md) già configurati con moltissimi esempi che è possibile sviluppare direttamente.

## <a name="eye-tracking-requirements-checklist"></a>Elenco di controllo per i requisiti del tracciamento oculare

Per il corretto funzionamento del tracciamento oculare, è necessario soddisfare i requisiti seguenti.
Se non si ha di nuovo il tracciamento oculare HoloLens 2 e come è configurato il tracciamento oculare in MRTK, non c'è da preoccuparsi.
Più avanti verranno fornite informazioni dettagliate su come risolvere ognuno di essi.

1. È _necessario aggiungere un provider di dati sguardo_ fisso al sistema di input. In questo modo vengono forniti dati di tracciamento oculare dalla piattaforma.
2. La _funzionalità 'GazeInput'_ deve essere abilitata nel manifesto dell'applicazione.
   **Questa funzionalità può essere impostata in Unity 2019, ma in Unity 2018 e versioni precedenti questa funzionalità è disponibile solo in Visual Studio e tramite lo strumento di compilazione MRTK**
3. Il HoloLens **deve essere** calibrato con gli occhi per l'utente corrente. Vedere l'esempio per rilevare se un utente è o meno [calibrato con gli occhi.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Nota sulla funzionalità GazeInput

Gli strumenti di compilazione forniti da MRTK(ad esempio Mixed Reality Toolkit -> Utilities -> Build Window) possono abilitare automaticamente la funzionalità GazeInput. A tale scopo, è necessario assicurarsi che la "Funzionalità di input sguardo fisso" sia selezionata nella scheda "Opzioni di compilazione Appx":

![Strumenti di compilazione MRTK](../images/eye-tracking/mrtk_et_buildsetup.png)

Questi strumenti troveranno il manifesto AppX dopo il completamento della compilazione di Unity e aggiungeranno manualmente la funzionalità GazeInput.
**Prima di Unity 2019,** questo strumento NON è attivo quando si usa la finestra di compilazione predefinita di Unity, ad esempio File -> Build Impostazioni.

Prima di Unity 2019, quando si usa la finestra di compilazione di Unity, la funzionalità dovrà essere aggiunta manualmente dopo la compilazione di Unity, come indicato di seguito:

1. Aprire il progetto Visual Studio e quindi aprire _'Package.appxmanifest'_ nella soluzione.
2. Assicurarsi di selezionare la casella _di controllo "GazeInput"_ in _Capabilities (Funzionalità)._ Se non viene visualizzata una funzionalità _"GazeInput",_ verificare che il sistema soddisfi i prerequisiti per l'uso di [MRTK](../../install-the-tools.md#prerequisites) (in particolare la versione Windows SDK).

_Si noti che:_ È necessario eseguire questa operazione solo se si compila in una nuova cartella di compilazione.
Ciò significa che se è già stato compilato il progetto Unity e si è configurato appxmanifest in precedenza e ora è stata impostata di nuovo come destinazione la stessa cartella, non sarà necessario riapplicare le modifiche.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configurazione dettagliata del tracciamento oculare

### <a name="setting-up-the-scene"></a>Configurazione della scena

Configurare _MixedRealityToolkit_ semplicemente facendo clic su _"Mixed Reality Toolkit -> Configure..."_ nella barra dei menu.

![Configurazione di MRTK](../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configurazione dei profili MRTK necessari per il tracciamento oculare

Dopo aver impostato la scena MRTK, ti verrà chiesto di scegliere un profilo per MRTK.
È sufficiente selezionare _DefaultMixedRealityToolkitConfigurationProfile_ e quindi selezionare l'opzione _"Copia_ & Personalizza".

![Profilo MRTK](../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Creare un "provider di dati di sguardo fisso"

- Fare clic sulla _scheda "Input"_ nel profilo MRTK.
- Per modificare quello predefinito ( _'DefaultMixedRealityInputSystemProfile'),_ fare clic sul _pulsante "Clona"_ accanto. Viene visualizzato il menu _"Clone Profile" (Clona_ profilo). È sufficiente fare _clic su "Clone" (Clona)_ nella parte inferiore del menu.
- Fare doppio clic sul nuovo profilo di input, espandere _"Provider di dati di input"_ e selezionare _"+ Aggiungi provider di dati"._
- Creare un nuovo provider di dati:
  - In **Tipo** selezionare _'Microsoft.MixedReality.Toolkit. WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - Per **Platform(s) (Piattaforme)** selezionare _"Windows Universal"._

![Provider di dati MRTK](../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulazione del tracciamento oculare nell'editor di Unity

È possibile simulare l'input del tracciamento oculare nell'editor di Unity per assicurarsi che gli eventi vengano attivati correttamente prima di distribuire l'app nel HoloLens 2.
Il segnale dello sguardo fisso viene simulato semplicemente usando la posizione della fotocamera come origine dello sguardo e il vettore in avanti della fotocamera come direzione dello sguardo fisso.
Anche se è ideale per i test iniziali, si noti che non è una buona idea per i movimenti oculari rapidi.
A tale scopo, è meglio garantire test frequenti delle interazioni basate sugli occhi sul HoloLens 2.

1. **Abilitare il tracciamento oculare simulato:**
    - Fare clic sulla _scheda "Input"_ nel profilo di configurazione di MRTK.
    - Da qui passare a _"Input Data Providers" (Provider di dati di_  ->  _input) "Input Simulation Service" (Servizio simulazione input)._
    - Clonare _'DefaultMixedRealityInputSimpulationProfile'_ per apportare modifiche.
    - Selezionare la _casella di controllo "Simulate Eye Position" (Simula posizione_ oculare).

    ![MrTK eyes simulate (Simulazione occhi MRTK)](../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Disabilitare il cursore predefinito** per lo sguardo fisso con la testa: in generale, è consigliabile evitare di visualizzare un cursore con sguardo fisso o se assolutamente necessario per renderlo _molto_ sottile.
È consigliabile nascondere il cursore di sguardo fisso con la testa predefinito collegato al profilo del puntatore dello sguardo fisso MRTK per impostazione predefinita.
    - Passare al profilo di configurazione MRTK -> _'Input'_  ->  _'Pointers' (Puntatori)_
    - Clonare _'DefaultMixedRealityInputPointerProfile'_ per apportare modifiche.
    - Nella parte superiore di _'Pointer Impostazioni'_ è necessario assegnare un prefab del cursore invisibile a _'GazeCursor'._ A tale scopo, selezionare il prefab _"EyeGazeCursor"_ da MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Abilitazione dello sguardo fisso nel provider di sguardo fisso

In HoloLens v1 è stato usato lo sguardo fisso con la testa come tecnica di puntamento principale.
Anche se lo sguardo fisso con la testa è ancora disponibile tramite _GazeProvider_ in MRTK collegato alla [fotocamera,](https://docs.unity3d.com/ScriptReference/Camera.html)puoi controllare di usare lo sguardo fisso selezionando invece la casella di controllo _'IsEyeTrackingEnabled'_ nelle impostazioni dello sguardo fisso del profilo del puntatore di input.

>[!NOTE]
>Gli sviluppatori possono alternare lo sguardo fisso basato sulla testa nel codice modificando la proprietà _'IsEyeTrackingEnabled'_ di _'GazeProvider'._  

>[!IMPORTANT]
>Se uno dei requisiti di tracciamento oculare non viene soddisfatto, l'applicazione torna automaticamente alla vista basata sulla testa.

### <a name="accessing-eye-gaze-data"></a>Accesso ai dati dello sguardo fisso

Ora che la scena è impostata per l'uso del tracciamento oculare, è possibile esaminare come accedervi negli script: Accesso ai dati di tracciamento oculare tramite [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e selezioni di destinazione supportate dagli [occhi.](eye-tracking-target-selection.md)

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Test dell'app Unity in un HoloLens 2

La compilazione dell'app con il tracciamento oculare dovrebbe essere simile alla compilazione di altre app HoloLens 2 MRTK. Assicurarsi di aver abilitato la funzionalità 'Input sguardo *fisso'* come descritto in precedenza nella sezione [*Nota sulla funzionalità GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Calibrazione oculare

Infine, non dimenticare di eseguire la calibrazione oculare sul HoloLens 2.
Il sistema di tracciamento oculare non restituirà alcun input se l'utente non è calibrato.
Il modo più semplice per ottenere la calibrazione è capovolgere il visore e tornare indietro.
Verrà visualizzata una notifica di sistema che chiede all'utente di eseguire la calibrazione oculare come nuovo utente.
In alternativa, è possibile trovare la calibrazione oculare nelle impostazioni di sistema: Impostazioni > System > Calibration > Run eye calibration (Esegui calibrazione oculare).

#### <a name="eye-tracking-permission"></a>Autorizzazione per il tracciamento oculare

Quando si avvia l'app nel HoloLens 2 per la prima volta, viene visualizzato un prompt che chiede all'utente l'autorizzazione per usare il tracciamento oculare.
Se non viene visualizzato, ciò indica in genere che la funzionalità _'GazeInput'_ non è stata impostata.

Quando la richiesta di autorizzazione è stata visualizzata una sola volta, non verrà visualizzata di nuovo automaticamente.
Se si _"nega l'autorizzazione di_ tracciamento oculare", è possibile reimpostarla in -Impostazioni -> Privacy -> Apps.

---

In questo modo si dovrebbe iniziare a usare il tracciamento oculare nell'app Unity MRTK.
Non dimenticare di consultare le esercitazioni e gli esempi di tracciamento oculare di [MRTK](eye-tracking-examples-overview.md) che illustrano come usare l'input del tracciamento oculare e fornire in modo pratico script che è possibile riutilizzare nei progetti.

---
[Torna a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)
