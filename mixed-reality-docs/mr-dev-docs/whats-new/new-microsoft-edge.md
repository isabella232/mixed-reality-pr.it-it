---
title: Windows Mixed Reality e il nuovo Microsoft Edge
description: Informazioni sul nuovo Microsoft Edge realtà mista, tra cui cosa aspettarsi, aggiornamenti da cercare e problemi noti.
author: mattzmsft
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: ca849f63d2a755639bedba68c47e419528006a6d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148653"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Il nuovo Microsoft Edge per Windows Mixed Reality

Il nuovo Microsoft Edge è ora disponibile per il [download,](https://blogs.windows.com/windowsexperience/?p=173496)ma i clienti possono anche attendere un aggiornamento futuro per installarlo [con Windows 10, seguendo](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)un approccio di implementazione misurato nei prossimi mesi. 

Con queste novità, i clienti dei visori VR di Windows Mixed Reality sanno cosa aspettarsi dal nuovo Microsoft Edge e mostrano gli aggiornamenti in sospeso per un'esperienza di esplorazione migliorata **in Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge

Il nuovo Microsoft Edge [adotta](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) il progetto Chromium open source sul desktop per creare una migliore compatibilità per i clienti e una minore frammentazione del Web per gli sviluppatori Web. Supporterà anche WebXR al lancio, il nuovo standard per la creazione di esperienze Web immersive per visori VR, al posto di WebVR.

>[!IMPORTANT]
>Quando installi Microsoft Edge in un dispositivo Windows 10 aggiornato, sostituirà la versione precedente (legacy) nel PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Prepararsi per il nuovo Microsoft Edge

Windows Mixed Reality I clienti di visori VR che vogliono usare il nuovo Microsoft Edge nel ambiente iniziale devono eseguire l'aggiornamento **a Windows 10 versione 1903** o successiva per il supporto nativo delle applicazioni Win32 (come la nuova Microsoft Edge) nel ambiente iniziale. Controllare Windows o installare [manualmente la versione più recente di Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Per un'esperienza di Microsoft Edge ottimale nel ambiente iniziale, è anche consigliabile attendere alcune ottimizzazioni del Windows Mixed Reality chiave per il nuovo Microsoft Edge in arrivo con l'aggiornamento cumulativo **2020-01 per Windows 10 versione 1903 (o successiva),** che dovrebbe essere disponibile nell'aggiornamento di Windows entro la fine di gennaio.

>[!IMPORTANT]
>Se si sceglie di scaricare il nuovo Microsoft Edge prima di eseguire questi aggiornamenti, si verificano alcuni problemi noti con il relativo comportamento in Windows Mixed Reality (che è possibile leggere di seguito).

## <a name="known-issues"></a>Problemi noti

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva)

- L'avvio di qualsiasi app Win32, inclusa la nuova Microsoft Edge, causa il breve blocco della visualizzazione del visore VR.
- Il Microsoft Edge viene rimosso dal Windows Mixed Reality menu Start (è possibile trovarlo nella cartella "App classiche").
- Windows precedenti Microsoft Edge vengono ancora posizionati intorno al ambiente iniziale, ma non possono essere usati. Il tentativo di attivare tali finestre avvia Edge nell'app desktop.
- Se si seleziona un collegamento ipertestuale ambiente iniziale viene avviato un Web browser sul desktop anziché il ambiente iniziale.
- L'app WebVR Showcase è presente nel ambiente iniziale, nonostante WebVR non sia più supportato.
- Miglioramenti generali all'avvio della tastiera e agli oggetti visivi.

### <a name="monitor-and-input-handling-issues"></a>Problemi di monitoraggio e gestione dell'input

Dopo l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva), i monitor virtuali verranno visualizzati come monitor fisici generici in Impostazioni > **System > Display** durante le sessioni Windows Mixed Reality. Alcuni clienti, in particolare con più monitor fisici, potrebbero notare problemi con il layout del desktop e la gestione dell'input di conseguenza.

**Perché ciò si verifica**

Il supporto per le applicazioni Win32 classiche in Windows Mixed Reality è stato introdotto con [Aggiornamento di Windows 10 (maggio 2019)](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Per abilitare questo supporto, è necessario creare un monitor virtuale per ospitare l'applicazione Win32. Ogni volta che viene avviata una nuova applicazione Win32, è necessario creare un altro monitor virtuale. Sfortunatamente, la creazione di un monitor virtuale è un'attività intensiva che può causare il breve blocco dello schermo del visore VR. I clienti hanno offerto commenti e suggerimenti che si tratta di un'esperienza disaffezionata e dirompente. A causa del feedback e dell'aumento dell'utilizzo delle applicazioni Win32, è stato deciso di preallocare tre monitor virtuali durante l'avvio Windows Mixed Reality. Ciò impedisce l'interruzione e consente ai clienti di avviare fino a tre applicazioni Win32 simultanee senza riscontrare il blocco dello schermo del visore VR.

**Soluzione alternativa**

Da allora abbiamo ricevuto commenti e suggerimenti che alcuni clienti, in particolare quelli con più monitor fisici, preferirebbero disabilitare la preallocazione di questo monitor virtuale. Per concedere ai clienti il controllo, è stata abilitata una soluzione alternativa che prevede la modifica di un valore della chiave del Registro di sistema, disponibile con gli aggiornamenti Windows seguenti:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>La modifica dei valori delle chiavi del Registro di sistema è destinata agli utenti avanzati.

>[!WARNING]
>La disabilitazione della preallocazione del monitor virtuale può causare un breve blocco della visualizzazione del visore VR all'avvio di un'applicazione Win32,ad esempio a Google Chrome o Microsoft Edge a Google Chrome, in Windows Mixed Reality.

Per disabilitare la preallocazione del monitoraggio virtuale:
1. Controllare **Windows update per** una delle versioni Windows 10'anteprima degli aggiornamenti cumulativi elencate in precedenza e installare l'aggiornamento quando disponibile. È possibile trovare l'aggiornamento in **Optional updates (Aggiornamenti facoltativi)** o Advanced options (Opzioni **avanzate)** nella pagina Windows Update settings (Impostazioni di aggiornamento)
2. Avviare **l'editor del Registro di sistema**
3. Passare a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Se il REG_DWORD "PreallocateVirtualMonitors" non è presente, crearlo selezionando Modifica > Nuovo **valore DWORD > (32 bit)** e immettendo PreallocateVirtualMonitors come nome
5. Se il REG_DWORD "PreallocateVirtualMonitors" è presente (o è appena stato creato), fare doppio clic sulla voce e modificare "Dati valore" da 1 (valore predefinito) a 0 (zero)
    * TRUE - 1
    * FALSE - 0

I monitoraggi virtuali verranno ora allocati quando si tenta di avviare un'applicazione Win32 in Windows Mixed Reality anziché preallocazione. Per reimpostare questa impostazione e abilitare nuovamente la preallocazione del monitor virtuale, restituire il valore DWORD "Dati valore" su 1.

### <a name="other-known-issues"></a>Altri problemi noti

-   L'audio Microsoft Edge finestre non è spazializzato.

## <a name="see-also"></a>Vedere anche

* [Panoramica di WebXR](../develop/javascript/webxr-overview.md)