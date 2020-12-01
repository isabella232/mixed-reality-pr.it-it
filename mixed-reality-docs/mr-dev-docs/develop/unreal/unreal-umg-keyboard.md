---
title: UMG e tastiera in Unreal
description: Informazioni su come usare i grafici di movimento di Unreal per creare un sistema di interfaccia utente all'esterno dei widget.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, widget, interfaccia utente, UMG, grafica di movimento non reale, Unreal Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355409"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG e tastiera in Unreal

Unreal Motion Graphics (UMG) è il sistema di interfaccia utente incorporato del motore di Unreal, usato per creare interfacce quali menu e caselle di testo. Le interfacce utente compilate con UMG sono costituite da widget. In questa guida viene illustrato come creare un nuovo widget, aggiungerlo allo spazio globale e abilitare l'interazione con tale widget in realtà mista, usando la tastiera di sistema come esempio. Per altre informazioni su UMG, vedere la [documentazione](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)ufficiale di Unreal Engine. 

## <a name="create-a-new-widget"></a>Creare un nuovo widget

- Creare un progetto widget per il layout dell'interfaccia utente del gioco:

![Screenshot dell'aggiunta di un progetto widget dal menu Unreal](images/unreal-umg-img-01.png)

- Aprire il nuovo progetto e aggiungere componenti dalla tavolozza all'area di disegno.  In questo caso sono stati aggiunti due componenti della casella di testo dalla sezione "input":

![Screenshot della finestra della gerarchia con componente del widget di testo evidenziato ed espanso](images/unreal-umg-img-02.png)

- Selezionare un widget nella gerarchia o nella finestra di progettazione e modificare i parametri nel pannello dei dettagli.  In questo caso, è stato aggiunto un "testo suggerimento" predefinito e un colore tinta quando il cursore è posizionato sulla casella di testo per fornire commenti e suggerimenti su cui il widget è pronto per l'interazione.  In una casella di testo viene visualizzata una tastiera virtuale in HoloLens quando viene interagito con:

![Screenshot dei parametri modificati nella finestra gerarchia](images/unreal-umg-img-03.png)

- È anche possibile sottoscrivere gli eventi nel pannello dei dettagli:

![Screenshot degli eventi nel pannello dei dettagli](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Aggiungere un widget allo spazio globale

- Creare un nuovo attore, aggiungere un componente widget e aggiungere l'attore alla scena:

![Screenshot di un attore con un widget collegato](images/unreal-umg-img-05.png)

- Nel pannello dei dettagli per il widget impostare la **classe Widget** sul progetto widget creato in precedenza:

![Screenshot del pannello Dettagli progetto con la classe Widget impostata](images/unreal-umg-img-06.png)

- Per un widget di testo, verificare che la **ricezione dell'input hardware** sia deselezionata, in modo da aggiornare solo il testo dalla tastiera virtuale:

![Screenshot della sezione interazione con l'input hardware di ricezione non selezionata](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interazione widget

I widget UMG ricevono in genere l'input da un mouse.  In HoloLens o VR è necessario simulare un mouse con un componente di interazione widget per ottenere gli stessi eventi.

- Creare un nuovo attore, aggiungere un componente di **interazione widget** e aggiungere l'attore alla scena:

![Screenshot di un nuovo attore con un componente di interazione widget evidenziato](images/unreal-umg-img-08.png)

- Nel pannello dei dettagli per il componente interazione widget impostare la distanza di interazione sulla distanza desiderata, impostare l' **origine interazione** su **personalizzata** e per lo sviluppo impostare **Mostra debug** su **true**:

![Screenshot delle proprietà del componente interazione e debug del widget](images/unreal-umg-img-09.png)

Il valore predefinito per l'origine interazione è "World", che deve inviare raycasts in base alla posizione globale del componente di interazione del widget, ma in AR e VR questa situazione non sembra essere la stessa.  L'abilitazione di "Mostra debug" e l'aggiunta di una tinta del passaggio del mouse ai widget durante lo sviluppo è importante per verificare la correttezza del componente interazione widget.  La soluzione alternativa consiste nell'usare un'origine personalizzata e impostare Raycast nel grafico eventi dal raggio della mano.  

Qui viene chiamato il simbolo di evento:

![Progetto del segno di evento](images/unreal-umg-img-10.png)

Aggiungere quindi gli eventi del puntatore del mouse virtuale al componente di interazione del widget che reagisce all'input HoloLens.  In questo caso, inviare un evento di pressione del mouse sinistro quando la mano viene afferrata e un evento di rilascio del mouse a sinistra quando non viene afferrato:

![Progetto con eventi di puntatore del mouse virtuale aggiunti](images/unreal-umg-img-13.png)

A questo punto, quando si distribuisce l'app in HoloLens 2, verrà visualizzato un raggio a mano che si estende da destra. Se viene indirizzato a una delle caselle di testo modificabili e al tocco aereo, la tastiera di sistema viene visualizzata davanti all'utente e consente di immettere il testo. 
 
> [!NOTE]
> La tastiera di sistema HoloLens richiede Unreal Engine 4,26 o versione successiva. Inoltre, la tastiera non verrà visualizzata quando l'app viene trasmessa da un editor non reale all'auricolare, solo quando l'app è in esecuzione nel dispositivo.

## <a name="see-also"></a>Vedere anche:
* [Documentazione di UMG di Unreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Esercitazioni di UMG di Unreal](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
