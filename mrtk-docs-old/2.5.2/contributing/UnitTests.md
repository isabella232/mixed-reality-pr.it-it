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
ms.locfileid: "101782206"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="33361-104">Scrittura ed esecuzione di test in MRTK</span><span class="sxs-lookup"><span data-stu-id="33361-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="33361-105">Per assicurarsi che MRTK sia affidabile, MRTK dispone di un set di test per garantire che le modifiche apportate al codice non regressionino il comportamento esistente.</span><span class="sxs-lookup"><span data-stu-id="33361-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="33361-106">Un ottimo code coverage dei test in una codebase di grandi dimensioni come MRTK è fondamentale per la stabilità e la sicurezza quando si apportano modifiche.</span><span class="sxs-lookup"><span data-stu-id="33361-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="33361-107">MRTK usa il [Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) che usa un'integrazione di Unity di [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="33361-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="33361-108">Questa guida fornirà un punto di partenza per l'aggiunta di test a MRTK.</span><span class="sxs-lookup"><span data-stu-id="33361-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="33361-109">Non verranno illustrati [unit test runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) e [NUnit](https://nunit.org/) che possono essere cercati nei collegamenti forniti.</span><span class="sxs-lookup"><span data-stu-id="33361-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="33361-110">Prima di inviare una richiesta pull, assicurarsi di:</span><span class="sxs-lookup"><span data-stu-id="33361-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="33361-111">Eseguire i test in locale, in modo che le modifiche non regressionino il comportamento esistente (il completamento delle richieste pull non sarà consentito in caso di esito negativo</span><span class="sxs-lookup"><span data-stu-id="33361-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="33361-112">Se si corregge un bug, scrivere un test per testare la correzione e assicurarsi che le future modifiche al codice non lo interrompano nuovamente.</span><span class="sxs-lookup"><span data-stu-id="33361-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="33361-113">Se si scrive una funzionalità, scrivere nuovi test per impedire che le modifiche al codice imminenti comportano l'esecuzione di questa funzionalità</span><span class="sxs-lookup"><span data-stu-id="33361-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="33361-114">Attualmente i test di PlayMode devono essere eseguiti in Unity 2018,4 e possono avere esito negativo in altre versioni di Unity</span><span class="sxs-lookup"><span data-stu-id="33361-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="33361-115">Esecuzione di test</span><span class="sxs-lookup"><span data-stu-id="33361-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="33361-116">Editor Unity</span><span class="sxs-lookup"><span data-stu-id="33361-116">Unity editor</span></span>

<span data-ttu-id="33361-117">[Unit test runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) si trova in **finestra**  >  **generale**  >  **Test Runner** e Mostra tutti i test disponibili in modalità di riproduzione e modifica MRTK.</span><span class="sxs-lookup"><span data-stu-id="33361-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="33361-118">Riga di comando</span><span class="sxs-lookup"><span data-stu-id="33361-118">Command line</span></span>

<span data-ttu-id="33361-119">I test possono essere eseguiti anche da uno script di [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) che si trova in `Scripts\test\run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="33361-119">Tests can also be run by a [powershell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="33361-120">Verranno eseguiti i test PlayMode esattamente come vengono eseguiti in GitHub/CI (vedere di seguito) e i risultati di stampa.</span><span class="sxs-lookup"><span data-stu-id="33361-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="33361-121">Di seguito sono riportati alcuni esempi di come eseguire lo script</span><span class="sxs-lookup"><span data-stu-id="33361-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="33361-122">Eseguire i test nel progetto situato in H:\mrtk.dev, con Unity 2018,4 (ad esempio Unity 2018.4.26 F1)</span><span class="sxs-lookup"><span data-stu-id="33361-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="33361-123">Eseguire i test nel progetto situato in H:\mrtk.dev, con Unity 2018,4, output results to C:\ playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="33361-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="33361-124">È anche possibile eseguire i test di PlayMode più volte tramite lo `run_repeat_tests.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="33361-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="33361-125">È possibile utilizzare tutti i parametri utilizzati in `run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="33361-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="33361-126">Convalida richiesta pull</span><span class="sxs-lookup"><span data-stu-id="33361-126">Pull request validation</span></span>

