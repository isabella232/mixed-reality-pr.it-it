---
title: Note sulla versione di MRTK 2.7
description: Note sulla versione di MRTK versione 2.7
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 418831cd4563a1a3ea03b87410ac72065c831a10
ms.sourcegitcommit: 65f58055c831d58a3d38fb333f09b323ee2ac9b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2021
ms.locfileid: "112064136"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.7

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

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Lo configuratore riprogettato ora guida l'utente nel processo di configurazione

Il nuovo configuratore MRTK fornisce agli utenti istruzioni dettagliate per configurare correttamente il progetto per lo sviluppo XR e usarlo con MRTK. Illustra la selezione della pipeline XR, il recupero dei plug-in specifici della piattaforma, l'importazione di TextMeshPro, la visualizzazione degli esempi (quando si usa UPM) e altre impostazioni consigliate incluse in precedenza per il progetto.

![Configurator che mostra l'elenco delle pipeline](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Hotspot di teletrasporto dismersi

È stato creato [un nuovo componente hotspot di teletrasporto.](../features/teleport-system/teleport-hotspot.md) Puoi aggiungere un hotspot di teletrasporto al GameObject per assicurarti che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.

![Esempio di hotspot di teletrasporto](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Tempo di insoddamento graduale

La funzionalità e l'esempio di dwell sono stati ora gradualmente esempleriti dalla fase sperimentale. Nella scena di esempio sono inclusi HoloLens 2 di stile volumetrici.

![Dwell hero](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Aggiunta del supporto per i moduli Leap Motion Unity versione 4.6.0, 4.7.0, 4.7.1 e 4.8.0

Il supporto per le versioni più recenti dei [moduli Leap Motion Unity](https://developer.leapmotion.com/unity) è ora compatibile con MRTK 2.7.0.  Per [altre informazioni, vedere How to Configure MRTK for Leap Motion (Come configurare MRTK](../supported-devices/leap-motion-mrtk.md) per Leap Motion).

Grazie per @jackyangzzh aver contribuito alla nuova scena LeapMotionOrientationExample.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Gli eventi vocali mirati generati non sono più limitati ai puntatori dello sguardo fisso

In precedenza, gli eventi vocali mirati potevano essere generati solo su oggetti incentrati su con il puntatore dello sguardo fisso. A questo punto, gli oggetti possono ricevere eventi vocali se sono incentrati su qualsiasi puntatore.

![Eventi vocali con puntatori da lontano](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Portabilità di TextToSpeech da HTK a MRTK

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
- IsNearObject è ora una proprietà virtuale, che offre maggiore flessibilità durante l'estensione della sfera o del puntatore di poke. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- I pulsanti ora visualizzano la parola chiave appropriata quando visualizzano il comando vocale disponibile. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus Controllers usa ora il proprio visualizzatore autonomo, impedendo che la visualizzazione MRTK sia in conflitto con la visualizzazione del pacchetto di integrazione Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Gli script correlati alla tastiera sono stati modificati per allinearsi al comportamento nelle versioni più recenti di Unity (2019.4.25+ & 2020.3.2+). Al rilascio sono ancora presenti un bug di completamento automatico e un bug del campo di input TMP (entrambi esterni a MRTK) che influiscono su HoloLens. Per altre informazioni, vedere [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) e [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Miglioramento delle prestazioni di Scrolling Object Collection. È stato risolto anche un problema che causava la perdita di materiale da parte di GameObject all'interno della raccolta in caso di duplicazione. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Nello script demo Scene Understanding è stata aggiunta la `GetSceneObjectsOfType` funzione per recuperare tutti gli oggetti scena osservati di un determinato tipo. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Nello strumento di compilazione da riga di comando solo le scene specificate dai flag o (quando è presente un `sceneList` `sceneListFile` flag) verranno incluse nella compilazione. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Nello strumento di compilazione è disponibile una nuova opzione per specificare un percorso e usarlo per eseguire il ripristino del pacchetto anziché `nuget.exe` `msbuild` usare (opzione predefinita). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- È stato risolto un problema per cui l'uso del plug-in Windows XR poteva causare giunzioni delle mani non datate e mesh a mano doppie. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Risolto un problema per cui l'uso della funzionalità di comunicazione remota automatica del plug-in Windows XR causava la mancanza di input e interazioni. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Risolto un problema per cui BuildDeployWindow tentava di eseguire una query su una chiave reg non valida per Windows SDK percorso. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Le utilità di importazione glTF di MRTK sono ora facoltative. Se sono presenti più utilità di importazione glTF, è possibile disabilitare mrtk aggiungendo ai `MRTK_GLTF_IMPORTER_OFF` simboli di definizione di scripting personalizzati. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- È stato risolto un problema a causa del quale i controller Diruckles in OpenVR non vengono rilevati correttamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Ridurre il numero di allocazioni per fotogramma quando si visualizza la mesh [mano #9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Aggiunta di una voce di menu per avviare il pacchetto di esempi MRTK (in Unity Gestione pacchetti) per semplificare l'importazione di esempi [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Riduzione del numero di avvisi in fase di caricamento quando si usa Unity 2020.3.
- Aggiunta della documentazione della funzionalità Finestra di compilazione: [visitare la pagina](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Problemi noti

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Nelle demo audio manca un file asmdef (pacchetto UPM)

Quando si importa MRTK tramite Mixed Reality Feature Tool, gli esempi e le demo vengono aggiunti al progetto usando l'interfaccia utente Gestione pacchetti Unity. Dopo aver importato le demo audio, la `WindowsMicrophoneStreamDemo.unity` scena non si comporterà correttamente. Questo è il risultato di un file asmdef mancante per l'esempio.

Per risolvere questo [problema,](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)seguire questa procedura:

- Copia libreria/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...] /MRTK. Examples.asmdef nella cartella "Assets/Samples/Mixed Reality Toolkit Examples"
- Rinominare il file copiato in Esempi
- Aprire il file Examples
- Nella casella Nome sostituire il contenuto con Esempi
- Fare clic su Applica
- Eseguire la compilazione e la distribuzione

Questo problema verrà risolto in una versione futura di MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La finestra di compilazione di MRTK attiva una finestra di dialogo "Importazione di asset" illimitata in Unity 2020.3

Esiste un [](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) problema noto con la finestra di compilazione di MRTK in Unity 2020.3 in cui dopo aver eseguito correttamente una compilazione UWP, la finestra di dialogo "Importazione di asset" non viene completata. Questo problema viene analizzato in collaborazione con Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avvisi del renderer canvas di Text Mesh Pro in Unity 2020

L'avviso seguente viene registrato nella maggior parte delle scene di esempio di MRTK durante l'uso di Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

L'avviso del renderer canvas è stato aggiunto in [TextMeshPro versione 3.0.3.](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)  Questi avvisi non influiscono sulle scene di esempio di MRTK e possono essere cancellati dalla console. Per [altri dettagli, vedere il problema 9811.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)
