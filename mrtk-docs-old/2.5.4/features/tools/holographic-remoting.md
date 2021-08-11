---
title: OlographicRemoting
description: Documentazione Holographic Remoting MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 095ebd577ed5b7217c87c641fd8f3b764ab9ecbf1e771b1c1cb364c517e2cc7a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218985"
---
# <a name="holographic-remoting"></a>Holographic Remoting

La comunicazione remota olografica trasmettere contenuto olografico da un PC al Microsoft HoloLens in tempo reale, usando una Wi-Fi o una connessione via cavo USB. Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà mista.

XR SDK come indicato di seguito fa riferimento alla nuova [pipeline XR di Unity in Unity 2019.3 e oltre.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Vedere [qui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) per altre informazioni sull'uso di XR SDK con MRTK. XR legacy si riferisce alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019.3 e rimossa in Unity 2020.

## <a name="initial-setup"></a>Configurazione iniziale

Per abilitare la comunicazione remota a HoloLens, è importante assicurarsi che il progetto utilizzi i componenti remoti più recenti.

1. Apri **finestra > Gestione pacchetti**
    - Se si usa XR legacy: verificare che sia installata la versione più recente **Windows Mixed Reality** pacchetto.
    - Se si usa XR SDK: verificare che sia installata la versione più recente **Windows pacchetto plug-in XR.**
1. Assicurarsi che l'applicazione Holographic Remoting più recente sia installata nel HoloLens, tramite il Microsoft Store.

Continuare con le [istruzioni di configurazione legacy di XR](#legacy-xr-setup-instructions) o [XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.

## <a name="legacy-xr-setup-instructions"></a>Istruzioni di configurazione XR legacy

Le istruzioni seguenti si applicano solo alla comunicazione remota con HoloLens 2. Se si esegue la comunicazione remota solo con HoloLens (prima generazione), passare a Connessione al HoloLens [con Wi-Fi](#connecting-to-the-hololens-with-wi-fi).

Quando si usa un HoloLens 2, è stato aggiunto il supporto per i dati di tracciamento oculare e mano articolati remoti a MRTK. Per abilitare queste funzionalità, seguire la procedura descritta in [Importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).

Dopo l'importazione, il passaggio successivo consiste nel selezionare **Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration**. Questo passaggio aggiunge una definizione di scripting che abilita la dipendenza DotNetWinRT.

Per abilitare il rilevamento delle giunzioni delle mani e del tracciamento oculare, seguire la procedura descritta in Debug **HoloLens 2 comunicazione** remota tramite l'importazione del pacchetto Unity e le sezioni correlate.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debug HoloLens 2 comunicazione remota tramite l'importazione di pacchetti Unity

Se HoloLens 2 le giunzioni delle mani e il tracciamento oculare non funzionano con la comunicazione remota, esistono alcuni punti comuni di potenziali problemi. Sono elencati di seguito nell'ordine in cui devono essere controllati.

Questi problemi sono particolarmente rilevanti quando vengono eseguiti **in Unity 2019.3** o versioni successive.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importare DotNetWinRT nel progetto

1. Installare un client NuGet client

    > [!Note]
    > Le istruzioni seguenti presupsumo [l'uso NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)

1. Passare all'interfaccia NuGet client

    ![Avviare l NuGet'interfaccia utente](../images/tools/remoting/LaunchNuGetForUnity.png)

1. Individuare il `Microsoft.Windows.MixedReality.DotNetWinRT` pacchetto

    ![Individuare il pacchetto](../images/tools/remoting/LocateDotNetWinRT.png)

1. Selezionare Installa

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definire scritto nelle impostazioni del lettore

A partire da MRTK versione 2.5.0, per motivi di prestazioni, questa #define non viene più impostata automaticamente. Per abilitare questo flag, usare la voce di **menu Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration** (Controlla configurazione).

> [!Note]
> L'elemento Controlla configurazione non visualizza una conferma. Per verificare che la definizione sia stata impostata, passare alla pagina unity player Impostazioni. Da qui, nella scheda UWP, selezionare in Altri Impostazioni simboli di definizione dello scripting. Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente in tale elenco. Se è presente, questo passaggio ha avuto esito positivo.

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Rimozione del HoloLens 2 remoto specifico

Se si verificano conflitti o altri problemi a causa della presenza dell'adapter DotNetWinRT, contattare una delle [risorse della Guida.](../../welcome-to-mrtk.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Istruzioni di configurazione di XR SDK

Seguire le Windows Mixed Reality di configurazione nella pagina Introduzione a [MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e XR SDK e assicurarsi di eseguire il passaggio necessario per la comunicazione remota nell'editor HoloLens remota.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Connessione al HoloLens con Wi-Fi

Dopo aver configurato il progetto, è possibile stabilire una connessione al HoloLens.

1. In **File > build Impostazioni** assicurarsi che il tipo di compilazione del progetto sia impostato su Universal Windows **Platform**
1. Nel HoloLens avviare **l'applicazione Holographic Remoting.**
1. In Unity selezionare **Window > XR > Holographic Emulation (se si usa XR legacy) /Windows XR Plugin Remoting (se si usa XR SDK).**

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Si applica solo a XR legacy)_** Selezionare La **versione del dispositivo**.

    ![Selezionare La versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Usando l'indirizzo IP visualizzato dall'applicazione Holographic Remoting Player, impostare il **campo Computer** remoto.

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

1. Fare clic su **Connetti**.

> [!NOTE]
> Se non è possibile connettersi, assicurarsi che il HoloLens 2 non sia collegato al PC e riavviare Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Connessione all'HoloLens con cavo USB

La connessione tramite cavo USB offre una qualità e una stabilità di rendering migliori. Per usare la connessione tramite cavo USB, disconnettersi dal HoloLens da Wi-Fi nel Impostazioni di HoloLens e avviare l'app Holographic Remoting Player. Verrà visualizzato un indirizzo IP che inizia con 169. Usare questo indirizzo IP nell'impostazione Di emulazione olografica di Unity per connettersi. Dopo aver identificato l'indirizzo IP per il cavo USB, è possibile connettere il HoloLens a Wi-Fi nuovo.

## <a name="starting-a-remoting-session"></a>Avvio di una sessione remota

Con Unity connesso al HoloLens, immettere la modalità di riproduzione nell'editor.

Al termine della sessione, uscire dalla modalità di riproduzione.

> [!NOTE]
> Esiste un problema noto con alcune versioni di Unity in cui l'editor può bloccarsi quando si entra in modalità di riproduzione durante una sessione remota. Questo problema può verificarsi se la finestra Holographic è aperta quando viene caricato il progetto. Per assicurarsi che questo problema non si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.

## <a name="see-also"></a>Vedi anche

- [Risoluzione dei problemi e limitazioni di Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Condizioni di licenza software di Microsoft Holographic Remoting](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
