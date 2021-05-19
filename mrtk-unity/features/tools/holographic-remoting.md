---
title: Holographic Remoting
description: Documentazione Holographic Remoting MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144585"
---
# <a name="holographic-remoting"></a>Holographic Remoting

La comunicazione remota olografica trasmettere contenuto olografico da un PC al Microsoft HoloLens in tempo reale, usando una Wi-Fi o una connessione via cavo USB. Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà mista.

XR SDK come indicato di seguito fa riferimento alla nuova [pipeline XR di Unity in Unity 2019.3 e versioni seguenti.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Vedere [qui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) per altre informazioni sull'uso di XR SDK con MRTK. XR legacy si riferisce alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019.3 e rimossa in Unity 2020.

## <a name="initial-setup"></a>Configurazione iniziale

Per abilitare la comunicazione remota a un holoLens, è importante assicurarsi che il progetto utilizzi i componenti remoti più recenti.

1. Apri **finestra > Gestione pacchetti**
    - Se si usa XR legacy: verificare che sia installata la versione più **recente Windows Mixed Reality** pacchetto.
    - Se si usa XR SDK: verificare che sia installata la versione più recente del pacchetto **plug-in Windows XR.**
1. Assicurarsi che l'applicazione Holographic Remoting più recente sia installata in HoloLens tramite il Microsoft Store.

Continuare con le [istruzioni di configurazione di XR legacy](#legacy-xr-setup-instructions) o le istruzioni di configurazione di [XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.

## <a name="legacy-xr-setup-instructions"></a>Istruzioni di configurazione XR legacy

Le istruzioni seguenti si applicano solo alla comunicazione remota con HoloLens 2. Se si esegue la comunicazione remota solo con HoloLens (prima generazione), passare a [Connessione a HoloLens con Wi-Fi.](#connecting-to-the-hololens-with-wi-fi)

Quando si usa un HoloLens 2, è stato aggiunto il supporto per i dati di tracciamento oculare e mano articolati remoti a MRTK. Per abilitare queste funzionalità, seguire la procedura descritta in [Importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).

Dopo l'importazione, il passaggio successivo consiste nel selezionare **Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality** Check Configuration  >  **(Controlla configurazione).** Questo passaggio aggiunge una definizione di scripting che abilita la dipendenza DotNetWinRT.

> [!NOTE]
> Quando si usa Unity 2019.4 e versione più recente, non è necessario eseguire l'utilità Controlla configurazione.

Per abilitare il tracciamento delle giunzioni delle mani e il tracciamento oculare, seguire la procedura descritta nelle sezioni Debug **HoloLens 2 remoto** tramite l'importazione di pacchetti Unity e le sezioni correlate.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debug di HoloLens 2 remota tramite l'importazione di pacchetti Unity

Se HoloLens 2 le giunzioni delle mani e il tracciamento oculare non funzionano con la comunicazione remota, esistono alcuni punti comuni di potenziali problemi. Sono elencati di seguito nell'ordine in cui devono essere controllati.

Questi problemi sono particolarmente rilevanti quando vengono eseguiti **in Unity 2019.3** o versioni successive.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importare DotNetWinRT nel progetto

1. Scaricare lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool)

1. Nella visualizzazione **Individua funzionalità** selezionare Mixed *Reality WinRT Projections (Proiezioni WinRT di realtà mista)*

    ![Selezionare il pacchetto DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. Fare **clic su Ottieni** funzionalità e continuare a [importare il pacchetto](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definite scritte nelle impostazioni del lettore

> [!NOTE]
> Quando si usa Unity 2019.4 e versione più recente, il DOTNETWINRT_PRESENT definito è contenuto nei file asmdef appropriati e non nelle impostazioni del lettore Unity. Il passaggio Controlla configurazione non è obbligatorio.

A partire da MRTK versione 2.5.0, per motivi di prestazioni, questo #define non viene più impostato automaticamente. Per abilitare questo flag, usa la voce di menu **Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality** Check Configuration  >  **(Controlla** configurazione).

> [!Note]
> L'elemento Controlla configurazione non visualizza una conferma. Per verificare che la definizione sia stata impostata, passare a Unity Player Settings (Impostazioni lettore Unity). Da qui, nella scheda UWP, controllare in Altre impostazioni per i simboli di definizione dello scripting. Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente nell'elenco. Se è presente, questo passaggio ha avuto esito positivo.

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Rimozione del HoloLens 2 remoto specifico del servizio

Se si verificano conflitti o altri problemi a causa della presenza dell'adapter DotNetWinRT, contattare una delle [risorse della Guida.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Istruzioni di installazione di XR SDK

Seguire le Windows Mixed Reality di configurazione nella pagina [Getting started with MRTK and XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) (Introduzione a MRTK e XR SDK) e assicurarsi di eseguire il passaggio necessario per holoLens Remoting nell'editor.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Connessione a HoloLens con Wi-Fi

Dopo aver configurato il progetto, è possibile stabilire una connessione a HoloLens.

1. In **Impostazioni > file** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**
1. In HoloLens avviare **l'applicazione Holographic Remoting.**
1. In Unity selezionare **Window > XR > Holographic Emulation (se si usa XR legacy) /Windows XR Plugin Remoting (se si usa XR SDK).**

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. (**_si applica solo a XR legacy)_** Selezionare La **versione del dispositivo.**

    ![Selezionare la versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Usando l'indirizzo IP visualizzato dall'applicazione Holographic Remoting Player, impostare il **campo Computer** remoto.

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

1. Fare clic su **Connetti**.

> [!NOTE]
> Se non è possibile connettersi, assicurarsi che HoloLens 2 dispositivo non sia collegato al PC e riavviare Unity.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Connessione a HoloLens con cavo USB

La connessione tramite cavo USB offre una qualità e una stabilità di rendering migliori. Per usare la connessione tramite cavo USB, disconnettiti da HoloLens Wi-Fi in Impostazioni di HoloLens e avvia l'app Holographic Remoting Player. Verrà visualizzato un indirizzo IP che inizia con 169. Usare questo indirizzo IP nell'impostazione Holographic Emulation (Emulazione olografica) di Unity per connettersi. Dopo aver identificato l'indirizzo IP per il cavo USB, è possibile connettere di nuovo HoloLens Wi-Fi dispositivo.

## <a name="starting-a-remoting-session"></a>Avvio di una sessione remota

Con Unity connesso a HoloLens, entra in modalità di riproduzione nell'editor.

Al termine della sessione, uscire dalla modalità di riproduzione.

> [!NOTE]
> Esiste un problema noto con alcune versioni di Unity a causa del quale l'editor potrebbe bloccarsi quando entra in modalità di riproduzione durante una sessione remota. Questo problema può manifestarsi se la finestra olografica è aperta quando viene caricato il progetto. Per assicurarsi che questo problema non si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.

## <a name="see-also"></a>Vedi anche

- [Risoluzione dei problemi e limitazioni di Holographic Remoting](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Condizioni di licenza software di Microsoft Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)