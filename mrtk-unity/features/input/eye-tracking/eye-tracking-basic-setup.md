---
title: Configurazione di base del tracciamento oculare
description: Come configurare Eye Tracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Eye Tracking,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144095"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Introduzione al tracciamento oculare in MRTK

Questa pagina illustra come configurare la scena di Unity MRTK per usare il tracciamento oculare nell'app.
Di seguito si presuppone che si inizi con una nuova scena.
In alternativa, è possibile consultare gli esempi di tracciamento oculare [MRTK](../../example-scenes/eye-tracking-examples-overview.md) già configurati con moltissimi esempi di cui è possibile basarsi direttamente.

## <a name="eye-tracking-requirements-checklist"></a>Elenco di controllo dei requisiti di tracciamento oculare

Per il corretto funzionamento del tracciamento oculare, è necessario soddisfare i requisiti seguenti.
Se non si ha di che HoloLens 2 e come è configurato il tracciamento oculare in MRTK, non preoccuparsi.
Verranno fornite informazioni dettagliate su come risolvere ognuno di essi più avanti.

1. È _necessario aggiungere un provider di dati 'Eye Gaze'_ al sistema di input. In questo modo vengono forniti i dati di tracciamento oculare dalla piattaforma.
2. La _funzionalità 'GazeInput'_ deve essere abilitata nel manifesto dell'applicazione.
   **Questa funzionalità può essere impostata in Unity 2019, ma in Unity 2018 e versioni precedenti questa funzionalità è disponibile solo in Visual Studio e tramite lo strumento di compilazione MRTK**
3. HoloLens deve **essere calibrato** con gli occhi per l'utente corrente. Vedere [l'esempio per rilevare se un utente è calibrato dagli occhi o meno.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Nota sulla funzionalità GazeInput

Gli strumenti di compilazione forniti da MRTK (ad esempio Mixed Reality Toolkit -> Utilities -> Build Window) possono abilitare automaticamente la funzionalità GazeInput. A tale scopo, è necessario assicurarsi che la "Funzionalità di input sguardo fisso" sia selezionata nella scheda "Opzioni di compilazione Appx":

