---
title: LeapMotionMRTK
description: Documentazione per la configurazione del movimento intercalare
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Leap Motion,
ms.openlocfilehash: 02e5393ec05ae206171dd30e55e9cb8e75e95295
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783808"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Come configurare il rilevamento manuale a salto (by Ultraleap) in MRTK

Per utilizzare questo provider di dati, è necessario un [controller di movimento Leap](https://www.ultraleap.com/product/leap-motion-controller/) .

Il movimento intercalare provider di dati Abilita il rilevamento a mano articolato per VR e può essere utile per la prototipazione rapida nell'editor.  Il provider di dati può essere configurato in modo da usare il controller di movimento Leap montato su un auricolare o posizionato su una scrivania.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Questo provider può essere usato nell'editor e nel dispositivo mentre si trova nella piattaforma autonoma.  Può anche essere usato nell'editor mentre si trova nella piattaforma UWP, ma non in una compilazione UWP.

|Versioni del modulo Leap Motion Unity supportate|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Uso del rilevamento della mano Leap Motion (by Ultraleap) in MRTK

1. Importazione dei moduli MRTK e LEAP Unity Motion Unity
    - Installare [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) se non è già installato
    - Importare il pacchetto **Microsoft. MixedReality. Toolkit. Foundation** nel progetto Unity.
    - Scaricare e importare la versione più recente dei [moduli Leap Motion Unity](https://developer.leapmotion.com/unity) nel progetto
        - Importa solo il pacchetto **principale** nei moduli Unity

1. Integrare i moduli Leap Motion Unity con MRTK
    - Dopo che i moduli Unity sono presenti nel progetto, passare a **mixed reality Toolkit**  >  **Leap Motion** Integration  >  **modules di Leap Motion Unity**
    > [!NOTE]
    > L'integrazione dei moduli Unity in MRTK aggiunge 10 definizioni di assembly al progetto e aggiunge riferimenti alla definizione dell'assembly **Microsoft. MixedReality. Toolkit. Providers. LeapMotion** . Verificare che Visual Studio sia chiuso.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Aggiunta del provider di dati di movimento Leap
    - Crea una nuova scena Unity
    - Per aggiungere MRTK alla scena, passare a **mixed reality Toolkit**  >  **Aggiungi alla scena e configurare**
    - Selezionare l'oggetto gioco MixedRealityToolkit nella gerarchia e selezionare **copia e Personalizza** per clonare il profilo di realtà mista predefinito.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Selezionare il profilo di configurazione di **input**

    ![InputConfigurationProfileView](../images/cross-platform/InputConfigurationProfile.png)

    - Selezionare **clona** nel profilo di sistema di input per abilitare la modifica.

    ![LeapMotionInputProfileCloneView](../images/cross-platform/CloneInputSystemProfile.png)

    - Aprire la sezione **provider di dati di input** , selezionare **Aggiungi provider di dati** nella parte superiore, verrà aggiunto un nuovo provider di dati alla fine dell'elenco.  Aprire il nuovo provider di dati e impostare il **tipo** su **Microsoft. MixedReality. Toolkit. LeapMotion. input > LeapMotionDeviceManager**

    ![Immagine di LeapAddDataProvider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Selezionare **clona** per modificare le impostazioni predefinite del movimento intercalare.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Il movimento intercalare provider di dati contiene la `LeapControllerOrientation` proprietà che rappresenta la posizione del controller di movimento LEAP. `LeapControllerOrientation.Headset` indica che il controller è montato su un auricolare. `LeapControllerOrientation.Desk` indica che il controller è posizionato sulla scrivania. Il valore predefinito è impostato su `LeapControllerOrientation.Headset` .
    - Ogni orientamento del controller contiene proprietà offset:
      - Le proprietà offset orientamento **auricolare** rispecchiano le proprietà offset nel componente LeapXRServiceProvider.  In `LeapVRDeviceOffsetMode` sono disponibili tre opzioni: predefinita, offset Head manuale e trasformazione.  Se la modalità offset è predefinita, un offset non verrà applicato al controller Leap Motion.  La modalità di offset Head manuale consente la modifica di tre proprietà: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` e `LeapVRDeviceTiltX` .  I valori della proprietà offset asse vengono quindi applicati al posizionamento predefinito del controller.  La modalità di offset della trasformazione contiene la `LeapVRDeviceOrigin` proprietà Transform che specifica una nuova origine per il controller di movimento LEAP.
      - L'orientamento della **scrivania** contiene la `LeapControllerOffset` proprietà che definisce la posizione di ancoraggio delle lancette del banco intercalare.  L'offset viene calcolato in relazione alla posizione principale della fotocamera e il valore predefinito è (0,-0,2, 0,35) per assicurarsi che le lancette vengano visualizzate in primo piano e in visualizzazione della fotocamera.

        > [!NOTE]
        > Le proprietà offset nel profilo vengono applicate una volta all'avvio dell'applicazione.  Per modificare i valori in fase di esecuzione, ottenere il provider di servizi di movimento Leap dal Gestione dispositivi di movimento intercalare:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` e `ExitPinchDistance` sono le soglie di distanza per il rilevamento del movimento del tocco di pizzico/aria.  Il gesto del pizzico viene calcolato misurando la distanza tra la punta del dito dell'indice e il suggerimento.  Per generare un evento su input inattivo, il valore predefinito `EnterPinchDistance` è impostato su 0,02.  Per generare un evento di input in uscita (uscendo dal pizzico), la distanza predefinita tra il suggerimento per il dito dell'indice e il suggerimento del pollice è 0,05.

    `LeapControllerOrientation`: Auricolare (impostazione predefinita) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Test del provider di dati di movimento intercalare
    - Dopo l'aggiunta del provider di dati di movimento Leap al profilo di sistema di input, premere Play, spostare la mano davanti a Leap Motion controller e visualizzare la rappresentazione congiunta della mano.

1. Compilazione del progetto
    - Passa a **File > impostazioni di compilazione**
    - Solo le compilazioni autonome sono supportate se si usa l'provider di dati Leap Motion.
    - Per istruzioni su come usare un auricolare di realtà mista di Windows per le compilazioni autonome, vedere [compilazione e distribuzione](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).

## <a name="getting-the-hand-joints"></a>Recupero delle giunzioni di mano

Il recupero di giunzioni tramite il provider di dati LEAP è identico a quello di una mano articolata MRTK.  Per ulteriori informazioni, vedere la pagina relativa al [rilevamento manuale](../input/HandTracking.md#polling-joint-pose-from-handjointutils).

Con MRTK in una scena Unity e il movimento Leap provider di dati aggiunto come input provider di dati nel profilo di sistema di input, creare un oggetto gioco vuoto e alleghi lo script di esempio seguente.

Questo script è un semplice esempio di come recuperare la funzione del giunto di Palma in una mano di movimento.  Una sfera segue la mano intercalare sinistra mentre un cubo segue la mano intercalare a destra.

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

## <a name="unity-editor-workflow-tip"></a>Suggerimento del flusso di lavoro dell'editor Unity

L'uso di Leap Motion provider di dati non richiede un auricolare VR.  Le modifiche apportate a un'app MRTK possono essere testate nell'editor con la mano intercalare senza cuffie.

Le lancette del movimento intercalare vengono visualizzate nell'editor, senza una cuffia VR collegata.  Se `LeapControllerOrientation` è impostato su **auricolare**, è necessario che il controller di movimento intercalare venga mantenuto da una mano con la fotocamera rivolte verso l'alto.

> [!NOTE]
> Se la fotocamera viene spostata usando chiavi WASD nell'editor e l' `LeapControllerOrientation` **auricolare** è, le mani non seguiranno la fotocamera. Le lancette seguiranno solo lo spostamento della fotocamera se una cuffia VR è collegata mentre `LeapControllerOrientation` è impostata l' **auricolare**.  Se l'oggetto `LeapControllerOrientation` è impostato su **desk**, seguirà lo spostamento della fotocamera nell'editor.

## <a name="removing-leap-motion-from-the-project"></a>Rimozione del movimento intercalare dal progetto

1. Passare al **Toolkit di realtà mista** per i moduli di movimento a  >    >  **balzo separato**
    - Consentire l'aggiornamento di Unity come riferimento nel file **Microsoft. MixedReality. Toolkit. Providers. LeapMotion. asmdef** vengono modificati in questo passaggio
1. Chiudi Unity
1. Chiudere Visual Studio, se è aperto
1. Aprire Esplora file e passare alla radice del progetto MRTK Unity
    - Elimina la directory **UnityProjectName/Library**
    - Elimina la directory **UnityProjectName/assets/plugins/LeapMotion**
    - Eliminare il file **UnityProjectName/assets/plugins/LeapMotion. meta**
1. Riaprire Unity

In Unity 2018,4, è possibile notare che gli errori rimangono nella console dopo aver eliminato la libreria e le risorse di base del movimento intercalare.
Se gli errori vengono registrati dopo la riapertura, riavviare Unity.

## <a name="common-errors"></a>Errori comuni

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion non è integrato con MRTK

Per verificare se i moduli Leap Motion Unity sono integrati con MRTK:

- Passare a **mixed reality Toolkit > Utilities > Leap Motion > controllare lo stato di integrazione**
  - Verrà visualizzata una finestra popup con un messaggio che indica se i moduli Leap Motion Unity sono stati integrati con MRTK.
- Se il messaggio indica che gli asset non sono stati integrati:
  - Assicurarsi che i moduli Leap Motion Unity siano nel progetto
  - Verificare che la versione aggiunta sia supportata, vedere la tabella nella parte superiore della pagina per le versioni supportate.
  - Provare **mixed reality Toolkit > Utilities > Leap motion > integrare i moduli Leap Motion Unity**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Copia HLAPI multiplayer assembly non riuscita

Durante l'importazione delle risorse di base di Leap Unity Motion, questo errore potrebbe essere registrato:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Soluzione**

- Una soluzione a breve termine prevede il riavvio di Unity. Per ulteriori informazioni, vedere il [problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .

## <a name="leap-motion-example-scene"></a>Scena di esempio Leap Motion

La scena di esempio usa il profilo DefaultLeapMotionConfiguration e determina se il progetto Unity è stato configurato correttamente per l'uso del provider di dati di movimento LEAP.

La scena di esempio è contenuta nel pacchetto **Microsoft. MixedReality. Toolkit. examples** in **MRTK/examples/Demos/HandTracking/** directory.  

## <a name="see-also"></a>Vedi anche

- [Provider di input](../input/InputProviders.md)
- [Rilevamento della mano](../input/HandTracking.md)
