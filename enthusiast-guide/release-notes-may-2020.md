---
title: Note sulla versione - Maggio 2020
description: Rimanere aggiornati sulle note sulla versione Windows Mixed Reality per l'aggiornamento Windows 10 maggio 2020.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: note sulla versione, versione, Windows 10, build, 19h1, sistema operativo, maggio 2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439171"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 note sulla versione - Maggio 2020

L'aggiornamento Windows 10 maggio **2020 (v2004)** include nuove funzionalità per i visori VR (Windows Mixed Reality), ad esempio la possibilità di avviare applicazioni Win32 nel ambiente iniziale. HoloLens (prima generazione) si trova in Long Term Servicing (LTS), con aggiornamenti di manutenzione che verranno rilasciati ogni mese.

Eseguire l'aggiornamento alla versione più recente del PC Windows Mixed Reality visori VR immersive, aprire Impostazioni > **Update & Security** (Verifica la disponibilità di **aggiornamenti).** In un PC Windows 10, è anche possibile installare manualmente l'aggiornamento Windows 10 maggio **2020** usando lo strumento Windows [di creazione di supporti.](https://www.microsoft.com/software-download/windows10)

**Versione più recente per desktop:** Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Aggiornamenti per i visori VR immersive Windows Mixed Reality

### <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge

Come [annunciato in](/windows/mixed-reality/new-microsoft-edge)precedenza, sono stati apportati aggiornamenti per supportare meglio l'uso del nuovo browser Microsoft Edge in Windows Mixed Reality. Il nuovo Microsoft Edge adotta il Chromium open source per creare una migliore compatibilità Web per i clienti e una minore frammentazione del Web per tutti gli sviluppatori Web. Supporta anche WebXR, il nuovo standard per la creazione di esperienze Web immersive per visori VR, al posto di WebVR.

### <a name="improved-settings-for-wmr"></a>Miglioramento Impostazioni per WMR

Grazie al feedback degli utenti, sono state aggiunte e chiarite le impostazioni nella pagina di visualizzazione del visore VR:

* **Qualità visiva della casa: la** modifica di queste impostazioni influisce solo sull'ambiente ambiente iniziale (Casa sulla scogliera e Skyloft):

* **Regolare il livello di dettaglio e la qualità** degli effetti nel ambiente iniziale: questa modifica modifica parte del rendering influisce sull'uso nella home page. In particolare, la qualità visiva dei diversi materiali ( wood, concrete e così via) verrà ridimensionata quando si modifica questa impostazione da bassa a alta.

* **Modificare la risoluzione della finestra dell'app:** per impostazione predefinita, la maggior parte delle finestre 2D avviate nella home page viene avviata con una risoluzione di 720 p. Anche se è possibile ridimensionarli manualmente & verticalmente, è anche possibile scegliere di avviarli tutti a 1080p. In precedenza questa opzione era disponibile come opzione Molto alta (beta) in Qualità visiva. Ora è stata suddivisa in modo appropriato come impostazione separata.

* **Opzioni di esperienza:** queste opzioni regolano l'esperienza di realtà mista per ridurre il carico sui sistemi in cui l'hardware potrebbe avere difficoltà a restare al passo con un valore illimitato di 90 fps. È possibile abilitare o disabilitare in modo esplicito queste impostazioni aggiuntive oppure scegliere Consenti Windows di decidere e lasciare che l'euristica continui a decidere quando attivare e disattivare queste impostazioni.

* **Risoluzione:** se si dispone di un visore VR ad alta risoluzione come HP Reverb, è possibile eseguire il dispositivo alla risoluzione nativa o a una risoluzione ridotta per motivi di prestazioni. I visori VR precedenti, ad esempio Samsung Odyssey e Odyssey+, supportano solo una singola risoluzione, quindi non è possibile modificare questa impostazione su tali visori VR.

* **Frequenza** dei fotogrammi: è ora possibile impostare manualmente la frequenza dei fotogrammi del visore VR o continuare Windows usare l'euristica per determinare se 60 Hz o 90 Hz sono più appropriati.

* **Calibrazione:** come in precedenza, è possibile regolare l'IPD (distanza interpupcinaria) se supportato dal visore VR.

* **Cambio di input:** attiva/disattiva il comportamento di cambio dello stato attivo di input (Win+Y) in modo che sia automatico (in base al feedback del sensore di presenza) o manuale.

### <a name="new-cortana-app"></a>Nuova app Cortana

Questo aggiornamento a Windows include la versione più recente dell'app Cortana, attualmente solo per l'inglese (Stati Uniti) e non supporta più alcuni comandi specifici della realtà mista, ad esempio "Take a picture" (Scattare una foto) e "Take a video". È possibile usare il nuovo Cortana per avviare le app e supporta anche nuovi comandi incentrati sulla produttività, ad esempio "When's next meeting?" o "Send an email to \< name \> that I'm running late".
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Aggiornamenti aggiuntivi in disponibili nella versione 19041.546 (data di rilascio ottobre 2020)

Questo aggiornamento di manutenzione mensile desktop include le modifiche seguenti per Windows Mixed Reality dispositivi: 
* Riduce le distorsioni e le aberrazioni Windows Mixed Reality schermi montati con la testa (HMD). 
* Aggiunge il supporto per i controller del movimento Windows Mixed Reality HP. 
* Modifica il comportamento dell'impostazione della frequenza di aggiornamento a 90 Hz in Windows Mixed Reality in modo da non tornare più automaticamente a 60 Hz in alcuni casi quando non è possibile ottenere 90 Hz. 

### <a name="help-us-improve"></a>Aiutaci a migliorare.

Microsoft cerca continuamente di migliorare la compatibilità.  Se l'applicazione Win32 classica preferita non si comporta correttamente mentre è Windows Mixed Reality, inviare commenti e suggerimenti tramite il Hub di Feedback [.](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - Maggio 2019](release-notes-may-2019.md)
* [Note sulla versione - ottobre 2018](release-notes-october-2018.md)
* [Note sulla versione - Aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedi anche
* [Supporto per visori VR immersive (collegamento esterno)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Commenti e suggerimenti](/windows/mixed-reality/give-us-feedback)