---
title: Domande frequenti su HP Reverb G2
description: È possibile rimanere sempre aggiornati sulle domande frequenti sull'uso di HP reverbi G2 Headset con auricolari immersivi con la realtà mista di Windows.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, prestazioni
appliesto:
- Windows 10
ms.openlocfilehash: 00338e1354dc04acc76fa2525c721a5e2bd4afe2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009471"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Domande frequenti su HP Reverb G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>È necessario seguire un ordine specifico per connettere i cavi dell'auricolare a un PC

HP consiglia:

- Collegare il cavo di 6 metri all'auricolare prima di connettersi al PC o all'alimentatore.
- Lasciare il cavo a 6 metri connesso all'auricolare dopo l'installazione iniziale.
- Quando la cuffia non è in uso, disconnettere l'alimentatore dal cavo a 6 metri.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>Cosa devo fare per ottenere un'immagine più nitida

Se si ritiene che la visualizzazione appaia leggermente sfocata, è possibile provare a eseguire alcune operazioni:

- Assicurarsi che l'auricolare si trovi correttamente con gli occhi centrati sulle lenti.
- Provare a modificare il dpi (interpupillare distance). Reverb G2 usa un hardware dpi. Per modificarlo, cercare la regolazione di DPI nell'auricolare.
- Se sono necessari occhiali o contatti, è necessario usarli quando si usa il dispositivo.
- Verificare che le lenti siano pulite (solo panno in microfibre-nessun fluido).
- A causa della progettazione avanzata di cuffie, potrebbe essere presente un'immagine secondaria dei primi minuti quando si avvia il dispositivo mentre si è a freddo finché gli LCD non hanno la possibilità di scaldarsi.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>Si è verificato un errore 7-14 "si è verificato un errore" durante il collegamento dell'auricolare

Il codice 7-14 qualcosa ha avuto esito negativo significa che alcuni dei componenti USB2 richiesti non sono stati trovati.  A causa del cavo molto lungo di HP reverbi G2, alcune delle tolleranze per i segnali USB sono più rigorose.  Ciò significa che una porta del computer potrebbe funzionare in modo più affidabile rispetto a un'altra.

Se viene visualizzato un errore 7-14 "si è verificato un errore", provare a eseguire i passaggi seguenti:

- Verificare che siano installati i driver più recenti per l'auricolare e il controller USB.
- Assicurarsi di usare un driver USB Microsoft. Il nome del dispositivo "eXtensible Host Controller" deve essere "Microsoft".
- Provare a collegare il cavo a una porta USB-3,0 diversa nel computer. (Provare le porte USB Type-C e Type-A)
- Usare l'unità C USB inclusa in un adapter per provare porte diverse.
- Provare a collegare la cuffia a un hub USB al computer.

