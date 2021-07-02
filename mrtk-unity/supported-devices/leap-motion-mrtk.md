---
title: Uso del movimento intercalare
description: Documentazione da configurare per Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176509"
---
# <a name="using-leap-motion"></a>Uso del movimento intercalare

Per [usare questo provider](https://www.ultraleap.com/product/leap-motion-controller/) di dati è necessario un leap motion controller.

La funzionalità Leap Motion provider di dati il tracciamento articolato della mano per la realtà virtuale e può essere utile per la creazione rapida di prototipi nell'editor.  Il provider di dati può essere configurato per l'uso del Leap Motion Controller montato su un visore o posizionato su un visore da tavolo.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Questo provider può essere usato nell'editor e nel dispositivo mentre si usa la piattaforma autonoma.  Può anche essere usato nell'editor nella piattaforma UWP, ma NON in una build UWP.

| Versione di MRTK | Versioni dei moduli Leap Motion Unity supportate |
| --- | --- |
|2.6.x | 4.5.0, 4.5.1|
|2.7.x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Uso del tracciamento manuale leap motion (by Ultraleap) in MRTK

1. Importazione di moduli MRTK e Leap Motion Unity
    - Installare [l'SDK Leap Motion più](https://developer.leapmotion.com/releases/?category=orion) recente se non è già installato
    - Importare **Microsoft.MixedReality.Toolkit. Pacchetto di** base nel progetto Unity.
    - Scaricare e importare la versione più recente [dei moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto
        - Importare solo il **pacchetto Core** all'interno dei moduli Unity

1. Integrare i moduli Leap Motion Unity con MRTK
    - Dopo aver fatto parte del progetto, passare a **Mixed Reality Toolkit** Leap  >  **Motion** Integrate Leap  >  **Motion Unity Modules**
    > [!NOTE]
    > L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti a **Microsoft.MixedReality.Toolkit. Definizione dell'assembly Providers.LeapMotion.** Verificare che Visual Studio sia chiuso.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Aggiunta del movimento leap provider di dati
    - Creare una nuova scena di Unity
    - Aggiungere MRTK alla scena passando a **Realtà mista Toolkit**  >  **Aggiungi alla scena e configura**
    - Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selezionare il **profilo di configurazione** di input

    ![Profilo di configurazione di input 1](../images/cross-platform/InputConfigurationProfile.png)

    - Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Aprire la **sezione Provider di** dati di input, selezionare **Aggiungi** provider di dati nella parte superiore, verrà aggiunto un nuovo provider di dati alla fine dell'elenco.  Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit. LeapMotion.Input > LeapMotionDeviceManager**

    ![Leap Add provider di dati](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Selezionare **Clona** per modificare le impostazioni predefinite di Leap Motion.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - L'provider di dati Leap Motion contiene `LeapControllerOrientation` la proprietà che rappresenta la posizione del controller di movimento Leap. `LeapControllerOrientation.Headset` indica che il controller è montato su un visore. `LeapControllerOrientation.Desk` indica che il controller è posizionato piano sulla scrivania. Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .
    - Ogni orientamento del controller contiene le proprietà di offset:
      - Le **proprietà di** offset dell'orientamento visore rispecchiano le proprietà di offset nel componente LeapXRServiceProvider.  Dispone `LeapVRDeviceOffsetMode` di tre opzioni: Predefinito, Offset testina manuale e Trasformazione.  Se la modalità di offset è Default, non verrà applicato un offset al Controller di movimento Leap.  La modalità Manual Head Offset consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` e `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .  I valori della proprietà offset dell'asse vengono quindi applicati al posizionamento predefinito del controller.  La modalità Offset trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per Leap Motion Controller.
      - **L'orientamento desk** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle mani intercalare della scrivania.  L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le mani vengano visualizzate davanti e in vista della fotocamera.

        > [!NOTE]
        > Le proprietà di offset nel profilo vengono applicate una volta all'avvio dell'applicazione.  Per modificare i valori durante il runtime, ottenere Leap Motion Service Provider da Leap Motion Device Manager:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento dei movimenti di tocco di avvicinamento/aria.  Il movimento di avvicinamento delle dita viene calcolato misurando la distanza tra la punta dell'indice e la punta del pollice.  Per generare un evento on input down, il valore `EnterPinchDistance` predefinito è 0,02.  Per generare un evento on input up (uscita dalla dita), la distanza predefinita tra la punta dell'indice e la punta del pollice è 0,05.

    `LeapControllerOrientation`: Visore (impostazione predefinita) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Test del movimento leap provider di dati
    - Dopo aver aggiunto leap motion provider di dati al profilo del sistema di input, premere play, spostare la mano davanti a Leap Motion Controller e si dovrebbe vedere la rappresentazione congiunta della mano.

1. Compilazione del progetto
    - Passare a **File > Build Impostazioni**
    - Solo le compilazioni autonome sono supportate se si usa leap motion provider di dati.
    - Per istruzioni su come usare un visore Windows Mixed Reality visore per le build autonome, vedere Compilazione e distribuzione di [MRTK in visori WMR (Standalone).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)

## <a name="getting-the-hand-joints"></a>Ottenere le giunzioni della mano

Ottenere le giunzioni usando il provider di dati leap è identico al recupero delle giunzioni della mano per una mano articolata MRTK.  Per altre informazioni, vedere [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

Con MRTK in una scena unity e leap motion provider di dati aggiunto come provider di dati di input nel profilo del sistema di input, creare un oggetto gioco vuoto e associare lo script di esempio seguente.

Questo script è un semplice esempio di come recuperare la posizione della giunzione del palmo in un Leap Motion Hand.  Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano di salto a destra.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a>Suggerimento per il flusso di lavoro dell'editor unity

L'uso di Leap Motion provider di dati non richiede un visore VR.  Le modifiche a un'app MRTK possono essere testate nell'editor con le mani Leap senza visore.

Leap Motion Hands verrà visualizzato nell'editor, senza un visore VR collegato.  Se `LeapControllerOrientation` l'opzione è impostata su **Headset,** il controller Leap Motion dovrà essere tenuto in mano da una mano con la fotocamera rivolta in avanti.

> [!NOTE]
> Se la fotocamera viene spostata usando chiavi WASD nell'editor e l'oggetto è Headset, le mani `LeapControllerOrientation` non seguiranno la fotocamera.  Le mani seguiranno lo spostamento della fotocamera solo se un visore VR è collegato mentre `LeapControllerOrientation` l'opzione è impostata **su Headset**.  Le mani leap seguiranno lo spostamento della fotocamera nell'editor se `LeapControllerOrientation` è impostato su **Desk**.

## <a name="removing-leap-motion-from-the-project"></a>Rimozione del movimento leap dalla Project

1. Passare ai moduli **Leap Motion Unity Toolkit** Leap  >  **Motion** Separate Leap Motion  >  **Unity**
    - Consentire l'aggiornamento di Unity come riferimenti in **Microsoft.MixedReality.Toolkit. Il file Providers.LeapMotion.asmdef** viene modificato in questo passaggio
1. Chiudere Unity
1. Chiudere Visual Studio, se è aperto
1. Aprire Esplora file e passare alla radice del progetto UNITY MRTK
    - Eliminare la directory **UnityProjectName/Library**
    - Eliminare la directory **UnityProjectName/Assets/Plugins/LeapMotion**
    - Eliminare il file **UnityProjectName/Assets/Plugins/LeapMotion.meta**
1. Riaprire Unity

In Unity 2018.4 è possibile notare che gli errori rimangono nella console dopo l'eliminazione della libreria e degli asset leap motion core.
Se vengono registrati errori dopo la riapertura, riavviare di nuovo Unity.

## <a name="common-errors"></a>Errori comuni

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion non è integrato con MRTK

Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:

- Passare a **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**
  - Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono o meno integrati con MRTK.
- Se il messaggio indica che gli asset non sono stati integrati:
  - Assicurarsi che i moduli Leap Motion Unity siano nel progetto
  - Assicurarsi che la versione aggiunta sia supportata, vedere la tabella nella parte superiore della pagina per le versioni supportate.
  - Provare **Mixed Reality Toolkit > Utilities > Leap Motion > Integrare moduli Leap Motion Unity**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Copia dell'assembly multiplayer HLAPI non riuscita

Durante l'importazione di Leap Motion Unity Core Assets questo errore potrebbe essere registrato:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Soluzione**

- Una soluzione a breve termine consiste nel riavviare Unity. Per altre informazioni, vedere Problema [7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)

## <a name="leap-motion-example-scene"></a>Scena di esempio di movimento intercalare

La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati.

La scena di esempio è contenuta in **Microsoft.MixedReality.Toolkit. Pacchetto** di esempi nella directory **MRTK/Examples/Demos/HandTracking/.**  

## <a name="see-also"></a>Vedere anche

- [Provider di input](../features/input/input-providers.md)
- [Tracciamento manuale](../features/input/hand-tracking.md)
