---
title: HoloLens (prima generazione) e Azure 301 - Traduzione in lingua
description: Completare questo corso per informazioni su come implementare l'API Azure Translator Text all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realtà mista, academy, unity, esercitazione, api, traduzione testuale, hololens, immersive, vr, traduzione linguistica, Windows 10, Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229591"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (prima generazione) e Azure 301: traduzione in lingua

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

In questo corso si apprenderà come aggiungere funzionalità di traduzione a un'applicazione di realtà mista usando Servizi cognitivi di Azure, con l'API Translator testo.

![Prodotto finale](images/AzureLabs-Lab1-00.png)

L Translator API Text è un servizio di traduzione che funziona in near real-time. Il servizio è basato sul cloud e, usando una chiamata API REST, un'app può usare la tecnologia di traduzione automatica neurale per tradurre il testo in un'altra lingua. Per altre informazioni, visitare la pagina [dell'API Translator Text di Azure.](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  L'utente parla in un microfono connesso a un visore VR immersive (o al microfono incorporato di HoloLens).
2.  L'app acquisisce la dettatura e la invia all'API Azure Translator Text.
3.  Il risultato della traduzione verrà visualizzato in un semplice gruppo di interfaccia utente nella scena Unity.

Questo corso illustra come ottenere i risultati dal servizio Translator in un'applicazione di esempio basata su Unity. L'utente dovrà applicare questi concetti a un'applicazione personalizzata che potrebbe essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 301: Traduzione</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in particolare in Windows Mixed Reality visori VR immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note sulle eventuali modifiche che potrebbe essere necessario applicare per supportare HoloLens. Quando si usa HoloLens, è possibile notare un'eco durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Unity e C#. Tenere presente anche che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (maggio 2018). È possibile usare il software più recente, come indicato nell'articolo Installare gli strumenti, anche se non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto elencato di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con le Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori VR immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [visore VR o](../../../discover/immersive-headset-hardware-details.md) un visore [Microsoft HoloLens](/hololens/hololens1-hardware) VR Windows Mixed Reality con la modalità sviluppatore abilitata
- Un set di cuffi con un microfono predefinito (se il visore VR non ha un microfono e altoparlanti predefiniti)
- Accesso a Internet per la configurazione di Azure e il recupero della traduzione

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare di riscontrare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o vicina alla radice (i percorsi di cartelle lunghi possono causare problemi in fase di compilazione).
- Il codice di questa esercitazione consente di registrare dal dispositivo microfono predefinito connesso al PC. Assicurarsi che il dispositivo microfono predefinito sia impostato sul dispositivo che si prevede di usare per acquisire la voce.
- Per consentire al PC di abilitare la dettatura, passare **Impostazioni > Privacy > Speech(Privacy > Speech),** digitare & input penna e selezionare il pulsante **Turn On speech services** and typing suggestions (Attiva servizi voce e suggerimenti).
- Se si usano un microfono e le cuffi connessa al visore VR (o a cui è integrato), assicurarsi che l'opzione "Quando indossi il visore VR, passa al microfono del visore VR" sia attivata in **Impostazioni > Mixed reality > Audio e voce.**

   ![Impostazioni di realtà mista](images/AzureLabs-Lab1-00-5.png)

   ![Impostazione microfono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Tenere presente che se si sviluppa per un visore VR immersive per questo lab, è possibile che si verifichino problemi del dispositivo di output audio. Ciò è dovuto a un problema con Unity, risolto nelle versioni successive di Unity (Unity 2018.2). Il problema impedisce a Unity di modificare il dispositivo di output audio predefinito in fase di esecuzione. Per risolvere il problema, assicurarsi di aver completato i passaggi precedenti e di chiudere e ria aprire nuovamente l'editor, quando questo problema si presenta.

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: Portale di Azure

Per usare l'API Translator Azure, è necessario configurare un'istanza del servizio in modo che sia resa disponibile per l'applicazione.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si ha già un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei protori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare "TRANSLATOR TEXT API". Premere **INVIO**.

    ![Nuova risorsa](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita **con Crea una risorsa** nei portali più nuovi.

3.  La nuova pagina fornirà una descrizione del servizio *API Translator testo.* Nella parte inferiore sinistra di questa pagina selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![Creare un Translator API Text](images/AzureLabs-Lab1-03.png)

4.  Dopo aver fatto clic su **Crea:**

    1. Inserire il nome **desiderato per** questa istanza del servizio.
    2. Selezionare una sottoscrizione **appropriata.**
    3. Selezionare il **piano tariffario** appropriato. Se è la prima volta che si crea un servizio di testo *di Translator,* dovrebbe essere disponibile un livello gratuito (denominato F0).
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo sui gruppi di risorse.](/azure/azure-resource-manager/resource-group-portal)

    5. Determinare **la località** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione sarebbe idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.
    6. È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.
    7. Selezionare **Crea**.

        ![Selezionare il pulsante Crea.](images/AzureLabs-Lab1-04.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.
6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica. 

    ![Notifica di creazione del servizio di Azure](images/AzureLabs-Lab1-05.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Passare al popup della risorsa.](images/AzureLabs-Lab1-06.png)

8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio API Translator testo. 

    ![Translator Pagina del servizio API Testo](images/AzureLabs-Lab1-07.png)

9.  In questa esercitazione l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita tramite la chiave di sottoscrizione del servizio. 
10. Dalla  pagina Avvio rapido del servizio di testo *Translator* passare al primo *passaggio,* Afferrare le chiavi e fare clic su **Chiavi.** A tale scopo, è anche possibile fare clic sul collegamento ipertestuale blu Chiavi, che si trova nel menu di spostamento Servizi, con l'icona a forma di chiave. Verranno così rivelate le chiavi *del servizio*.
11. Prendere una copia di una delle chiavi visualizzate, che sarà necessaria più avanti nel progetto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: Configurare il progetto Unity

Configurare e testare il visore VR immersive di realtà mista.

> [!NOTE]
> Per questo corso non sono necessari controller del movimento. Se è necessario supporto per la configurazione di un visore VR immersive, [seguire questa procedura.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, è un buon modello per altri progetti:

1.  Aprire *Unity e* fare clic su New **(Nuovo).** 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab1-08.png)

2.  È ora necessario specificare un nome Project Unity. Inserire **MR_Translation**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Il *percorso su* un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica > preferenze** e quindi dalla nuova finestra passare a Strumenti **esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Aggiornare le preferenze dell'editor di script.](images/AzureLabs-Lab1-10.png)

4.  Passare quindi a **File > Build Impostazioni** e impostare la piattaforma su Universal Windows **Platform** facendo clic sul pulsante **Switch Platform** (Cambia piattaforma).

    ![Compilare Impostazioni finestra, passare dalla piattaforma alla piattaforma UWP.](images/AzureLabs-Lab1-11.png)

5.  Passare a **File > Build Impostazioni** (Compilazione file) e assicurarsi che:

    1. **Dispositivo di destinazione** è impostato su **Qualsiasi dispositivo.**

        > Per Microsoft HoloLens, impostare **Dispositivo di destinazione** *su HoloLens*.

    2. **Il tipo di** compilazione è impostato **su D3D**
    3. **L'SDK** è impostato su **Più recente installato**
    4. **Visual Studio versione è** impostata su **Versione più recente installata**
    5. **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab1-12.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

            ![Creare una nuova cartella di script](images/AzureLabs-Lab1-13.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file*: digitare **MR_TranslationScene** e quindi fare clic su **Salva.**

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab1-14.png)

            > Tenere presente che è necessario salvare le scene di Unity all'interno *della cartella Assets,* perché devono essere associate al Project Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7. Le impostazioni rimanenti, in *Build Impostazioni*, per il momento devono essere lasciato come predefinite.

6. Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova *il controllo.* 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab1-15.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1. **La versione del runtime di** scripting deve essere **Stabile** (equivalente a .NET 3.5).
        2. **Il back-end di** scripting deve **essere .NET**
        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab1-16.png)
      
    2. **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab1-17.png)

    3. Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Aggiornare il Impostazioni X R.](images/AzureLabs-Lab1-18.png)