> [!NOTE]
> HP consiglia di usare solo i controller USB incorporati nella scheda madre con i dispositivi G2 del riverbero.
> Se non è possibile connettere il dispositivo, contattare il [supporto tecnico HP](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Si è verificato un errore 13-14 "si è verificato un errore" quando il PC riprende da ibernazione (S4)

In alcuni casi, durante il processo di ripresa, la scheda video non è in grado di stabilire una connessione, quindi scollegando il tipo di USB C dal PC e inserendolo di nuovo, potrebbe essere utile stabilire una connessione.

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>Il joystick di HP Motion controller a volte viene attaccato da un lato

Questo problema è stato corretto deselezionando completamente il joystick fino a quando non viene fatto clic e verrà spostato liberamente.

## <a name="others-state-i-am-loud-or-that-my-audio-is-clipping-while-i-am-using-the-microphone-with-some-applications"></a>Gli altri Stati sono ad alta voce o che l'audio sta per ritagliare mentre sto usando il microfono con alcune applicazioni

I livelli del volume di input vengono impostati automaticamente su 100% quando il microfono di HP Reverb G2 viene riconosciuto per la prima volta da un computer Windows. A causa dei microfoni G2 di qualità elevata, la sensibilità di input è molto più elevata rispetto alle impostazioni predefinite di Windows 10. Si consiglia di impostare il livello di input del microfono di Reverb G2 a partire dal 50% e di scalare verticalmente. Un'impostazione ottimale è specifica dell'utente, soprattutto quando si usano applicazioni che non hanno un'impostazione del microfono "guadagno automatico". Gli esempi di applicazioni con "guadagno automatico" sono Skype, zoom, teams e Cisco WebEx, ma non tutte le applicazioni di telecomunicazioni o di telecomunicazione VR hanno questa funzionalità.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Il portale per la realtà mista indica che "non è possibile eseguire la realtà mista in questo auricolare", ma questa operazione è stata eseguita correttamente con la WMR

Questo problema può verificarsi perché il sistema HP Reverb G2 richiede un PC più potente per garantire la migliore esperienza. Per ulteriori informazioni, esaminare i requisiti minimi per il [PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Sembra che lo schermo a sinistra sia allungato e che la visualizzazione destra sia disattivata e mezza nera

Questo problema può verificarsi quando la cuffia non viene eseguita con la risoluzione nativa. A causa della natura degli schermi ad alta risoluzione in HP reverbi G2 HMD, non tutti i sistemi possono eseguire il rendering della risoluzione nativa. Una correzione verrà rilasciata in un Windows Update futuro che risolverà il problema di rendering quando l'auricolare non è alla risoluzione nativa.

Esistono alcuni motivi per cui il sistema non è in grado di eseguire il rendering alla risoluzione nativa:

- Il DisplayPort del sistema potrebbe non essere compatibile con 1,3 o potrebbe non supportare tutte e quattro le corsie.
- Se si usa un adapter, potrebbe non essere compatibile con HBR3 o potrebbe non supportare tutte e quattro le corsie.
- Se il sistema dispone di una GPU ibrida, è possibile che la larghezza di banda disponibile per DisplayPort sia limitata.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Perché i modelli HP Motion controller non vengono visualizzati correttamente in un gioco

Anche se la maggior parte dei giochi non Visualizza i controller o usa i modelli installati dal driver, alcuni giochi usano le rispettive versioni dei modelli di controller, per personalizzarli o per visualizzare la guida contestuale per gli input disponibili. In genere, questo non blocca le funzionalità dei giochi, ma potrebbe causare confusione o persino artefatti visivi. Questo problema può essere risolto solo con un aggiornamento del gioco stesso.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>I miei giochi SteamVR non sembrano funzionare correttamente con i controller di movimento HP

Sebbene gli sviluppatori stiano lavorando per aggiornare i giochi per la compatibilità di HP Motion controller, abbiamo fornito associazioni controller personalizzate per molti dei giochi più diffusi su Steam. Con "realtà mista di Windows per SteamVR" completamente aggiornato alla versione 1.2.444, questi binding devono essere prelevati automaticamente quando il gioco è in esecuzione. Tuttavia, se il gioco non sembra registrare le azioni in questo momento, è possibile cercare manualmente i profili di binding personalizzati usando il menu delle impostazioni di SteamVR.
Per

- Aprire il menu SteamVR premendo il pulsante di menu del controller di movimento destro
- Selezionare l'icona "Settings" (impostazioni) nell'angolo in basso a destra del menu SteamVR.
- Selezionare la scheda "controller"
- Selezionare l'opzione "Gestisci binding controller"

Da qui è possibile modificare il binding del controller attivo in "Custom", in modo da aprire l'opzione per provare le associazioni di gioco condivise dalla community.
Se non è ancora stata condivisa alcuna associazione di gioco personalizzata per questo gioco (o se non si è pienamente soddisfatti di quelli usati), è anche possibile creare binding di gioco personalizzati e anche aiutare il resto della community condividendo questi ultimi dopo alcune sessioni di gioco.