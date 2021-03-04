---
title: UnitTests
description: UnitTests per controllare reliablity di MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, UnitTest,
ms.openlocfilehash: 958f6ae59736003141d0cc96a6706d211be5709c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783043"
---
# <a name="writing-and-running-tests-in-mrtk"></a>Scrittura ed esecuzione di test in MRTK

Per assicurarsi che MRTK sia affidabile, MRTK dispone di un set di test per garantire che le modifiche apportate al codice non regressionino il comportamento esistente. Un ottimo code coverage dei test in una codebase di grandi dimensioni come MRTK è fondamentale per la stabilità e la sicurezza quando si apportano modifiche.

MRTK usa il [Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) che usa un'integrazione di Unity di [NUnit](https://nunit.org/). Questa guida fornirà un punto di partenza per l'aggiunta di test a MRTK. Non verranno illustrati [unit test runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) e [NUnit](https://nunit.org/) che possono essere cercati nei collegamenti forniti.

Prima di inviare una richiesta pull, assicurarsi di:

1. Eseguire i test in locale, in modo che le modifiche non regressionino il comportamento esistente (il completamento delle richieste pull non sarà consentito in caso di esito negativo

1. Se si corregge un bug, scrivere un test per testare la correzione e assicurarsi che le future modifiche al codice non lo interrompano nuovamente.

1. Se si scrive una funzionalità, scrivere nuovi test per impedire che le modifiche al codice imminenti comportano l'esecuzione di questa funzionalità

Attualmente i test di PlayMode devono essere eseguiti in Unity 2018,4 e possono avere esito negativo in altre versioni di Unity

## <a name="running-tests"></a>Esecuzione di test

### <a name="unity-editor"></a>Editor Unity

[Unit test runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) si trova in **finestra**  >  **generale**  >  **Test Runner** e Mostra tutti i test disponibili in modalità di riproduzione e modifica MRTK.

### <a name="command-line"></a>Riga di comando

I test possono essere eseguiti anche da uno script di [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) che si trova in `Scripts\test\run_playmode_tests.ps1` . Verranno eseguiti i test PlayMode esattamente come vengono eseguiti in GitHub/CI (vedere di seguito) e i risultati di stampa. Di seguito sono riportati alcuni esempi di come eseguire lo script

Eseguire i test nel progetto situato in H:\mrtk.dev, con Unity 2018,4 (ad esempio Unity 2018.4.26 F1)

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Eseguire i test nel progetto situato in H:\mrtk.dev, con Unity 2018,4, output results to C:\ playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

È anche possibile eseguire i test di PlayMode più volte tramite lo `run_repeat_tests.ps1` script. È possibile utilizzare tutti i parametri utilizzati in `run_playmode_tests.ps1` .

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Convalida richiesta pull

CI compilerà MRTK in tutte le configurazioni ed eseguirà tutti i test in modalità di modifica e riproduzione. CI può essere attivato inviando un commento in GitHub pull `/azp run mrtk_pr` se l'utente dispone di diritti sufficienti. Le esecuzioni CI possono essere visualizzate nella scheda ' verifiche ' della richiesta pull.

Solo dopo che tutti i test sono stati superati, è possibile eseguire il merge della richiesta pull in mrtk_development.

### <a name="stress-tests--bulk-tests"></a>Test di stress/test bulk

A volte i test avranno esito negativo solo occasionalmente, che può essere frustrante per eseguire il debug.

Per eseguire più test in locale, modificare gli script di test in base a. Lo script Python seguente dovrebbe rendere questo scenario più pratico.

Il prerequisito per l'esecuzione dello script Python è che [Python 3. X è installato](https://www.python.org/downloads/).

Per un singolo test che deve essere eseguito più volte:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Eseguire il comando seguente da una riga di comando (si consiglia[PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true) )

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Copiare e incollare l'output nel file di test. Lo script seguente è per l'esecuzione di più test in sequenza:

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

Il nuovo file di test dovrebbe ora contenere

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

Aprire Test Runner e osservare i nuovi test che ora possono essere chiamati ripetutamente.

## <a name="writing-tests"></a>Scrittura di test

Esistono due tipi di test che è possibile aggiungere per il nuovo codice

* Test in modalità di riproduzione
* Test in modalità di modifica

### <a name="play-mode-tests"></a>Test in modalità di riproduzione

I test in modalità di riproduzione MRTK sono in grado di testare il modo in cui la nuova funzionalità risponde a diverse origini di input, ad esempio mani o occhi.

I nuovi test in modalità di riproduzione possono ereditare [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) o la struttura seguente può essere usata.

Per creare un nuovo test in modalità di riproduzione:

* Passare a Asset > MRTK > test > PlayModeTests
* Fare clic con il pulsante destro del mouse su Crea > test > script di test C#
* Sostituire il modello predefinito con lo scheletro riportato di seguito

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a>Test in modalità di modifica

I test in modalità di modifica vengono eseguiti in modalità di modifica di Unity e possono essere aggiunti nella  >  cartella **test** MRTK  >  **EditModeTests** nel repository del Toolkit di realtà mista.
Per creare un nuovo test è possibile usare il modello seguente:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a>Testare le convenzioni di denominazione

I test devono essere in genere denominati in base alla classe da testare o allo scenario che sta testando.
Ad esempio, data una classe da sottoporre a test:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Prendere in considerazione la denominazione del test

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Provare a collocare il test in una gerarchia di cartelle simile al file non di test corrispondente.
Ad esempio:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Ciò consente di verificare che esista un modo ovvio per trovare la classe di test corrispondente di ogni classe, se tale classe di test esiste.

Il posizionamento dei test basati sullo scenario è meno definito: se il test esercita il sistema di input globale, ad esempio, è consigliabile inserirlo in una cartella "InputSystem" nella cartella di test della modalità di modifica o della modalità di riproduzione corrispondente.

### <a name="test-script-icons"></a>Icone script di test

Quando si aggiunge un nuovo test, modificare lo script in modo che abbia l'icona MRTK corretta. A tale scopo, è disponibile uno strumento MRTK semplice:

1. Vai alla voce di menu del Toolkit per realtà mista
1. Fare clic su utilità, quindi su Aggiorna e quindi su icone
1. Fare clic su test e l'aggiornamento verrà eseguito automaticamente, aggiornando gli script di test privi di icone

### <a name="mrtk-utility-methods"></a>Metodi di utilità MRTK

Questa sezione illustra alcuni dei frammenti di codice/metodi di uso comune durante la scrittura di test per MRTK.

Sono disponibili due classi di utilità che semplificano la configurazione di MRTK e il test delle interazioni con i componenti in MRTK

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities fornisce i metodi seguenti per configurare la scena MRTK e GameObject:

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

Vedere la documentazione dell'API di [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) e [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) per altri metodi di queste classi util Man mano che vengono estese a intervalli regolari mentre vengono aggiunti nuovi test a MRTK.

## <a name="see-also"></a>Vedi anche

* [Guida alla generazione del portale della documentazione](DevDocGuide.md)
