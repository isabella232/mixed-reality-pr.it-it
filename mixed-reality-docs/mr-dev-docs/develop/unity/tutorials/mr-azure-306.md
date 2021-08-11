---
title: HoloLens (prima generazione) e Azure 306 - Streaming video
description: Completare questo corso per informazioni su come implementare Servizi multimediali di Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, servizi multimediali, streaming video, 360, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224374"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (prima generazione) e Azure 306: Streaming video

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br> 

![final product -start ](images/AzureLabs-Lab6-00.png)
 ![ final product -start](images/AzureLabs-Lab6-01.png)

In questo corso si apprenderà come connettere il Servizi multimediali di Azure a un'esperienza vr Windows Mixed Reality per consentire la riproduzione video a 360 gradi in visori immersivi. 

**Servizi multimediali di Azure** sono una raccolta di servizi che offre servizi di streaming video di qualità broadcast per raggiungere un pubblico più ampio sui dispositivi mobili più diffusi di oggi. Per altre informazioni, visitare la [pagina Servizi multimediali di Azure .](https://azure.microsoft.com/services/media-services)

Dopo aver completato questo corso, si avrà un'applicazione visore vr immersiva di realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1. Recuperare un video a 360 gradi da **un Archiviazione di Azure**, tramite il **Servizio multimediale di Azure.**

2. Visualizzare il video a 360 gradi recuperato all'interno di una scena di Unity.

3. Spostarsi tra due scene, con due video diversi.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è progettato per illustrare come integrare un servizio di Azure con il servizio Unity Project. È compito dell'utente usare le conoscenze acquisite da questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 306: Streaming video</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). È possibile usare il software più recente, come elencato nell'articolo installare gli strumenti [,](../../install-the-tools.md)anche se non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito.

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Visore [Windows Mixed Reality vr immersiva](../../../discover/immersive-headset-hardware-details.md)
- Accesso a Internet per l'installazione e il recupero dei dati di Azure
- Due video a 360 gradi in formato mp4 (è possibile trovare alcuni video senza diritti reali [in questa pagina di download)](https://www.mettle.com/360vr-master-series-free-360-downloads-page)

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).
2.  Configurare e testare l'visore vr vr immersive di realtà mista.

    > [!NOTE]
    > Per questo **corso non** saranno necessari controller di movimento. Se è necessario supporto per la configurazione dell'visore immersivo, fare clic sul collegamento per configurare [Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capitolo 1 - Portale di Azure: creazione dell'account Archiviazione di Azure account

Per usare il **Archiviazione di Azure ,** è necessario creare e configurare un **account** Archiviazione nel portale di Azure.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic **Archiviazione account nel** menu a sinistra.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab6-02.png)

3.  Nella scheda **Archiviazione Account** fare clic su **Aggiungi**.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab6-03.png)

4.  Nella scheda **Crea account di archiviazione:**

    1.  Inserire un **nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.

    2.  Per **Modello di distribuzione selezionare** Gestione **risorse**.

    3.  Per **Tipo di account** selezionare Archiviazione **(utilizzo generico v1).**

    4.  Per **Prestazioni** selezionare **Standard*.**

    5.  Per **Replica** selezionare **Archiviazione con ridondanza locale .**

    6.  Lasciare **Trasferimento sicuro obbligatorio** come **Disabilitato.**

    7.  Selezionare una **Sottoscrizione**.

    8.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.

    9.  Determinare **la posizione** per il gruppo di risorse (se si crea un nuovo gruppo di risorse). Il percorso si trova idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.

5.  È necessario confermare di aver compreso i Termini e Condizioni applicati al servizio.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab6-04.png)

6.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.

7.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab6-05.png)

8.  A questo punto non è necessario seguire la risorsa, semplicemente passare al capitolo successivo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capitolo 2 - Portale di Azure: creazione del servizio multimediale

Per usare il Servizio multimediale di Azure, è necessario configurare un'istanza del servizio per essere resa disponibile per l'applicazione (in cui il titolare dell'account deve essere un amministratore).

1.  Nel portale di Azure fare clic su **Crea una** risorsa nell'angolo superiore sinistro e cercare **Servizio multimediale e** premere **INVIO.** La risorsa desiderata ha attualmente un'icona rosa. fare clic su questo pulsante per visualizzare una nuova pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-06.png)

