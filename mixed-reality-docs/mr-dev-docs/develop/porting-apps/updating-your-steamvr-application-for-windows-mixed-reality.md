---
title: Aggiornamento di app SteamVR per Windows Mixed Reality
description: Procedure consigliate per l'aggiornamento dell'applicazione SteamVR per ottimizzare la compatibilità con Windows Mixed Reality visori VR.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: WirelessVR, compatibilità, portabilità, HoloLens prima generazione, visore VR di realtà mista, visore VR windows di realtà mista, migrazione, Windows 10, flussi, controller del movimento, aptiche
ms.openlocfilehash: ee72994691970a3701ec8462ab0f42b6d1da1820589ca68a92c9a78fe1c18a41
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196191"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Aggiornamento di app SteamVR per Windows Mixed Reality

Si consiglia agli sviluppatori di testare e ottimizzare le proprie esperienze Dirvr per l'esecuzione Windows Mixed Reality visori VR. Questa documentazione illustra i miglioramenti comuni che è possibile apportare per migliorare l'esecuzione delle esperienze Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Istruzioni di configurazione iniziale

Per iniziare a testare il gioco o l'app Windows Mixed Reality assicurarsi di seguire prima la [guida introduttiva.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>Modelli controller

1. Se l'app esegue il rendering dei modelli del controller:
    * Usare i modelli [Windows Mixed Reality controller del movimento](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * Usare IVRRenderModel::GetComponentState per ottenere le trasformazioni locali nelle parti del componente (ad esempio, la posizione del puntatore)
2. Le esperienze che hanno una nozione di mani dovrebbero ottenere suggerimenti dalle API di input per differenziare i controller [(esempio di Unity)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controlli

Quando si progetta o si modifica il layout dei controlli, tenere presente il set di comandi riservati seguente:
1. Fare clic sulla **levetta analoga sinistra e** destra è riservata per **dashboard di dashboard.**

> [!NOTE]
> Se si usa un controller HP Reverb G2, fare clic sul pulsante di menu a destra è riservato a **Dashboard Di Dashboard.**

2. Il **Windows di accesso** restituirà sempre gli utenti alla Windows Mixed Reality home page.

Se possibile, per impostazione predefinita il teletrasporto basato su levetta deve corrispondere Windows Mixed Reality [comportamento](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) di teletrasporto domestico

## <a name="tooltips-and-ui"></a>Descrizioni comando e interfaccia utente

Molti giochi per la realtà virtuale sfruttano le descrizioni comando e le sovrimpressione del controller del movimento per insegnare agli utenti i comandi più importanti dell'app o dei giochi. Quando si ottimizzazione l'applicazione per Windows realtà mista, è consigliabile rivedere questa parte dell'esperienza per assicurarsi che le descrizioni comando siano mappate ai modelli Windows controller.

Inoltre, se sono presenti punti dell'esperienza in cui si visualizzano le immagini dei controller, assicurarsi di fornire immagini aggiornate usando i controller del movimento Windows Mixed Reality dispositivo.

## <a name="haptics"></a>Aptics

A partire [dall'Windows 10 di aprile 2018,](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)gli aptici sono ora supportati per le esperienze di SteamVR Windows Mixed Reality. Se l'app o il gioco Dirvr include già il supporto per gli aptici, dovrebbe ora funzionare (senza operazioni aggiuntive) con i controller Windows Mixed Reality [movimento.](../../design/motion-controllers.md)

Windows Mixed Reality controller del movimento usano un motore aptico standard, a differenza degli attuatori lineari presenti in altri controller di movimento Aptics. Questo può portare a un'esperienza utente leggermente diversa dal previsto. È quindi consigliabile testare e ottimizzazione la progettazione aptica con Windows Mixed Reality controller del movimento. Ad esempio, a volte gli pulse aptici brevi (5-10 ms) sono meno evidenti Windows Mixed Reality controller del movimento. Per produrre un pulsazione più evidente, provare a inviare un "clic" più lungo (40-70 ms) per concedere al motore più tempo per ruotare prima di essere nuovamente spento.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Avvio di app Dirvr da Windows Mixed Reality menu Start

Per le esperienze di realtà virtuale distribuite tramite Steam, abbiamo aggiornato [Windows Mixed Reality per SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme alle versioni [Windows più recenti.](https://insider.windows.com) I titoli di SteamVR vengono ora visualizzati nella Windows Mixed Reality menu Start nell'elenco "Tutte le app" automaticamente.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality logo

Per visualizzare Windows Mixed Reality supporto per il titolo, passare al collegamento "Edit Store Page" (Modifica pagina store) nella pagina di destinazione dell'app, selezionare la scheda "Informazioni di base" e scorrere verso il basso fino a "Virtual Reality". Deselezionare "Nascondi Windows Mixed Reality" e quindi pubblicare nello Store.

## <a name="bugs-and-feedback"></a>Bug e feedback

Il feedback degli utenti è molto utile quando si tratta di migliorare l'esperienza Windows Mixed Reality Dirvr. Inviare tutti i commenti e i bug [tramite il Hub di Windows Feedback](/windows/mixed-reality/enthusiast-guide/filing-feedback). Di seguito sono [riportati alcuni suggerimenti su come rendere il feedback di SteamVR il più utile possibile.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)

In caso di domande o commenti da condividere, è anche possibile contattare Microsoft nel [forum di Forum di Forum di Microsoft.](https://steamcommunity.com/app/719950/discussions/)

## <a name="faqs-and-troubleshooting"></a>Domande frequenti e risoluzione dei problemi

Se si verificano problemi generali durante la configurazione o la riproduzione dell'esperienza, [vedere i passaggi più recenti per la risoluzione dei problemi.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)

## <a name="see-also"></a>Vedere anche

* [Installare gli strumenti](../install-the-tools.md)
* [Cronologia del visore VR e del driver del controller del movimento](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality linee guida minime per la compatibilità hardware del PC](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)