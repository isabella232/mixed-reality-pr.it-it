---
title: EyeTracking_BasicSetup
description: Come configurare la gestione degli occhi in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, monitoraggio degli occhi,
ms.openlocfilehash: c36c29d86f8ff47c57857bc36f358c9213ae4744
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682454"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Introduzione a Eye Tracking in MRTK

Questa pagina illustra come configurare la scena MRTK Unity per l'uso della traccia degli occhi nell'app.
Di seguito si presuppone che si inizi con una nuova scena.
In alternativa, è possibile consultare gli [esempi di MRTK Eye Tracking](EyeTracking_ExamplesOverview.md) già configurati con numerosi esempi eccezionali che è possibile compilare direttamente in.

## <a name="eye-tracking-requirements-checklist"></a>Elenco di controllo dei requisiti di rilevamento degli occhi

Per il corretto funzionamento del rilevamento degli occhi, è necessario soddisfare i requisiti seguenti.
Se non si ha familiarità con la registrazione degli occhi su HoloLens 2 e il modo in cui la verifica degli occhi è configurata in MRTK, non è un problema.
Verranno illustrati in dettaglio come indirizzarli a ognuno di essi.

1. È necessario aggiungere al sistema di input un _"provider di dati occhio a occhio"_ . Che fornisce i dati di rilevamento degli occhi dalla piattaforma.
2. La funzionalità _' GazeInput '_ deve essere abilitata nel manifesto dell'applicazione.
   **Questa funzionalità può essere impostata in Unity 2019, ma in Unity 2018 e versioni precedenti questa funzionalità è disponibile solo in Visual Studio e tramite lo strumento di compilazione MRTK**
3. Il HoloLens **deve** essere a occhio calibrato per l'utente corrente. Vedere l' [esempio per rilevare se un utente è calibrato o meno a occhio](EyeTracking_IsUserCalibrated.md).

### <a name="a-note-on-the-gazeinput-capability"></a>Una nota sulla funzionalità GazeInput

Gli strumenti di compilazione forniti da MRTK, ad esempio il Toolkit di realtà mista-> Utilities-> finestra di compilazione, possono abilitare automaticamente la funzionalità GazeInput. Per eseguire questa operazione, è necessario assicurarsi che la funzionalità di input di sguardi sia selezionata nella scheda ' appx Build Options ' (opzioni di compilazione):

![Strumenti di compilazione MRTK](../images/eye-tracking/mrtk_et_buildsetup.png)

Questo strumento consente di trovare il manifesto di AppX dopo il completamento della compilazione Unity e di aggiungere manualmente la funzionalità GazeInput.
**Prima di unity 2019, questi strumenti non sono attivi quando si usa la finestra di compilazione incorporata di Unity** (ad esempio, le impostazioni di compilazione di file >).

Prima di Unity 2019, quando si usa la finestra di compilazione di Unity, è necessario aggiungere manualmente la funzionalità dopo la compilazione Unity, come indicato di seguito:

