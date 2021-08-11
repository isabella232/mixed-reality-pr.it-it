---
title: Windows Mixed Reality e il nuovo Microsoft Edge
description: Informazioni sul nuovo Microsoft Edge per la realtà mista, inclusi cosa aspettarsi, gli aggiornamenti da cercare e i problemi noti.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: 51efc5c4d3afb4d46ba7722867514f740a9f60a4280652fdbd665134f83af23d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218823"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Il nuovo Microsoft Edge per Windows Mixed Reality

Il nuovo Microsoft Edge è ora disponibile per il [download,](https://blogs.windows.com/windowsexperience/?p=173496)ma i clienti possono anche attendere un aggiornamento futuro per installarlo con [Windows 10 , seguendo](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)un approccio di implementazione misurato nei prossimi mesi. 

Con questa novità, i clienti di visori VR Windows Mixed Reality sapere cosa aspettarsi dal nuovo Microsoft Edge e mostrare gli aggiornamenti in sospeso per un'esperienza di esplorazione migliorata **in** Windows Mixed Reality .

## <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge

Il nuovo Microsoft Edge adotta il progetto [Chromium open source sul](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) desktop per creare una migliore compatibilità per i clienti e una minore frammentazione del Web per gli sviluppatori Web. Supporterà anche WebXR al lancio, il nuovo standard per la creazione di esperienze Web immersive per visori VR, al posto di WebVR.

>[!IMPORTANT]
>Quando si installa Microsoft Edge in un dispositivo Windows 10 aggiornato, verrà sostituita la versione precedente (legacy) nel PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Prepararsi per il nuovo Microsoft Edge

Windows Mixed Reality I clienti con visore VR che vogliono usare il nuovo Microsoft Edge nel ambiente iniziale devono eseguire l'aggiornamento **a Windows 10 versione 1903** o successiva per il supporto nativo delle applicazioni Win32 (come il nuovo Microsoft Edge) nel ambiente iniziale. Controllare Windows update o [installare manualmente la versione più recente di Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Per la migliore esperienza Microsoft Edge possibile nel ambiente iniziale, è anche consigliabile attendere alcune ottimizzazioni di Windows Mixed Reality chiave per il nuovo Microsoft Edge in arrivo con l'aggiornamento cumulativo **2020-01 per Windows 10 versione 1903 (o successiva),** che dovrebbe essere disponibile in Windows Update entro la fine di gennaio.

>[!IMPORTANT]
>Se si sceglie di scaricare il nuovo Microsoft Edge prima di eseguire questi aggiornamenti, ci saranno alcuni problemi noti con il comportamento in Windows Mixed Reality (che è possibile leggere di seguito).

## <a name="known-issues"></a>Problemi noti

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva)

- L'avvio di qualsiasi app Win32, incluso il nuovo Microsoft Edge, causa il blocco breve dello schermo del visore.
- Il Microsoft Edge riquadro scompare dal Windows Mixed Reality menu Start (è possibile trovarlo nella cartella "App classiche").
- Windows precedenti Microsoft Edge vengono ancora posizionati intorno al ambiente iniziale, ma non possono essere usati. Il tentativo di attivare tali finestre avvia Edge nell'app Desktop.
- Se si seleziona un collegamento ipertestuale nel ambiente iniziale viene avviato un Web browser sul desktop anziché nel ambiente iniziale.
- L'app WebVR Showcase è presente nel ambiente iniziale, nonostante WebVR non sia più supportato.
- Miglioramenti generali all'avvio della tastiera e agli oggetti visivi.

### <a name="monitor-and-input-handling-issues"></a>Problemi di monitoraggio e gestione dell'input

Dopo aver preso l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva), i monitoraggi virtuali verranno visualizzati come monitor fisici generici in Impostazioni > **System > Display** durante le sessioni Windows Mixed Reality. Alcuni clienti, in particolare con più monitor fisici, potrebbero notare problemi con il layout del desktop e la gestione dell'input.

**Perché ciò accade**

