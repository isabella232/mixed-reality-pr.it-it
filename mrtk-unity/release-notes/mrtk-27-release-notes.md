---
title: Note sulla versione di MRTK 2.7
description: Note sulla versione per MRTK versione 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: e257fd95d01eab249201a0f412842d20164e7e5c
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562481"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-272"></a>Novità nella versione 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Correzione di un problema di dipendenza del pacchetto UPM

Si è verificato un problema con i pacchetti UPM MRTK 2.7.1 per cui le dipendenze non sono state configurate correttamente. Il problema ha causato la mancata importazione corretta dei pacchetti MRTK 2.7.1 da parte dello strumento di funzionalità di realtà mista. Il problema è stato risolto nella versione 2.7.2. In questa versione non è stata apportata alcuna modifica al codice rispetto alla versione 2.7.1.


## <a name="whats-new-in-271"></a>Novità nella versione 2.7.1

### <a name="show-version"></a>Mostra versione

Il menu contiene ora una voce che esamina il pacchetto Mixed Reality Toolkit Foundation per determinare la versione di `Mixed Reality`  >  `Toolkit` `Show version...` MRTK usata dal progetto.

![Menu Mostra versione](images/ShowVersionMenu.png)

![Finestra di dialogo della versione di MRTK](images/VersionDialog.png)