1. Aprire il progetto di Visual Studio compilato e quindi aprire il _pacchetto "Package. appxmanifest"_ nella soluzione.
2. Assicurarsi di selezionare la casella di controllo _' GazeInput '_ in _funzionalità_. Se non viene visualizzata la funzionalità _' GazeInput '_ , verificare che il sistema soddisfi i [prerequisiti per l'uso di MRTK](../../Installation.md#prerequisites) (in particolare la versione Windows SDK).

_Nota:_ È necessario eseguire questa operazione solo se si compila in una nuova cartella di compilazione.
Ciò significa che se è già stato compilato il progetto Unity e si configura il appxmanifest prima e ora la destinazione della stessa cartella, non sarà necessario riapplicare le modifiche.

## <a name="setting-up-eye-tracking-step-by-step"></a>Procedura dettagliata per la configurazione del monitoraggio degli occhi

### <a name="setting-up-the-scene"></a>Impostazione della scena

Per configurare il _MixedRealityToolkit_ , è sufficiente fare clic su _' mixed reality Toolkit-> configure.. .'_ nella barra dei menu.

![Configurazione dell'installazione di MRTK](../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Configurazione dei profili MRTK necessari per la verifica degli occhi

Dopo aver configurato la scena MRTK, verrà richiesto di scegliere un profilo per MRTK.
È sufficiente selezionare _DefaultMixedRealityToolkitConfigurationProfile_ e quindi selezionare l'opzione _"copia & Personalizza"_ .

![Impostazioni del profilo MRTK](../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Creare un "provider di dati con occhio sguardo"

- Fare clic sulla scheda _"input"_ nel profilo MRTK.
- Per modificare quello predefinito ( _"DefaultMixedRealityInputSystemProfile"_ ), fare clic sul pulsante _"Clona"_ accanto. Verrà visualizzato il menu _' clona profilo '_ . È sufficiente fare clic su _' clone '_ nella parte inferiore del menu.
- Fare doppio clic sul nuovo profilo di input, espandere _"provider di dati di input"_ e selezionare _"+ Aggiungi provider di dati"_.
- Creare un nuovo provider di dati:
  - In **tipo** selezionare _' Microsoft. MixedReality. Toolkit. WindowsMixedReality. input '_  ->  _' WindowsMixedRealityEyeGazeDataProvider '_
  - Per le **piattaforme** selezionare _"universale di Windows"_.

![Provider di dati MRTK](../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulazione del rilevamento degli occhi nell'editor di Unity

È possibile simulare l'input di rilevamento degli occhi nell'editor di Unity per assicurarsi che gli eventi vengano attivati correttamente prima di distribuire l'app in HoloLens 2.
Il segnale di sguardi occhi viene simulato semplicemente usando la posizione della fotocamera come origine dello sguardo oculare e il vettore di avanzamento della fotocamera come direzione degli sguardi oculari.
Sebbene questo sia ideale per i test iniziali, tenere presente che non si tratta di un'imitazione efficace per i movimenti rapidi degli occhi.
A tale fine, è preferibile garantire i test frequenti delle interazioni basate sugli occhi in HoloLens 2.

1. **Abilita rilevamento occhi simulato**:
    - Fare clic sulla scheda _"input"_ nel profilo di configurazione di MRTK.
    - Passare a _"provider di dati di input"_  ->  _"servizio di simulazione input_".
    - Clonare l'oggetto _' DefaultMixedRealityInputSimpulationProfile '_ per apportare modifiche.
    - Selezionare la casella di controllo _"simula posizione occhio"_ .

    ![MRTK Eyes simulare l'installazione](../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Disabilitare il cursore per lo sguardo a capo predefinito**: in generale, è consigliabile evitare di visualizzare un cursore con lo sguardo d'occhio o, se necessario, per renderlo _estremamente_ sottile.
Per impostazione predefinita, è consigliabile nascondere il cursore predefinito per lo sguardo a capo associato al profilo del puntatore MRTK per impostazione predefinita.
    - Passare al profilo di configurazione di MRTK-> _' input '_  ->  _' puntatori '_
    - Clonare l'oggetto _' DefaultMixedRealityInputPointerProfile '_ per apportare modifiche.
    - Nella parte superiore di _' Pointer Settings '_ è necessario assegnare un cursore invisibile prefabbricato a _' GazeCursor '_. Questa operazione può essere eseguita selezionando la prefabbricata _' EyeGazeCursor '_ di MRTK Foundation.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Abilitazione dello sguardo basato sull'occhio nel provider di sguardi

In HoloLens V1, il primo sguardo è stato usato come tecnica di puntamento principale.
Mentre lo sguardo a capo è ancora disponibile tramite _GazeProvider_ in MRTK, che è collegato alla [fotocamera](https://docs.unity3d.com/ScriptReference/Camera.html), è possibile selezionare l'opzione per l'uso degli occhi, selezionando la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni dello sguardo del profilo del puntatore di input.

>[!NOTE]
>Gli sviluppatori possono passare da un sguardo a un occhio basato sull'occhio a quello basato su Head nel codice modificando la proprietà _' IsEyeTrackingEnabled '_ di _' GazeProvider '_.  

>[!IMPORTANT]
>Se non vengono soddisfatti i requisiti di rilevamento degli occhi, l'applicazione eseguirà automaticamente il fallback allo sguardo basato su Head.

### <a name="accessing-eye-gaze-data"></a>Accesso ai dati di Eye sguardi

Ora che la scena è configurata in modo da usare la verifica degli occhi, esaminiamo come accedervi negli script: [accesso ai dati di rilevamento degli occhi tramite EyeGazeProvider](EyeTracking_EyeGazeProvider.md) e [selezioni di destinazione supportate dagli occhi](EyeTracking_TargetSelection.md).

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Test dell'app Unity in un HoloLens 2

La compilazione dell'app con la verifica degli occhi dovrebbe essere simile a quella di altre app MRTK HoloLens 2. Assicurarsi di aver abilitato la funzionalità di *"input dello sguardo"* , come descritto in precedenza nella sezione [*una nota sulla funzionalità GazeInput*](#a-note-on-the-gazeinput-capability).

#### <a name="eye-calibration"></a>Calibrazione degli occhi

Infine, non dimenticare di eseguire la taratura degli occhi sulla HoloLens 2.
Il sistema di rilevamento degli occhi non restituirà alcun input se l'utente non è calibrato.
Il modo più semplice per ottenere la calibrazione consiste nell'instradare la visiera e viceversa.
Una notifica di sistema dovrebbe essere visualizzata come un nuovo utente e chiedere di esaminare la calibrazione degli occhi.
In alternativa, è possibile trovare la calibrazione degli occhi nelle impostazioni di sistema: impostazioni > sistema > la calibrazione > eseguire la calibrazione degli occhi.

#### <a name="eye-tracking-permission"></a>Autorizzazione per la verifica degli occhi

Quando si avvia l'app in HoloLens 2 per la prima volta, viene visualizzato un messaggio che richiede all'utente l'autorizzazione per l'uso di Eye Tracking.
Se non viene visualizzato, indica in genere che non è stata impostata la funzionalità _' GazeInput '_ .

Una volta visualizzata la richiesta di autorizzazione, questa non verrà visualizzata di nuovo automaticamente.
Se è stata _negata l'autorizzazione per la verifica degli occhi_, è possibile reimpostarla in impostazioni-> Privacy-> app.

---

Questa operazione dovrebbe iniziare a usare la verifica degli occhi nell'app MRTK Unity.
Non dimenticare di consultare [le esercitazioni e gli esempi di MRTK Eye Tracking](EyeTracking_ExamplesOverview.md) che illustrano come usare l'input di rilevamento degli occhi e fornire facilmente gli script che è possibile riutilizzare nei progetti.

---
[Torna a "Eye Tracking in the MixedRealityToolkit"](EyeTracking_Main.md)
