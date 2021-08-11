---
title: Note sulla versione - agosto 2016
description: Rimanere aggiornati sulle note sulla versione HoloLens per la versione Windows 10 anniversary per l'autunno 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, note sulla versione, sistema operativo, piattaforma, funzionalità, suite commerciale
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202463"
---
# <a name="release-notes---august-2016"></a>Note sulla versione - agosto 2016

Il HoloLens team sta ascoltando i commenti e suggerimenti degli sviluppatori Windows Programma Insider per classificare in ordine di priorità il lavoro. Continuare a [inviare commenti e](/windows/mixed-reality/give-us-feedback) suggerimenti tramite Hub di Feedback, [i forum per sviluppatori](https://forums.hololens.com) e Twitter [tramite @HoloLens ](https://twitter.com/hololens). Quando Windows 10'aggiornamento dell'anniversario, il team HoloLens è contento di offrire un miglioramento ulteriore all'esperienza olografica. In questo aggiornamento sono stati incentrati sulle principali correzioni, miglioramenti e sull'introduzione delle funzionalità richieste dalle aziende e disponibili nel Microsoft HoloLens Commercial Suite.

**Versione più recente:** Windows aggiornamento di holographic di agosto 2016 (**10.0.14393.0**, Windows 10 anniversary release)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Per [eseguire l'aggiornamento](/windows/mixed-reality/updating-hololens)alla versione corrente, aprire l'app  Impostazioni, passare a Update & Security (Aggiorna & *Security)* e quindi selezionare il pulsante Check for updates (Controlla *aggiornamenti).*

## <a name="new-features"></a>Nuove funzionalità

**Collega a processo debug** HoloLens ora supporta il debug di collegamento a processo. È possibile usare Visual Studio 2015 Update 3 per connettersi a un'app in esecuzione in un HoloLens e avviare [il debug.](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app) Questa operazione funziona senza la necessità di eseguire la distribuzione da un Visual Studio progetto.

**Aggiornamento HoloLens Emulator** È stata rilasciata anche una versione aggiornata del HoloLens Emulator.

**Supporto di Gamepad** È ora possibile associare e usare Bluetooth gamepad con HoloLens! Le nuove funzionalità di Xbox Wireless Controller S Bluetooth funzionalità e possono essere usate per riprodurre i giochi e le app abilitati per gamepad preferiti. È [necessario applicare un](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) aggiornamento del controller prima di poter connettere xbox Wireless Controller S con HoloLens. Il controller wireless Xbox S è supportato [da XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) [e Windows. API Gaming.Input.](/uwp/api/Windows.Gaming.Input) È possibile accedere a più Bluetooth modelli di controller tramite il [Windows. API Gaming.Input.](/uwp/api/Windows.Gaming.Input)

## <a name="improvements-and-fixes"></a>Miglioramenti e correzioni

Microsoft è sincronizzata con il resto dell'aggiornamento dell'anniversario di Windows 10, quindi, oltre alle correzioni specifiche di HoloLens, si riceve anche tutto il bene dell'aggiornamento Windows per aumentare l'affidabilità e le prestazioni della piattaforma. I commenti e suggerimenti sono altamente apprezzati e classificati in ordine di priorità per le correzioni nella versione.

Sono state migliorate le esperienze seguenti:
* accedere alle esperienze.
* aggiunta di ambienti di lavoro.
* efficienza dell'alimentazione per le transizioni dello stato di alimentazione del dispositivo.
* stabilità con le acquisizioni di realtà mista.
* affidabilità per Bluetooth connettività
* persistenza di ologrammi in uno scenario multi-app.

Sono stati risolti i problemi seguenti:
* I Visual Studio profiler e il debugger di grafica non riescono a connettersi.
* le & documenti non vengono mostrate in Esplora file nel portale per dispositivi.
* La barra dell'app può lampeggiare quando il cursore viene posizionato sopra di essa in modalità Regolazione.
* Quando è attiva la modalità Regola, il cursore punto sguardo fisso cambierà in cursore a 4 frecce a volte più lentamente.
* "Hey Cortana play music" non viene avviato Groove.
* dopo l'aggiornamento precedente, l'opzione "Vai a casa" non visualizza correttamente il pannello dei segnaposto.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introduzione a Microsoft HoloLens Commercial Suite

Il Microsoft HoloLens Commercial Suite è pronto per la distribuzione aziendale. Sono state aggiunte diverse funzionalità commerciali molto [richieste](/windows/mixed-reality/commercial-features) dai primi partner commerciali.

Contattare il responsabile account Microsoft locale per acquistare il Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Funzionalità commerciali principali 

* **Modalità tutto schermo.** Con HoloLens modalità tutto schermo, è possibile limitare le app da eseguire per abilitare la demo o presentare esperienze.<br>
  ![Con la modalità tutto schermo, HoloLens viene avviato direttamente nell'app di propria scelta.](images/201608-kioskmode-400px.png)
* **Gestione dei dispositivi mobili (MDM) per HoloLens.** Il reparto IT può gestire più dispositivi HoloLens contemporaneamente usando soluzioni come Microsoft Intune. È possibile gestire le impostazioni, selezionare le app da installare e impostare configurazioni di sicurezza personalizzate in base alle esigenze dell'organizzazione.<br>
  ![Gestione dei dispositivi mobili in HoloLens la gestione dei dispositivi di livello aziendale tra più dispositivi.](images/201608-enterprisemanagement-400px.png)
* **Windows Aggiornamento per le aziende.** Aggiornamenti del sistema operativo controllati ai dispositivi e supporto per il ramo di manutenzione a lungo termine.
* **Sicurezza dei dati.** La crittografia dei dati di BitLocker è abilitata HoloLens per fornire lo stesso livello di protezione di sicurezza di qualsiasi altro Windows dispositivo.
* **Accesso al lavoro.** Tutti gli utenti dell'organizzazione possono connettersi in remoto alla rete aziendale tramite una rete privata virtuale in un HoloLens. HoloLens accedere anche alle Wi-Fi che richiedono credenziali.
* **Microsoft Store per le aziende.** Il reparto IT può anche configurare un archivio privato aziendale, contenente solo le app aziendali per l'utilizzo HoloLens specifico. Distribuire in modo sicuro il software aziendale a un gruppo selezionato di utenti aziendali.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition e Commercial Suite

<table>
<tr>
<th>Funzionalità</th><th>Development Edition</th><th>Suite commerciale</th>
</tr><tr>
<td>Crittografia dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rete privata virtuale (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Modalità tutto schermo</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gestione e distribuzione</th>
</tr><tr>
<td>Gestione di dispositivi mobili</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Possibilità di bloccare l'annullamento della registrazione</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Cert Based Corporate Wi-Fi Access</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumer)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Applicazione di filtri tramite MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Portale di Business Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicurezza e Identity</th>
</tr><tr>
<td>Accedere con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Accedere con l'account Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenziali di nuova generazione con sblocco PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Avvio sicuro</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Manutenzione e supporto</th>
</tr><tr>
<td>Aggiornamenti automatici del sistema all'arrivo</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedi anche
* [Problemi noti di HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Funzionalità commerciali](/windows/mixed-reality/commercial-features)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Uso dell'emulatore HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)