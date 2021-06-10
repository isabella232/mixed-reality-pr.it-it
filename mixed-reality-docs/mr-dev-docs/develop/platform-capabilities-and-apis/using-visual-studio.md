---
title: Uso di Visual Studio per la distribuzione e il debug
description: Informazioni su come compilare, sottoporre a debug e distribuire app per HoloLens e Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543227"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso di Visual Studio per la distribuzione e il debug

Indipendentemente dal fatto che venga usato DirectX o Unity per lo sviluppo di un'app di realtà mista, Visual Studio rimane lo strumento ideale per il debug e la distribuzione. In questa sezione imparerai a eseguire le operazioni seguenti:
* Distribuire applicazioni nel visore VR immersive di HoloLens o Windows Mixed Reality tramite Visual Studio.
* Usare l'emulatore HoloLens incorporato in Visual Studio.
* Eseguire il debug di app di realtà mista.

## <a name="prerequisites"></a>Prerequisiti

1. Per le istruzioni di installazione, vedi [Installare gli strumenti](../../develop/install-the-tools.md#installation-checklist).
2. Crea un progetto di app di Windows universale in Visual Studio.  Per HoloLens (prima generazione), usa Visual Studio 2017 o versione successiva.  Per HoloLens 2, usare Visual Studio 2019 16.2 o versione successiva. C# e C++ sono supportati. In alternativa, segui le istruzioni per [creare un'app in Unity](../../develop/unity/tutorials/holograms-100.md).

## <a name="enabling-developer-mode"></a>Abilitazione della modalità sviluppatore

Per iniziare, abilita **Modalità sviluppatore** sul tuo dispositivo per consentire a Visual Studio di connettersi.

### <a name="hololens"></a>HoloLens

1. Accendi HoloLens e il dispositivo.
2. Usare il [gesto Start](../../design/system-gesture.md) per avviare il menu principale.
3. Seleziona il riquadro **Impostazioni** per avviare l'app nell'ambiente in uso.
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilitare **Usa le funzionalità per sviluppatori** per distribuire le app Visual Studio in HoloLens. Se il dispositivo esegue Windows Holographic versione 21H1 o successiva, abilitare anche **Individuazione dispositivi**.
7. Facoltativo: scorrere verso il basso e abilitare anche il **Portale di dispositivi**, che consente di connettersi al [Portale di dispositivi di Windows](using-the-windows-device-portal.md) in HoloLens da un Web browser.

### <a name="windows-pc"></a>PC Windows

Se si usa un visore VR di Windows Mixed Reality connesso al PC, è necessario abilitare **Modalità sviluppatore** nel PC.
1. Vai a **Impostazioni**
2. Seleziona **Aggiornamento e sicurezza**
3. Seleziona **Per gli sviluppatori**
4. Abilitare **Modalità sviluppatore**, leggere la dichiarazione di non responsabilità relativa all'impostazione scelta e quindi selezionare Sì per accettare la modifica.

## <a name="deploying-a-hololens-app-over-wi-fi"></a>Distribuzione di un'app HoloLens Wi-Fi 

Configurare il Visual Studio progetto con le proprietà seguenti:

1. Selezionare le opzioni di compilazione delle app
    * Per i progetti Unity scegliere **Versione o** **Master** 
    * Per tutti gli altri progetti, scegliere **Versione**

> [!NOTE]
> È possibile trovare definizioni complete per ogni opzione di compilazione nell'esportazione e nella [Visual Studio soluzioni](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Selezionare la configurazione di compilazione in base al dispositivo

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Seleziona **Computer remoto** nel menu a discesa delle destinazioni di distribuzione

![Destinazione di distribuzione computer remoto in Visual Studio](images/remotemachinesetting_arm64.png)

Successivamente, è necessario impostare la connessione remota. Per i progetti C++ e JavaScript, vai a **Progetto > Proprietà > Proprietà di configurazione > Debug**. Se si lavora in un progetto C#, verrà visualizzata automaticamente una finestra di dialogo.

> [!NOTE]
> Se la finestra di dialogo di connessione remota non viene visualizzata nel progetto C#, è possibile aprirla manualmente da **Proprietà > Debug**.

1. Immetti l'indirizzo IP del tuo dispositivo nel campo **Indirizzo** o **Nome computer**. 
    * È possibile trovare l'indirizzo IP in HoloLens in Impostazioni **> rete & Internet > opzioni avanzate**
    * È sempre consigliabile immettere manualmente l'indirizzo IP anziché a seconda della funzionalità Rilevata automaticamente

2. Impostare la **modalità di autenticazione** su Universale **(protocollo non crittografato)**

  ![Finestra di dialogo connessione remota in Visual Studio](images/remotedeploy.png)

3. Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze
    * Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug
    * Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

4. La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

## <a name="deploying-a-hololens-app-over-usb"></a>Distribuzione di un'app HoloLens tramite USB 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Selezionare le opzioni di compilazione delle app
    * Per i progetti Unity scegliere **Versione o** **Master** 
    * Per tutti gli altri progetti, scegliere **Versione**

> [!NOTE]
> È possibile trovare definizioni complete per ogni opzione di compilazione nell'esportazione e nella [Visual Studio soluzioni](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Selezionare la configurazione di compilazione in base al dispositivo

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Seleziona **Dispositivo** nel menu a discesa delle destinazioni di distribuzione

![Distribuzione dispositivi in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze
    * Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug
    * Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)</br>

5. La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN. Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.

> [!NOTE]
> Se si verifica un ritardo notevole con la distribuzione delle app tramite USB, è consigliabile usare le istruzioni del [computer](#deploying-a-hololens-app-over-wi-fi) remoto nella sezione precedente.

## <a name="deploying-an-app-to-the-hololens-emulator"></a>Distribuzione di un'app nell'emulatore HoloLens

1. Assicurarsi di aver installato **[l'emulatore HoloLens 2 o HoloLens (prima generazione)](../install-the-tools.md#installation-checklist)**
2. Selezionare la configurazione di compilazione e l'emulatore in base al dispositivo

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze
    * Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug
    * Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debugg

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a>Distribuzione di un'app VR nel PC locale 

Per usare un visore VR immersive di Windows Mixed Reality che si connette al PC o al [simulatore di realtà mista](using-the-windows-mixed-reality-simulator.md):
1. Seleziona una configurazione di build **x86** o **x64** per l'app
2. Seleziona **Computer locale** nel menu a discesa delle destinazioni di distribuzione
3. Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze
    * Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug
    * Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug

## <a name="pairing-your-device"></a>Associazione del dispositivo

La prima volta che viene distribuita un'app da Visual Studio al dispositivo HoloLens, verrà chiesto di specificare un PIN. In HoloLens generare un PIN avviando l'app Settings, passare a **Update > For Developers** (Aggiorna > Per gli sviluppatori) e toccare **Pair** (Associa). Quando il PIN viene visualizzato in HoloLens, digitarlo in Visual Studio. Al termine dell'associazione, tocca **Fine** su HoloLens per chiudere la finestra di dialogo. Il PC è ora associato a HoloLens ed è possibile distribuire le app automaticamente. Ripetere questi passaggi per tutti i PC usati per distribuire app in HoloLens.

Per dissociare HoloLens da tutti i computer associati:
* Avviare l'app **Settings**, passare a **Update > For Developers** (Aggiorna > Per sviluppatori) e toccare **Clear** (Cancella).

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Debugger grafica per HoloLens (prima generazione)

Gli strumenti di Diagnostica della grafica di Visual Studio sono utili per la scrittura e l'ottimizzazione di un'app olografica. Per informazioni dettagliate, vedi [Diagnostica della grafica di Visual Studio su MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).

**Per avviare Debugger grafica**
1. Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Vai a **Debug > Grafica > Avvia diagnostica**
3. La prima volta che viene avviata la diagnostica con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato. Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.

## <a name="profiling"></a>Profilatura

Gli strumenti di profilatura di Visual Studio consentono di analizzare le prestazioni e l'uso delle risorse dell'app. Sono inclusi strumenti per ottimizzare l'uso di CPU, memoria, grafica e rete. Per i dettagli completi, vedi [Eseguire strumenti di diagnostica senza debug in MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).

**Per avviare gli strumenti di profilatura con HoloLens**
1. Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore
2. Vai a **Debug > Avvia strumenti di diagnostica senza debug**
3. Seleziona gli strumenti che vuoi usare
4. Selezionare **Avvia**.
5. La prima volta che viene avviata la diagnostica senza debug con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato. Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.

## <a name="debugging-an-installed-or-running-app"></a>Debug di un'app installata o in esecuzione

È possibile usare Visual Studio per eseguire il debug di un'app di Windows universale installata senza distribuzione da un progetto di Visual Studio. Questa opzione è utile se si vuole eseguire il debug di un pacchetto dell'app installato o di un'app già in esecuzione.
1. Vai a **Debug -> Altre destinazioni debug -> Debug del pacchetto dell'app installato**
2. Seleziona la destinazione **Computer remoto** per HoloLens o **Computer locale** per i visori VR immersive.
3. Immetti l'**indirizzo IP** del dispositivo
4. Scegli la modalità di autenticazione **Universale**
5. La finestra mostra le app in esecuzione e inattive. Seleziona quella di cui vuoi eseguire il debug.
6. Scegli il tipo di codice di cui eseguire il debug (gestito, nativo, misto)
7. Selezionare **Associa** o **Avvia**.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo con Unity che è stato delineato, ci si trova nella fase di distribuzione. Da qui, è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [Distribuzione nell'emulatore HoloLens](using-the-hololens-emulator.md)

In alternativa, passare direttamente all'aggiunta di servizi avanzati:

> [!div class="nextstepaction"]
> [Servizi avanzati](../../develop/unity/unity-development-overview.md#5-adding-services)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Distribuzione e debug delle app UWP (Universal Windows Platform)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [Abilitare il dispositivo per lo sviluppo](/windows/uwp/get-started/enable-your-device-for-development)