8.  Tornando alla **compilazione Impostazioni**, i *progetti C# Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).
10. Salvare la scena e Project **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3: Configurazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il [](https://docs.unity3d.com/Manual/AssetPackages.html)codice, è possibile scaricare questo file con estensione [unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [5.](#chapter-5--create-the-results-class) Sarà comunque necessario creare un'istanza di Unity Project.

1.  Nel pannello *Hierarchy (Gerarchia)* è presente un oggetto denominato **Main Camera**(Fotocamera principale), che rappresenta il punto di vista "head" quando ci si trova "all'interno" dell'applicazione.
2.  Con il dashboard di Unity davanti all'utente, selezionare Main Camera GameObject ( **GameObject della fotocamera principale).** Si noterà che il pannello inspector *(in* genere disponibile a destra, all'interno del dashboard) mostrerà i vari componenti di *tale GameObject,* con *Transform* nella parte superiore, seguito da *Camera* e da altri componenti. Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionata correttamente.
3.  A tale scopo, selezionare **l'icona** a forma di ingranaggio accanto al componente *Transform (Trasforma)* della fotocamera e selezionare **Reset (Reimposta).** 

    ![Reimpostare la trasformazione Fotocamera principale.](images/AzureLabs-Lab1-19.png)
 
4.  Il *componente Transform* dovrebbe quindi essere simile al seguente:

    1. La *posizione* è impostata su **0, 0, 0**
    2. *La* rotazione è impostata **su 0, 0, 0**
    3. La *scalabilità* è impostata **su 1, 1, 1**

        ![Informazioni di trasformazione per Camera](images/AzureLabs-Lab1-20.png)