2.  La nuova pagina fornirà una descrizione del **Servizio multimediale**. Nella parte inferiore sinistra del prompt fare clic sul **pulsante Crea** per creare un'associazione con questo servizio.

    ![Portale di Azure](images/AzureLabs-Lab6-07.png)

3.  Dopo aver fatto clic su **Crea** un pannello, verrà visualizzato il riquadro in cui è necessario fornire alcuni dettagli sul nuovo Servizio multimediale:

    1.  Inserire il nome **account desiderato per** questa istanza del servizio.

    2.  Selezionare una **Sottoscrizione**.

    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 
    
    > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento su [come gestire i gruppi di risorse di Azure.](/azure/azure-resource-manager/resource-group-portal)

    4.  Determinare **la posizione** per il gruppo di risorse (se si crea un nuovo gruppo di risorse). Il percorso si trova idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.

    5.  Per la **Archiviazione Account** fare clic sulla sezione Please **select...** **(Seleziona)** e quindi fare clic sull'account Archiviazione creato nell'ultimo capitolo.

    6.  È anche necessario verificare di aver compreso i termini e le condizioni applicati al servizio.

    7.  Fare clic su **Crea**.

        ![Portale di Azure](images/AzureLabs-Lab6-08.png)

4.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.

5.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Portale di Azure](images/AzureLabs-Lab6-09.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Portale di Azure](images/AzureLabs-Lab6-10.png)

7.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio.

8.  All'interno della nuova pagina di Servizi multimediali, all'interno del pannello a sinistra, fare clic sul **collegamento Asset,** che si trova a circa metà della pagina.

9.  Nell'angolo superiore sinistro della pagina successiva fare clic su **Upload**.

    ![Portale di Azure](images/AzureLabs-Lab6-11.png)