> [!NOTE]
> Se MRTK è stato clonato dal [repository GitHub,](https://aka.ms/mrtk)le informazioni sulla versione non saranno state impostate.
>
> ![Impossibile determinare la versione](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Elenco autori

A partire da MRTK 2.7.1, il file di elenco degli autori è incluso nel pacchetto Mixed Reality Toolkit Foundation.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>Configurazione del progetto OpenXR integrato nel flusso di configurazione dello configuratore

A partire da MRTK 2.7.1, gli utenti del plug-in OpenXR di Realtà mista riceveranno istruzioni su come configurare il plug-in con MRTK. È disponibile un'opzione che consente agli utenti che HoloLens 2 di applicare automaticamente le impostazioni consigliate.

![Finestra Configurator con istruzioni di configurazione di OpenXR](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Correzioni di bug e modifiche di valore

- Contrassegnato Unity UnityStick Manager come supportato nella pipeline XR SDK [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- Aggiunta di controlli al codice di controllo interagiscibile per evitare errori [null #9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- Aggiungere il provider di mesh OpenXR per l'uso della scena di esempio pulse shader [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- Ripristinare il profilo di fisica della mano in esempi di [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- Alcune operazioni di pulizia per gli script HandConstraint* [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- Correzione di alcuni bug che interessano la creazione e la clonazione [di profili #9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>Novità nella versione 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR è ora ufficialmente supportato in MRTK

Poiché i nuovi plug-in OpenXR stanno diventando sempre più maturi, MRTK ora supporta ufficialmente OpenXR. Rispetto alle versioni precedenti sono state aggiunte le funzionalità seguenti ai progetti che usano OpenXR:

- [Supporto per il modello di controller del movimento fornito dal sistema](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Supporto per i movimenti WinMR (selezione, attesa, manipolazione e [navigazione) #9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Supporto per l'attico dei controller](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Supporto per la mesh a mano articolata HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Supporto per il mapping spaziale HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Supporto per La comprensione della scena HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

Se la destinazione è un visore VR HoloLens 2 o Windows Mixed Reality tramite OpenXR, assicurati di installare/aggiornare il plug-in **Mixed Reality OpenXR versione 0.9.5** o successiva tramite [Mixed Reality Feature Tool,](https://aka.ms/MRFeatureTool)altrimenti potresti perdere alcuni dei miglioramenti precedenti.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>I provider di dati XR e XR SDK legacy possono ora essere usati all'interno dello stesso profilo

I provider di dati verranno ora caricati solo quando viene selezionata la pipeline appropriata, consentendo ai provider di dati legacy XR e XR SDK di coesistere all'interno dello stesso profilo. A tale scopo, i provider di dati legacy XR e XR SDK sono ora organizzati in schede diverse all'interno della visualizzazione del profilo, consentendo agli utenti di determinare se hanno il profilo corretto per la pipeline XR di destinazione.

![I provider di dati legacy e XR SDK possono ora essere unificati con un unico profilo](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

A questo scopo, i provider di dati Null non verranno più caricati e visualizzati nel controllo profilo. Gli utenti possono passare da Edit -> Project Settings -> Mixed Reality Toolkit (Modifica -impostazioni progetto `Show null data providers in the profile inspector` **-> Mixed Reality Toolkit)** per eseguire il debug di comportamenti imprevisti con provider di dati mancanti.

![I provider di dati Null sono ora nascosti per impostazione ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ predefinita. Attiva/Disattiva mostra provider di dati Null nel controllo profilo](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Aggiunta delle impostazioni dell'esperienza e di un comportamento del contenuto della scena di realtà mista associato

Gli utenti possono ora configurare [le impostazioni dell'esperienza,](../features/experience-settings/experience-settings.md)che consentiranno a MRTK di visualizzare [il](../features/experience-settings/scene-content.md) contenuto della scena di realtà mista in modo appropriato in base all'esperienza di destinazione.

Se le impostazioni precedenti della scalabilità dell'esperienza dell'utente non corrispondono al nuovo profilo delle impostazioni dell'esperienza, gli verrà richiesto di correggerlo nel controllo

![Migrazione della scalabilità dell'esperienza](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Configurator riprogettato ora guida l'utente nel processo di configurazione

Il nuovo configuratore MRTK fornisce agli utenti istruzioni dettagliate per configurare correttamente il progetto per lo sviluppo XR e usarlo con MRTK. Illustra la selezione della pipeline XR, il recupero dei plug-in specifici della piattaforma, l'importazione di TextMeshPro, la visualizzazione degli esempi (quando si usa UPM) e altre impostazioni consigliate incluse in precedenza per il progetto.

![Configurator che mostra l'elenco delle pipeline](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Hotspot di teletrasporto dismersi

È stato creato [un nuovo componente hotspot di teletrasporto.](../features/teleport-system/teleport-hotspot.md) Puoi aggiungere un hotspot di teletrasporto al GameObject per assicurarti che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.

![Esempio di hotspot di teletrasporto](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Tempo di insoddamento graduale

La funzionalità e l'esempio di dwell sono stati ora gradualmente esempleriti dalla fase sperimentale. Nella scena di esempio sono inclusi HoloLens 2 di stile volumetrici.

![Dwell hero](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Aggiunta del supporto per i moduli Leap Motion Unity versione 4.6.0, 4.7.0, 4.7.1 e 4.8.0

Il supporto per le versioni più recenti dei [moduli Leap Motion Unity](https://developer.leapmotion.com/unity) è ora compatibile con MRTK 2.7.0. Per [altre informazioni, vedere How to Configure MRTK for Leap Motion (Come configurare MRTK](../supported-devices/leap-motion-mrtk.md) per Leap Motion).

Grazie per @jackyangzzh aver contribuito alla nuova scena LeapMotionOrientationExample.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Gli eventi vocali mirati generati non sono più limitati ai puntatori dello sguardo fisso

In precedenza, gli eventi vocali mirati potevano essere generati solo su oggetti incentrati su con il puntatore dello sguardo fisso. A questo punto, gli oggetti possono ricevere eventi vocali se sono incentrati su qualsiasi puntatore.

![Eventi vocali con puntatori da lontano](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Ported TextToSpeech from HTK to MRTK

Lo script TextToSpeech è ora disponibile in MRTK per facilitare la generazione del parlato dal testo nella piattaforma UWP usando [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . È stata anche aggiunta una scena di esempio per illustrare la funzionalità.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Supporto per il modello di controller del movimento fornito dal sistema in OpenXR

Aggiunta del supporto, sia nell'editor che in fase di esecuzione, per il modello di controller del movimento fornito dal sistema in OpenXR.

![Finestra dell'editor che mostra due modelli di controller del movimento](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Supporto per HoloLens 2 mesh a mano articolata in OpenXR

![La mesh mano in esecuzione sul dispositivo in una scena di esempio di MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Supporto per l'attico dei controller in WMR legacy, plug-in Windows XR e OpenXR

Aggiunta del supporto per l'attico dei controller in WMR legacy, plug-in Windows XR e OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Supporto per il tracciamento oculare nel plug-in Windows XR

Aggiunta del supporto per lo sguardo fisso quando si usano le versioni minime 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) e 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Correzioni di bug e modifiche di valore

- Il rilevamento delle dita è stato reso più uniforme. È ora più difficile eliminare accidentalmente il movimento di avvicinamento delle dita. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Gli oggetti con il componente Object Manipulator ora mantengono costantemente la velocità al momento del rilascio quando il flag è impostato. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Il back-strafing ora verifica la presenza di un piano, consentendo di evitare situazioni in cui la fotocamera può ritagliarsi nell'ambiente o in cui l'utente viene lasciato passare il puntatore del mouse su uno spazio vuoto. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject è ora una proprietà virtuale, che offre maggiore flessibilità quando si estende la sfera o il puntatore poke. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- I pulsanti visualizzano ora la parola chiave appropriata quando visualizzano il comando vocale disponibile. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus Controllers usa ora il proprio visualizzatore autonomo, impedendo che la visualizzazione MRTK sia in conflitto con la visualizzazione del pacchetto di integrazione Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Gli script correlati alla tastiera sono stati modificati per allinearsi al comportamento nelle versioni più recenti di Unity (2019.4.25+ & 2020.3.2+). Al rilascio sono ancora presenti un bug di completamento automatico e un bug del campo di input TMP (entrambi esterni a MRTK) che influiscono su HoloLens. Per altre informazioni, [vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) #9056 e [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Miglioramento delle prestazioni di Scrolling Object Collection. È stato risolto anche un problema che causava la perdita di materiale da parte di GameObject all'interno della raccolta in caso di duplicazione. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Nello script demo Informazioni sulla scena è stata aggiunta la `GetSceneObjectsOfType` funzione per recuperare tutti gli oggetti scena osservati di un determinato tipo. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Nello strumento di compilazione da riga di comando, nella compilazione verranno incluse solo le scene specificate dai flag o (quando è presente `sceneList` `sceneListFile` un flag). [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Nello strumento di compilazione è disponibile una nuova opzione per specificare un percorso e usarlo per eseguire il ripristino del pacchetto anziché `nuget.exe` `msbuild` usare (opzione predefinita). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- È stato risolto un problema a causa del quale l'uso del plug-in XR di Windows potrebbe causare giunzioni della mano non stantie e mesh a mano doppia. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- È stato risolto un problema per cui l'uso della funzionalità di comunicazione remota automatica del plug-in XR di Windows causava la mancanza di input e interazioni. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- È stato risolto un problema a causa del quale BuildDeployWindow tentava di eseguire una query su una chiave reg non valida per il Windows SDK percorso. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Gli importatori glTF di MRTK sono ora facoltativi. Se sono presenti più utilità di importazione glTF, è possibile disabilitate le funzioni MRTK aggiungendo `MRTK_GLTF_IMPORTER_OFF` simboli di definizione di scripting personalizzati. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Correzione del problema per cui i controller Knuckles in OpenVR non sono stati rilevati correttamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Ridurre il numero di allocazioni per frame quando si visualizza la mesh [manuale #9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Aggiunta di una voce di menu per avviare il pacchetto esempi MRTK (in Unity Gestione pacchetti) per semplificare l'importazione di esempi [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Riduzione del numero di avvisi in fase di caricamento quando si usa Unity 2020.3.
- Aggiunta della documentazione della funzionalità Finestra di compilazione: [visitare la pagina](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Problemi noti

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Nelle demo audio manca un file asmdef (pacchetto UPM)

Quando si importa MRTK tramite lo strumento di funzionalità di realtà mista, esempi e demo vengono aggiunti al progetto usando l'interfaccia utente Gestione pacchetti Unity. Dopo l'importazione delle demo audio, `WindowsMicrophoneStreamDemo.unity` la scena non si comporterà correttamente. Questo è il risultato di un file asmdef mancante per l'esempio.

Per risolvere questo [problema,](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)seguire questa procedura:

- Copia libreria/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...] /MRTK. Examples.asmdef nella cartella "Assets/Samples/Mixed Reality Toolkit Examples"
- Rinominare il file copiato in Esempi
- Aprire il file Examples
- Nella casella Nome sostituire il contenuto con Esempi
- Fare clic su Applica
- Eseguire la compilazione e la distribuzione

Questo problema verrà risolto in una prossima versione di MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La finestra di compilazione MRTK attiva la finestra di dialogo indefinita "Importazione di asset" in Unity 2020.3

Si è [](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) verificato un problema noto con la finestra di compilazione MRTK in Unity 2020.3 in cui dopo aver eseguito correttamente una compilazione UWP, la finestra di dialogo "Importazione di asset" non viene completata. Questo problema viene analizzato in collaborazione con Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avvisi del renderer Canvas Di Text Mesh Pro in Unity 2020

L'avviso seguente viene registrato nella maggior parte delle scene di esempio di MRTK durante l'uso di Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

L'avviso del renderer canvas è stato aggiunto in [TextMeshPro versione 3.0.3.](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3) Questi avvisi non influiscono sulle scene di esempio di MRTK e possono essere cancellati dalla console. Per altre informazioni, vedere Problema [9811.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)