5.  Successivamente, con **l'oggetto Main Camera** selezionato, vedi il pulsante Add **Component** (Aggiungi componente) nella parte inferiore di Inspector *Panel (Pannello di controllo).* 
6.  Selezionare il pulsante e cercare il componente Audio Source (Origine audio) digitando *Audio Source* (Origine audio) nel campo di ricerca o esplorando le sezioni, per il componente denominato Audio Source (Origine **audio),** come illustrato di seguito, e selezionarlo (è anche possibile premere INVIO).
7.  Un *componente Audio Source* (Origine audio) verrà aggiunto alla fotocamera **principale,** come illustrato di seguito.

    ![Aggiungere un componente Origine audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Per Microsoft HoloLens, sarà necessario modificare anche quanto segue, che fanno parte del componente **Fotocamera** nella **fotocamera principale:**
    > - **Cancella flag:** Colore a tinta unita.
    > - **Sfondo** 'Black, Alpha 0': colore esadecimale: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capitolo 4: Configurare l'area di disegno di debug

Per visualizzare l'input e l'output della traduzione, è necessario creare un'interfaccia utente di base. Per questo corso si creerà un oggetto canvas dell'interfaccia utente, con diversi oggetti 'Text' per visualizzare i dati.

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *pannello Gerarchia*, nell'interfaccia **utente** aggiungere un oggetto **Canvas.**

    ![Aggiungere un nuovo oggetto canvas dell'interfaccia utente.](images/AzureLabs-Lab1-22.png)

2.  Con l'oggetto Canvas selezionato, nel pannello *inspector* (all'interno del componente "Canvas") modifica **Modalità di** rendering in World **Space (Spazio mondo).** 
3.  Modificare quindi i parametri seguenti nella trasformazione Rect del *pannello di controllo:*

    1. *POS*  -   **X** 0 **Y** 0 **Z** 40
    2. *Larghezza* - 500
    3. *Altezza* - 300
    4. *Scalabilità*  -  **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Aggiornare la trasformazione del rettificato per l'area di disegno.](images/AzureLabs-Lab1-23.png)
 
4.  Fare clic con il pulsante **destro del mouse** sull'area di disegno nel pannello *Gerarchia*, **in Interfaccia utente** e aggiungere un elemento **Panel**. Questo **pannello** fornirà uno sfondo al testo che verrà visualizzato nella scena.
5.  Fare clic con il pulsante **destro del** mouse su Panel (Pannello) nel pannello *Hierarchy (Gerarchia),* **in UI (Interfaccia utente)** e aggiungere un **oggetto Text**. Ripetere lo stesso processo fino a quando non sono stati creati quattro oggetti Text dell'interfaccia utente in totale (suggerimento: se è stato selezionato il primo oggetto 'Text', è sufficiente premere **'CTRL' + 'D'** per duplicarlo, fino a quando non ne sono presenti quattro in totale). 
6.  Per ogni **oggetto di testo,** selezionarlo e usare le tabelle seguenti per impostare i parametri nel *pannello inspector.*

    1. Per il *componente Rect Transform (Trasformazione* rect):

        | Nome                   | Transform - *Position*             | Larghezza      | Altezza    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | Etichetta di dettatura         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Per il **componente Testo (script):**


        | Nome                   | Testo               | Dimensione carattere    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Stato microfono: | 20           |
        | AzureResponseLabel     | Risposta Web di Azure | 20           |
        | Etichetta di dettatura         |   Hai appena detto:   | 20           |
        | TranslationResultLabel |    Conversione:    | 20           |

        ![Immettere i valori corrispondenti per le etichette dell'interfaccia utente.](images/AzureLabs-Lab1-24.png)

    3. Impostare anche Stile carattere su **Grassetto.** In questo modo il testo sarà più facile da leggere.

        ![Carattere grassetto.](images/AzureLabs-Lab1-25.png)

7.  Per ogni oggetto *Text dell'interfaccia* utente creato [nel capitolo 5,](#chapter-5--create-the-results-class)creare un nuovo oggetto **Text dell'interfaccia utente figlio.**  Questi elementi figlio visualizzano l'output dell'applicazione. Creare *oggetti* figlio facendo clic con il pulsante destro del mouse sull'elemento padre desiderato (ad esempio *MicrophoneStatusLabel),* quindi selezionare **Interfaccia** utente e infine **Testo.**
8.  Per ognuno di questi elementi figlio, selezionarlo e usare le tabelle seguenti per impostare i parametri nel pannello di controllo.

    1. Per il **componente Rect Transform (Trasformazione** rect):

        | Nome                  | Transform - *Position* | Larghezza      | Altezza    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | Testo di dettatura         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Per il **componente Testo (script):**

        | Nome                  | Testo          | Dimensione carattere    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | Testo di dettatura         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Selezionare quindi l'opzione di allineamento "al centro" per ogni componente di testo:

    ![allineare il testo.](images/AzureLabs-Lab1-26.png)

10. Per assicurarsi che gli **oggetti Text dell'interfaccia** utente figlio siano facilmente leggibili, modificarne *il colore.* A tale scopo, fare clic sulla barra (attualmente "Nero") accanto a *Colore*. 

    ![Immettere i valori corrispondenti per gli output di testo dell'interfaccia utente.](images/AzureLabs-Lab1-27.png)
 
11. Quindi, nella nuova finestra *Colore,* piccola, modificare il colore *esadecimale* in: **0032EAFF**

    ![Aggiornare il colore in blu.](images/AzureLabs-Lab1-28.png)
 
12. Di seguito è riportato **l'aspetto dell'interfaccia** utente.
    1.  Nel pannello *Hierarchy (Gerarchia):*

        ![Avere una gerarchia nella struttura fornita.](images/AzureLabs-Lab1-29.png)

    2.  In *Scene* and *Game Views (Visualizzazioni scena e gioco):*

        ![Avere le visualizzazioni della scena e del gioco nella stessa struttura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capitolo 5: Creare la classe Results

Il primo script da creare è la *classe Results,* responsabile di fornire un modo per visualizzare i risultati della traduzione. La classe archivia e visualizza quanto segue: 

- Risultato della risposta da Azure.
- Stato del microfono. 
- Risultato della dettatura (voce in testo).
- Risultato della traduzione.

Per creare questa classe: 

1.  Fare clic con il pulsante destro *del mouse nel Project,* quindi **scegliere > cartella**. Assegnare alla cartella il **nome Scripts**. 
 
    ![Creare la cartella scripts.](images/AzureLabs-Lab1-31.png)

    ![Aprire la cartella scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Dopo avere **creato la** cartella Script, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse **e scegliere >** quindi Script **C#.** Assegnare allo script il *nome Results.* 

    ![Creare il primo script.](images/AzureLabs-Lab1-33.png)
 
3.  Fare doppio clic sul nuovo script *Results* (Risultati) per aprirlo **con Visual Studio**.
4.  Inserire gli spazi dei nomi seguenti:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Aggiungere quindi il *metodo Awake(),* che verrà chiamato quando la classe viene inizializzata. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Aggiungere infine i metodi responsabili dell'output delle varie informazioni sui risultati nell'interfaccia utente. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capitolo 6: Creare la *classe MicrophoneManager*

La seconda classe che si creerà è *MicrophoneManager.*

Questa classe è responsabile di:

- Rilevamento del dispositivo di registrazione collegato al visore VR o al computer (a seconda dell'impostazione predefinita).
- Acquisire l'audio (voce) e usare la dettatura per archiviarlo come stringa.
- Dopo che la voce è stata sospesa, inviare la dettatura alla Translator classe.
- Ospitare un metodo in grado di arrestare l'acquisizione vocale, se necessario.

Per creare questa classe: 
1.  Fare doppio clic sulla **cartella** Script per aprirla. 
2.  Fare clic con il pulsante destro del **mouse all'interno** della **cartella Script e scegliere > script C#.** Assegnare allo script *il nome MicrophoneManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi in modo che siano uguali ai seguenti, all'inizio della *classe MicrophoneManager:*

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *della classe MicrophoneManager:*

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().* Questi verranno chiamati quando la classe inizializza:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  È possibile *eliminare* il *metodo Update()* perché questa classe non lo userà.
8.  A questo punto sono necessari i metodi che l'app usa per avviare e arrestare l'acquisizione vocale e passarla alla *classe Translator,* che verrà compilata a breve. Copiare il codice seguente e incollarlo sotto il *metodo Start().*

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Anche se questa applicazione non la userà, qui è stato fornito anche il metodo *StopCapturingAudio(),* se si vuole implementare la possibilità di arrestare l'acquisizione di audio nell'applicazione.

9.  È ora necessario aggiungere un gestore di dettatura che verrà richiamato quando la voce si arresta. Questo metodo passerà quindi il testo determinato alla *Translator* classe .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.

> [!WARNING]  
> A questo punto si noterà un errore visualizzato nel pannello della *console* dell'editor unity ("Il nome 'Translator' non esiste..."). Questo perché il codice fa riferimento *Translator* classe , che verrà creata nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capitolo 7: Chiamata ad Azure e al servizio translator

L'ultimo script che è necessario creare è *Translator* classe . 

Questa classe è responsabile di:

-   Autenticazione dell'app con *Azure,* in cambio di un **token di autenticazione**.
-   Usare il **token di autenticazione** per inviare il testo (ricevuto dalla classe *MicrophoneManager)* da tradurre.
-   Ricevere il risultato tradotto e passarlo alla *classe Results* da visualizzare nell'interfaccia utente.

Per creare questa classe: 
1.  Passare alla cartella **Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro **del mouse nel pannello Project ,**> script **C#.** Chiamare lo script *Translator*.
3.  Fare doppio clic sul nuovo script *Translator* per aprirlo **con Visual Studio**.
4.  Aggiungere gli spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *Translator* classe :

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - I linguaggi inseriti **nell'enumerazione** languages sono solo esempi. Se si vuole, è possibile aggiungervi altri elementi. [l'API supporta più di 60 lingue](/azure/cognitive-services/translator/languages) (incluso Klingon).
    > - È disponibile una pagina più interattiva che copre le lingue [disponibili,](https://www.microsoft.com/translator/business/languages/)anche se tenere presente che la pagina sembra funzionare solo quando la lingua del sito è impostata su '' (e il sito Microsoft probabilmente reindirizza alla lingua nativa). È possibile modificare la lingua del sito nella parte inferiore della pagina o modificando l'URL.
    > - Il **valore authorizationKey,** nel frammento di  codice precedente, deve essere la chiave ricevuta quando è stata effettuata la sottoscrizione all'API Di testo di *Azure Translator*. Questa operazione è stata trattata [nel capitolo 1.](#chapter-1--the-azure-portal)

6.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().* 
7.  In questo caso, il codice effettua una chiamata ad *Azure* usando la chiave di autorizzazione per ottenere un *token*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Il token scadrà dopo 10 minuti. A seconda dello scenario per l'app, potrebbe essere necessario effettuare la stessa chiamata di coroutine più volte.

8.  La coroutine per ottenere il token è la seguente:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Se si modifica il nome del metodo IEnumerator **GetTokenCoroutine(),** è necessario aggiornare i valori della stringa di chiamata *StartCoroutine* e *StopCoroutine* nel codice precedente. [Come illustrato nella documentazione di Unity,](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)per arrestare una *coroutine specifica* è necessario usare il metodo del valore stringa.

9.  Aggiungere quindi la coroutine (con un metodo di flusso "supporto" subito sotto) per ottenere la traduzione del testo ricevuto dalla *classe MicrophoneManager.* Questo codice crea una stringa di query da inviare all'API Text di *Azure Translator* e quindi usa la classe UnityWebRequest interna per effettuare una chiamata 'Get' all'endpoint con la stringa di query. Il risultato viene quindi usato per impostare la traduzione nell'oggetto Results. Il codice seguente illustra l'implementazione:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-8--configure-the-unity-scene"></a>Capitolo 8: Configurare la scena unity

1.  Nell'editor di Unity fare clic  e trascinare la classe *Results* dalla **cartella Scripts** (Script) all'oggetto **Main Camera (Fotocamera** principale) nel *pannello Hierarchy (Gerarchia).*
2.  Fare clic su **Main Camera (Fotocamera** principale) e osservare *inspector panel (Pannello di controllo).* Si noterà che all'interno del componente *script* appena aggiunto sono presenti quattro campi con valori vuoti. Questi sono i riferimenti di output alle proprietà nel codice. 
3.  Trascinare gli **oggetti Text** appropriati dal pannello *Hierarchy (Gerarchia)* a questi quattro slot, come illustrato nell'immagine seguente.

    ![Aggiornare i riferimenti di destinazione con i valori specificati.](images/AzureLabs-Lab1-34.png)
  
4.  Successivamente, fare clic e trascinare *Translator* classe dalla **cartella Scripts** all'oggetto **Main Camera** nel pannello *Hierarchy*. 
5.  Quindi, fare clic e trascinare la *classe MicrophoneManager* dalla **cartella Scripts** all'oggetto **Main Camera** nel *pannello Hierarchy*. 
6.  Infine, fare clic sulla **fotocamera principale** e osservare il *pannello inspector*. Si noterà che nello script trascinato sono disponibili due caselle a discesa che consentono di impostare le lingue.
 
    ![Assicurarsi che le lingue di traduzione siano di input.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capitolo 9: Testare in realtà mista

A questo punto è necessario verificare che la scena sia stata implementata correttamente.

Assicurarsi che:

- Tutte le impostazioni indicate nel [capitolo 1](#chapter-1--the-azure-portal) sono impostate correttamente. 
- Gli *script Results,* *Translator* e *MicrophoneManager* sono collegati **all'oggetto Main Camera.** 
- La chiave del servizio *API Translator*  testo di Azure è stata inserita all'interno della **variabile authorizationKey** all'interno dello script *Translator.*  
- Tutti i campi nel pannello *di controllo della fotocamera principale* vengono assegnati correttamente.
- Il microfono funziona durante l'esecuzione della scena (in  caso [contrario,](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)verificare che il microfono collegato sia il dispositivo predefinito e che sia stato configurato correttamente all'interno di Windows ).

È possibile testare il visore VR immersive premendo il **pulsante Play** (Riproduci) nell'editor *di Unity.*
L'app dovrebbe funzionare tramite il visore VR immersive collegato.

> [!WARNING]  
> Se nella console di Unity viene visualizzato un errore che riguarda la modifica del dispositivo audio predefinito, la scena potrebbe non funzionare come previsto. Ciò è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per i visori VR che li hanno. Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e tutto dovrebbe funzionare come previsto.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capitolo 10: Creare la soluzione UWP e il sideload nel computer locale

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è il momento di compilarlo da Unity.

1.  Passare a **Build Impostazioni**: File > **Build Impostazioni...**
2.  Nella finestra **Build Impostazioni** (Compila) fare clic su **Build (Compila).**

    ![Compilare la scena Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Se non è già presente, selezionare **Progetti C# unity.**
4.  Fare clic su **Compila**. Unity avvierà una *Esplora file,* in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome *App*. Quindi, con la *cartella App* selezionata, premere **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella *cartella App.* 
6.  Al termine della compilazione, Unity aprirà una finestra *di Esplora file nella* posizione della compilazione(controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma invierà una notifica dell'aggiunta di una nuova finestra).

## <a name="chapter-11--deploy-your-application"></a>Capitolo 11: Distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova build di Unity (la *cartella App)* e aprire il file della soluzione *con Visual Studio*.
2.  In Configurazione soluzione selezionare **Debug.**
3.  In Piattaforma soluzione selezionare **x86**, **Computer locale**. 

    > Per il Microsoft HoloLens, potrebbe risultare più semplice impostarlo su *Computer* remoto , in modo che non sia stato impostato il tethering sul computer. Tuttavia, è necessario eseguire anche le operazioni seguenti:
    > - Conoscere **l'indirizzo IP** del HoloLens, che si trova all'interno del Impostazioni > rete & *Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Assicurarsi *che la modalità sviluppatore* sia **attivata.** disponibile in *Impostazioni > Update & Security > For developers*.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel PC.
5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.
6.  Dopo l'avvio, l'app richiederà di autorizzare l'accesso al microfono. Assicurarsi di fare clic sul **pulsante** SÌ.
7.  A questo punto è possibile iniziare a tradurre.

## <a name="your-finished-translation-text-api-application"></a>Applicazione dell'API Traduzione testuale completata

È stata creata un'app di realtà mista che sfrutta l'API Traduzione testuale di Azure per convertire la voce in testo tradotto.

![Prodotto finale.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

È possibile aggiungere funzionalità di sintesi vocale all'app, in modo che il testo restituito sia pronunciato?

### <a name="exercise-2"></a>Esercizio 2

Consente all'utente di modificare le lingue di origine e di output ('from' e 'to') all'interno dell'app stessa, quindi l'app non deve essere ricompilata ogni volta che si vogliono cambiare le lingue.