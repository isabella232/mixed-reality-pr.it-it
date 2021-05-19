---
title: Leap Motion MRTK
description: Documentazione da configurare per Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145198"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Come configurare il tracciamento delle mani Leap Motion (by Ultraleap) in MRTK

Per usare questo provider di dati, è necessario un controller del movimento [Leap.](https://www.ultraleap.com/product/leap-motion-controller/)

Leap Motion provider di dati il tracciamento delle mani articolato per la realtà virtuale e può essere utile per la creazione rapida di prototipi nell'editor.  Il provider di dati può essere configurato per l'uso di Leap Motion Controller montato su un visore VR o posizionato su un visore della console.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Questo provider può essere usato nell'editor e nel dispositivo nella piattaforma autonoma.  Può essere usato anche nell'editor nella piattaforma UWP, ma NON in una build UWP.

|Versioni supportate dei moduli Leap Motion Unity|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Uso del tracciamento delle mani Leap Motion (by Ultraleap) in MRTK

1. Importazione di moduli MRTK e Leap Motion Unity
    - Installare [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) se non è già installato
    - Importare **il pacchetto Microsoft.MixedReality.Toolkit.Foundation** nel progetto Unity.
    - Scaricare e importare la versione più recente [dei moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto
        - Importare solo il **pacchetto Core** all'interno dei moduli Unity

1. Integrare i moduli Leap Motion Unity con MRTK
    - Quando i moduli Unity sono nel progetto, passare a **Mixed Reality Toolkit** Leap Motion Integrate Leap Motion Unity Modules (Mixed Reality Toolkit Leap  >  **Motion** Integrate Leap Motion Unity  >  **Modules)**
    > [!NOTE]
    > L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti alla definizione dell'assembly **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.** Verificare che Visual Studio sia chiuso.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Aggiunta della proprietà Leap Motion provider di dati
    - Creare una nuova scena Unity
    - Aggiungere MRTK alla scena passando a **Mixed Reality Toolkit** Add to Scene and Configure (Aggiungi alla scena e  >  **configura)**
    - Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare Copia e **personalizza** per clonare il profilo di realtà mista predefinito.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selezionare il profilo **di configurazione** dell'input

    ![Profilo di configurazione dell'input 1](../images/cross-platform/InputConfigurationProfile.png)

    - Selezionare **Clona** nel profilo di sistema di input per abilitare la modifica.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Aprire la **sezione Provider di** dati di input, selezionare **Provider di dati** nella parte superiore. Alla fine dell'elenco verrà aggiunto un nuovo provider di dati.  Aprire il nuovo provider di dati e impostare **Type** su **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**

    ![Leap Add provider di dati](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Selezionare **Clona** per modificare le impostazioni predefinite di Leap Motion.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - L'provider di dati leap contiene `LeapControllerOrientation` la proprietà che rappresenta la posizione del controller del movimento Leap. `LeapControllerOrientation.Headset` indica che il controller è montato su un visore VR. `LeapControllerOrientation.Desk` indica che il controller è posizionato in posizione piatta sulla postazione. Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .
    - Ogni orientamento del controller contiene proprietà di offset:
      - Le **proprietà di** offset dell'orientamento del visore VR rispecchiano le proprietà di offset nel componente LeapXRServiceProvider.  Ha `LeapVRDeviceOffsetMode` tre opzioni: Default, Manual Head Offset e Transform.  Se la modalità di offset è Default, non verrà applicato un offset al controller del movimento Leap.  La modalità Manual Head Offset (Offset head manuale) consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` e `LeapVRDeviceTiltX` .  I valori della proprietà offset dell'asse vengono quindi applicati alla posizione predefinita del controller.  La modalità Offset trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per leap motion controller.
      - **L'orientamento desk** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle mani di salto della cassa.  L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le mani vengano visualizzate davanti e in vista della fotocamera.

        > [!NOTE]
        > Le proprietà di offset nel profilo vengono applicate una sola volta all'avvio dell'applicazione.  Per modificare i valori in fase di esecuzione, ottenere Leap Motion Service Provider da Leap Motion Device Manager:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento del movimento di avvicinamento delle dita/tocco dell'aria.  Il movimento di avvicinamento delle dita viene calcolato misurando la distanza tra la punta del dito indice e la punta del pollice.  Per generare un evento on input down, il valore `EnterPinchDistance` predefinito è 0,02.  Per generare un evento on input up (uscita dalla avvicinamento delle dita), la distanza predefinita tra la punta del dito indice e la punta del pollice è 0,05.

    `LeapControllerOrientation`: Visore VR (predefinito) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Test del movimento leap provider di dati
    - Dopo aver aggiunto leap motion provider di dati al profilo del sistema di input, premere play, spostare la mano davanti a Leap Motion Controller. Dovrebbe essere visualizzata la rappresentazione congiunta della mano.

1. Compilazione del progetto
    - Passare a **Impostazioni di compilazione > file**
    - Sono supportate solo le build autonome se si usa leap motion provider di dati.
    - Per istruzioni su come usare un visore VR Windows Mixed Reality per le build autonome, vedere Compilazione e distribuzione di [MRTK (Standalone).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)

## <a name="getting-the-hand-joints"></a>Ottenere le giunzioni delle mani

Ottenere giunzioni usando il provider di dati leap è identico al recupero delle giunzioni delle mani per una mano articolata MRTK.  Per altre informazioni, vedere [Tracciamento delle mani.](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)

Con MRTK in una scena unity e il provider di dati Leap Motion aggiunto come provider di dati di input nel profilo input system, creare un oggetto gioco vuoto e allegare lo script di esempio seguente.

Questo script è un semplice esempio di come recuperare la posizione del giunzione del palmo in un leap motion hand.  Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano intercalare destra.

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

L'uso dell'provider di dati Leap non richiede un visore VR.  Le modifiche apportate a un'app MRTK possono essere testate nell'editor con le mani leap senza visore VR.

Leap Motion Hands verrà visualizzato nell'editor, senza un visore VR collegato.  Se è `LeapControllerOrientation` impostato su **Visore VR,** il controller Leap Motion dovrà essere tenuto in mano da una mano con la fotocamera rivolta in avanti.

> [!NOTE]
> Se la fotocamera viene spostata usando i tasti WASD nell'editor e il visore VR è , le mani `LeapControllerOrientation` non seguiranno la fotocamera.  Le mani seguiranno il movimento della fotocamera solo se un visore VR è collegato mentre è impostato il `LeapControllerOrientation` **visore VR**.  Le mani leap seguiranno il movimento della fotocamera nell'editor se `LeapControllerOrientation` è impostato su **Desk.**

## <a name="removing-leap-motion-from-the-project"></a>Rimozione di Leap Motion dal progetto

1. Passare ai moduli **Leap**  >  **Motion Separate** leap  >  **motion unity di** Mixed Reality Toolkit
    - Consentire l'aggiornamento di Unity quando i riferimenti nel file **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** vengono modificati in questo passaggio
1. Chiudere Unity
1. Chiudere Visual Studio, se è aperto
1. Aprire Esplora file e passare alla radice del progetto Unity MRTK
    - Eliminare la directory **UnityProjectName/Library**
    - Eliminare la directory **UnityProjectName/Assets/Plugins/LeapMotion**
    - Eliminare il file **UnityProjectName/Assets/Plugins/LeapMotion.meta**
1. Riaprire Unity

In Unity 2018.4 è possibile notare che gli errori rimangono ancora nella console dopo l'eliminazione degli asset Library e Leap Motion Core.
Se gli errori vengono registrati dopo la riapertura, riavviare di nuovo Unity.

## <a name="common-errors"></a>Errori comuni

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion non è integrato con MRTK

Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:

- Passare a **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status (Controlla stato integrazione)**
  - Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono integrati o meno con MRTK.
- Se il messaggio indica che gli asset non sono stati integrati:
  - Assicurarsi che i moduli Leap Motion Unity siano presenti nel progetto
  - Assicurarsi che la versione aggiunta sia supportata. Vedere la tabella nella parte superiore della pagina per le versioni supportate.
  - Provare **Mixed Reality Toolkit > Utilities > Leap Motion > integrare i moduli Leap Motion Unity**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Copia dell'assembly multiplayer HLAPI non riuscita

Durante l'importazione di Leap Motion Unity Core Assets questo errore potrebbe essere registrato:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Soluzione**

- Una soluzione a breve termine consiste nel riavviare Unity. Per altre informazioni, vedere Problema [7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)

## <a name="leap-motion-example-scene"></a>Scena di esempio di movimento intercalare

La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati.

La scena di esempio è contenuta nel pacchetto **Microsoft.MixedReality.Toolkit.Examples** nella directory **MRTK/Examples/Demos/HandTracking/.**  

## <a name="see-also"></a>Vedi anche

-[Provider di input](../features/input/input-providers.md) 
- [Tracciamento manuale](../features/input/hand-tracking.md)
