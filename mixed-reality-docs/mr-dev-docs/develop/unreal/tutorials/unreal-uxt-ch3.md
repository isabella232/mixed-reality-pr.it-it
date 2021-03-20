---
title: 3. Configurazione del progetto per la realtà mista
description: Parte 3 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609702"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configurazione del progetto per la realtà mista

Nell'esercitazione precedente ti sei dedicato alla configurazione del progetto dell'app di scacchi. In questa sezione viene illustrato come configurare l'app per lo sviluppo in realtà mista, ovvero aggiungendo una sessione AR. Per questa attività si userà un asset di dati ARSessionConfig che include impostazioni AR utili come il mapping spaziale e l'occlusione. Nella documentazione di Unreal sono disponibili altre informazioni dettagliate sull'asset [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e la classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).

## <a name="objectives"></a>Obiettivi

* Uso delle impostazioni AR di Unreal Engine
* Uso di un asset di dati ARSessionConfig
* Configurazione di un pedone e modalità di gioco

## <a name="adding-the-session-asset"></a>Aggiunta dell'asset della sessione

Le sessioni AR in Unreal non funzionano da sole. Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:

1. Fai clic su **Add New > Miscellaneous > Data Asset** (Aggiungi nuovo > Varie > Asset dati) in **Content Browser** (Browser contenuto). Assicurati di essere nella cartella **Content** radice.
    * Seleziona **ARSessionConfig**, fai clic su **Select** (Seleziona) e assegna all'asset il nome **ARSessionConfig**.

![Creazione di un'origine dati](images/unreal-uxt/3-createasset.PNG)

3. Fai doppio clic su **ARSessionConfig** per aprirlo, lascia tutte le impostazioni predefinite e premi **Save** (Salva). Torna alla finestra principale.

![ARSessionConfig](images/unreal-uxt/3-arsessionconfig.PNG)

Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina. In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello. La connessione dell'asset ARSessionConfig in **Level Blueprint** (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.

1. Fai clic su **Blueprints > Open Level Blueprint** (Progetti > Apri progetto livello) sulla barra degli strumenti dell'editor:

![Open Level Blueprint (Apri progetto livello)](images/unreal-uxt/3-level-blueprint.PNG)

5. Trascinare il nodo esecuzione (icona a forma di freccia rivolta verso sinistra) da **evento BeginPlay** e rilasciare, quindi cercare il nodo **Start AR Session** (Avvia sessione AR) e premere INVIO.  
    * Fai clic sull'elenco a discesa **Select Asset** (Seleziona asset) in **Session Config** (Configurazione sessione) e scegli l'asset **ARSessionConfig**.

![Start AR Session (Avvia sessione AR)](images/unreal-uxt/3-start-ar-session.PNG)

6. Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**. Trascinare il pin di esecuzione e rilasciare, quindi cercare un nodo **Stop AR Session** (Arresta sessione AR) e premere INVIO. Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.
    * Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.

![Stop AR Session (Arresta sessione AR)](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Creare un pedone

A questo punto, il progetto necessita ancora di un oggetto Player. In Unreal, l'oggetto **Pawn** (Pedone) rappresenta l'utente del gioco, ma in questo caso sarà l'esperienza HoloLens 2.

1. Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** ed espandi la sezione **All Classes** (Tutte le classi) in fondo.
    * Cercare **DefaultPawn**, fare clic su **Select** (Seleziona), assegnare il nome **MRPawn** e fare doppio clic sull'asset per aprirlo.

![Creare un nuovo pedone basato su DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2. Fare clic su **Add Component > Camera** (Aggiungi componente > Fotocamera) nel pannello **Components** (Componenti) e assegnare all'elemento il nome **Camera** (Fotocamera). Verificare che il componente **Camera** sia un figlio diretto della radice (**CollisionComponent**). In tal modo, la fotocamera del giocatore si muoverà insieme al dispositivo HoloLens 2.

> [!NOTE]
> Per impostazione predefinita, i pedoni hanno componenti mesh e collisione. Nella maggior parte dei progetti Unreal, i pedoni sono oggetti solidi che possono collidere con altri componenti. Dato che il pedone e l'utente coincidono nella realtà mista, è necessario poter passare attraverso gli ologrammi senza collisioni.

3. Seleziona **CollisionComponent** nel pannello **Components** (Componenti) e scorri fino alla sezione **Collision** (Collisione) del pannello **Details** (Dettagli).
    * Fai clic sull'elenco a discesa **Collision Presets** (Set di impostazioni di collisione) e cambia il valore in **NoCollision**.
    * Eseguire la stessa operazione per **MeshComponent**.

![Modifica dei set di impostazioni di collisione del pedone](images/unreal-uxt/3-nocollision.PNG)

4. Fare clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto.

Al termine, torna alla finestra principale.

## <a name="create-a-game-mode"></a>Crea una modalità di gioco

Per completare la configurazione della realtà mista manca solo la modalità di gioco. La modalità di gioco determina una serie di impostazioni relative al gioco o all'esperienza, incluso il pedone predefinito da usare.

1.  Fare clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** (Contenuto) e selezionare **Game Mode Base** (Base modalità gioco) come classe padre. Denominarla **MRGameMode** e fare doppio clic per aprirla.

![MRGameMode nel browser dei contenuti](images/unreal-uxt/3-gamemode.PNG)

2.  Passa alla sezione **Classes** (Classi) nel pannello **Details** (Dettagli) e modifica **Default Pawn Class** (Classe pedone predefinito) in **MRPawn**.
    * Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.

![Impostazione della classe di pedone predefinita](images/unreal-uxt/3-setpawn.PNG)

3.  Seleziona **Edit > Projects Settings** (Modifica > Impostazioni progetti) e fai clic su **Maps & Modes** (Mappe e modalità) nell'elenco a sinistra.
    * Espandi **Default Modes** (Modalità predefinite) e cambia **Default Game Mode** (Modalità gioco predefinita) in **MRGameMode**.
    * Espandi **Default Maps** (Mappe predefinite) e imposta sia **EditorStartupMap** sia **GameDefaultMap** su **Main** (Principale). Quando si chiude e si riapre l'editor o si usa il gioco, per impostazione predefinita viene selezionata la mappa principale.

![Project Settings - Maps & Modes (Impostazioni progetto - Mappe e modalità)](images/unreal-uxt/3-mapsandmodes.PNG)

Dopo aver completato la configurazione del progetto per la realtà mista, è possibile passare all'esercitazione successiva e iniziare ad aggiungere input utente alla scena.

[Sezione successiva: 4. Rendere la scena interattiva](unreal-uxt-ch4.md)