10. Fare clic **sull'icona** Cartella per esplorare i file e selezionare il primo video 360 che si vuole trasmettere in streaming. 
    
    > È possibile seguire questo [collegamento per scaricare un video di esempio.](https://vimeo.com/214401712)

    ![Portale di Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> I nomi file lunghi possono causare un problema con il codificatore. Per assicurarsi che i video non presentino problemi, è consigliabile abbreviare la lunghezza dei nomi dei file video.

11. L'indicatore di stato sarà verde al termine del caricamento del video.

    ![Portale di Azure](images/AzureLabs-Lab6-13.png)

12. Fare clic sul testo precedente (**nomeservizio - Asset)** per tornare alla **pagina Asset.**

13. Si noterà che il video è stato caricato correttamente. Fare clic su di esso.

    ![Portale di Azure](images/AzureLabs-Lab6-14.png)

14. La pagina a cui si viene reindirizzati mostrerà informazioni dettagliate sul video. Per poter usare il video, è necessario codificarlo facendo clic sul pulsante **Encode** (Codifica) in alto a sinistra nella pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-15.png)

15. Verrà visualizzato un nuovo pannello a destra, in cui sarà possibile impostare le opzioni di codifica per il file. Impostare le proprietà seguenti (alcune saranno già impostate per impostazione predefinita):

    1.  **Nome del codificatore *multimediale Media Encoder Standard***

    2.  **Set di impostazioni di *codifica Content Adaptive Multiple Bitrate MP4***

    3.  **Nome del *processo Media Encoder Standard'elaborazione di Video1.mp4***

    4.  **Nome asset multimediale di *outputVideo1.mp4 -- Media Encoder Standard codificato***

        ![Portale di Azure](images/AzureLabs-Lab6-16.png)

16. Fare clic sul pulsante **Crea**.

17. Si noterà che è stata aggiunta **una** barra con il processo di codifica aggiunto, fare clic su tale barra per visualizzare un pannello con l'avanzamento codifica visualizzato.

    ![Portale di Azure](images/AzureLabs-Lab6-17.png)

    ![Portale di Azure](images/AzureLabs-Lab6-18.png)

18. Attendere il completamento del processo. Al termine, chiudere il pannello con la "X" in alto a destra.

    ![Portale di Azure](images/AzureLabs-Lab6-19.png)

    ![Portale di Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Il tempo necessario dipende dalle dimensioni del file del video. Questo processo può richiedere molto tempo.

19. Ora che è stata creata la versione codificata del video, è possibile pubblicarla per renderlo accessibile. A tale scopo, fare clic sul collegamento **blu Assets (Asset)** per tornare alla pagina assets (Asset).

    ![Portale di Azure](images/AzureLabs-Lab6-21.png)

20. Verrà visualizzato il video insieme a un altro, che è di tipo **Asset _Multi-Bitrate MP4_**.

    ![Portale di Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > È possibile notare che il nuovo asset, insieme al video iniziale, è *Sconosciuto* e ha "0" byte per la proprietà **Size.** È sufficiente aggiornare la finestra per l'aggiornamento.

21. Fare clic su questo nuovo asset.

    ![Portale di Azure](images/AzureLabs-Lab6-23.png)

22. Verrà visualizzato un pannello simile a quello usato in precedenza, ma si tratta di un asset diverso. Fare clic **sul** pulsante Pubblica nella parte superiore centrale della pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-24.png)

23. Verrà richiesto di impostare un localizzatore **,** ovvero il punto di ingresso, su file/s negli asset. Per lo scenario impostare le proprietà seguenti:

    1.  **Tipo di localizzatore**  >  **Oggetto progressivo.**

    2.  La **data** e **l'ora** verranno impostate automaticamente, dalla data corrente, a un'ora futura (in questo caso cento anni). Lasciare il campo così come è o modificarlo in base alle esigenze.

    > [!NOTE]
    > Per altre informazioni sui localizzatori e su ciò che è possibile scegliere, visitare la documentazione [Servizi multimediali di Azure.](/azure/media-services/media-services-concepts)

24. Nella parte inferiore del pannello fare clic sul **pulsante** Aggiungi.

    ![Portale di Azure](images/AzureLabs-Lab6-25.png)

25. Il video è ora pubblicato e può essere trasmesso tramite il relativo endpoint. Più in basso nella pagina è presente **una sezione** File. In questa posizione saranno disponibili le diverse versioni codificate del video. Selezionare la risoluzione più alta possibile (nell'immagine seguente è il file 1920x960) e quindi verrà visualizzato un pannello a destra. Qui è presente un **URL di download.** Copiare **questo endpoint** perché verrà utilizzato più avanti nel codice.

    ![Portale di Azure](images/AzureLabs-Lab6-26.png)    

    ![Portale di Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > È anche possibile premere il **pulsante Riproduci** per riprodurre il video e testarlo.

26. È ora necessario caricare il secondo video che verrà utilizzato in questo lab. Seguire i passaggi precedenti, ripetendo lo stesso processo per il secondo video. Assicurarsi di copiare anche il **secondo endpoint.** Usare il collegamento [seguente per scaricare un secondo video.](https://vimeo.com/214402865)

27. Dopo aver pubblicato entrambi i video, è possibile passare al capitolo successivo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3 - Configurazione del Project Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity e** fare clic su New **(Nuovo).** 

    ![Portale di Azure](images/AzureLabs-Lab6-28.png)

2.  È ora necessario specificare un nome Project Unity, inserire **MR \_ 360VideoStreaming.**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Il percorso su un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Portale di Azure](images/AzureLabs-Lab6-29.png)

3.  Con Unity aperto, è opportuno controllare che **l'editor** di script predefinito sia impostato **su Visual Studio.** Passare a **_Modifica_ *preferenze*** e quindi dalla nuova finestra passare a Strumenti **esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Portale di Azure](images/AzureLabs-Lab6-30.png)

4.  Passare quindi a ***File* *Build Impostazioni*** e impostare la piattaforma su Universal Windows **Platform** facendo clic sul pulsante **Switch Platform** (Cambia piattaforma).

5.  Assicurarsi anche che:

    1. **Dispositivo di destinazione** è impostato su **Qualsiasi dispositivo.**
    
    2.  **Tipo di** compilazione è impostato su **D3D.**

    3.  **L'SDK** è impostato su **Più recente installato.**

    4.  **Visual Studio versione è** impostata su **Versione più recente installata.**

    5.  **Build and Run (Compilazione** ed esecuzione) è **impostato su Local Machine (Computer locale).**

    6.  Non preoccuparsi di configurare Scenes in **questo** momento, perché verranno impostate in un secondo momento.

    7.  Per il momento, le impostazioni rimanenti dovrebbero rimanere come predefinite.

        ![Configurazione del Project Unity](images/AzureLabs-Lab6-31.png)

6.  Nella finestra **build Impostazioni** fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova **il controllo.** 

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione** **del runtime di** scripting deve essere **Stabile** (equivalente a .NET 3.5).

        2. **Il back-end di** scripting deve **essere .NET.**

        3. **Il livello di compatibilità** api deve **essere .NET 4.6.**

            ![Configurazione del Project Unity](images/AzureLabs-Lab6-32.png)

    2.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Configurazione del Project Unity](images/AzureLabs-Lab6-33.png)

    3.  Nella scheda **Pubblicazione Impostazioni,** in **Funzionalità**, controllare:

        - **InternetClient**

            ![Configurazione di Unity Project](images/AzureLabs-Lab6-34.png)

8.  Dopo aver apportato queste modifiche, chiudere la **finestra Impostazioni** compilazione.

9.  Salvare il Project **File* *Salva Project**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capitolo 4 - Importazione del pacchetto InsideOutSphere Unity

> [!IMPORTANT]
> Se si vuole ignorare il componente *Unity Set up* di questo corso e continuare direttamente nel codice, è [](https://docs.unity3d.com/Manual/AssetPackages.html)possibile scaricare questo file [unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo **5.** Sarà comunque necessario creare un'istanza di Unity Project.

Per questo corso è necessario scaricare un pacchetto di asset unity denominato [**InsideOutSphere.unitypackage.**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)

Procedura per importare **unitypackage:**

1.  Con il dashboard unity davanti all'utente, fare clic su Asset **nel** menu nella parte superiore della schermata, quindi fare clic su Importa pacchetto > **pacchetto personalizzato**.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  Usare la selezione file per selezionare il **pacchetto InsideOutSphere.unitypackage** e fare clic su **Apri**. Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic **su Importa**.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  Al termine dell'importazione, si noterà che alla cartella **Assets** sono state aggiunte tre nuove cartelle, **Materials**, **Models** e **Prefabs.** Questo tipo di struttura di cartelle è tipico per un progetto Unity.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  Aprire la **cartella** Models (Modelli) per verificare che il **modello InsideOutSphere** sia stato importato.

    2.  Nella **cartella Materials** è disponibile il materiale *Lambert1* **di InsideOutSpheres,** insieme a un materiale denominato *ButtonMaterial,* usato da GazeButton, che verrà visualizzato a breve.

    3.  La **cartella Prefabs** contiene il prefab **InsideOutSphere** che contiene sia il **modello InsideOutSphere** *che* *GazeButton*.

    4.  **Non è incluso codice**, il codice verrà scritto seguendo questo corso.


4.  In **Gerarchia** selezionare **l'oggetto Fotocamera** principale e aggiornare i componenti seguenti:

    1.  **Trasformare**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotazione = **X**: 0, **Y**: 0, **Z**: 0.

        3. Scala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Fotocamera**

        1. **Cancella flag:** colore a tinta unita.

        2.  **Piani di ritaglio:** Vicino: 0.1, Lontano: 6.

            ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  Passare alla cartella **Prefab** e quindi trascinare il prefab **InsideOutSphere** nel pannello **Gerarchia.**

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  Espandere **l'oggetto InsideOutSphere** all'interno **della gerarchia** facendo clic sulla piccola freccia accanto. Sotto di esso **verrà visualizzato** un oggetto figlio **denominato GazeButton**. Verrà usato per modificare le scene e quindi i video.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  Nella finestra inspector fare clic sul componente Transform di **InsideOutSphere,** assicurarsi che siano impostate le proprietà seguenti:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRASFORMAZIONE - ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  Fare clic **sull'oggetto figlio GazeButton** e impostarne **la trasformazione come** segue:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRASFORMAZIONE - ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capitolo 5- Creare la classe VideoController

La **classe VideoController** ospita i due endpoint video che verranno usati per trasmettere il contenuto dal Servizio multimediale di Azure.

Per creare questa classe:

1.  Fare clic con il pulsante destro **del mouse** nella cartella Asset , nel **pannello Project** e scegliere Crea > **cartella**. Assegnare alla cartella il nome **Scripts**.

    ![Creare la classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Creare la classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Fare doppio clic sulla **cartella Script** per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della **cartella, quindi scegliere Crea > script C \#**. Assegnare allo script il **nome VideoController**.

    ![Creare la classe VideoController](images/AzureLabs-Lab6-45.png)

4.  Fare doppio clic sul nuovo script **VideoController** per aprirlo con **Visual Studio 2017.**

    ![Creare la classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Aggiornare gli spazi dei nomi all'inizio del file di codice come indicato di seguito:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Immettere le variabili seguenti nella **classe VideoController,** insieme al **metodo Awake():**

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  È ora possibile immettere gli endpoint dai video di Servizio multimediale di Azure:

    1.  Il primo nella *variabile video1endpoint.*
    
    2.  Il secondo nella *variabile video2endpoint.*

    > [!WARNING]
    > Si è verificato un problema noto con l'uso di *https* in Unity, con la versione 2017.4.1f1. Se i video forniscono un errore in riproduzione, provare a usare "http".

8.  Successivamente, **è necessario** modificare il metodo Start(). Questo metodo verrà attivato ogni volta che l'utente cambia scena (di conseguenza spostando il video) osservando il pulsante Sguardo fisso.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Seguendo il **metodo Start(),** inserire il metodo **PlayVideo()** *IEnumerator,* che verrà usato per avviare i video senza problemi (quindi non viene visualizzato alcun stutter).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. L'ultimo metodo necessario per questa classe è il **metodo ChangeScene(),** che verrà usato per lo scambio tra le scene.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Il **metodo ChangeScene()** usa una pratica funzionalità C \# denominata *operatore condizionale*. In questo modo è possibile verificare le condizioni e quindi restituire i valori in base al risultato del controllo, il tutto all'interno di una singola istruzione. Seguire questo [collegamento per altre informazioni sull'operatore condizionale](/dotnet/csharp/language-reference/operators/conditional-operator).

11. Salvare le modifiche in Visual Studio prima di tornare a Unity.

12. Nell'editor di Unity fare clic e trascinare la classe  **VideoController** [da]{.underline} all'oggetto **Fotocamera** principale nel pannello **Gerarchia.**

13. Fare clic sulla **fotocamera principale** e osservare il **pannello Inspector**. Si noterà che all'interno del componente Script appena aggiunto è presente un campo con un valore vuoto. Si tratta di un campo di riferimento destinato alle variabili pubbliche all'interno del codice.

14. Trascinare **l'oggetto InsideOutSphere** dal pannello **Gerarchia** nello slot **Sphere,** come illustrato nell'immagine seguente.

    ![Creare la classe VideoController ](images/AzureLabs-Lab6-47.png)
     ![ Creare la classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capitolo 6 - Creare la classe Gaze

Questa classe è responsabile della creazione di **un raycast** che verrà proiettato in avanti dalla fotocamera principale **per** rilevare l'oggetto che l'utente sta esaminando. In questo caso, **Raycast** dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro **del mouse Project** pannello di controllo, **Crea* \# *Script C**. Assegnare allo script il **nome Gaze**.

3.  Fare doppio clic sul nuovo script ***Gaze** _ per aprirlo con _ *Visual Studio 2017.**

4.  Verificare che lo spazio dei nomi seguente si trova all'inizio dello script e rimuovere tutti gli altri:

    ```csharp
    using UnityEngine;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno **della classe Gaze:**

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  È ora necessario aggiungere il codice per i metodi **Awake()** e **Start().**

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Aggiungere il codice seguente nel metodo **Update()** per proiettare un raycast e rilevare l'hit di destinazione:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

9.  Fare clic e trascinare la classe **Gaze** dalla cartella Scripts (Script) all'oggetto Main Camera (Fotocamera principale) nel **pannello Hierarchy (Gerarchia).**

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capitolo 7: Configurare le due scene di Unity

Lo scopo di questo capitolo è quello di configurare le due scene, ognuna delle quali ospita un video da trasmettere in streaming. Duplicare la scena già creata, in modo che non sia necessario configurarla nuovamente, anche se si modificherà quindi la nuova scena, in modo che l'oggetto *GazeButton* si trova in una posizione diversa e abbia un aspetto diverso. In questo modo viene illustrato come passare da una scena all'altro.

1.  A tale scopo, accedere **a File > Save Scene as...**(Salva scena con nome). Verrà visualizzata una finestra di salvataggio. Fare clic **sul pulsante Nuova** cartella.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-49.png)

2.  Assegnare alla cartella il **nome Scenes**.

3.  La **finestra Salva** scena sarà ancora aperta. Aprire la cartella **Scenes appena** creata.

4.  Nel campo **di testo Nome file:** digitare **VideoScene1** e quindi premere **Salva.**

5.  In Unity aprire la cartella **Scenes** e fare clic con il pulsante destro del mouse sul file **VideoScene1.** Usare la tastiera e premere **CTRL+D per** duplicare la scena

    > [!TIP]
    > Il **comando** Duplica può essere eseguito anche passando a **Modifica > Duplica.**

6.  Unity incrementerà automaticamente il numero dei nomi delle scene, ma lo controlla comunque per assicurarsi che corrisponda al codice inserito in precedenza.

    >  È necessario disporre **di VideoScene1** e **VideoScene2**.

7.  Con le due scene, passare a **File > Build Impostazioni**. Con la **finestra Impostazioni** compilazione aperta, trascinare le scene nella sezione Scenes in **Build (Scene nella compilazione).**

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > È possibile selezionare entrambe le scene dalla cartella **Scenes** tenendo premuto il pulsante **CTRL,** quindi fare clic su ogni scena e infine trascinare entrambe le scene.

8.  Chiudere la **finestra build Impostazioni** e fare doppio clic su **VideoScene2.**

9.  Con la seconda scena aperta, fare clic sull'oggetto **figlio GazeButton** di **InsideOutSphere** e impostarne la trasformazione come segue:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORM - ROTATION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Con **l'elemento figlio GazeButton** ancora selezionato, osserva **Inspector (Controllo)** e **Mesh Filter (Filtro mesh).** Fare clic sulla piccola destinazione accanto al **campo Riferimento** mesh:

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-51.png)

11. Verrà **visualizzata la finestra** popup Seleziona mesh. Fare doppio clic **sulla** mesh Cubo nell'elenco **asset .**

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-52.png)

12. Il **filtro mesh** verrà aggiornato e ora sarà un **cubo**. A questo punto, fare clic **sull'icona** a forma di ingranaggio accanto a **Sphere Collider (Collisore** sfera) e fare clic su Remove Component (Rimuovi **componente)** per eliminare il collisore da questo oggetto.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-53.png)

13. Con **gazeButton ancora** selezionato, fare clic **sul pulsante Add Component** (Aggiungi componente) nella parte inferiore di Inspector **(Controllo).** Nel campo di ricerca digitare **box** e **Box Collider** sarà un'opzione. Fai clic su di questa opzione per aggiungere **un Collisore** di box all'oggetto **GazeButton.**

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-54.png)

14. **GazeButton** è ora parzialmente aggiornato, per avere un aspetto diverso, tuttavia ora crei un nuovo **material**, in modo che sia completamente diverso ed è più facile da riconoscere come oggetto diverso rispetto all'oggetto nella prima scena.

15. Passare alla cartella **Materials** all'interno del **Project.** Duplicare **ButtonMaterial** Material (premere **CTRL** D sulla tastiera oppure fare clic con il pulsante destro del mouse su Material, quindi scegliere Duplica) dal  +   menu Edit file  **(Modifica** file). 

    ![Capitolo 7 - Configurare le due scene di Unity ](images/AzureLabs-Lab6-55.png)
     ![ Capitolo 7 - Configurare le due scene di Unity](images/AzureLabs-Lab6-56.png)

16. Selezionare il nuovo **materiale ButtonMaterial** (denominato **ButtonMaterial 1)** e all'interno di **Inspector (Controllo)** fare clic sulla **finestra Colore albedo.** Verrà visualizzata una finestra popup, in cui è possibile selezionare un altro colore (scegliere quello desiderato), quindi chiudere il popup. Material sarà la propria istanza e diversa dall'originale.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-57.png)

17. Trascinare il nuovo **oggetto Material** nell'elemento figlio **GazeButton** per aggiornarne completamente l'aspetto, in modo che sia facilmente distinguibile dal pulsante delle prime scene.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-58.png)

18. A questo punto è possibile testare il progetto nell'editor prima di compilare il progetto UWP.

    -  Premere il **pulsante Play (Riproduci)** nell'editor **e** portare il visore VR.

        ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-59.png)

19. Esaminare i due **oggetti GazeButton** per passare dal primo al secondo video.

## <a name="chapter-8---build-the-uwp-solution"></a>Capitolo 8: Creare la soluzione UWP

Dopo aver garantito che l'editor non contiene errori, si è pronti per la compilazione.

Per compilare:

1.  Salvare la scena corrente facendo clic su **File > Salva**.

2.  Selezionare la casella progetti **Unity C \#** (questo è importante perché consente di modificare le classi al termine della compilazione).

3.  Passare a **File > Build Impostazioni**, fare clic su Build **(Compila).**

4.  Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione.

5.  Creare una **cartella BUILDS** e all'interno di tale cartella creare un'altra cartella con il nome appropriato desiderato.

6.  Fare clic sulla nuova cartella e quindi su **Seleziona cartella**, in modo da scegliere tale cartella per iniziare la compilazione in tale percorso.

    ![Capitolo 8 - Creare la soluzione UWP ](images/AzureLabs-Lab6-60.png)
     ![ Capitolo 8 - Creare la soluzione UWP](images/AzureLabs-Lab6-61.png)

7.  Al termine della compilazione di Unity (potrebbe essere  necessario del tempo), verrà aperta una Esplora file nella posizione della compilazione.

## <a name="chapter-9---deploy-on-local-machine"></a>Capitolo 9: Distribuire nel computer locale

Una volta completata la compilazione, verrà **Esplora file** finestra di dialogo nella posizione della compilazione. Aprire la cartella denominata e compilata, quindi fare doppio clic sul file della soluzione (con estensione sln) all'interno di tale cartella per aprire la soluzione con Visual Studio 2017.

L'unica cosa da fare è distribuire l'app nel computer (o *nel computer locale).*

Per eseguire la distribuzione nel computer locale:

1.  In **Visual Studio 2017** aprire il file di soluzione appena creato.

2.  In **Piattaforma soluzione selezionare** **x86, Computer locale.**

3.  In Configurazione **soluzione selezionare** **Debug.**

    ![Capitolo 9 : Distribuire nel computer locale](images/AzureLabs-Lab6-62.png)

4.  Sarà ora necessario ripristinare tutti i pacchetti nella soluzione. Fare clic con il pulsante destro **del mouse sulla** soluzione e scegliere Ripristina NuGet pacchetti per la **soluzione...**

    > [!NOTE] 
    > Questa operazione viene eseguita perché i pacchetti compilati da Unity devono essere destinati per funzionare con i riferimenti ai computer locali.

5.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer. Visual Studio compila e quindi distribuisce l'applicazione.

6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.

    ![Capitolo 9 : Distribuire nel computer locale](images/AzureLabs-Lab6-63.png)

Quando si esegue l'applicazione Mixed Reality, si sarà all'interno del modello **InsideOutSphere** usato all'interno dell'app. Questa sfera sarà la posizione in cui verrà trasmesso il video, fornendo una visualizzazione a 360 gradi, del video in ingresso (che è stato filmato per questo tipo di prospettiva). Non sorprendersi se il caricamento del video richiede un paio di secondi, l'app è soggetta alla velocità Internet disponibile, perché il video deve essere recuperato e quindi scaricato, in modo da eseguire lo streaming nell'app.
Quando si è pronti, cambiare scena e aprire il secondo video, guardando la sfera rossa. È quindi possibile tornare indietro usando il cubo blu nella seconda scena.

## <a name="your-finished-azure-media-service-application"></a>Applicazione del Servizio multimediale di Azure completata
 
È stata creata un'app di realtà mista che sfrutta il Servizio multimediale di Azure per trasmettere video a 360.

![risultato del lab](images/AzureLabs-Lab6-00.png)

![risultato del lab](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

È possibile usare solo una singola scena per modificare i video all'interno di questa esercitazione. Sperimentare con l'applicazione e trasformarla in una singola scena. È anche possibile aggiungere un altro video alla combinazione.

**Esercizio 2**

Provare con Azure e Unity e provare a implementare la possibilità per l'app di selezionare automaticamente un video con dimensioni di file diverse, a seconda del livello di una connessione Internet.