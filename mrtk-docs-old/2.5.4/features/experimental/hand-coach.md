---
title: README_HandCoach
description: Descrizione ed esempi per Hand Coach.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1c5884224e530b09d1cfe15c828b4a9f8c30cf19
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783617"
---
# <a name="hand-coach"></a>Coach mano

![Menu di coaching a mano](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

Hand Coach è la mano modellata 3D che viene attivata quando il sistema non rileva le mani dell'utente. Viene implementato come componente "didattico" che aiuta a guidare l'utente quando il movimento non è stato insegnato. Se gli utenti non hanno eseguito il movimento specificato per un periodo, il ciclo passa con un ritardo. È possibile usare Hand Coach per rappresentare la pressione di un pulsante o la selezione di un ologramma.

Il modello di interazione corrente rappresenta un'ampia gamma di controlli di movimento, ad esempio scorrimento, selezione e prossimità. Di seguito è riportato un elenco completo di esempi di allenamenti della mano esistenti:

- Near TAP: usato per i pulsanti o per chiudere gli oggetti interactabili
- Gran parte: usato per gli oggetti che sono lontani
- Move: usato per spostare un ologramma nello spazio
- Rotazione: usata per mostrare come ruotare gli ologrammi o gli oggetti
- Scale: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli
- Hand Flip: usato per attivare un pannello di avvio dell'interfaccia utente o menu a mano
- Palm up: usato per il momento di Hummingbird nell'esperienza predefinita. Un altro suggerimento potrebbe essere quello di visualizzare un pannello di avvio dell'interfaccia utente
- Scroll: usato per scorrere un elenco o un documento lungo

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella scena **HandCoachExample** in: [MixedRealityToolkit. examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Asset 3D a mano

È possibile trovare gli asset in: [MixedRealityToolkit. SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualità

Se si notano distorsioni sulla mesh con skin, è necessario assicurarsi che il progetto usi la quantità corretta di giunzioni.
Passare alle impostazioni del progetto modifica > di Unity > qualità > altri pesi > Blend. Assicurarsi che siano selezionate "4 ossa" per visualizzare le giunzioni uniformi.
![Impostazione del progetto](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Script

### <a name="interaction-hint"></a>Hint di interazione

Lo `InteractionHint.cs` script fornisce funzionalità wrapper per l'attivazione di animazioni e dissolvenze per la mano rig.

#### <a name="how-to-set-up-an-interaction-hint"></a>Come configurare un hint di interazione

Per configurare un hint di interazione, è consigliabile usare i prefabbricati forniti "StaticHandCoachRoot_L. prefabbricate" e "StaticHandCoachRoot_R. prefabbricate". Questa prefabbricata contiene lo script InteractionHint e il rig a mano, nonché la gerarchia appropriata per garantire che le animazioni di hint fornite funzionino come previsto.
In caso contrario, sarà necessario inserire lo script in un gameObject un livello padre dal Rig a mano con l'animatore.

#### <a name="inspector-properties"></a>Proprietà di Inspector

- **HideIfHandTracked** Questo valore booleano specifica se utilizzare lo stato di rilevamento della mano per nascondere gli oggetti visivi quando vengono rilevate le mani di un utente. Se è impostato su false, verrà utilizzata solo la proprietà di scripting "customShouldHideVisuals" per determinare se nascondere l'hint.

- **MinDelay** Questa proprietà specifica il ritardo minimo per la visualizzazione degli oggetti visivi. Per impostazione predefinita, gli oggetti visivi per la mano verranno visualizzati dopo questo numero di secondi se le mani dell'utente non vengono rilevate.

- **MaxDelay** Questa proprietà specifica il ritardo massimo per la visualizzazione degli oggetti visivi. Per impostazione predefinita, gli oggetti visivi per la mano verranno visualizzati dopo questo numero di secondi anche se le mani dell'utente vengono rilevate.

- **UseMaxTimer** Se questo valore booleano è impostato su false, Disabilita il timer massimo e consente di visualizzare l'hint per la mano solo quando le mani dell'utente sono fuori vista o la condizione personalizzata restituisce false.

- **Ripetizioni** Questa proprietà controlla il numero di volte in cui l'animazione del suggerimento viene riprodotta quando è trascorso il timer min o max. Il suggerimento viene quindi nascosto e resta in attesa del ritardo.

- **Attivazione attiva** Quando questo valore booleano è impostato su true, l'hint viene eseguito automaticamente attraverso la logica del timer quando il GameObject dello script è attivo nella gerarchia e lo script è abilitato. Questa impostazione deve essere impostata su false solo se si intende controllare manualmente l'aspetto e la scomparsa del suggerimento tramite codice.

- **AnimationState** Nome dello stato di animazione che deve essere riprodotto quando l'hint è attivo. È necessario impostare questa funzione prima che venga chiamata la funzione StartHintLoop () (durante OnEnable se AutoActivate è selezionato).

#### <a name="controlling-interactionhint-via-script"></a>Controllo di InteractionHint tramite script

- **StartHintLoop** Questa funzione avvia il ciclo di visualizzazione/Nascondi che altrimenti avvia OnEnable se il flag AutoActivate è impostato su true.
- **StopHintLoop** Questa funzione chiama lo stato di animazione di dissolvenza in uscita se non è in esecuzione, disattiva il ciclo Mostra/Nascondi e imposta il rig della mano inattivo nella gerarchia.
- **AnimationState** Questa stringa determina quale stato di animazione viene riprodotto durante il ciclo. È possibile modificare questa stringa per modificare lo stato di riproduzione, ma è necessario eseguire questa operazione dopo avere chiamato StopHintLoop ed è necessario chiamare di nuovo StartHintLoop dopo aver modificato lo stato.
- **CustomShouldHideVisuals** È possibile impostare questa proprietà con la propria funzione, che dovrebbe restituire true quando si desidera nascondere gli oggetti visivi della mano (tenere presente MinMaxTimer, in particolare il parametro max)

#### <a name="custom-animation-considerations"></a>Considerazioni sull'animazione personalizzata

Per impostazione predefinita, le dissolvenze vengono riportate a 0,5 secondi, quindi le animazioni personalizzate create per l'uso con il rig dovrebbero essere minime di 1,5 secondi per la trasmissione di informazioni significative

Gli Stati di dissolvenza e dissolvenza predefiniti specificati, Fade_In e Fade_Out possono essere modificati modificando il timestamp del secondo fotogramma chiave per impostare la lunghezza della dissolvenza.

L'animatore e lo script sono stati configurati in modo da semplificare il più possibile l'installazione. Per aggiungere nuovi Stati di animazione, è sufficiente importare i FBX, verificare che il nome dell'animazione sia impostato con un nome distinto e trascinare tale animazione nell'animatore.

### <a name="movetotarget"></a>MoveToTarget

Lo script MoveToTarget.cs fornisce la funzionalità per spostare l'hint di mano da una posizione di rilevamento a una posizione di destinazione nel tempo.

#### <a name="how-to-set-up-movetotarget"></a>Come configurare MoveToTarget

I prefabbricati forniti "MovingHandCoachRoot_L. prefabbricate" e "MovingHandCoachRoot_R. prefabbricate" contengono un MoveToTarget nelle rispettive gerarchie. Se si vuole usare questo script nella propria configurazione, è necessario inserirlo nella GameObject radice contenente l'animatore del rig.

#### <a name="inspector-properties"></a>Proprietà di Inspector

- **TrackingObject** Impostare questa proprietà con l'oggetto che deve essere seguito dal rig prima di avviare il movimento. È consigliabile creare un GameObject vuoto e spostarlo in una posizione specifica per facilitare l'individuazione del rilevamento.
- **TargetObject** Impostare questa proprietà con l'oggetto a cui si vuole spostare il rig durante il movimento. È consigliabile creare un GameObject vuoto e spostarlo in una posizione specifica per facilitare l'individuazione del rilevamento.
- **RootObject** Impostare questa impostazione su un elemento padre condiviso tra il rilevamento e l'oggetto di destinazione in modo che sia possibile calcolare correttamente le posizioni relative. La prefabbricazione inclusa include sia gli oggetti di rilevamento che quelli di destinazione nella relativa gerarchia, ma è possibile impostare l'oggetto di destinazione come gameObject al di fuori della prefabbricata e modificare l'oggetto radice in un elemento padre condiviso.
- **Durata** La quantità di tempo necessaria (in secondi) per passare da TrackingObject a TargetObject in secondi.
- **TargetOffset** Offset ottimizzabile che consente di ottenere il GameObject per arrivare alla posizione di destinazione corretta. Questa operazione è utile se l'animazione include un offset di posizione durante l'animazione.
- **AnimationCurve** Il valore predefinito è una curva lineare, ma è possibile modificare la curva per fornire l'interpolazione quando si avvia e si arresta il tracciato di movimento.

#### <a name="controlling-movetotarget-via-script"></a>Controllo di MoveToTarget tramite script

Nello script personalizzato, effettuare una chiamata a follow () se si vuole che il rig della mano segua il TrackingObject, quindi effettuare una chiamata a MoveToTargetPosition () quando si vuole che il rig della mano avvii il movimento verso il TargetObject.

#### <a name="controlling-movetotarget-via-animations"></a>Controllo di MoveToTarget tramite animazioni

Nell'animazione che deve essere spostata, impostare due eventi: uno con una chiamata a follow () e uno con una chiamata a MoveToTargetPosition (). Il primo fotogramma chiave deve essere impostato come segue, perché fa in modo che il rig della mano segua la TrackingObject. MoveToTargetPosition deve essere impostato sul fotogramma chiave in cui si vuole che il rig inizi a trasferirsi nella destinazione. Questo è il modo in cui viene usata la funzionalità script nei prefabbricati forniti.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

Lo script RotateAroundPoint.cs fornisce la funzionalità per ruotare l'hint di mano intorno a un punto pivot nel tempo.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Come configurare RotateAroundPoint

I prefabbricati forniti "RotatingHandCoachRoot_L. prefabbricate" e "RotatingHandCoachRoot_R. prefabbricate" contengono un RotateAroundPoint nelle rispettive gerarchie. Se si vuole usare questo script nella propria configurazione, è necessario inserirlo nella GameObject radice contenente l'animatore del rig.

#### <a name="inspector-properties"></a>Proprietà di Inspector

- **CenteredParent** Impostare questa impostazione con l'oggetto padre per il quale si desidera che il rig venga trasformato.
- **InverseParent** Impostare questo oggetto con l'elemento padre per ruotare l'inverso in centeredParent in modo da garantire lo stesso orientamento della mano. In generale, questo sarà l'oggetto padre con lo script InteractionHint.
- **PivotPosition** Impostare questo valore su un punto in cui si desidera che l'hint avvii lo spostamento in.
- **Durata** La quantità di tempo necessaria (in secondi) per ruotare intorno all'CenteredParent.
- **AnimationCurve** Il valore predefinito è una curva lineare, ma è possibile modificare la curva per fornire l'interpolazione quando si avvia e si arresta il tracciato di movimento.
- **RotationVector** Numero di gradi da ruotare lungo ogni asse.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Controllo di RotateAroundPoint tramite script

Nello script personalizzato effettuare una chiamata a RotateToTarget () quando si vuole che il rig della mano avvii la rotazione intorno al CenteredParent. Quando si desidera che la posizione venga reimpostata sul PivotPosition originale, effettuare una chiamata a ResetAndDeterminePivot ().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controllo di RotateAroundPoint tramite animazioni

Nell'animazione che deve essere spostata, impostare due eventi: uno con una chiamata a ResetAndDeterminePivot () e uno con una chiamata a RotateToTarget (). ResetAndDeterminePivot deve essere impostato sul primo fotogramma chiave, perché causa la reimpostazione del rig della mano sul PivotPosition. RotateToTarget deve essere impostato sul fotogramma chiave in cui si vuole che il rig inizi a ruotare intorno al CenteredParent. Questo è il modo in cui viene usata la funzionalità script nei prefabbricati forniti.
