---
title: HolographicRemoting
description: Documentazione di comunicazione remota olografica MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 8e7a2bcbadd8f07ceb9c9bba5391a93aec51d903
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782807"
---
# <a name="holographic-remoting"></a>Holographic Remoting

La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione via cavo Wi-Fi o USB. Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà miste.

XR SDK come indicato di seguito si riferisce alla [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Vedere [qui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) per altre informazioni sull'uso di XR SDK con MRTK. La versione precedente di XR si riferisce alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019,3 ed è stata rimossa in Unity 2020.

## <a name="initial-setup"></a>Configurazione iniziale

Per abilitare la comunicazione remota a una HoloLens, è importante assicurarsi che il progetto usi i componenti .NET Remoting più recenti.

1. Apri **finestra > gestione pacchetti**
    - Se si usa la versione precedente di XR: verificare che sia installata la versione più recente del pacchetto di **realtà mista di Windows** .
    - Se si usa XR SDK: verificare che sia installata la versione più recente del pacchetto di plug-in **Windows XR** .
1. Verificare che nell'HoloLens sia installata la versione più recente dell'applicazione di comunicazione remota olografica tramite il Microsoft Store.

Continuare con [le istruzioni di installazione legacy XR](#legacy-xr-setup-instructions) o [le istruzioni di installazione di XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.

## <a name="legacy-xr-setup-instructions"></a>Istruzioni per l'installazione di XR legacy

Le istruzioni seguenti sono valide solo per la comunicazione remota con HoloLens 2. Se si esegue solo la comunicazione remota con HoloLens (1a generazione), passare alla [connessione a HoloLens con Wi-Fi](#connecting-to-the-hololens-with-wi-fi).

Quando si usa HoloLens 2, è stato aggiunto il supporto per i dati di rilevamento a mano e a occhio articolato per la comunicazione remota in MRTK. Per abilitare queste funzionalità, seguire i passaggi descritti in [importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).

Una volta importato, il passaggio successivo consiste nel selezionare le utilità del **Toolkit di realtà misto**  >    >  Windows configurazione controllo della **realtà mista**  >  . Questo passaggio aggiunge una definizione di script che Abilita la dipendenza DotNetWinRT.

Per abilitare il rilevamento dei giunti della mano e del rilevamento degli occhi, seguire i passaggi descritti nell' **importazione di servizi remoti HoloLens 2 tramite l'importazione dei pacchetti Unity** e le sezioni correlate.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debug di HoloLens 2 Remoting tramite l'importazione di pacchetti Unity

Se HoloLens 2 e la verifica degli occhi non funzionano sulla comunicazione remota, esistono alcuni punti comuni di potenziali problemi. Questi elementi sono elencati di seguito nell'ordine in cui devono essere controllati.

Questi problemi sono particolarmente rilevanti quando vengono eseguiti in **unity 2019,3** o versioni successive.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importa DotNetWinRT nel progetto

1. Installare un client NuGet

    > [!Note]
    > Le istruzioni seguenti presuppongono l'uso di [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)

1. Passare all'interfaccia utente del client NuGet

    ![Avviare l'interfaccia utente di NuGet](../images/tools/remoting/LaunchNuGetForUnity.png)

1. Individuare il `Microsoft.Windows.MixedReality.DotNetWinRT` pacchetto

    ![Individua pacchetto](../images/tools/remoting/LocateDotNetWinRT.png)

1. Selezionare Installa

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definire scritte in Impostazioni lettore

A partire da MRTK versione 2.5.0, per motivi di prestazioni, questo #define non viene più impostato automaticamente. Per abilitare questo flag, usare la voce di menu configurazione di Microsoft Mixed **reality Toolkit**  >  **Utilities**  >    >   .

> [!Note]
> L'elemento di configurazione check non visualizza una conferma. Per confermare che la definizione è stata impostata, passare alle impostazioni del lettore Unity. Da qui, nella scheda UWP, controllare le altre impostazioni per i simboli di definizione dello scripting. Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente in tale elenco. Questa operazione è stata completata.

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Rimozione del supporto per servizi remoti specifici di HoloLens 2

Se si verificano conflitti o altri problemi causati dalla presenza dell'adattatore DotNetWinRT, contattare [una delle risorse della Guida](../../welcome-to-mrtk.md#getting-help).

## <a name="xr-sdk-setup-instructions"></a>Istruzioni di installazione di XR SDK

Seguire le [istruzioni di configurazione della realtà mista di Windows nella pagina Introduzione a MRTK e XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e assicurarsi di eseguire il passaggio necessario per la comunicazione remota HoloLens in-Editor.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Connessione a HoloLens con Wi-Fi

Una volta configurato il progetto, è possibile stabilire una connessione a HoloLens.

1. In **File > impostazioni di compilazione** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**
1. In HoloLens avviare l'applicazione di **comunicazione remota olografica** .
1. In Unity selezionare la **finestra > XR > emulazione olografica (se si usa il plug-in Legacy XR)/Windows XR plug-in (se si usa XR SDK)**.

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. Impostare la **modalità di emulazione** su da **remoto a dispositivo**.

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Si applica solo a una versione precedente di XR_**) Selezionare la **versione del dispositivo**.

    ![Selezionare la versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. Usando l'indirizzo IP visualizzato dall'applicazione del lettore di comunicazione remota olografico, impostare il campo **computer remoto** .

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

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