![Strumenti di compilazione MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

Questi strumenti troveranno il manifesto AppX dopo il completamento della compilazione di Unity e aggiungeranno manualmente la funzionalità GazeInput.
**Prima di Unity 2019,** questo strumento NON è attivo quando si usa la finestra di compilazione predefinita di Unity, ad esempio File -> Build Settings (Impostazioni di compilazione file-> compilazione).

Prima di Unity 2019, quando si usa la finestra di compilazione di Unity, la funzionalità dovrà essere aggiunta manualmente dopo la compilazione di Unity, come indicato di seguito:

1. Aprire il progetto Visual Studio e quindi aprire _'Package.appxmanifest'_ nella soluzione.
2. Assicurarsi di selezionare la casella _di controllo "GazeInput"_ in _Capabilities (Funzionalità)._ Se non viene visualizzata una funzionalità _"GazeInput",_ verificare che il sistema soddisfi i prerequisiti per l'uso di [MRTK](/windows/mixed-reality/develop/install-the-tools) (in particolare la Windows SDK precedente.

_Si noti che:_ È necessario eseguire questa operazione solo se si compila in una nuova cartella di compilazione.
Ciò significa che se il progetto Unity è già stato compilato e si è configurato appxmanifest in precedenza e ora è stata impostata di nuovo come destinazione la stessa cartella, non sarà necessario riapplicare le modifiche.

## <a name="setting-up-eye-tracking-step-by-step"></a>Configurazione dettagliata del tracciamento oculare

### <a name="setting-up-the-scene"></a>Configurazione della scena

Configurare _MixedRealityToolkit_ semplicemente facendo clic su _"Mixed Reality Toolkit -> Configura"._ nella barra dei menu.

![Configurazione di MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configurazione dei profili MRTK necessari per il tracciamento oculare

Dopo aver impostato la scena MRTK, ti verrà chiesto di scegliere un profilo per MRTK.
È sufficiente selezionare _DefaultMixedRealityToolkitConfigurationProfile_ e quindi selezionare l'opzione _"Copia_ & Personalizza".

![Profilo MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Creare un "provider di dati di sguardo fisso"

- Fare clic sulla _scheda "Input"_ nel profilo MRTK.
- Per modificare quello predefinito ( _'DefaultMixedRealityInputSystemProfile'),_ fare clic sul _pulsante "Clona"_ accanto. Viene visualizzato il menu _"Clone Profile" (Clona_ profilo). È sufficiente fare _clic su "Clone" (Clona)_ nella parte inferiore del menu.
- Fare doppio clic sul nuovo profilo di input, espandere _"Provider di dati di input"_ e selezionare _"+ Aggiungi provider di dati"._
- Creare un nuovo provider di dati:
  - In **Tipo** selezionare _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_
  - Per **Piattaforme selezionare** _"Universale di Windows"._

![Provider di dati MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulazione del tracciamento oculare nell'editor di Unity

È possibile simulare l'input del tracciamento oculare nell'editor di Unity per assicurarsi che gli eventi vengano attivati correttamente prima di distribuire l'app nel HoloLens 2.
Il segnale dello sguardo fisso viene simulato semplicemente usando la posizione della fotocamera come origine dello sguardo e il vettore in avanti della fotocamera come direzione dello sguardo fisso.
Anche se è ideale per i test iniziali, si noti che non è una buona idea per i movimenti oculari rapidi.
A questo scopo, è meglio garantire test frequenti delle interazioni basate sugli occhi sul HoloLens 2.

1. **Abilitare il tracciamento oculare simulato:**
    - Fare clic sulla _scheda "Input"_ nel profilo di configurazione di MRTK.
    - Da qui passare a _"Input Data Providers" (Provider di dati di_  ->  _input) "Input Simulation Service" (Servizio simulazione input)._
    - Clonare _'DefaultMixedRealityInputSimpulationProfile'_ per apportare modifiche.
    - Selezionare la _casella di controllo "Simulate Eye Position" (Simula posizione_ oculare).

    ![MrTK eyes simulate (Simulazione occhi MRTK)](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Disabilitare il cursore predefinito** per lo sguardo fisso con la testa: in generale, è consigliabile evitare di visualizzare un cursore con sguardo fisso o se assolutamente necessario per renderlo _molto_ sottile.
È consigliabile nascondere il cursore dello sguardo fisso predefinito associato al profilo del puntatore dello sguardo fisso MRTK per impostazione predefinita.
    - Passare al profilo di configurazione MRTK -> _'Input'_  ->  _'Pointers'_
    - Clonare _'DefaultMixedRealityInputPointerProfile'_ per apportare modifiche.
    - Nella parte superiore di _"Impostazioni puntatore"_ è necessario assegnare un prefab del cursore invisibile a _'GazeCursor'._ A tale scopo, selezionare il prefab _"EyeGazeCursor"_ da MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Abilitazione dello sguardo oculare nel provider di sguardo

In HoloLens v1, lo sguardo rivolto verso la testa è stato usato come tecnica di puntamento principale.
Mentre lo sguardo della testa è ancora disponibile tramite _GazeProvider_ in MRTK collegato alla [fotocamera,](https://docs.unity3d.com/ScriptReference/Camera.html)è possibile controllare di usare lo sguardo fisso selezionando invece la casella di controllo _"IsEyeTrackingEnabled"_ nelle impostazioni dello sguardo fisso del profilo del puntatore di input.

>[!NOTE]
>Gli sviluppatori possono alternare lo sguardo visivo e lo sguardo con la testa nel codice modificando la proprietà _'IsEyeTrackingEnabled'_ di _'GazeProvider'._  

>[!IMPORTANT]
>Se uno dei requisiti di tracciamento oculare non viene soddisfatto, l'applicazione torna automaticamente alla vista basata sulla testa.

### <a name="accessing-eye-gaze-data"></a>Accesso ai dati dello sguardo fisso

Ora che la scena è stata impostata per l'uso del tracciamento oculare, è possibile esaminare come accedervi negli script: Accesso ai dati di tracciamento oculare tramite [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e selezioni di destinazione supportate dagli [occhi.](eye-tracking-target-selection.md)

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Test dell'app Unity in un HoloLens 2

La compilazione dell'app con il tracciamento oculare dovrebbe essere simile alla compilazione di altre app HoloLens 2 MRTK. Assicurarsi di aver abilitato la funzionalità *"Gaze Input"* come descritto in precedenza nella sezione Nota sulla [*funzionalità GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Calibrazione oculare

Infine, non dimenticare di eseguire la calibrazione dell'occhio sul HoloLens 2.
Il sistema di tracciamento oculare non restituirà alcun input se l'utente non è calibrato.
Il modo più semplice per ottenere la calibrazione è capovolgere la visiera e tornare indietro.
Verrà visualizzata una notifica di sistema che indica l'utente come nuovo utente e chiede di eseguire la calibrazione oculare.
In alternativa, è possibile trovare la calibrazione oculare nelle impostazioni di sistema: Impostazioni > sistema > calibrazione > Calibrazione oculare.

#### <a name="eye-tracking-permission"></a>Autorizzazione di tracciamento oculare

Quando si avvia l'app nel HoloLens 2 per la prima volta, viene visualizzata una richiesta che richiede all'utente l'autorizzazione per usare il tracciamento oculare.
Se non viene visualizzato, in genere si tratta di un'indicazione che la funzionalità _'GazeInput'_ non è stata impostata.

Dopo che la richiesta di autorizzazione è stata visualizzata una sola volta, non verrà visualizzata di nuovo automaticamente.
Se si _"nega l'autorizzazione di_ tracciamento oculare", è possibile reimpostarla in Impostazioni -> Privacy -> App.

---

Questo dovrebbe iniziare a usare il tracciamento oculare nell'app MRTK Unity.
Non dimenticare di consultare le esercitazioni e gli esempi sul tracciamento oculare [di MRTK](../../example-scenes/eye-tracking-examples-overview.md) che illustrano come usare l'input di tracciamento oculare e forniscono in modo pratico script che è possibile riutilizzare nei progetti.

---
[Tornare a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)