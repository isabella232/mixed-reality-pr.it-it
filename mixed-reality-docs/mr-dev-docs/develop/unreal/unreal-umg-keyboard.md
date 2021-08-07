---
title: UMG e tastiera in Unreal
description: Informazioni su come usare Unrealm Motion Graphics per creare un sistema di interfaccia utente nei widget.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, HoloLens 2, tracciamento oculare, input dello sguardo fisso, display montato sulla testa, motore Unreal, visore di realtà mista, visore windows di realtà mista, visore di realtà virtuale, widget, INTERFACCIA UTENTE, UMG, Unreal Motion Graphics, Unreal Engine, UE, UE4
ms.openlocfilehash: 8cb1c804757332ce7b78f0cb92cf895b873c1835208962b20d5bbbfae4684785
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212842"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG e tastiera in Unreal

Unreal Motion Graphics (UMG) è il sistema di interfaccia utente predefinito del motore Unreal, usato per creare interfacce come menu e caselle di testo. Le interfacce utente compilate con UMG sono costituite da widget. Verrà illustrato come creare un nuovo widget, aggiungerlo allo spazio mondiale e abilitare l'interazione usando la tastiera di sistema come esempio. Per altre informazioni su UMG, vedere la documentazione ufficiale di Unreal [Engine.](https://docs.unrealengine.com/en-US/Engine/UMG/index.html) 

## <a name="create-a-new-widget"></a>Creare un nuovo widget

- Creare un progetto widget per creare il provisioning dell'interfaccia utente del gioco:

![Screenshot dell'aggiunta di un progetto widget dal menu Unreal](images/unreal-umg-img-01.png)

- Aprire il nuovo progetto e aggiungere componenti dalla tavolozza all'area di disegno.  In questo caso, sono stati aggiunti due componenti Casella di testo dalla sezione "Input":

![Screenshot della finestra della gerarchia con il componente widget di testo evidenziato ed espanso](images/unreal-umg-img-02.png)

- Selezionare un widget nella finestra Gerarchia o Finestra di progettazione e modificare i parametri nel pannello dei dettagli.  In questo caso, sono stati aggiunti un "Testo suggerimento" predefinito e un colore della tinta che viene visualizzato quando si passa il mouse sulla casella di testo.  Una casella di testo verrà visualizzata una tastiera virtuale HoloLens quando viene interagita con:

![Screenshot dei parametri modificati nella finestra della gerarchia](images/unreal-umg-img-03.png)

- Gli eventi possono essere sottoscritti anche nel pannello dei dettagli:

![Screenshot degli eventi nel pannello dei dettagli](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Aggiungere un widget allo spazio mondiale

- Creare un nuovo attore, aggiungere un componente Widget e aggiungere l'attore alla scena:

![Screenshot di un attore con un widget allegato](images/unreal-umg-img-05.png)

- Nel pannello dei dettagli del widget impostare Classe **widget** sul progetto widget creato in precedenza:

![Screenshot del pannello dei dettagli del progetto con la classe widget impostata](images/unreal-umg-img-06.png)

- Per un widget di testo, assicurarsi che l'opzione Receive Hardware Input (Ricezione **input hardware)** sia deselezionata, quindi il testo viene aggiornato solo dalla tastiera virtuale:

![Screenshot della sezione di interazione con l'input hardware di ricezione deselezionato](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interazione con i widget

I widget UMG ricevono in genere l'input da un mouse.  In HoloLens vr, è necessario simulare un mouse con un componente Interazione widget per ottenere gli stessi eventi.

- Creare un nuovo attore, aggiungere un **componente Interazione widget** e aggiungere l'attore alla scena:

![Screenshot di un nuovo attore con un componente di interazione del widget evidenziato](images/unreal-umg-img-08.png)

- Nel pannello dei dettagli per il componente Interazione widget:
    - Impostare la distanza di interazione sul valore di distanza desiderato
    - Impostare **l'origine interazione** su **personalizzata**
    - Per lo sviluppo, impostare **Mostra debug** su **true**:

![Screenshot delle proprietà del componente interazione e debug del widget](images/unreal-umg-img-09.png)

L'impostazione predefinita per Origine interazione è "World", che deve inviare raycast in base alla posizione del componente Interazione widget. In AR e VR, questo non è il caso.  L'abilitazione di "Mostra debug" e l'aggiunta di una tinta al passaggio del mouse ai widget è importante per controllare che il componente di interazione del widget stia eseguendo le attività previste.  La soluzione alternativa consiste nell'usare un'origine personalizzata e impostare il raycast nel grafico degli eventi dal raggio della mano.  

Di seguito viene chiamato questo oggetto dal tick dell'evento:

![Progetto del tick dell'evento](images/unreal-umg-img-10.png)

Aggiungere quindi eventi virtuali del puntatore del mouse al componente di interazione del widget che reagisce HoloLens input.  In questo caso, inviare un evento di pressione del mouse sinistro quando viene afferrata la mano e un evento di rilascio del mouse sinistro se non afferrato:

![Progetto con eventi del puntatore del mouse virtuali aggiunti](images/unreal-umg-img-13.png)

Ora, quando si distribuisce l'app nel HoloLens 2, verrà visualizzato un raggio della mano che si estende dalla mano destra. Se la si indirizza a una delle caselle di testo modificabili e si tocca l'aria, la tastiera di sistema verrà visualizzata davanti all'utente e consentirà di immettere testo. 
 
> [!NOTE]
> La HoloLens di sistema richiede Unreal Engine 4.26 o versione successiva. Inoltre, la tastiera non verrà visualizzata quando l'app viene trasmessa dall'editor Unreal al visore, solo quando l'app è in esecuzione nel dispositivo.

## <a name="see-also"></a>Vedere anche:
* [Documentazione umg di Unreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Esercitazioni su UMG di Unreal](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
