---
title: HolographicRemoting
description: Documentazione di comunicazione remota olografica MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 28baab75d6aacb79d60a79a67681021906435521
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687971"
---
# <a name="holographic-remoting"></a>Holographic Remoting

La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione via cavo Wi-Fi o USB. Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà miste.

## <a name="initial-setup"></a>Configurazione iniziale

Per abilitare la comunicazione remota a una HoloLens, è importante assicurarsi che il progetto usi i componenti .NET Remoting più recenti.

1. Apri **finestra > gestione pacchetti**
    - Verificare che sia installata la versione più recente del pacchetto di **realtà mista di Windows** .
1. Verificare che nell'HoloLens sia installata la versione più recente dell'applicazione di comunicazione remota olografica tramite il Microsoft Store.

### <a name="hololens-2"></a>HoloLens 2

Quando si usa HoloLens 2, è stato aggiunto il supporto per i dati di rilevamento a mano e a occhio articolato per la comunicazione remota in MRTK. Per abilitare queste funzionalità, configurare il progetto seguendo questa procedura.

1. Eseguire l'utilità MRTK Configurator (**mixed reality Toolkit > Utilities > configurare il progetto Unity**)
1. Espandi **modifiche configurazioni**

    ![MRTK Configurator](../Images/Tools/Remoting/EnableMSBuildForUnity.png)

1. Assicurarsi che sia selezionata l'opzione **Abilita MSBuild per Unity**
1. Fare clic su **Applica**.

Quando si usa **unity 2019,3** e versioni successive, l' **Abilitazione di MSBuild per Unity** non è disponibile. per abilitare la comunicazione remota olografica, attenersi alle procedure riportate di seguito.

1. Eseguire l'utilità MRTK Configurator (**mixed reality Toolkit > Utilities > configurare il progetto Unity**)
1. Impostare la piattaforma di destinazione in **File > impostazioni di compilazione** su **piattaforma UWP (Universal Windows Platform)**
1. Fare clic su **Applica**.
1. Apri **finestra > gestione pacchetti**
    - Verificare che il **plug-in Windows XR** non sia installato se il progetto non usa [XR SDK](../../configuration/GettingStartedWithMRTKAndXRSDK.md), perché il pacchetto di **realtà mista di Windows** legacy non funzionerà insieme a esso.
1. Apri **Impostazioni progetto modifica > > lettore**

    ![SDK di realtà mista di Windows](../Images/Tools/Remoting/WindowsMixedRealitySDK.png)

1. Verificare che sia selezionata l'opzione **realtà virtuale supportata** e che la **realtà mista di Windows** venga aggiunta agli **SDK di realtà virtuale**

Per abilitare il rilevamento dei giunti della mano e del rilevamento degli occhi, seguire i passaggi descritti nell' **importazione di servizi remoti HoloLens 2 tramite l'importazione dei pacchetti Unity** e le sezioni correlate.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debug di HoloLens 2 Remoting tramite l'importazione di pacchetti Unity

Se HoloLens 2 e la verifica degli occhi non funzionano sulla comunicazione remota, esistono alcuni punti comuni di potenziali problemi. Questi elementi sono elencati di seguito nell'ordine in cui devono essere controllati.

Questi problemi sono particolarmente rilevanti quando vengono eseguiti in **unity 2019,3** o versioni successive.

#### <a name="msbuildforunity-package-import-via-writing-into-the-packagemanifest"></a>Importazione del pacchetto MSBuildForUnity tramite la scrittura nel file Package. manifest

