---
title: Uso di Microsoft Edge in realtà mista di Windows
description: Prepararsi per la nuova Microsoft Edge in realtà mista di Windows. Include le modifiche da prevedere, gli aggiornamenti per la ricerca e i problemi noti.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, Home, esplorazione, esplorazione, app, giochi, Microsoft Edge, Chromium, Edge, 360, 360 video, 360 Viewer
ms.openlocfilehash: 26691dd3cf1b8e620373ef150de61cd2c7f461db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581299"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Realtà mista di Windows e la nuova Microsoft Edge

Il [nuovo Microsoft Edge](https://www.microsoft.com/edge) è disponibile per il download e ha iniziato a implementare automaticamente i clienti tramite Windows Update. 

Il nuovo Microsoft Edge [adotta il progetto Chromium Open Source](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) sul desktop. In questo modo si crea una migliore compatibilità per i clienti e una minore frammentazione per gli sviluppatori Web. Supporta anche WebXR al lancio, che è il nuovo standard per la creazione di esperienze Web Immersive per gli auricolari VR, al posto di WebVR.

>[!IMPORTANT]
>Quando si installa Microsoft Edge in un dispositivo Windows 10 aggiornato, la versione precedente (legacy) del PC verrà sostituita.

## <a name="installing-the-new-microsoft-edge"></a>Installazione del nuovo Microsoft Edge 

Prima di installare il nuovo Microsoft Edge, **eseguire l'aggiornamento a Windows 10 versione 1903 o successiva per il supporto delle applicazioni Win32 native come il nuovo Microsoft Edge** in realtà mista di Windows. Controllare Windows Update o [installare manualmente la versione più recente di Windows 10](https://www.microsoft.com/software-download/windows10).

Una volta installato Windows 10 versione 1903 o successiva, si è pronti per la nuova Microsoft Edge. La nuova Microsoft Edge viene implementata tramite Windows Update, ma è possibile installare manualmente il nuovo Microsoft Edge dal [sito Web Microsoft Edge](https://www.microsoft.com/edge) , se lo si vuole prima.

>[!IMPORTANT]
>Il nuovo Microsoft Edge viene avviato con supporto per WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR. Quando si installa il nuovo Microsoft Edge, non sarà più possibile riprodurre esperienze WebVR in Microsoft Edge. 

## <a name="known-issues"></a>Problemi noti

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o versioni successive)

- L'avvio di qualsiasi app Win32, incluso il nuovo Microsoft Edge, causa un blocco breve della visualizzazione dell'auricolare.
- Il riquadro Microsoft Edge scompare dal menu Start della realtà mista di Windows (è possibile trovarlo nella cartella "app classiche").
- Windows dal Microsoft Edge precedente è ancora situato intorno alla Home realtà mista, ma non può essere usato. Il tentativo di attivare tali finestre viene avviato nell'app desktop.
- Selezionando un collegamento ipertestuale nella Home realtà mista viene avviato un Web browser sul desktop anziché la Home realtà mista.
- L'app WebVR Showcase è presente nella Home realtà mista, nonostante WebVR non sia più supportata.
- Miglioramenti generali al lancio da tastiera e agli oggetti visivi.

### <a name="monitor-and-input-handling-issues"></a>Problemi di monitoraggio e gestione degli input

Dopo aver eseguito l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 o successiva, i monitoraggi virtuali verranno visualizzati come monitoraggi fisici generici nelle **impostazioni > sistema > visualizzare durante le** sessioni di realtà mista di Windows. Alcuni clienti, in particolare quelli con più di un monitor fisico, possono riscontrare problemi con il layout del desktop e la gestione degli input di conseguenza.

**Perché si verifica questo problema**

Il supporto per le applicazioni Win32 classiche nella realtà mista di Windows è stato introdotto con l' [aggiornamento 2019 di Windows 10](/windows/mixed-reality/release-notes-may-2019). Per abilitare questo supporto, è necessario creare un monitor virtuale per ospitare l'applicazione Win32. Ogni volta che viene avviata una nuova applicazione Win32, è necessario creare un altro monitor virtuale. Sfortunatamente, la creazione di un monitoraggio virtuale è un'attività intensa che può causare un blocco breve della visualizzazione dell'auricolare. I clienti hanno offerto commenti e suggerimenti sull'esperienza di disagio e di disturbo. Grazie a questo feedback, oltre a un maggiore utilizzo delle applicazioni Win32, abbiamo deciso di pre-allocare tre monitoraggi virtuali durante l'avvio della realtà mista di Windows per evitare questa situazione di disturbo e consentire ai clienti di avviare fino a tre applicazioni Win32 simultanee senza dover visualizzare il blocco dello schermo dell'auricolare.

**Soluzione alternativa**

Abbiamo ricevuto il feedback che alcuni clienti, in particolare quelli con più monitoraggi fisici, preferiscono disabilitare questa pre-allocazione di monitoraggio virtuale. Per offrire ai clienti maggiore controllo, è stata abilitata una soluzione alternativa che comporta la modifica di un valore della chiave del registro di sistema, disponibile con gli aggiornamenti di Windows seguenti:

- 2020-07 Anteprima aggiornamento cumulativo per Windows 10 versione 2004 (KB4568831)
- 2020-10 Anteprima aggiornamento cumulativo per Windows 10 versione 1909 (KB4580386)
- 2020-10 Anteprima aggiornamento cumulativo per Windows 10 versione 1903 (KB4580386)

>[!NOTE]
>La modifica dei valori delle chiavi del registro di sistema è destinata agli utenti avanzati.

>[!WARNING]
>La disabilitazione della preallocazione di monitoraggio virtuale può comportare un blocco rapido della visualizzazione dell'auricolare quando si avvia un'applicazione Win32 (ad esempio, Steam, il nuovo Microsoft Edge o Google Chrome) in realtà mista di Windows.

Per disabilitare la preallocazione di monitoraggio virtuale:
1. Controllare **Windows Update** per una delle versioni di anteprima dell'aggiornamento cumulativo di Windows 10 elencate in precedenza e installare l'aggiornamento, se disponibile. È possibile trovare l'aggiornamento in **aggiornamenti facoltativi** o **Opzioni avanzate** nella pagina Impostazioni Windows Update
2. Avviare l' **Editor del registro di sistema**
3. Passa a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se il REG_DWORD "PreallocateVirtualMonitors" non è presente, crearlo selezionando **modifica > nuovo valore > DWORD (32 bit)** e immettendo PreallocateVirtualMonitors come nome.
5. Se è presente il REG_DWORD "PreallocateVirtualMonitors" (o è stato appena creato), fare doppio clic sulla voce e modificare "dati valore" da 1 (valore predefinito) a 0 (zero).
    * TRUE-1
    * FALSE-0

I monitoraggi virtuali verranno allocati quando si tenta di avviare un'applicazione Win32 in realtà mista di Windows anziché pre-allocare. Per reimpostare questa impostazione e riabilitare la preallocazione di monitoraggio virtuale, restituire il valore DWORD "valore dati" su 1.

### <a name="other-known-issues"></a>Altri problemi noti

-   I siti Web aperti in realtà mista di Windows andranno perduti quando si chiude il portale di realtà mista, anche se le finestre Microsoft Edge rimarranno nella posizione in cui sono state inserite nella Home realtà mista.
- Le esperienze di WebXR, tra cui l'estensione del Visualizzatore 360, potrebbero non essere avviate correttamente nei PC con una configurazione GPU ibrida. Per risolvere questo problema, è possibile abilitare una funzionalità di anteprima nel nuovo Microsoft Edge. Passare a `edge://flags` , cercare "multiGPU" e abilitare il flag denominato **WEBXR multiGPU support**.
-   L'audio da Microsoft Edge Windows non è spaziale.
-   **Correzione della versione dell'estensione del visualizzatore 360 2.3.8**: l'apertura di un video 360 da YouTube in realtà mista di Windows può comportare la distorsione del video nell'auricolare. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione del Visualizzatore 360 per risolvere il problema. Per verificare quale versione dell'estensione è possibile immettere `edge://system/` nella barra degli indirizzi e selezionare il pulsante **Espandi** accanto a "estensioni".