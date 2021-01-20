---
title: Note sulla versione - agosto 2016
description: È possibile rimanere sempre aggiornati sulle note sulla versione di HoloLens per la versione di anniversario di Windows 10 per la versione 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, note sulla versione, sistema operativo, piattaforma, funzionalità, suite commerciale
ms.openlocfilehash: c70da10043cfbcfa88105635f2467c8feaadbedf
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581647"
---
# <a name="release-notes---august-2016"></a>Note sulla versione - agosto 2016

Il team di HoloLens è in attesa di commenti e suggerimenti da parte degli sviluppatori del programma Windows Insider per definire le priorità del lavoro. Continua a [inviare commenti e suggerimenti](/windows/mixed-reality/give-us-feedback) tramite l'hub di feedback, i [forum per sviluppatori](https://forums.hololens.com) e il [ @HoloLens Twitter tramite ](https://twitter.com/hololens). Poiché Windows 10 abbraccia l'aggiornamento dell'anniversario, il team di HoloLens è lieto di offrire un ulteriore miglioramento dell'esperienza olografica. In questo aggiornamento abbiamo dedicato alle principali correzioni, miglioramenti e introduzione alle funzionalità richieste dalle aziende e disponibili in Microsoft HoloLens Commercial Suite.

**Ultima versione:** Aggiornamento di Windows olografico 2016 (**10.0.14393.0**, versione anniversario di Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Per eseguire l' [aggiornamento alla versione corrente](/windows/mixed-reality/updating-hololens), aprire l'app *Impostazioni* , passare a *Aggiorna & sicurezza*, quindi selezionare il pulsante *Controlla aggiornamenti* .

## <a name="new-features"></a>Nuove funzionalità

**Connetti a processo di debug** HoloLens supporta ora il debug da Connetti a processo. È possibile usare Visual Studio 2015 Update 3 per connettersi a un'app in esecuzione in un HoloLens e [avviarne il debug](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app). Questa operazione funziona senza la necessità di eseguire la distribuzione da un progetto di Visual Studio.

**Aggiornamento dell'emulatore di HoloLens** È stata rilasciata anche una versione aggiornata dell'emulatore di HoloLens.

**Supporto di gamepad** È ora possibile associare e usare gamepad Bluetooth con HoloLens. Le funzionalità Bluetooth del controller wireless appena rilasciate e possono essere usate per riprodurre app e giochi abilitati per gamepad preferiti. Prima di poter connettere il controller senza fili Xbox a HoloLens, è necessario applicare un [aggiornamento del controller](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) . Il controller wireless Xbox S è supportato dalle API [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) e [Windows. Gaming. input](/uwp/api/Windows.Gaming.Input) . È possibile accedere a più modelli di controller Bluetooth tramite l'API [Windows. Gaming. input](/uwp/api/Windows.Gaming.Input) .

## <a name="improvements-and-fixes"></a>Miglioramenti e correzioni

Ci siamo sincronizzati con il resto dell'aggiornamento dell'anniversario di Windows 10, quindi, oltre alle correzioni specifiche di HoloLens, stai ricevendo tutti i vantaggi di Windows Update per aumentare l'affidabilità e le prestazioni della piattaforma. I commenti e i suggerimenti sono altamente valutati e classificati in ordine di priorità per le correzioni della versione.

Sono state migliorate le esperienze seguenti:
* Accedi all'esperienza.
* aggiunta all'area di lavoro.
* efficienza energetica per le transizioni di stato dell'alimentazione del dispositivo.
* stabilità con acquisizioni di realtà miste.
* affidabilità per la connettività Bluetooth
* persistenza ologramma nello scenario con più app.

Sono stati corretti i problemi seguenti:
* non è possibile connettere i profiler e il debugger della grafica di Visual Studio.
* le foto & documenti non vengono visualizzati in Esplora file nel portale del dispositivo.
* la barra dell'app può lampeggiare quando il cursore viene posizionato sopra di esso in modalità di regolazione.
* Quando si usa la modalità di regolazione, il cursore a forma di occhio si passa al cursore a 4 frecce in un momento più lento.
* "Hey Cortana Play Music" non avvia Groove.
* dopo l'aggiornamento precedente, se si dice "Vai a casa", il pannello pin non viene visualizzato correttamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introduzione a Microsoft HoloLens Commercial Suite

Microsoft HoloLens Commercial Suite è pronto per la distribuzione aziendale. Sono state aggiunte diverse [funzionalità commerciali](/windows/mixed-reality/commercial-features) altamente richieste dai partner commerciali iniziali.

Contattare il gestore di account Microsoft locale per acquistare Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Caratteristiche commerciali principali 

* **Modalità tutto schermo.** Con la modalità tutto schermo HoloLens, è possibile limitare le app da eseguire per abilitare le esperienze demo o Showcase.<br>
  ![Con la modalità tutto schermo, HoloLens viene avviato direttamente nell'app che preferisci.](images/201608-kioskmode-400px.png)
* **Gestione di dispositivi mobili (MDM) per HoloLens.** Il reparto IT può gestire più dispositivi HoloLens contemporaneamente usando soluzioni come Microsoft Intune. È possibile gestire le impostazioni, selezionare le app per installare e impostare le configurazioni di sicurezza adattate alle esigenze dell'organizzazione.<br>
  ![La gestione dei dispositivi mobili in HoloLens offre la gestione dei dispositivi di livello aziendale tra più dispositivi.](images/201608-enterprisemanagement-400px.png)
* **Windows Update per le aziende.** Aggiornamenti del sistema operativo controllati ai dispositivi e supporto per Long-Term Servicing Branch.
* **Sicurezza dei dati.** La crittografia dei dati BitLocker è abilitata in HoloLens per fornire lo stesso livello di protezione di qualsiasi altro dispositivo Windows.
* **Accesso al lavoro.** Tutti gli utenti dell'organizzazione possono connettersi in remoto alla rete aziendale tramite la rete privata virtuale in una HoloLens. HoloLens può accedere anche alle reti Wi-Fi che richiedono le credenziali.
* **Microsoft Store per le aziende.** Il reparto IT può anche configurare un archivio privato aziendale, contenente solo le app aziendali per l'utilizzo specifico di HoloLens. Distribuisci in modo sicuro il software aziendale a un gruppo selezionato di utenti aziendali.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition rispetto alla suite commerciale

<table>
<tr>
<th>Funzionalità</th><th>Development Edition</th><th>Suite commerciale</th>
</tr><tr>
<td>Crittografia del dispositivo (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
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
<td>Accesso Wi-Fi aziendale basato su certificati</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumer)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Filtraggio tramite MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Portale di business Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicurezza e Identity</th>
</tr><tr>
<td>Accedi con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Accedi con l'account Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenziali di nuova generazione con sblocco PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Avvio protetto</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Assistenza e supporto</th>
</tr><tr>
<td>Aggiornamenti automatici del sistema man mano che arrivano</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Problemi noti di HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Funzionalità commerciali](/windows/mixed-reality/commercial-features)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Uso dell'emulatore HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)