> [!Note]
> Si è verificato un problema noto che impedisce a MSBuild per Unity di funzionare correttamente in alcune versioni di Unity 2019. Per evitare questo problema, MRTK non supporta MSBuild per Unity in Unity 2019,3.
>
> Per acquisire il pacchetto NuGet necessario quando si esegue in Unity 2019,3, vedere le [istruzioni di installazione manuale](#manual-dotnetadapter-installation).

Il modo migliore per verificare è aprire Gestione pacchetti > finestra e assicurarsi che MSBuild per Unity venga visualizzato nell'elenco dei pacchetti. Se è presente, si supponga che questo passaggio sia riuscito. Se non è presente, provare a eseguire il Toolkit di realtà mista-> Utilities-> configurare Unity e ripetere i passaggi precedenti per l'esecuzione di MRTK Configurator.

![Gestione pacchetti MSB4U](../Images/Tools/Remoting/MSB4UPackageManager.png)

#### <a name="dotnetwinrt-nuget-package-resolution"></a>Risoluzione del pacchetto NuGet DotNetWinRT

Il modo migliore per verificare la ricerca consiste nel cercare DotNetWinRT.dll nella cartella assets. Se il problema persiste, passare alla cartella Asset nella visualizzazione del progetto e selezionare `[ProjectName].Dependencies.msb4u.csproj` . Supponendo che la parte 1 abbia avuto esito positivo, deve essere presente un controllo personalizzato con pulsanti Compila, ricompila e Pulisci. Provare a fare clic su Compila o Ricompila, quindi eseguire di nuovo la ricerca DotNetWinRT.dll. Se la DLL esiste ora, il passaggio è riuscito.

![Controllo DotNetAdapter](../Images/Tools/Remoting/DotNetAdapterInspector.png)

#### <a name="dotnetadaptercsproj-missing"></a>DotNetAdapter. csproj mancante

Se il passaggio precedente non riesce, è opportuno verificare che nel progetto sia presente il csproj appropriato. Controllare in MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter e verificare che sia presente DotNetAdapter. csproj. Un caso comune in cui questo file potrebbe non esistere è se il file con estensione gitignore ignora i file csproj ed è stato eseguito il commit dei file MRTK in un repository remoto. In tal caso, assicurarsi di forzare l'aggiunta di DotNetAdapter. csproj con `git add -f [path/to]/DotNetAdapter.csproj` per assicurarsi che venga eseguito il commit e la clonazione per tutti gli altri collaboratori o computer.

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>`DOTNETWINRT_PRESENT` #define scritte in Impostazioni lettore

Passare alle impostazioni del lettore Unity. Da qui, nella scheda UWP, controllare le altre impostazioni per i simboli di definizione dello scripting. Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente in tale elenco. Questa operazione è stata completata.

![DotNetWinRT presente](../Images/Tools/Remoting/DotNetWinRTPresent.png)

#### <a name="failure-to-find-dotnetexe"></a>Impossibile trovare dotnet.exe

MSBuild per Unity dipende da dotnet.exe esistente nel percorso di sistema. dotnet.exe devono essere installati e presenti nella variabile di ambiente PATH. Se nessuno di questi requisiti è true, questo errore può essere manifesto nella console di Unity:

```cmd
Win32Exception: ApplicationName='dotnet', CommandLine='msbuild DotNetAdapter.csproj -restore  -v:minimal -p:NuGetInteractive=true  -t:Build -p:Configuration=Release -nologo', CurrentDirectory='C:\src\Assets\MRTK\Providers\WindowsMixedReality\Shared\DotNetAdapter', Native error= The system cannot find the file specified.
```

La soluzione consiste nel verificare che gli strumenti di [interfaccia della riga di comando di .NET Core siano installati](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) e riavviare il sistema per forzare l'esecuzione di un percorso di sistema aggiornato per tutte le app.

Se le giunzioni di mano sulla comunicazione remota continuano a non funzionare dopo aver eseguito i passaggi precedenti, potrebbe essersi verificato un problema di configurazione nei profili per le giunzioni di mano generale sul dispositivo. In tal caso, contattare [una delle risorse della Guida](../../WelcomeToMRTK.md#getting-help).

#### <a name="manual-dotnetadapter-installation"></a>Installazione manuale di DotNetAdapter

Nel caso in cui l'installazione di DotNetAdapter non possa essere eseguita tramite MSBuild per Unity, è possibile eseguire i passaggi seguenti.

> [!Important]
> L'uso di MSBuild per Unity e di un altro client NuGet nello stesso progetto non è supportato e può causare potenziali problemi di risoluzione delle dipendenze.

1. Installare un client NuGet

    > [!Note]
    > Le istruzioni seguenti presuppongono l'uso di [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)

1. Passare all'interfaccia utente del client NuGet

    ![Avviare l'interfaccia utente di NuGet](../Images/Tools/Remoting/LaunchNuGetForUnity.png)

1. Individuare il `Microsoft.Windows.MixedReality.DotNetWinRT` pacchetto

    ![Individua pacchetto](../Images/Tools/Remoting/LocateDotNetWinRT.png)

1. Selezionare Installa

### <a name="removing-hololens-2-specific-remoting-support"></a>Rimozione del supporto per servizi remoti specifici di HoloLens 2

Se si verificano conflitti o altri problemi causati dalla presenza dell'adattatore DotNetWinRT, contattare [una delle risorse della Guida](../../WelcomeToMRTK.md#getting-help).

È anche possibile rimuovere temporaneamente l'adapter per aggirare il problema tramite i passaggi seguenti:

1. In Unity passare a Window-> Package Manager e disinstallare MSBuild for Unity.
1. Cercare DotNetWinRT.dll nell'elenco asset in Unity ed eliminare la DLL o eliminare i plug-in (MRTK 2,2 o versioni precedenti) o le dipendenze (MRTK 2,3 o versione successiva) che contengono alcuni livelli. Questo dovrebbe rimuovere questi spazi dei nomi in conflitto, mantenendo MRTK.
1. Opzionale Passare a MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter in Esplora file (non la visualizzazione asset di Unity) ed eliminare le `.bin` `.obj` cartelle e. In questo modo viene rimossa la cache locale dei pacchetti NuGet ripristinati per DotNetWinRT.
1. Se si esegue di nuovo lo strumento di configurazione di MRTK, assicurarsi di non abilitare di nuovo MSBuild per Unity.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Connessione a HoloLens con Wi-Fi

Una volta configurato il progetto, è possibile stabilire una connessione a HoloLens.

1. In **File > impostazioni di compilazione** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**
1. In HoloLens avviare l'applicazione di **comunicazione remota olografica** .
1. In Unity selezionare **Window > XR > emulazione olografica**.

    ![Avviare l'emulazione olografica](../Images/Tools/Remoting/StartHolographicEmulation.png)

1. Impostare la **modalità di emulazione** su da **remoto a dispositivo**.

    ![Impostare la modalità di emulazione](../Images/Tools/Remoting/SelectEmulationMode.png)

1. Selezionare la **versione del dispositivo**.

    ![Selezionare la versione del dispositivo](../Images/Tools/Remoting/SelectDeviceVersion.png)

1. Usando l'indirizzo IP visualizzato dall'applicazione del lettore di comunicazione remota olografico, impostare il campo **computer remoto** .

    ![Immettere l'indirizzo IP](../Images/Tools/Remoting/EnterIPAddress.png)

1. Fare clic su **Connect** (Connetti).

> [!NOTE]
> Se non è possibile connettersi, assicurarsi che HoloLens 2 non sia collegato al PC e riavviare Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Connessione a HoloLens con cavo USB

La connessione via cavo USB garantisce maggiore qualità e stabilità di rendering. Per usare la connessione via cavo USB, disconnettersi da HoloLens da Wi-Fi nelle impostazioni di HoloLens e avviare l'app lettore remoto olografico. Verrà visualizzato un indirizzo IP che inizia con 169. Usare questo indirizzo IP nell'impostazione di emulazione olografica di Unity per connettersi. Quando l'indirizzo IP per il cavo USB è stato identificato, è possibile connettere il HoloLens a Wi-Fi nuovamente.

## <a name="starting-a-remoting-session"></a>Avvio di una sessione remota

Con Unity connected to the HoloLens, immettere Play Mode nell'editor.

Al termine della sessione, uscire dalla modalità di riproduzione.

> [!NOTE]
> Si è verificato un problema noto con alcune versioni di Unity in cui l'editor potrebbe bloccarsi dopo l'immissione della modalità di riproduzione durante una sessione remota. Questo problema può manifestarsi se la finestra olografica è aperta quando il progetto viene caricato. Per evitare che il problema si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.

## <a name="see-also"></a>Vedi anche

- [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Condizioni di licenza del software Microsoft olografico Remoting](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
