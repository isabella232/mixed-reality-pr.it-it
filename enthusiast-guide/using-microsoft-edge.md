---
title: Uso Microsoft Edge in Windows Mixed Reality
description: Prepararsi per il nuovo Microsoft Edge in Windows Mixed Reality. Include le modifiche previste, gli aggiornamenti da cercare e i problemi noti.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Home, Navigate, Get around, apps, games, Microsoft Edge, chromium, Edge, 360, 360 video, 360 viewer
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436699"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality e il nuovo Microsoft Edge

Il [nuovo Microsoft Edge](https://www.microsoft.com/edge) è disponibile per il download e ha iniziato automaticamente l'implementazione ai clienti tramite Windows Update. 

Il nuovo Microsoft Edge [adotta il Chromium open source sul](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) desktop. Ciò consente una migliore compatibilità per i clienti e una minore frammentazione per gli sviluppatori Web. Supporterà anche WebXR al lancio, che è il nuovo standard per la creazione di esperienze Web immersive per visori VR, al posto di WebVR.

>[!IMPORTANT]
>Quando installi Microsoft Edge in un dispositivo Windows 10 o Windows 11 aggiornato, sostituirà la versione precedente (legacy) nel PC.

## <a name="installing-the-new-microsoft-edge"></a>Installazione del nuovo Microsoft Edge 

Prima di installare il nuovo Microsoft Edge, eseguire l'aggiornamento **a Windows 10 versione 1903** o successiva o Windows 11 per il supporto nativo delle applicazioni Win32, come il nuovo Microsoft Edge in Windows Mixed Reality. Controllare Windows o [installare manualmente la versione più recente](https://www.microsoft.com/software-download/windows10) di Windows 10 o Windows 11.

Dopo aver creato Windows 10 versione 1903 o successiva o Windows 11, si è pronti per il nuovo Microsoft Edge. La nuova Microsoft Edge viene implementazione tramite Windows Update, ma è possibile installare manualmente il nuovo Microsoft Edge dal sito Web [di Microsoft Edge,](https://www.microsoft.com/edge) se lo si desidera prima.

>[!IMPORTANT]
>Il nuovo Microsoft Edge viene avviato con il supporto per WebXR, il nuovo standard per la creazione di esperienze Web immersive per visori VR. Quando si installa il nuovo Microsoft Edge, non sarà più possibile riprodurre esperienze WebVR in Microsoft Edge. 

## <a name="known-issues"></a>Problemi noti

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva)

- L'avvio di qualsiasi app Win32, inclusa la nuova Microsoft Edge, causa il breve blocco della visualizzazione del visore VR.
- Il Microsoft Edge viene rimosso dal Windows Mixed Reality menu Start (è possibile trovarlo nella cartella "App classiche").
- Windows delle versioni precedenti Microsoft Edge vengono ancora posizionati intorno al ambiente iniziale, ma non possono essere usati. Il tentativo di attivare tali finestre avvia Edge nell'app desktop.
- Se si seleziona un collegamento ipertestuale ambiente iniziale viene avviato un Web browser sul desktop anziché il ambiente iniziale.
- L'app WebVR Showcase è presente nel ambiente iniziale, nonostante WebVR non sia più supportato.
- Miglioramenti generali all'avvio della tastiera e agli oggetti visivi.

### <a name="monitor-and-input-handling-issues"></a>Problemi di monitoraggio e gestione dell'input

Dopo l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 o successiva, i monitor virtuali verranno visualizzati come monitor fisici generici in Impostazioni > **System > Display** durante le sessioni Windows Mixed Reality. Di conseguenza, alcuni clienti, in particolare quelli con più monitor fisici, potrebbero notare problemi con il layout del desktop e la gestione dell'input.

**Perché ciò si verifica**

Il supporto per le applicazioni Win32 classiche in Windows Mixed Reality è stato introdotto con [Aggiornamento di Windows 10 (maggio 2019)](/windows/mixed-reality/release-notes-may-2019). Per abilitare questo supporto, è necessario creare un monitor virtuale per ospitare l'applicazione Win32. Ogni volta che viene avviata una nuova applicazione Win32, è necessario creare un altro monitor virtuale. Sfortunatamente, la creazione di un monitor virtuale è un'attività intensiva che può causare il breve blocco dello schermo del visore VR. I clienti hanno offerto commenti e suggerimenti in cui si è detto che l'esperienza è stata disaffezionata e disagi. Grazie a questi commenti e suggerimenti, oltre all'aumento dell'utilizzo delle applicazioni Win32, abbiamo deciso di preallocare tre monitor virtuali durante l'avvio di Windows Mixed Reality per evitare questa interruzione e consentire ai clienti di avviare fino a tre applicazioni Win32 simultanee senza riscontrare il blocco del display del visore VR.

**Soluzione alternativa**

Da allora abbiamo ricevuto commenti e suggerimenti che alcuni clienti, in particolare quelli con più monitor fisici, preferirebbero disabilitare la preallocazione di questo monitor virtuale. Per offrire ai clienti maggiore controllo, è stata abilitata una soluzione alternativa che prevede la modifica di un valore della chiave del Registro di sistema, disponibile con gli aggiornamenti Windows seguenti:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 version 1903 (KB4580386)

>[!NOTE]
>La modifica dei valori delle chiavi del Registro di sistema è destinata agli utenti avanzati.

>[!WARNING]
>La disabilitazione della preallocazione del monitor virtuale può causare un breve blocco della visualizzazione del visore VR quando si avvia un'applicazione Win32 (ad esempio, Steam, il nuovo Microsoft Edge o Google Chrome) in Windows Mixed Reality.

Per disabilitare la preallocazione del monitoraggio virtuale:
1. Controllare **Windows update per** una delle versioni Windows 10'anteprima dell'aggiornamento cumulativo elencate in precedenza e installare l'aggiornamento quando disponibile. È possibile trovare l'aggiornamento in **Optional updates (Aggiornamenti facoltativi)** o Advanced options (Opzioni **avanzate)** nella pagina Windows Update settings (Impostazioni di aggiornamento)
2. Avviare **l'editor del Registro di sistema**
3. Passare a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se il REG_DWORD "PreallocateVirtualMonitors" non è presente, crearlo selezionando Modifica > Nuovo **valore DWORD > (32 bit)** e immettendo PreallocateVirtualMonitors come nome
5. Se il REG_DWORD "PreallocateVirtualMonitors" è presente (o è appena stato creato), fare doppio clic sulla voce e modificare "Dati valore" da 1 (valore predefinito) a 0 (zero)
    * TRUE - 1
    * FALSE - 0

I monitoraggi virtuali verranno ora allocati quando si tenta di avviare un'applicazione Win32 in Windows Mixed Reality anziché preallocazione. Per reimpostare questa impostazione e abilitare nuovamente la preallocazione del monitor virtuale, restituire il valore DWORD "Dati valore" su 1.

### <a name="other-known-issues"></a>Altri problemi noti

-   I siti Web aperti in Windows Mixed Reality andranno persi alla chiusura Portale realtà mista, anche se le finestre Microsoft Edge rimarranno nella posizione in cui si trovavano nella ambiente iniziale.
- Le esperienze WebXR, inclusa l'estensione 360 Viewer, potrebbero non essere avviate correttamente nei PC con una configurazione gpu ibrida. È possibile risolvere questo problema abilitando una funzionalità di anteprima nel nuovo Microsoft Edge. Passare a `edge://flags` , cercare "multi gpu" e abilitare il flag denominato **WebXR Multi GPU Support (Supporto GPU multi WebXR).**
-   L'audio Microsoft Edge finestre non è spazializzato.
-   Problema risolto nella **versione 2.3.8 dell'estensione 360 Viewer:** l'apertura di un video 360 da YouTube in Windows Mixed Reality può causare la distorsione del video nel visore VR. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione 360 Viewer per risolvere questo problema. È possibile verificare la versione dell'estensione disponibile immettendo nella barra degli indirizzi e selezionando il pulsante Espandi `edge://system/` accanto a  "estensioni".