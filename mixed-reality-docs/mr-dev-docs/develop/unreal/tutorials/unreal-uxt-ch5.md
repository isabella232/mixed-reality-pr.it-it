---
title: 5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi
description: Parte 5 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609692"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi

Nell'esercitazione precedente hai aggiunto attori di interazione manuale al pedone e componenti manipolatore alla scacchiera per renderli entrambi interattivi. In questa sezione si continuerà a usare il plug-in UX Tools di Mixed Reality Toolkit per creare l'app per gli scacchi con le nuove funzioni e i riferimenti agli attori nei progetti. Al termine di questa sezione sarai in grado di creare un pacchetto dell'app di realtà mista e distribuirla in un dispositivo o emulatore.

## <a name="objectives"></a>Obiettivi

* Aggiunta di un pulsante interattivo
* Creazione di una funzione per la riportare un pezzo nella posizione iniziale
* Associazione del pulsante in modo che attivi la funzione quando viene premuto

## <a name="creating-a-reset-function"></a>Creazione di una funzione di reimpostazione

La prima attività consiste nel creare un progetto di funzione che riporta un pezzo degli scacchi nella sua posizione originale nella scena.

1.  Aprire **WhiteKing** (Re bianco), selezionare l'icona **+** accanto alla sezione **Functions** (Funzioni) in **My Blueprint** (Progetto personale) e assegnare alla funzione il nome **Reset Location** (Ripristina posizione).

2.  Trascina e rilascia l'esecuzione da **Reset Location** (Ripristina posizione) nella griglia del progetto per creare un nodo **SetActorRelativeTransform**.
    * Questa funzione imposta la trasformazione (posizione, rotazione e scala) di un attore rispetto al relativo elemento padre. Questa funzione verrà usata per ripristinare la posizione del Re sulla scacchiera, anche se è stata spostata dalla posizione originale.

3. Fai clic con il pulsante destro del mouse all'interno di Event Graph (Grafico eventi), scegli **Make Transform** (Crea trasformazione) e imposta **Location** (Posizione) su **X = -26**, **Y = 4**, **Z = 0**.
    * Connetti il relativo **Return Value** (Valore restituito) al segnaposto **New Relative Transform** (Nuova trasformazione relativa) in **SetActorRelativeTransform**.

![Funzione di ripristino della posizione](images/unreal-uxt/5-function.PNG)

Scegli **Compile** (Compila) e **Save** (Salva) per compilare e salvare il progetto prima di tornare alla finestra princpale.


## <a name="adding-a-button"></a>Aggiunta di un pulsante

Ora che la funzione è stata configurata correttamente, l'attività successiva consiste nel creare un pulsante che la attiva quando viene toccato.

1.  Fare clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto), espandere la sezione **All Classes** (Tutte le classi) e cercare **UxtPressableButtonActor**.
    * Assegna il nome **ResetButton** e fai doppio clic per aprire il progetto.

![Creare il nuovo progetto come sottoclasse del pulsante di stile HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. Verificare che sia selezionata l'opzione **ResetButton(self)** nel pannello **Components** (Componenti). Nel pannello **Details** (Dettagli) passare alla sezione **Button** (Pulsante). Cambiare il valore predefinito di **Button Label** (Etichetta pulsante) in "Reset" (Ripristina), espandere la sezione **Button Icon Brush** (Pennello icona pulsante) e selezionare il pulsante **Open Icon Brush Editor** (Apri Icon Brush Editor).

![Impostare l'etichetta e l'icona sul pulsante](images/unreal-uxt/5-buttonconfig.PNG)

Si aprirà Icon Brush Editor, che può essere usato per selezionare una nuova icona per il pulsante.

![Selezionare un'icona per il pulsante](images/unreal-uxt/5-iconbrusheditor.PNG)

È possibile modificare molte altre impostazioni per configurare il pulsante. Per altre informazioni sul componente UXT Pressable Button, vedere la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).

3. Fare clic su **ButtonComponent (Inherited)** (ButtonComponent - Ereditato) nel pannello **Components** (Componenti) e scorrere verso il basso nel pannello **Details** (Dettagli) fino alla sezione **Events** (Eventi).
    * Fai clic sul pulsante **+** verde accanto a **On Button Pressed** (Alla pressione del pulsante) per aggiungere un evento al grafico degli eventi, che verrà chiamato ogni volta che viene premuto il pulsante.

A questo punto puoi chiamare la funzione **Reset Location** (Ripristina posizione) di **WhiteKing** (Re bianco), che necessita un riferimento all'attore **WhiteKing** (Re bianco) nel livello.

4.  Nel pannello **My Blueprint** (Progetto personale) passare alla sezione **Variables** (Variabili), fare clic sul pulsante **+** e assegnare alla variabile il nome **WhiteKing**.
    * Nel pannello **Details** (Dettagli) selezionare l'elenco a discesa accanto a **Variable Type** (Tipo di variabile), cercare **WhiteKing** e selezionare **Object Reference** (Riferimento oggetto).
    * Selezionare la casella accanto a **Instance Editable** (Modificabile dell'istanza), che consente di impostare la variabile dal livello principale.

![Creazione di una variabile](images/unreal-uxt/5-var.PNG)

5.  Trascina la variabile WhiteKing da **My Blueprint > Variables** (Progetto personale > Variabili) in Reset Button Event Graph (Grafico eventi ResetButton) e scegli **Get WhiteKing** (Ottieni WhiteKing).

## <a name="firing-the-function"></a>Attivazione della funzione

A questo punto non resta che attivare la funzione di reimpostazione alla pressione del pulsante.

1.  Trascina il pin di output di WhiteKing e rilascialo per inserire un nuovo nodo. Seleziona la funzione **Reset Location** (Ripristina posizione). Trascina infine il pin di esecuzione in uscita da **On Button Pressed** (Alla pressione del pulsante) al pin di esecuzione in ingresso in **Reset Location** (Ripristina posizione). Fai clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto ResetButton e quindi torna alla finestra principale.

![Chiamata della funzione di ripristino della posizione alla pressione del pulsante](images/unreal-uxt/5-callresetloc.PNG)

2.  Trascina **ResetButton** nel viewport e impostane la posizione su **X = 50**, **Y = -25** e **Z = 10**. Impostarne la rotazione su **Z = 180**. In **Default** (Valore predefinito) imposta il valore della variabile **WhiteKing** su **WhiteKing**.

![Impostazione della variabile](images/unreal-uxt/5-buttonlevel.PNG)

Eseguire l'app, spostare il pezzo in una nuova posizione e premere il pulsante di stile HoloLens 2 per vedere in azione la logica di reimpostazione.

A questo punto si ha un'app di realtà mista con un pezzo degli scacchi interattivo e una scacchiera, insieme a un pulsante completamente funzionante che ripristina la posizione del pezzo. L'app completata fino a questo punto è disponibile nel repository di [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) corrispondente. Al termine di questa esercitazione è possibile proseguire configurando gli altri pezzi degli scacchi, in modo da ripristinare l'intera scacchiera quando si preme il pulsante per il ripristino.

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

È ora possibile passare alla sezione finale di questa esercitazione, in cui viene illustrato come creare un pacchetto dell'app e distribuirla in un dispositivo o emulatore.

> [!IMPORTANT]
> A questo punto è consigliabile aggiornare il progetto con le **[Impostazioni per le prestazioni di Unreal](../performance-recommendations-for-unreal.md)** consigliate prima di distribuire l'applicazione in un dispositivo o emulatore.

[Sezione successiva: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore](unreal-uxt-ch6.md)
