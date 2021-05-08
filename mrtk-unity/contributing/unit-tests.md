---
title: UnitTests
description: UnitTests per verificare la reliblità di MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, UnitTest,
ms.openlocfilehash: 51a485ff258ceafb8841ff1b86e715b1623f3255
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489241"
---
# <a name="writing-and-running-tests-in-mrtk"></a>Scrittura ed esecuzione di test in MRTK

Per garantire l'affidabilità di MRTK, MRTK dispone di un set di test per garantire che le modifiche al codice non regredino nel comportamento esistente. Avere un buon code coverage di test in una grande codebase come MRTK è fondamentale per la stabilità e la sicurezza quando si apportano modifiche.

MRTK usa [l'Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) che usa un'integrazione unity di [NUnit](https://nunit.org/). Questa guida fornirà un punto di partenza per aggiungere test a MRTK. Non verranno illustrate le Test Runner [Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) e [NUnit](https://nunit.org/) che possono essere cercate nei collegamenti forniti.

Prima di inviare una richiesta pull, assicurarsi di:

1. Eseguire i test in locale in modo che le modifiche non regrediscano il comportamento esistente (il completamento delle PR non sarà consentito se i test hanno esito negativo).

1. Se si corregge un bug, scrivere un test per testare la correzione e assicurarsi che le future modifiche al codice non lo interrompano di nuovo.

1. Se si scrive una funzionalità, scrivere nuovi test per evitare che le prossime modifiche del codice infrangono questa funzionalità.

Attualmente i test playmode devono essere eseguiti in Unity 2018.4 e potrebbero non riuscire in altre versioni di Unity

## <a name="running-tests"></a>Esecuzione di test

### <a name="unity-editor"></a>Editor Unity

Il [Test Runner Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) è disponibile in **Finestra** generale Test Runner e mostra tutti i test di riproduzione e modifica  >    >   MRTK disponibili.

### <a name="command-line"></a>Riga di comando

I test possono essere eseguiti anche da uno script [di PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) disponibile in `Scripts\test\run_playmode_tests.ps1` . Verranno eseguiti i test playmode esattamente come vengono eseguiti in GitHub/CI (vedere di seguito) e verranno stampati i risultati. Ecco alcuni esempi di come eseguire lo script

Eseguire i test sul progetto che si trova in H:\mrtk.dev, con Unity 2018.4 (ad esempio Unity 2018.4.26f1)

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Eseguire i test sul progetto che si trova in H:\mrtk.dev, con Unity 2018.4, restituisce i risultati a C:\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

È anche possibile eseguire i test playmode più volte tramite lo `run_repeat_tests.ps1` script. È possibile usare tutti `run_playmode_tests.ps1` i parametri usati in .

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Convalida delle richieste pull

L'interfaccia utente di MRTK compila MRTK in tutte le configurazioni ed esegue tutti i test in modalità di modifica e riproduzione. L'cid può essere attivata pubblicando un commento nella richiesta pull di GitHub `/azp run mrtk_pr` se l'utente dispone di diritti sufficienti. Le esecuzioni ci sono visibili nella scheda "controlli" della richiesta pull.

Solo dopo che tutti i test sono stati superati correttamente, la richiesta pull può essere unita in main.

### <a name="stress-tests--bulk-tests"></a>Test di stress/test in blocco

In alcuni casi i test avranno esito negativo solo occasionalmente e ciò può risultare frustrante per il debug.

Per eseguire più test in locale, modificare gli script di test in base a . Lo script Python seguente dovrebbe rendere questo scenario più pratico.

Il prerequisito per l'esecuzione dello script Python [è l'installazione di Python 3.X.](https://www.python.org/downloads/)

Per un singolo test che deve essere eseguito più volte:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Eseguire il comando seguente dalla riga di comando[(è consigliato PowerShell)](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)

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

Aprire il Test Runner e osservare i nuovi test che ora possono essere chiamati ripetutamente.

## <a name="writing-tests"></a>Scrittura di test

Esistono due tipi di test che è possibile aggiungere per il nuovo codice

* Test della modalità di riproduzione
* Test in modalità di modifica

### <a name="play-mode-tests"></a>Test della modalità di riproduzione

I test della modalità di riproduzione MRTK hanno la possibilità di testare il modo in cui la nuova funzionalità risponde a diverse origini di input, ad esempio mani o occhi.

I nuovi test della modalità di riproduzione possono [ereditare BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) oppure è possibile usare lo scheletro seguente.

Per creare un nuovo test della modalità di riproduzione:

* Passare ad Assets > MRTK > Tests > PlayModeTests
* Fare clic con il pulsante destro del mouse su Crea > test > script di test C#
* Sostituire il modello predefinito con lo scheletro seguente

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

I test in modalità di modifica vengono eseguiti in modalità di modifica di Unity e possono essere aggiunti nella cartella EditModeTests dei test **MRTK** nel  >    >   repo Mixed Reality Toolkit.
Per creare un nuovo test, è possibile usare il modello seguente:

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

I test devono in genere essere denominati in base alla classe che stanno testando o allo scenario in cui vengono testati.
Ad esempio, data una classe da testare:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Provare a assegnare un nome al test

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Provare a inserire il test in una gerarchia di cartelle simile al file non di test corrispondente.
Ad esempio:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Ciò consente di verificare che sia disponibile un modo ovvio per trovare la classe di test corrispondente di ogni classe, se esiste una classe di test di questo tipo.

Il posizionamento dei test basati su scenario è meno definito. Se il test esegue l'esercizio del sistema di input complessivo, ad esempio, è consigliabile inserire il test in una cartella "InputSystem" nella cartella di test della modalità di modifica o di riproduzione corrispondente.

### <a name="test-script-icons"></a>Icone dello script di test

Quando si aggiunge un nuovo test, modificare lo script in modo che abbia l'icona MRTK corretta. A tale scopo, è possibile usare un semplice strumento MRTK:

1. Passare alla voce di menu Mixed Reality Toolkit
1. Fare clic su Utilità, quindi su Aggiorna e infine su Icone
1. Fare clic su Test. Lo updater verrà eseguito automaticamente, aggiornando tutti gli script di test senza le relative icone

### <a name="mrtk-utility-methods"></a>Metodi dell'utilità MRTK

Questa sezione illustra alcuni dei frammenti di codice/metodi di uso comune durante la scrittura di test per MRTK.

Sono disponibili due classi di utilità che consentono di configurare MRTK e testare le interazioni con i componenti in MRTK

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities offre i metodi seguenti per configurare la scena MRTK e i GameObject:

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

Per altri metodi di queste classi util, vedere la documentazione dell'API di e perché vengono estese a intervalli regolari mentre vengono aggiunti nuovi test [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) a MRTK.