Il supporto per le applicazioni Win32 classiche in Windows Mixed Reality è stato introdotto con Aggiornamento di Windows 10 (maggio 2019) [.](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019) Per abilitare questo supporto, è necessario creare un monitoraggio virtuale per ospitare l'applicazione Win32. Ogni volta che viene avviata una nuova applicazione Win32, è necessario creare un altro monitoraggio virtuale. Sfortunatamente, la creazione di un monitoraggio virtuale è un'attività intensiva che può causare il blocco breve dello schermo del visore. I clienti hanno offerto feedback che si tratta di un'esperienza disaffezionata e dirompente. Grazie al feedback e all'aumento dell'utilizzo delle applicazioni Win32, è stata presa la decisione di preallocare tre monitor virtuali durante l'avvio Windows Mixed Reality. In questo modo si evitano interruzioni e i clienti possono avviare fino a tre applicazioni Win32 simultanee senza che si verifichi il blocco dello schermo del visore.

**Soluzione alternativa**

Da allora è stato ricevuto un feedback che alcuni clienti, in particolare quelli con più monitor fisici, preferiscono disabilitare la preallocazione del monitoraggio virtuale. Per concedere ai clienti il controllo, è stata abilitata una soluzione alternativa che prevede la modifica di un valore di chiave del Registro di sistema, disponibile con gli aggiornamenti Windows seguenti:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 version 1903 (KB4580386)

>[!NOTE]
>La modifica dei valori delle chiavi del Registro di sistema è destinata agli utenti esperti.

>[!WARNING]
>La disabilitazione della preallocazione del monitor virtuale può causare un breve blocco dello schermo del visore quando si avvia un'applicazione Win32 (ad esempio, Steam, il nuovo Microsoft Edge o Google Chrome) in Windows Mixed Reality.

Per disabilitare la preallocazione del monitoraggio virtuale:
1. Controllare **Windows update** per una delle versioni Windows 10 di anteprima dell'aggiornamento cumulativo elencate in precedenza e installare l'aggiornamento quando disponibile. È possibile trovare l'aggiornamento in **Aggiornamenti facoltativi** o **Opzioni avanzate** nella pagina Windows impostazioni di aggiornamento
2. Avviare **l'editor del Registro di sistema**
3. Passare a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se il REG_DWORD "PreallocateVirtualMonitors" non è presente, crearlo selezionando Modifica **> Nuovo valore DWORD > (32 bit)** e immettendo PreallocateVirtualMonitors come nome
5. Se il REG_DWORD "PreallocateVirtualMonitors" è presente (o è appena stato creato), fare doppio clic sulla voce e modificare "Dati valore" da 1 (valore predefinito) a 0 (zero)
    * TRUE - 1
    * FALSE - 0

I monitoraggi virtuali verranno ora allocati quando si tenta di avviare un'applicazione Win32 Windows Mixed Reality anziché preallocazione. Per reimpostare questa impostazione e abilitare nuovamente la preallocazione del monitoraggio virtuale, restituire il valore DWORD "Dati valore" su 1.

### <a name="other-known-issues"></a>Altri problemi noti

-   I siti Web aperti in Windows Mixed Reality andranno persi quando Portale realtà mista si chiude. Le Microsoft Edge finestre rimarranno nelle posizioni posizionate nell'ambiente iniziale.
- Le esperienze WebXR, inclusa l'estensione 360 Viewer, potrebbero non essere avviate correttamente nei PC con una configurazione ibrida della GPU. È possibile risolvere questo problema abilitando una funzionalità di anteprima nel nuovo Microsoft Edge. Passare a `edge://flags` , cercare "multi gpu" e abilitare il flag **denominato WebXR Multi GPU Support**.
-   L'audio Microsoft Edge finestre non è spazializzato.
-   Correzione nell'estensione **360 Viewer versione 2.3.8:** l'apertura di un video a 360 da YouTube in Windows Mixed Reality può causare la distorsione del video nel visore. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione 360 Viewer per risolvere il problema. È possibile verificare la versione dell'estensione disponibile immettendo nella barra degli indirizzi e selezionando il pulsante Espandi `edge://system/` accanto a  "estensioni".