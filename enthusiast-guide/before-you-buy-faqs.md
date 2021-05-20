---
title: Prima di acquistare - Domande frequenti
description: Risposte alle domande frequenti che i potenziali acquirenti possono avere prima di acquistare un visore windows mixed reality e un PC compatibile.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, pre-vendita, ricerca, acquisto, prima di acquistare
appliesto:
- Windows 10
ms.openlocfilehash: 82ae2af5a8edd60317ba7d7c343c80a25b226301
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196616"
---
# <a name="before-you-buy-frequently-asked-questions"></a>Prima di acquistare le domande frequenti

## <a name="general-questions"></a>Domande generali

### <a name="where-can-i-buy-a-windows-mixed-reality-ready-pc-or-headset"></a>Dove è possibile acquistare un PC Windows Mixed Reality o un visore

**Risposta rapida:** È possibile acquistare un PC o un visore Windows Mixed Reality presso un rivenditore locale approvato o online da diversi rivenditori, incluso il Microsoft Store. Trovare online Windows Mixed Reality pc o visore pronti per la configurazione: <https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1>

### <a name="where-can-i-try-windows-mixed-reality"></a>Dove è possibile provare Windows Mixed Reality

**Risposta rapida:** È possibile provare a Windows Mixed Reality presso [microsoft reactor](https://developer.microsoft.com/reactor/?WT.mc_id=docs-faq-ayyonet) nelle vicinanze.

* Trovare gli eventi di Microsoft Reactor Meetup.com: <https://www.meetup.com/pro/microsoft-reactor>

### <a name="which-manufacturers-are-selling-windows-mixed-reality-devices"></a>Quali produttori vendono Windows Mixed Reality dispositivi

**Risposta rapida:** Visori e controller di movimento sono attualmente disponibili da HP. Vedere <https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1>

### <a name="where-can-i-buy-standalone-motion-controllers"></a>Dove è possibile acquistare controller di movimento autonomi

**Risposta rapida:** Sfortunatamente, al momento non si è a conoscenza di rivenditori che vendono controller di movimento autonomi.

### <a name="what-is-the-difference-between-a-windows-mixed-reality-pc-and-a-windows-mixed-reality-ultra-pc"></a>Qual è la differenza tra un PC Windows Mixed Reality e un PC Windows Mixed Reality Ultra

**Risposta rapida:** I dettagli Windows Mixed Reality PC e ULTRA sono acquisiti qui: <https://aka.ms/mrcompat>

### <a name="why-is-this-called-windows-mixed-reality-when-the-devices-look-like-they-provide-a-virtual-reality-experience"></a>Perché si chiama "Realtà mista" di Windows quando i dispositivi sembrano offrire un'esperienza di "realtà virtuale"

**Risposta rapida:** La realtà mista si riferisce all'intero spettro del calcolo spaziale, dalla realtà aumentata e dagli ologrammi alla realtà virtuale. Windows Mixed Reality piattaforma supporta i dispositivi in realtà virtuale (VR) e realtà aumentata (AR). Attualmente sono supportati due tipi di dispositivi con tecnologia simile in questo spettro: visori HoloLens (AR) e Windows Mixed Reality (VR) con controller di movimento.

Per altre informazioni sulla realtà mista, vedere: <https://docs.microsoft.com/windows/mixed-reality/mixed-reality>

### <a name="what-is-the-difference-between-windows-mixed-reality-and-other-vr-headsets"></a>Qual è la differenza tra Windows Mixed Reality visori VR e altri visori VR?

**Risposta rapida:** Windows Mixed Reality visori VR sono disponibili per il rilevamento inside-out (le fotocamere di rilevamento sono nel visore VR) e la configurazione plug-and-play con Windows 10.

Altri **dettagli:** Windows Mixed Reality offre diverse funzionalità, tra cui una configurazione semplice (senza bisogno di sensori esterni per tenere traccia dell'utente e dei controller), la scelta di visori VR per soddisfare il comfort e il prezzo, visori VR con risoluzioni competitive e infine un'esperienza utente unica che offre un'interfaccia spaziale, che consente di usare migliaia di app dal Microsoft Store.

### <a name="does-mixed-reality-mean-that-inside-out-cameras-are-passthrough-can-you-experience-augmented-reality-in-addition-to-virtual-reality"></a>Realtà mista significa che le fotocamere interne sono pass-through? È possibile sperimentare la realtà aumentata oltre alla realtà virtuale

**Risposta rapida:** No, le fotocamere interne su Windows Mixed Reality visori VR vengono usate solo per il rilevamento posizionale. Windows Mixed Reality visori VR sono occlusi, vale a dire che sono per la realtà virtuale e non offrono una visualizzazione del mondo reale o della realtà aumentata.

### <a name="what-is-inside-out-tracking-how-is-it-different-than-outside-in-tracking-or-lighthouse-tracking"></a>Che cos'è il rilevamento inside-out? Qual è la sua differente rispetto al tracciamento esterno o al tracciamento lighthouse

* **Rilevamento inside-out** Windows Mixed Reality, Oculus Quest e Vive/Index usano il rilevamento inside-out. Con le fotocamere di rilevamento interne vengono integrate nel visore VR e vengono rilevate le modifiche nell'ambiente per determinare la posizione del visore VR in base all'ambiente mentre ci si sposta. Alcuni sistemi, ad esempio l'INDICE DELLE VALVOLE e DELLA STAZIONI, usano sensori a globo anziché fotocamere e dipendono da "fari" o "stazioni di base" esterni che proiettano la luce a forma di globo per tenere traccia dell'ambiente.

* **Rilevamento esterno** Sistemi come Oculus Rift e PlayStation VR usano il rilevamento esterno.  Con il rilevamento esterno, il visore VR viene monitorato da uno o più dispositivi esterni. Le fotocamere sono integrate in tali dispositivi esterni, posizionate intorno all'ambiente e vengono usate per determinare la posizione del visore in base all'ambiente.

Altre informazioni sul [rilevamento interno.](./tracking-system.md)

### <a name="can-inside-out-tracking-of-motion-controllers-impact-my-game-play-due-to-camera-fov"></a>Il rilevamento interno dei controller di movimento può influire sul gioco a causa della fotocamera FOV

 Come i visori, i Windows Mixed Reality di movimento non richiedono la configurazione di sensori di rilevamento esterni. I controller vengono invece monitorati dai sensori nel visore stesso. Se l'utente sposta i controller dal campo di visualizzazione del visore, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e a fornirli all'app. Quando il controller ha perso il rilevamento visivo per un tempo sufficiente, le posizioni del controller scenderanno a posizioni di accuratezza approssimativa. A questo punto, il sistema bloczzerà il controller all'utente, tenendo traccia della posizione dell'utente mentre si sposta, pur esponendo il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con accuratezza approssimativa senza che l'utente ne se ne sia nemmeno a riconoscimento. Il modo migliore per ottenere un'esperienza a questo scopo è provarlo da soli.

### <a name="how-is-windows-mixed-reality-different-from-samsung-gear-vr"></a>Come è Windows Mixed Reality diversa da Samsung Gear VR

**Risposta rapida:** Tutti i prodotti VR basati su smartphone, tra cui Samsung Gear VR e Google Daydream, usano tre sistemi di rilevamento della posizione della testa (3DOF). I sistemi basati su 3DOF consentono di spostare la **testa** solo dal collo verso l'alto nel mondo virtuale. Windows MR, d'altra parte, usa un sistema di rilevamento della posizione di sei gradi di libertà (6DOF). I sistemi basati su 6DOF consentono di spostare l'intero corpo nel mondo virtuale; in modo da poter aggirare un oggetto e vederlo da prospettive diverse, proprio come nel mondo fisico. Anche Rift e Vive sono sistemi basati su 6DOF.

* Per altre informazioni su 3DOF e 6DOF, vedere qui: <https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system#what-is-the-difference-between-3dof-and-6dof> 
* Per altre informazioni su Positional Tracking and Degree's of Freedom (DOF), vedere qui: <https://www.roadtovr.com/introduction-positional-tracking-degrees-freedom-dof/>

## <a name="technical-specifications"></a>Specifiche tecniche

<table>
<tr>
<th style="width:25%"> Cuffie </th>
<th style="width:15%"> Soluzione </th>
<th style="width:10%"> Visualizza </th>
<th style="width:10%"> Frequenza di aggiornamento </th>
<th style="width:10%"> Fov </th>
<th style="width:15%"> Audio </th>
<th style="width:10%"> Bluetooth </th>
<th style="width:10%"> Regolazione IPD </th>
<th style="width:10%"> Data di rilascio </th>
<th style="width:25%"> Altre informazioni </th>
</tr>

<tr>
<td> Acer AH101 </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 100˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Fall 2017 </td>
<td> <a href="https://www.acer.com/ac/en/US/content/windows-mixed-reality-home">Acer</a> </td>
</tr>

<tr>
<td> Acer OJO 500 </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 100˚ </td>
<td> Jack integrato + 3,5 mm </td>
<td> Predefinito </td>
<td style="text-align: center;">Meccanica</td>
<td> Fall 2018 </td>
<td> <a href="https://www.acer.com/ac/en/US/press/2018/427890">Acer</a> </td>
</tr>

<tr>
<td> ASUS HC102 </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 95˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Autunno 2017 </td>
<td> <a href="https://www.asus.com/us/Headset/ASUS-Windows-Mixed-Reality-Headset-HC102/">Asus</a> </td>
</tr>

<tr>
<td> Visore Dell </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Autunno 2017 </td>
<td> <a href="https://www.dell.com/en-us/shop/accessories/apd/536-bbbr?~ck=mn">Dell</a> </td>
</tr>

<tr>
<td> Visore Fujitsu FMV </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Autunno 2017 </td>
<td> <a href="http://pr.fujitsu.com/jp/news/2017/10/17.html">Fujitsu</a> </td>
</tr>

<tr>
<td> Riverbero HP </td>
<td> 4320x2160 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 114˚ </td>
<td> Jack integrato + 3,5 mm </td>
<td> Predefinito </td>
<td style="text-align: center;">Software</td>
<td> Spring 2019 </td>
<td> <a href="https://www8.hp.com/us/en/workstations/mixed-reality-headset/index.html">Hp</a> </td>
</tr>

<tr>
<td> HP VR1000 </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Fall 2017 </td>
<td> <a href="https://store.hp.com/us/en/pdp/hp-windows-mixed-reality-headset-vr1000-100">Hp</a> </td>
</tr>

<tr>
<td> Lenovo Explorer </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Autunno 2017 </td>
<td> <a href="https://www.lenovo.com/us/en/virtual-reality-and-smart-devices/virtual-and-augmented-reality/lenovo-explorer/Lenovo-Explorer/p/G10NREAG0A2">Lenovo</a> </td>
</tr>

<tr>
<td> Medion ERAZER MR X1000 </td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Autunno 2017 </td>
<td> <a href="https://www.medion.com/be/shop/monitoren-medion-erazer-mr-x1000-vr-headset-controllers-30023616a1.html">Medion</a> </td>
</tr>

<tr>
<td> Samsung HMD Odyssey</td>
<td> 2880x1600 </td>
<td> Amoled </td>
<td> Fino a 90 Hz </td>
<td> 110˚ </td>
<td> Integrato </td>
<td> nessuno </td>
<td style="text-align: center;">Meccanica</td>
<td> Autunno 2017 </td>
<td> <a href="https://www.samsung.com/us/computing/hmd/windows-mixed-reality/xe800zaa-hc1us-xe800zaa-hc1us/?redir=windows%20mixed%20reality">Samsung</a> </td>
</tr>

<tr>
<td> Samsung HMD Odyssey+</td>
<td> 2880x1600 </td>
<td> Amoled </td>
<td> Fino a 90 Hz </td>
<td> 110˚ </td>
<td> Integrato </td>
<td> Predefinito </td>
<td style="text-align: center;">Meccanica</td>
<td> Fall 2018 </td>
<td> <a href="https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/">Samsung</a> </td>
</tr>

<tr>
<td> 3Glasses Blubur S2</td>
<td> 2880x1440 </td>
<td> Lcd </td>
<td> Fino a 90 Hz </td>
<td> 105˚ </td>
<td> Jack da 3,5 mm </td>
<td> nessuno </td>
<td style="text-align: center;">Software</td>
<td> Fall 2017 </td>
<td> <a href="http://3glasses.com/goods.action?gid=30">3 Occhiali</a> </td>
</tr>
</table>

I dettagli tecnici elencati sopra sono indicati dalle specifiche del produttore e sono soggetti a modifiche.

### <a name="does-mixed-reality-mean-that-the-inside-out-cameras-are-passthrough"></a>"Realtà mista" significa che le fotocamere interne all'esterno sono pass-through?

**Risposta rapida:** No, le fotocamere interne vengono usate solo per il rilevamento posizionale. Windows Mixed Reality visori VR sono occluded.

### <a name="do-the-mixed-reality-headsets-have-ipd-adjustment"></a>I visori VR di realtà mista hanno la regolazione dell'IPD?

**Risposta rapida:** A seconda del visore, alcuni visori di realtà mista presentano regolazione IPD meccanica. Altri visori presentano regolazione IPD software, che migliora la distorsione dell'immagine e l'accuratezza della profondità in base all'IPD. Gli utenti possono impostare il proprio IPD personalizzato tramite Impostazioni > visualizzazione visore > realtà mista **> calibrazione**.

### <a name="do-the-mixed-reality-headsets-have-eye-relief-adjustment"></a>I visori di realtà mista hanno la regolazione del rilievo oculare?

**Risposta rapida:** No, le Windows Mixed Reality visori non hanno regolazione del rilievo oculare.

### <a name="will-there-be-issues-with-motion-controller-tracking-if-multiple-windows-mixed-reality-headsets-are-in-close-proximity"></a>Si verificano problemi con il rilevamento del controller di movimento se Windows Mixed Reality visori sono in prossimità?

**Risposta rapida:** È stato rilevato che non sono presenti interferenze con i controller di movimento, ma è consigliabile concedere agli utenti spazio sufficiente per la migliore esperienza nella realtà mista, ad esempio 10 piedi x 10 piedi.

### <a name="is-there-boundary-chaperone-or-guardian-system-in-windows-mixed-reality"></a>Esiste un sistema limite, chaperone o guardiano Windows Mixed Reality?

**Risposta rapida:** Windows Mixed Reality consente di configurare un limite. Inoltre, alcuni visori Windows MR hanno un display a cernie anteriore, quindi è possibile capovolgere il visore durante il lavoro.

### <a name="do-windows-mixed-reality-headsets-work-in-the-dark"></a>Le Windows Mixed Reality visori funzionano al scuro?

**Risposta rapida:** Una buona regola generale è che se non è possibile spostarsi in tutta sicurezza per la stanza perché è troppo scura, anche il sistema di rilevamento avrà difficoltà a lavorare in tale ambiente.

### <a name="what-is-the-cable-length-of-the-windows-mixed-reality-headset"></a>Qual è la lunghezza del cavo del visore Windows Mixed Reality visore?

**Risposta rapida:** In genere la lunghezza del cavo Windows Mixed Reality visori è di 4 metri, ma dipende dal visore. Per altre informazioni, vedere: <https://www.microsoft.com/en-us/store/collections/vrandmixedrealityheadsets>

### <a name="can-i-use-a-usb--hdmi-extension-cable-with-windows-mixed-reality-headsets"></a>È possibile usare un cavo di estensione USB/HDMI con Windows Mixed Reality visori?

**Risposta rapida:** È stato progettato Windows Mixed Reality per funzionare senza cavi di estensione. L'uso di cavi di estensione con visore di realtà mista non è supportato e l'uso potrebbe influire sull'esperienza.

## <a name="pc-compatibility"></a>Compatibilità con i PC

### <a name="will-my-pc-work-with-windows-mixed-reality-what-are-the-minimum-specs"></a>Il PC funzionerà con Windows Mixed Reality? Quali sono le specifiche minime?

**Risposta rapida:** È possibile trovare le specifiche minime [qui](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) [](https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab) oppure è possibile scaricare ed eseguire Portale realtà mista per verificare se il PC funzionerà con Windows Mixed Reality.

### <a name="will-windows-mixed-reality-work-with-my-xbox"></a>L Windows Mixed Reality funziona con xbox?

**Risposta rapida:** No, Windows Mixed Reality funziona solo con i PC. Scaricare ed eseguire [Portale realtà mista](https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab) per verificare se il PC è pronto per WMR.

### <a name="what-pcs-have-been-badged-for-windows-mixed-reality"></a>Quali PC sono stati notificati per Windows Mixed Reality?

**Risposta rapida:** L'elenco completo dei PC con badge non è ancora stato pubblicato, ma lo sarà più avanti quest'anno. Scaricare ed eseguire [Portale realtà mista](https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab) per verificare se il PC è pronto per WMR.

### <a name="what-windows-version-supports-windows-mixed-reality"></a>Quale versione di Windows supporta Windows Mixed Reality?

**Risposta rapida:** È necessario che sia Windows 10 Fall Creators Update versione 1709 o successiva. Scaricare ed eseguire [Portale realtà mista](https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab) per verificare se il PC è pronto per WMR.

### <a name="does-the-windows-mixed-reality-platform-support-rift-and-vive-hardware"></a>La piattaforma Windows Mixed Reality supporta hardware Rift e Vive?

**Risposta rapida:** Windows Mixed Reality funziona solo con visori VR Windows Mixed Reality/controller approvati. Vedere <https://www.microsoft.com/en-us/store/b/virtualreality>

## <a name="motion-controllers"></a>Controller del movimento

### <a name="how-do-motion-controllers-work-with-my-pc"></a>Come funzionano i controller del movimento con il PC?

**Risposta rapida:** Windows Mixed Reality controller del movimento usano Bluetooth. A seconda del visore VR, i controller del movimento vengono associati alla radio Bluetooth sul visore VR (se dotato) o alla radio Bluetooth nel PC.

* Alcuni visori VR Windows Mixed Reality, tra cui le radio Bluetooth integrate Acer OJO 500, Samsung Odyssey+, HP Reverb e HP Reverb G2, per l'uso con controller del movimento. I controller del movimento che sono disponibili con questi visori VR sono pre-associati al visore VR dalla fabbrica e non richiedono che il PC abbia una radio Bluetooth separata.
* Altri Windows Mixed Reality visori VR dovranno essere associati a una radio Bluetooth nel PC.

### <a name="are-windows-mixed-reality-motion-controllers-cross-compatible-between-windows-mixed-reality-headsets"></a>I Windows Mixed Reality di movimento sono cross-compatible tra Windows Mixed Reality visori?

**Risposta rapida:** Sì, i Windows Mixed Reality di movimento funzionano su tutti Windows Mixed Reality visori.

### <a name="how-do-i-connect-motion-controllers-if-i-do-not-have-built-in-bluetooth"></a>Ricerca per categorie collegare i controller di movimento se non si dispone di Bluetooth integrato?

**Risposta rapida:** Se il PC non dispone del supporto Bluetooth incorporato, è necessario collegare un adattatore Bluetooth USB che supporta Bluetooth 4.0 per abilitare i controller di movimento.

### <a name="will-the-controllers-work-with-bluetooth-31-or-do-i-need-bluetooth-40"></a>Il controller funzionerà con Bluetooth 3.1 o è necessario Bluetooth 4.0?

**Risposta rapida:** La specifica minima supportata per Windows Mixed Reality è Bluetooth 4.0. Se il PC ha Bluetooth 3.1, non verrà impedito l'uso dei controller, ma l'esperienza migliore è in BT 4.0. Scaricare ed eseguire [Portale realtà mista](https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab) per verificare se il PC è pronto per WMR.

### <a name="will-windows-mixed-reality-controllers-work-with-hololens"></a>I Windows Mixed Reality funzioneranno con HoloLens?

**Risposta rapida:** No, Windows Mixed Reality di movimento non funzionano con HoloLens.

### <a name="will-windows-mixed-reality-work-with-my-oculus-touch-controllers-or-htc-vive-headsets--controllers"></a>È Windows Mixed Reality con i controller Oculus Touch o i visori/controller DIsinvati DISA?

**Risposta rapida:** No, Windows Mixed Reality funziona solo con visori/controller approvati. Vedere <https://www.microsoft.com/en-us/store/collections/VRandMixedrealityheadsets>

### <a name="will-windows-mixed-reality-work-with-my-steamvr-knuckle-controllers"></a>Verranno Windows Mixed Reality con i controller di SteamVR Knuckle?

**Risposta rapida:** No, Windows Mixed Reality funziona solo con visori/controller approvati. Vedere <https://www.microsoft.com/en-us/store/collections/VRandMixedrealityheadsets>

### <a name="will-windows-mixed-reality-support-my-xbox-one-controller-with-the-wireless-xbox-adapter"></a>Supporterà Windows Mixed Reality controller Xbox One con l'adattatore Xbox wireless?

**Risposta rapida:** Sì, funzionerà con un adattatore Xbox wireless (non è necessario Bluetooth).

## <a name="comfort"></a>Comfort

### <a name="can-i-wear-a-windows-mixed-reality-headset-with-glasses"></a>È possibile usare un visore Windows Mixed Reality visore con gli occhiali?

**Risposta rapida:** Sì, è possibile usare un visore Windows Mixed Reality visore con e senza occhiali.

### <a name="does-windows-mixed-reality-support-productivity-within-a-vr-headset-on-a-desktop-environment"></a>È Windows Mixed Reality la produttività all'interno di un visore VR in un ambiente desktop?

**Risposta rapida:** All'interno di un visore VR Windows Mixed Reality è possibile usare più attività con app UWP di Windows, ad esempio Calendario di Mail &, e accedere alle app Win32 complete in esecuzione sul desktop usando l'app Desktop Preview.

### <a name="can-i-see-my-keyboard-from-inside-a-windows-mixed-reality-headset"></a>È possibile visualizzare la tastiera dall'interno di un visore WINDOWS MIXED REALITY visore VR?

**Risposta rapida:** Non è possibile visualizzare la tastiera fisica dal visore VR, ma è possibile usare la tastiera software. Inoltre, molti Windows Mixed Reality visori VR hanno un display con cernie anteriore, quindi è possibile capovolgere il visore VR durante il lavoro. Altri dettagli: <https://www.microsoft.com/en-us/windows/windows-mixed-reality#specs>

### <a name="what-games-require-a-gamepad-as-opposed-to-motion-controllers"></a>Quali giochi richiedono un game pad anziché controller del movimento?

**Risposta rapida:** Si prevede che la maggior parte delle applicazioni Windows Mixed Reality immersive sceglierà di supportare i controller del movimento, ma non è un requisito. Il supporto del controller del movimento è in grado di supportare gli sviluppatori dell'esperienza. È lo sviluppatore a decidere quale modalità di input vuole supportare nel gioco. È possibile visualizzare i tipi di controller supportati nella pagina dei dettagli del prodotto di un determinato gioco o app nello Store.

### <a name="if-i-am-using-xbox-game-streaming-can-i-use-my-xbox-controller"></a>Se si usa lo streaming di giochi Xbox, è possibile usare il controller Xbox?

**Risposta rapida:** Sì, lo streaming di un gioco da una Xbox richiede un controller Xbox, come se ci si trovasse nella console.

### <a name="will-windows-mixed-reality-work-if-i-have-no-space-in-my-room"></a>Non Windows Mixed Reality lavoro se non ho spazio nella stanza?

**Risposta rapida:** Sì, Windows Mixed Reality funzionerà anche se non si ha molto spazio. È possibile impostare questa opzione durante l'installazione selezionando l'esperienza "desk-scale".

## <a name="content"></a>Content

### <a name="what-games-and-apps-run-on-windows-mixed-reality"></a>Quali giochi e app vengono eseguiti in Windows Mixed Reality?

**Risposta rapida:** Windows Mixed Reality è compatibile con la libreria SteamVR e con il contenuto disponibile in [Microsoft Store.](https://www.microsoft.com/en-us/store/collections/MR-All-ImmersiveContent/pc?rtc=2) Per la compatibilità dei Windows Mixed Reality, cercare il logo di Windows Mixed Reality in Steam.  

### <a name="will-vive-be-able-to-run-windows-mixed-reality-content"></a>Vive sarà in grado di eseguire Windows Mixed Reality contenuto?

**Risposta rapida:** I visori VR Vive non sono compatibili con Windows Mixed Reality.

### <a name="can-i-play-my-xbox-one-games-in-windows-mixed-reality"></a>È possibile riprodurre i Xbox One in Windows Mixed Reality?

**Risposta rapida:** È possibile riprodurre tutti i giochi Xbox One preferiti in Windows Mixed Reality usando la funzionalità di streaming del app Xbox per Windows 10. È possibile ridimensionare l'app all'interno Windows Mixed Reality home per riempire la parete. Per informazioni su come configurare lo streaming Xbox One gioco, vedere le istruzioni qui: <http://support.xbox.com/en-US/games/game-setup/how-to-use-game-streaming>

## <a name="steamvr"></a>SteamVR

### <a name="are-the-minimum-specs-for-steamvr-higher-than-a-windows-mixed-reality-ultra-pc"></a>Le specifiche minime per SteamVR sono più elevate rispetto a un PC Windows Mixed Reality Ultra computer?

**Risposta rapida:** È possibile eseguire SteamVR con i requisiti del PC Ultra per Windows Mixed Reality. È tuttavia consigliabile eseguire l'anteprima di SteamVR in un PC con una scheda video GTX 1070 (o superiore) e un processore Intel Core i7. Microsoft continua a esaminare i commenti e suggerimenti e a ottimizzare le prestazioni per supportare configurazioni di sistema aggiuntive negli aggiornamenti futuri. Il PC non sarà bloccato dall'esecuzione di Windows Mixed Reality SteamVR se non si soddisfano queste specifiche più elevate, ma ciò inciderà sulle prestazioni e sulla qualità dell'esperienza complessiva.

### <a name="are-all-steam-vr-games-be-supported"></a>Sono supportati tutti i giochi vr di Steam?

**Risposta rapida:** L'obiettivo è supportare il più ampio possibile una gamma di giochi di Steam, ma tenere presente che i giochi di Steam possono prendere dipendenze da configurazioni hardware e controller specifiche in base alle decisioni dello sviluppatore del gioco durante lo sviluppo.