<span data-ttu-id="33361-127">CI compilerà MRTK in tutte le configurazioni ed eseguirà tutti i test in modalità di modifica e riproduzione.</span><span class="sxs-lookup"><span data-stu-id="33361-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="33361-128">CI può essere attivato inviando un commento in GitHub pull `/azp run mrtk_pr` se l'utente dispone di diritti sufficienti.</span><span class="sxs-lookup"><span data-stu-id="33361-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="33361-129">Le esecuzioni CI possono essere visualizzate nella scheda ' verifiche ' della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="33361-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="33361-130">Solo dopo che tutti i test sono stati superati, è possibile eseguire il merge della richiesta pull in mrtk_development.</span><span class="sxs-lookup"><span data-stu-id="33361-130">Only after all of the tests have passed successfully can the PR be merged into mrtk_development.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="33361-131">Test di stress/test bulk</span><span class="sxs-lookup"><span data-stu-id="33361-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="33361-132">A volte i test avranno esito negativo solo occasionalmente, che può essere frustrante per eseguire il debug.</span><span class="sxs-lookup"><span data-stu-id="33361-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="33361-133">Per eseguire più test in locale, modificare gli script di test in base a.</span><span class="sxs-lookup"><span data-stu-id="33361-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="33361-134">Lo script Python seguente dovrebbe rendere questo scenario più pratico.</span><span class="sxs-lookup"><span data-stu-id="33361-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="33361-135">Il prerequisito per l'esecuzione dello script Python è che [Python 3. X è installato](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="33361-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="33361-136">Per un singolo test che deve essere eseguito più volte:</span><span class="sxs-lookup"><span data-stu-id="33361-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="33361-137">Eseguire il comando seguente da una riga di comando (si consiglia[PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true) )</span><span class="sxs-lookup"><span data-stu-id="33361-137">Run the following from a command line ([PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="33361-138">Copiare e incollare l'output nel file di test.</span><span class="sxs-lookup"><span data-stu-id="33361-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="33361-139">Lo script seguente è per l'esecuzione di più test in sequenza:</span><span class="sxs-lookup"><span data-stu-id="33361-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="33361-140">Il nuovo file di test dovrebbe ora contenere</span><span class="sxs-lookup"><span data-stu-id="33361-140">The new test file should now contain</span></span>

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

<span data-ttu-id="33361-141">Aprire Test Runner e osservare i nuovi test che ora possono essere chiamati ripetutamente.</span><span class="sxs-lookup"><span data-stu-id="33361-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="33361-142">Scrittura di test</span><span class="sxs-lookup"><span data-stu-id="33361-142">Writing tests</span></span>

<span data-ttu-id="33361-143">Esistono due tipi di test che è possibile aggiungere per il nuovo codice</span><span class="sxs-lookup"><span data-stu-id="33361-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="33361-144">Test in modalità di riproduzione</span><span class="sxs-lookup"><span data-stu-id="33361-144">Play mode tests</span></span>
* <span data-ttu-id="33361-145">Test in modalità di modifica</span><span class="sxs-lookup"><span data-stu-id="33361-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="33361-146">Test in modalità di riproduzione</span><span class="sxs-lookup"><span data-stu-id="33361-146">Play mode tests</span></span>

<span data-ttu-id="33361-147">I test in modalità di riproduzione MRTK sono in grado di testare il modo in cui la nuova funzionalità risponde a diverse origini di input, ad esempio mani o occhi.</span><span class="sxs-lookup"><span data-stu-id="33361-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="33361-148">I nuovi test in modalità di riproduzione possono ereditare [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) o la struttura seguente può essere usata.</span><span class="sxs-lookup"><span data-stu-id="33361-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) or the skeleton below can be used.</span></span>

<span data-ttu-id="33361-149">Per creare un nuovo test in modalità di riproduzione:</span><span class="sxs-lookup"><span data-stu-id="33361-149">To create a new play mode test:</span></span>

* <span data-ttu-id="33361-150">Passare a Asset > MRTK > test > PlayModeTests</span><span class="sxs-lookup"><span data-stu-id="33361-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="33361-151">Fare clic con il pulsante destro del mouse su Crea > test > script di test C#</span><span class="sxs-lookup"><span data-stu-id="33361-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="33361-152">Sostituire il modello predefinito con lo scheletro riportato di seguito</span><span class="sxs-lookup"><span data-stu-id="33361-152">Replace the default template with the skeleton below</span></span>

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

