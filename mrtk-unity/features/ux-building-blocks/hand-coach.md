---
title: Coach mano
description: descrizione ed esempi per Hand hand hand.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f6042fce7c95c106de9c72adc854e2b7112da63c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177154"
---
# <a name="hand-coach"></a>Coach mano

![Hand Coach Menu](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

La mano mano è una mano modellata 3D che viene attivata quando il sistema non rileva le mani dell'utente. Viene implementato come componente "teaching" che consente di guidare l'utente quando il movimento non è stato insegnato. Se gli utenti non hanno eseguito il movimento specificato per un periodo, le mani scorreranno a ciclo continuo con un ritardo. È possibile usare la mano per rappresentare la pressione di un pulsante o la selezione di un ologramma.

Il modello di interazione corrente rappresenta un'ampia gamma di controlli di movimento, ad esempio scorrimento, selezione da lontano e tocco vicino. Di seguito è riportato un elenco completo di esempi di hand-of-hand esistenti:

- Tocco vicino: usato per i pulsanti o per chiudere gli oggetti che possono interagire
- Selezione da lontano: usata per gli oggetti che sono distorsi
- Move: usato per spostare un ologramma nello spazio
- Ruota: usato per mostrare come ruotare ologrammi o oggetti
- Scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli
- Capovolgimento manuale: usato per visualizzare un pannello iniziale dell'interfaccia utente o i menu a mano
- Palm up: usato per l'esperienza di colibrì. Un altro suggerimento potrebbe essere quello di visualizzare un pannello iniziale dell'interfaccia utente
- Scroll: usato per scorrere un elenco o un documento lungo

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella **scena HandCoachExample** in: [MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Mano asset 3D

È possibile trovare gli asset in: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualità

Se si notano distorsioni nella mesh con interfaccia, è necessario assicurarsi che il progetto utilizzi la quantità corretta di giunzioni.
Passare a Edit > Project Impostazioni > Quality > Other > Blend Weights (Modifica > qualità di Unity). Assicurarsi che siano selezionati "4 puntini" per visualizzare Smooth Joints (Giunzioni uniformi).
![Project Impostazione](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Script

### <a name="interaction-hint"></a>Suggerimento per l'interazione

Lo `InteractionHint.cs` script fornisce funzionalità wrapper per l'attivazione di animazioni e dissolvenze per la mano.

#### <a name="how-to-set-up-an-interaction-hint"></a>Come configurare un suggerimento per l'interazione

Per configurare un hint di interazione, è consigliabile usare i prefab "StaticHandCoachRoot_L.prefab" e "StaticHandCoachRoot_R.prefab". Questo prefab contiene lo script InteractionHint e il supporto manuale, nonché la gerarchia appropriata per garantire che le animazioni dei suggerimenti fornite funzionino come previsto.
In caso contrario, dovrai posizionare lo script in un gameObject a un livello padre verso l'alto dal dispositivo mano con l'animatore.

#### <a name="inspector-properties"></a>Proprietà del controllo

- **HideIfHandTracked** Questo valore booleano specifica se lo stato di tracciamento della mano deve essere usato per nascondere gli oggetti visivi quando vengono rilevate le mani di un utente. Se è impostato su false, verrà usata solo la proprietà di scripting "customShouldHideVisuals" per determinare se nascondere l'hint.

- **MinDelay** Questa proprietà specifica il ritardo minimo per la visualizzazione degli oggetti visivi. Per impostazione predefinita, gli oggetti visivi per la mano verranno visualizzati dopo questo numero di secondi se le mani dell'utente non vengono rilevate.

- **MaxDelay** Questa proprietà specifica il ritardo massimo per la visualizzazione degli oggetti visivi. Per impostazione predefinita, gli oggetti visivi per la mano verranno visualizzati dopo questo numero di secondi anche se le mani dell'utente vengono rilevate.

- **UseMaxTimer** Se questo valore booleano è impostato su false, disabilita il timer massimo e consente di visualizzare il suggerimento della mano solo quando le mani dell'utente non sono visualizzate o la condizione personalizzata restituisce false.

- **Ripetizioni** Questa proprietà controlla il numero di volte in cui l'animazione dei suggerimenti viene riprodotta quando viene superato il timer minimo o massimo. L'hint nasconde quindi e attende di nuovo il ritardo.

- **Attivazione automatica** Quando questo valore booleano è impostato su true, l'hint verrà eseguito automaticamente tramite la logica del timer quando il GameObject dello script è attivo nella gerarchia e lo script è abilitato. Questa proprietà deve essere impostata su false solo se si intende controllare manualmente l'aspetto e l'aspetto dei suggerimenti tramite codice.

- **AnimationState** Nome dello stato dell'animazione che deve essere riprodotto quando l'hint è attivo. Questo valore deve essere impostato prima che venga chiamata la funzione StartHintLoop() (durante OnEnable se l'opzione AutoActivate è selezionata).

#### <a name="controlling-interactionhint-via-script"></a>Controllo di InteractionHint tramite script

- **StartHintLoop** Questa funzione avvia il ciclo show/hide che in caso contrario avvia OnEnable se il flag AutoActivate è impostato su true.
- **StopHintLoop** Questa funzione chiama lo stato dell'animazione con dissolvenza in uscita se non è attualmente in riproduzione, quindi disattiva il ciclo show/hide e imposta il dispositivo mano inattivo nella gerarchia.
- **AnimationState** Questa stringa determina quale stato dell'animazione viene riprodotto durante il ciclo. È possibile modificare questa stringa per modificare lo stato riprodotto, ma è necessario farlo dopo aver chiamato StopHintLoop ed è necessario chiamare di nuovo StartHintLoop dopo aver modificato lo stato.
- **CustomShouldHideVisuals** È possibile impostare questa opzione con una funzione personalizzata, che dovrebbe restituire true quando si vogliono nascondere gli oggetti visivi mano (tenere presente MinMaxTimer, in particolare il parametro max)

#### <a name="custom-animation-considerations"></a>Considerazioni sull'animazione personalizzata

Le dissolvenze vengono usate per impostazione predefinita su 0,5 secondi, quindi tutte le animazioni personalizzate create per l'uso con il rig devono avere un valore minimo di 1,5 secondi per la trasmissione di informazioni significative

Gli stati predefiniti di dissolvenza in entrata e in uscita, Fade_In e Fade_Out possono essere modificati modificando il timestamp del secondo fotogramma chiave per impostare la lunghezza della dissolvenza.

L'animatore e lo script sono stati impostati in modo da rendere la configurazione il più semplice possibile. Per aggiungere nuovi stati di animazione, è sufficiente importare fbx, assicurarsi che il nome dell'animazione sia impostato con un nome distinto e trascinare l'animazione nell'animatore.

### <a name="movetotarget"></a>MoveToTarget

Lo script MoveToTarget.cs fornisce funzionalità per spostare l'hint della mano da una posizione di rilevamento a una posizione di destinazione nel tempo.

#### <a name="how-to-set-up-movetotarget"></a>Come configurare MoveToTarget

I prefab "MovingHandCoachRoot_L.prefab" e "MovingHandCoachRoot_R.prefab" forniti contengono moveToTarget nelle gerarchie. Se si vuole usare questo script nella propria configurazione, è necessario posizionarlo nel gameobject radice contenente l'animatore per il dispositivo.

#### <a name="inspector-properties"></a>Proprietà del controllo

- **TrackingObject** Impostarlo con l'oggetto che si vuole che il rig segua prima di avviare il movimento. È consigliabile creare un GameObject vuoto e spostarlo in una posizione specifica per individuare il rilevamento.
- **TargetObject** Imposta questo valore con l'oggetto a cui vuoi che il rig si sposti durante il movimento. È consigliabile creare un GameObject vuoto e spostarlo in una posizione specifica per individuare il rilevamento.
- **RootObject** Impostare questa proprietà su un elemento padre condiviso tra il rilevamento e l'oggetto di destinazione in modo che le posizioni relative possano essere calcolate correttamente. Il prefab incluso include sia oggetti di rilevamento che oggetti di destinazione nella gerarchia, ma è possibile impostare l'oggetto di destinazione come gameObject all'esterno del prefab e modificare l'oggetto radice in un elemento padre condiviso.
- **Durata** Tempo necessario (in secondi) per passare da TrackingObject a TargetObject in secondi.
- **TargetOffset** Offset regolabile per fare in modo che il GameObject arrivi alla posizione di destinazione corretta. Ciò è utile se l'animazione include un offset di posizione durante l'animazione.
- **AnimationCurve** L'impostazione predefinita è una curva lineare, ma è possibile modificare la curva per consentire l'interpolazione all'avvio e all'arresto del percorso di movimento.

#### <a name="controlling-movetotarget-via-script"></a>Controllo di MoveToTarget tramite script

Nello script personalizzato, effettuare una chiamata a Follow() mentre si vuole che il dispositivo mano segua TrackingObject, quindi effettuare una chiamata a MoveToTargetPosition() quando si vuole che il dispositivo di gestione della mano inizi il movimento verso TargetObject.

#### <a name="controlling-movetotarget-via-animations"></a>Controllo di MoveToTarget tramite animazioni

Nell'animazione che deve essere spostata, impostare due eventi: uno con una chiamata a Follow() e uno con una chiamata a MoveToTargetPosition(). Seguire deve essere impostato sul primo fotogramma chiave, perché fa sì che il dispositivo mano segua TrackingObject. MoveToTargetPosition deve essere impostato sul fotogramma chiave in cui si vuole che il rig inizi a passare alla destinazione. Ecco come viene usata la funzionalità di script nei prefab forniti.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

Lo script RotateAroundPoint.cs fornisce funzionalità per ruotare l'hint della mano intorno a un punto pivot nel tempo.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Come configurare RotateAroundPoint

I prefab "RotatingHandCoachRoot_L.prefab" e "RotatingHandCoachRoot_R.prefab" contengono un rotateAroundPoint nelle gerarchie. Se si vuole usare questo script nella propria configurazione, è necessario posizionarlo nel gameobject radice contenente l'animatore per il dispositivo.

#### <a name="inspector-properties"></a>Proprietà del controllo

- **Padre centrato** Impostare questa proprietà con l'oggetto padre che si vuole far spostarsi tra il rig.
- **InverseParent** Impostarla con l'elemento padre per ruotare inversa su centeredParent per mantenere lo stesso orientamento della mano. In generale, si tratta dell'oggetto padre su cui è associato lo script InteractionHint.
- **PivotPosition** Impostare su un punto in cui si vuole che l'hint inizi lo spostamento.
- **Durata** Tempo necessario (in secondi) per ruotare intorno a CenteredParent.
- **AnimationCurve** L'impostazione predefinita è una curva lineare, ma è possibile modificare la curva per consentire l'interpolazione all'avvio e all'arresto del percorso di movimento.
- **RotationVector** Quanti gradi ruotare lungo ogni asse.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Controllo di RotateAroundPoint tramite script

Nello script personalizzato, effettua una chiamata a RotateToTarget() quando vuoi che il maniere inizi la rotazione intorno a CenteredParent. Quando si vuole ripristinare la posizione originale di PivotPosition, effettuare una chiamata a ResetAndDeterminePivot().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controllo di RotateAroundPoint tramite animazioni

Nell'animazione che deve essere spostata, impostare due eventi: uno con una chiamata a ResetAndDeterminePivot() e uno con una chiamata a RotateToTarget(). ResetAndDeterminePivot deve essere impostato sul primo fotogramma chiave, perché fa sì che il rig manuale riposiziona l'oggetto PivotPosition. RotateToTarget deve essere impostato sul fotogramma chiave in cui si vuole che il rig inizi a ruotare intorno a CenteredParent. Questa è la modalità di utilizzo della funzionalità script nei prefab forniti.
