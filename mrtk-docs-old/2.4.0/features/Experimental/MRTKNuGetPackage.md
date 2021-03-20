---
title: MRTKNuGetPakages
description: Pakages NuGet in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: eb41896977bded6dd5b1aec7c4b17632435c6b94
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692728"
---
# <a name="mixed-reality-toolkit-nuget-package"></a>Pacchetto NuGet del Toolkit per realtà mista

Il Toolkit di realtà mista (MRTK) è ora disponibile come pacchetto NuGet in NuGet.org. Esistono alcune differenze per quanto riguarda l'utilizzo della versione NuGet di MRTK anziché di un file unitypackage Tools, leggere le [considerazioni sui pacchetti NuGet](#nuget-package-considerations) di seguito. Se si verificano problemi, archiviare un problema usando questo [modello](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=).

> [!NOTE]
> La migrazione dei progetti esistenti per l'utilizzo di MRTK come pacchetto NuGet non è ancora supportata. Usare MRTK tramite NuGet solo per i nuovi progetti.

## <a name="installing-the-nuget-package"></a>Installazione del pacchetto NuGet

Seguire queste istruzioni per aggiungere il Toolkit di realtà mista come pacchetto NuGet al progetto.

1. Scaricare la versione più recente di [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) . file unitypackage Tools.
    1. Se *NuGetForUnity* è già installato, verificare che sia la versione **2.0.0 o successiva**.
1. Importare il pacchetto nel progetto Unity, [istruzioni](https://docs.unity3d.com/Manual/AssetPackages.html).
1. Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**.

    ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
1. Nella casella di ricerca immettere **Microsoft. MixedReality. Toolkit**.

    ![Manage NuGet Packages](../Images/NuGet/SearchBox.png)
1. Scegliere il pacchetto MRTK Core:
    - **Microsoft. MixedReality. Toolkit. Foundation** : pacchetto principale per MRTK.
1. Opzionale Scegliere i pacchetti facoltativi MRTK.
    - **Microsoft. MixedReality. Toolkit. examples** : pacchetto che contiene tutti i nostri esempi.
    - **Microsoft. MixedReality. Toolkit. Extensions** : pacchetto che contiene i servizi e/o i provider di dati delle estensioni.
    - **Microsoft. MixedReality. Toolkit. Tools** : contiene alcuni degli strumenti forniti con MRTK (finestra di compilazione e così via).

### <a name="updating-mrtk-nuget-packages"></a>Aggiornamento dei pacchetti NuGet MRTK

I passaggi 1-2 precedenti dovranno essere eseguiti una sola volta per il progetto e l'aggiornamento è un passaggio molto più semplice. Quando i pacchetti più recenti sono disponibili in NuGet.org (inclusa la versione preliminare), seguire questa procedura:

1. Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**
1. Passare alla scheda **aggiornamenti** .
    - Se si desidera ottenere la versione provvisoria più recente, selezionare la casella di controllo **Mostra versione preliminare** .
1. Aggiornare i pacchetti desiderati.

## <a name="nuget-package-considerations"></a>Considerazioni sui pacchetti NuGet

Il rilascio di MRTK come pacchetto NuGet è un nuovo meccanismo di distribuzione che viene esaminato e ci sono due vantaggi chiave e considerazioni che è necessario apportare quando si sceglie se utilizzare la versione NuGet di MRTK.

### <a name="migrating-to-nuget-from-unitypackage-or-source-not-yet-supported"></a>Migrazione a NuGet da. file unitypackage Tools o source (non ancora supportata)

Il pacchetto NuGet è costituito da binari compilati e non da file script separati. gli identificatori degli asset di script C# sono diversi. Di conseguenza, gli asset come i prefabbricati nel pacchetto MRTK sono stati aggiornati per fare riferimento allo script compilato appropriato. Un progetto che usa la versione con estensione file unitypackage Tools o source di MRTK dovrà ridestinare anche le proprie risorse e anche se è presente codice per questo scenario non è ancora supportato.

> [!IMPORTANT]
> Non è attualmente supportata la migrazione a NuGet da. file unitypackage Tools o source. Questo cambiamento verrà modificato quando si continua a sviluppare questo meccanismo di recapito.

### <a name="compiled-binaries-nuget-vs-source-files-unitypackage"></a>File binari compilati (NuGet) e file di origine (con estensione file unitypackage Tools)

Poiché il pacchetto NuGet contiene i binari compilati anziché gli script, questo presenta due vantaggi principali:

- Tempo di compilazione ridotto
- Un numero notevolmente inferiore di file di progetto C# in Visual Studio

### <a name="debugging-mixed-reality-toolkit"></a>Debug del Toolkit per realtà mista

Esistono problemi noti relativi a Unity & Visual Studio Tools per Unity che impediscono il debug di un PDB nel debugger di Visual Studio. Quindi, anche se il pacchetto viene fornito con PDB e l'origine incorporata, il debug delle dll è possibile solo se è stato compilato localmente (leggere più avanti). Esiste una soluzione alternativa compilata come parte di [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/), più aggiornamenti in quel momento.

## <a name="locally-building-the-nuget-package"></a>Compilazione locale del pacchetto NuGet

Con l'origine più recente di MRTK, è possibile compilare il pacchetto NuGet localmente e configurare NuGetForUnity per selezionarlo.

1. Scaricare la versione più recente dell'origine MRTK.
1. Eseguire lo `scripts\packaging\createnugetpackages.ps1` script di PowerShell.
    - Specificare il `-UnityDirectory` flag passando la cartella dell'editor dell'installazione di Unity
    - Specificare il `-Version` del pacchetto da creare, nel formato x. x. x. **Verificare che la versione sia superiore a quella disponibile in NuGet.org**
    - **Esempio:** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`
1. Una volta completata la compilazione, aprire il progetto di destinazione con i pacchetti NuGet.
    - Fare clic sul menu **modifica**  >  **Preferenze...**

        ![Modifica la voce di menu preferenze](../Images/NuGet/ProjectPreferences.png)
    - A sinistra, trovare **NuGet per la scheda Unity** .

        ![Modifica la voce di menu preferenze](../Images/NuGet/NuGetForUnityPreferencesTab.png)
    - Premere **Aggiungi nuova origine** e sostituire **source_path** con il `<Path to your Repository>\NuGet\artifacts`

        ![Modifica la voce di menu preferenze](../Images/NuGet/AddNewSource.png)
    - Nella parte inferiore, fare clic sul pulsante **Salva** .

        ![Modifica la voce di menu preferenze](../Images/NuGet/SaveNewSource.png)
1. Se la prima volta che si compila o la versione è stata incrementata, seguire il processo di aggiornamento:
    1. Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**.

        ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
    1. Passare alla scheda **aggiornamenti** .

        ![Manage NuGet Packages](../Images/NuGet/UpdatesTab.png)
    1. Aggiornare i pacchetti alla versione appena compilata desiderata.
1. In caso contrario, è sufficiente eliminare la `Assets\Packages` cartella e consentire a NuGetForUnity di ripristinare i pacchetti.

## <a name="see-also"></a>Vedi anche

- [Compilazione e distribuzione di MRTK](../../updates-deployment/BuildAndDeploy.md)
- [Contenuto del pacchetto MRTK](MRTK_PackageContents.md)