### <a name="edit-mode-tests"></a><span data-ttu-id="33361-153">Test in modalità di modifica</span><span class="sxs-lookup"><span data-stu-id="33361-153">Edit mode tests</span></span>

<span data-ttu-id="33361-154">I test in modalità di modifica vengono eseguiti in modalità di modifica di Unity e possono essere aggiunti nella  >  cartella **test** MRTK  >  **EditModeTests** nel repository del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="33361-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="33361-155">Per creare un nuovo test è possibile usare il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="33361-155">To create a new test the following template can be used:</span></span>

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

### <a name="test-naming-conventions"></a><span data-ttu-id="33361-156">Testare le convenzioni di denominazione</span><span class="sxs-lookup"><span data-stu-id="33361-156">Test naming conventions</span></span>

<span data-ttu-id="33361-157">I test devono essere in genere denominati in base alla classe da testare o allo scenario che sta testando.</span><span class="sxs-lookup"><span data-stu-id="33361-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="33361-158">Ad esempio, data una classe da sottoporre a test:</span><span class="sxs-lookup"><span data-stu-id="33361-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="33361-159">Prendere in considerazione la denominazione del test</span><span class="sxs-lookup"><span data-stu-id="33361-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="33361-160">Provare a collocare il test in una gerarchia di cartelle simile al file non di test corrispondente.</span><span class="sxs-lookup"><span data-stu-id="33361-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="33361-161">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="33361-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="33361-162">Ciò consente di verificare che esista un modo ovvio per trovare la classe di test corrispondente di ogni classe, se tale classe di test esiste.</span><span class="sxs-lookup"><span data-stu-id="33361-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="33361-163">Il posizionamento dei test basati sullo scenario è meno definito: se il test esercita il sistema di input globale, ad esempio, è consigliabile inserirlo in una cartella "InputSystem" nella cartella di test della modalità di modifica o della modalità di riproduzione corrispondente.</span><span class="sxs-lookup"><span data-stu-id="33361-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="33361-164">Icone script di test</span><span class="sxs-lookup"><span data-stu-id="33361-164">Test script icons</span></span>

<span data-ttu-id="33361-165">Quando si aggiunge un nuovo test, modificare lo script in modo che abbia l'icona MRTK corretta.</span><span class="sxs-lookup"><span data-stu-id="33361-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="33361-166">A tale scopo, è disponibile uno strumento MRTK semplice:</span><span class="sxs-lookup"><span data-stu-id="33361-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="33361-167">Vai alla voce di menu del Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="33361-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="33361-168">Fare clic su utilità, quindi su Aggiorna e quindi su icone</span><span class="sxs-lookup"><span data-stu-id="33361-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="33361-169">Fare clic su test e l'aggiornamento verrà eseguito automaticamente, aggiornando gli script di test privi di icone</span><span class="sxs-lookup"><span data-stu-id="33361-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="33361-170">Metodi di utilità MRTK</span><span class="sxs-lookup"><span data-stu-id="33361-170">MRTK Utility methods</span></span>

<span data-ttu-id="33361-171">Questa sezione illustra alcuni dei frammenti di codice/metodi di uso comune durante la scrittura di test per MRTK.</span><span class="sxs-lookup"><span data-stu-id="33361-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="33361-172">Sono disponibili due classi di utilità che semplificano la configurazione di MRTK e il test delle interazioni con i componenti in MRTK</span><span class="sxs-lookup"><span data-stu-id="33361-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="33361-173">TestUtilities fornisce i metodi seguenti per configurare la scena MRTK e GameObject:</span><span class="sxs-lookup"><span data-stu-id="33361-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

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

<span data-ttu-id="33361-174">Vedere la documentazione dell'API di [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) e [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) per altri metodi di queste classi util Man mano che vengono estese a intervalli regolari mentre vengono aggiunti nuovi test a MRTK.</span><span class="sxs-lookup"><span data-stu-id="33361-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>

## <a name="see-also"></a><span data-ttu-id="33361-175">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="33361-175">See also</span></span>

* [<span data-ttu-id="33361-176">Guida alla generazione del portale della documentazione</span><span class="sxs-lookup"><span data-stu-id="33361-176">Documentation portal generation guide</span></span>](DevDocGuide.md)
