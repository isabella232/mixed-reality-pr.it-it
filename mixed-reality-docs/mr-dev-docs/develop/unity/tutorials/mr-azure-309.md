---
title: HoloLens (prima generazione) e Azure 309 - Application Insights
description: Completare questo corso per informazioni su come raccogliere analisi relative al comportamento degli utenti all'interno di un'applicazione di realtà mista usando il applicazione Azure Insights Service.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, application insights, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 549afbd1e5a3f42bb0540714500d31edf022d36511961e887ac9e927b9af1ea3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222171"
---
# <a name="hololens-1st-gen-and-azure-309-application-insights"></a>HoloLens (prima generazione) e Azure 309: Application Insights

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

![final product -start](images/AzureLabs-Lab309-00.png)

In questo corso si apprenderà come aggiungere funzionalità Insights application Insights a un'applicazione di realtà mista, usando l'API applicazione Azure Insights per raccogliere analisi relative al comportamento dell'utente.

Application Insights è un servizio Microsoft che consente agli sviluppatori di raccogliere analisi dalle applicazioni e gestirla da un portale di facile utilizzo. L'analisi può essere qualsiasi cosa, dalle prestazioni alle informazioni personalizzate che si vuole raccogliere. Per altre informazioni, visitare la [pagina Application Insights](https://azure.microsoft.com/services/application-insights/).

Dopo aver completato questo corso, si avrà un'applicazione visore vr immersiva di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Consente all'utente di guardare e spostarsi in una scena.
2.  Attivare l'invio di analisi al *servizio Insights applicazione* tramite l'uso di Sguardo fisso e Prossimità agli oggetti nella scena.
3.  L'app chiamerà anche il servizio, recuperando informazioni sull'oggetto più avvicinato dall'utente, nelle ultime 24 ore. Tale oggetto cambierà il colore in verde.

Questo corso illustra come ottenere i risultati da Application Insights Service in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che potrebbe essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in Windows Mixed Reality visore vr immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note su eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare un'eco durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (luglio 2018). È possibile usare il software più recente, come elencato nell'articolo Installare gli strumenti, anche se non si deve presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Visore [Windows Mixed Reality vr o](../../../discover/immersive-headset-hardware-details.md) visore [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Un set di cuffia con un microfono predefinito (se l'headset non ha un microfono e altoparlanti predefiniti)
- Accesso a Internet per l'installazione di Azure e il recupero Insights dati dell'applicazione

## <a name="before-you-start"></a>Prima di iniziare

Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).

> [!WARNING] 
> Tenere presente che i dati in *Application Insights* richiede tempo, quindi sii paziente. Per verificare se il servizio ha ricevuto i dati, vedere il capitolo [14,](#chapter-14---the-application-insights-service-portal)che illustra come esplorare il portale.

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - Portale di Azure

Per usare *application Insights*, è necessario creare e configurare un servizio Insights *applicazione* nel portale di Azure.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare *Application Insights* e fare clic su **Invio.**

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita con **Crea una** risorsa nei portali più nuovi.

    ![Portale di Azure](images/AzureLabs-Lab309-01.png)

3.  La nuova pagina a destra fornirà una descrizione del *applicazione Azure Insights* servizio. Nella parte inferiore sinistra di questa pagina selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-02.png)

4.  Dopo aver fatto clic su **Crea**:

    1.  Inserire il nome **desiderato per** questa istanza del servizio.

    2.  In **Tipo di applicazione** selezionare **Generale.**

    3.  Selezionare una sottoscrizione **appropriata.**

    4.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto,ad esempio questi corsi, in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo gruppo di risorse](/azure/azure-resource-manager/resource-group-portal).

    5.  Selezionare un **percorso**.

    6.  È anche necessario verificare di aver compreso i termini e le condizioni applicati al servizio.

    7.  Selezionare **Crea**.

        ![Portale di Azure](images/AzureLabs-Lab309-03.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Portale di Azure](images/AzureLabs-Lab309-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-05.png)

8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà eseguita la nuova istanza *di Application Insights Service.*

    ![Portale di Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenere questa pagina Web aperta e facile da accedere. Si tornerà spesso qui per visualizzare i dati raccolti.

    > [!IMPORTANT]
    > Per implementare application Insights, è necessario usare tre (3) valori specifici: **Instrumentation Key**(Chiave di strumentazione), Application **ID (ID** applicazione) **e API Key (Chiave API).** Di seguito viene illustrato come recuperare questi valori dal servizio. Assicurarsi di annotare questi valori in una pagina *Blocco note* vuota, perché verranno presto utilizzati nel codice.

9.  Per trovare la **chiave di** strumentazione , è necessario scorrere verso il basso l'elenco delle funzioni del servizio e fare clic su Proprietà **.** La scheda visualizzata visualizza la chiave **del servizio**.

    ![Portale di Azure](images/AzureLabs-Lab309-07.png)

10. Un po' più **avanti in Proprietà** è possibile trovare **l'accesso all'API,** su cui è necessario fare clic. Il pannello a destra fornirà **l'ID applicazione** dell'app.

    ![Portale di Azure](images/AzureLabs-Lab309-08.png)

11. Con il **pannello ID applicazione** ancora aperto, fare clic su Crea chiave **API** per aprire il pannello Crea *chiave API.*

    ![Portale di Azure](images/AzureLabs-Lab309-09.png)

12. All'interno del *pannello tasto Crea API ora* aperto digitare una descrizione e selezionare le tre **caselle**.

13. Fare clic **su Genera chiave**. La **chiave API** verrà creata e visualizzata. 

    ![Portale di Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Questa è l'unica volta **che la chiave** del servizio verrà visualizzata, quindi assicurarsi di crearne una copia ora.

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2 - Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **Nuovo**.

    ![Configurare unity Project](images/AzureLabs-Lab309-11.png)

2.  È ora necessario specificare un nome di Project Unity e inserire **MR \_ Azure Application \_ \_ Insights**. Assicurarsi che *l'opzione Modello* sia impostata su **3D.** Impostare Il *percorso su* un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Configurare l'Project Unity](images/AzureLabs-Lab309-12.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica \> preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Configurare l'Project Unity](images/AzureLabs-Lab309-13.png)

4.  Passare quindi a **File \> Build Impostazioni** e impostare la piattaforma su Universal Windows **Platform** facendo clic sul pulsante **Switch Platform** (Cambia piattaforma).

    ![Configurare l'Project Unity](images/AzureLabs-Lab309-14.png)

5.  Passare a **File \> Build Impostazioni** (Compilazione file) e assicurarsi che:

    1.  **Dispositivo di destinazione** impostato su **Qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **Dispositivo di destinazione** su *HoloLens*.

    2.  **Il tipo di** compilazione è impostato **su D3D**

    3.  **L'SDK** è impostato su **Più recente installato**

    4.  **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**

    5.  Salvare la scena e aggiungerla alla compilazione.

        1.  A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.

            ![Configurare l'Project Unity](images/AzureLabs-Lab309-15.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi fare clic sul pulsante Nuova cartella per creare una nuova cartella e assegnare alla cartella il nome **Scenes**.

            ![Configurare l'Project Unity](images/AzureLabs-Lab309-16.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file:* digitare **ApplicationInsightsScene** e quindi fare clic su **Salva.**

            ![Configurare l'Project Unity](images/AzureLabs-Lab309-17.png)

6.  Le impostazioni rimanenti, in **Build Impostazioni**, per il momento devono essere lasciato come predefinite.

7.  Nella finestra **build Impostazioni** fare clic sul pulsante **Player Impostazioni** (Impostazioni lettore). Verrà aperto il pannello correlato nello spazio in cui si trova **il** controllo.

    ![Configurare l'Project Unity](images/AzureLabs-Lab309-18.png)

8. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione** **del runtime di** scripting deve essere sperimentale (equivalente a **.NET 4.6),** che attiverà la necessità di riavviare l'editor.

        2.  **Il back-end di** scripting deve **essere .NET**

        3.  **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

        ![Configurare l'Project Unity](images/AzureLabs-Lab309-19.png)

    2.  **All'interno della Impostazioni** pubblicazione, in **Funzionalità,** controllare:

        - **InternetClient**     

            ![Configurare l'Project Unity](images/AzureLabs-Lab309-20.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Publishing Impostazioni**), selezionare Virtual **Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Configurare l'Project Unity](images/AzureLabs-Lab309-21.png)

9.  Tornando alla **compilazione Impostazioni**, i **progetti C# Unity** non sono più disattivati; Selezionare la casella di controllo accanto a questo.

10.  Chiudere la finestra Build Settings (Impostazioni di compilazione).

11.  Salvare la scena e Project **(FILE**  >  **SAVE SCENE/FILE**  >  **SAVE PROJECT**).


## <a name="chapter-3---import-the-unity-package"></a>Capitolo 3: Importare il pacchetto Unity

> [!IMPORTANT]
> Se si vuole ignorare i componenti di configurazione di *Unity* di questo corso e continuare direttamente con il codice, è possibile scaricare il file [Azure-MR-309.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)importarlo nel progetto come pacchetto [**personalizzato.**](https://docs.unity3d.com/Manual/AssetPackages.html) Conterrà anche le DLL del capitolo successivo. Dopo l'importazione, continuare [**dal capitolo 6.**](#chapter-6---create-the-applicationinsightstracker-class)

> [!IMPORTANT]
> Per usare application Insights all'interno di Unity, è necessario importare la DLL, insieme alla DLL Newtonsoft. Esiste attualmente un problema noto in Unity che richiede la riconfigurazione dei plug-in dopo l'importazione. Questi passaggi (da 4 a 7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare application Insights nel proprio progetto, assicurarsi di aver scaricato [il file '.unitypackage', contenente i plug-in](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Procedere quindi come segue:

1.  Aggiungere il **file con estensione unitypackage** a Unity usando l'opzione di menu **Assets Import Package Custom Package \> \> (Importa pacchetto personalizzato** di asset).

2.  Nella casella **Import Unity Package (Importa** pacchetto Unity) visualizzata verificare che sia selezionato tutto il contenuto di Plugins (e including) Plugins (Plug-in inclusi). 

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-22.png)

3.  Fare clic **sul** pulsante Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Insights** in **Plugins (Plug-in)** nella visualizzazione Project e selezionare solo i plug-in *seguenti:*

    -   Microsoft.ApplicationInsights

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-23.png)

5.  Con questo *plug-in* selezionato, assicurarsi che l'opzione **Any Platform** (Qualsiasi piattaforma) sia deselezionata, quindi assicurarsi che anche **WSAPlayer** sia deselezionato **e** quindi fare clic su Apply **(Applica).** Questa operazione viene eseguita solo per verificare che i file siano configurati correttamente.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Contrassegnando i plug-in come questo, questi vengono configurati in modo da essere usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso di DLL che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la **cartella WSA,** all'interno **Insights** cartella . Verrà visualizzata una copia dello stesso file appena configurato. Selezionare questo file e quindi nel controllo verificare che l'opzione  **Any Platform** (Qualsiasi piattaforma) sia deselezionata, quindi verificare che sia selezionato solo **WSAPlayer.** Fare clic su **Applica**.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25.png)

7. È ora necessario seguire i **passaggi da 4 a 6,** ma per i *plug-in Newtonsoft.* Vedere lo screenshot seguente per l'aspetto del risultato.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capitolo 4: Configurare la fotocamera e i controlli utente

In questo capitolo si configurano la fotocamera e i controlli per consentire all'utente di vedere e spostarsi nella scena.

1.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello Gerarchia e quindi **scegliere**  >  **Crea vuoto.**

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-26.png)

2.  Rinominare il nuovo GameObject vuoto in **Camera Parent.**

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-27.png)

3.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello gerarchia, quindi su **3D Object (Oggetto 3D)** e **infine su Sphere**.

4.  Rinominare sphere in **Right Hand**.

5.  Impostare La **scala di trasformazione** della mano destra su **0.1, 0.1, 0.1**

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-28.png)

6.  Rimuovere il **componente Sphere Collider (Collisore** sfera) dalla mano destra facendo clic sull'ingranaggio nel componente Sphere *Collider (Collisore* sfera) e **quindi su Remove Component (Rimuovi componente).** 

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-29.png)

7.  Nel pannello Hierarchy (Gerarchia) trascinare **gli oggetti Main Camera (Fotocamera** principale) e Right **Hand** (Mano destra) **sull'oggetto Camera Parent (Padre** fotocamera).

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-30.png)

8.  Impostare posizione **di trasformazione** sia della fotocamera **principale che** dell'oggetto della **mano** destra su **0, 0, 0**.

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-31.png)

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capitolo 5- Configurare gli oggetti nella scena Unity

A questo punto si creeranno alcune forme di base per la scena, con cui l'utente può interagire.

1.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello *Gerarchia*, quindi in **Oggetto 3D** selezionare **Piano.**

2.  Impostare Posizione **trasformazione piano** su **0, -1, 0**.

3.  Impostare La scala di **trasformazione piano** su **5, 1, 5**.

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-33.png)

4.  Creare un materiale di base da usare con **l'oggetto Plane,** in modo che le altre forme siano più facili da visualizzare. Passare al pannello *Project ,* fare clic con il pulsante destro del mouse, quindi scegliere Crea **,** **quindi** Cartella per creare una nuova cartella. Assegnare il nome **Materials**.

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-34.png) ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-35.png)

5.  Aprire la cartella **Materials,** quindi fare clic con il pulsante destro del mouse, **scegliere Crea**, **quindi Material** per creare un nuovo materiale. Assegnare al file il **nome Blue.**

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-36.png) ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-37.png)

6.  Con il nuovo **materiale blu** selezionato, esaminare inspector *e* fare clic sulla finestra rettangolare accanto **ad Albedo.** Selezionare un colore blu (l'immagine seguente è **Colore esadecimale: \# 3592FFFF).** Fare clic sul pulsante Chiudi dopo aver scelto .

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-38.png)

7.  Trascinare il nuovo materiale dalla cartella **Materials** (Materiali) al piano appena **creato,** all'interno della scena (o rilasciarlo sull'oggetto **Plane** all'interno della *gerarchia).*

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-39.png)

8.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello *Gerarchia* e quindi scegliere **3D Object (Oggetto 3D) e Infine .**

    -  Con **l'opzione Dragon** selezionata, **modificarne la posizione di** *trasformazione* in: **-10, 1, 0**.

9.  Fare clic con il pulsante destro del mouse in un'area vuota nel *pannello Gerarchia*, quindi scegliere Oggetto **3D, Cubo**.

    -  Con il **cubo** selezionato, modificare **la posizione di** *trasformazione* in: **0, 0, 10**.

10. Fare clic con il pulsante destro del mouse in un'area vuota nel *pannello gerarchia* e quindi scegliere Oggetto **3D, Sphere.**

    -  Con la **sfera** selezionata, modificare la **posizione di** *trasformazione* in: **10, 0, 0**.

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Questi *valori position* sono *suggerimenti.* È possibile impostare le posizioni degli oggetti su qualsiasi valore, anche se è più semplice per l'utente dell'applicazione se le distanze degli oggetti non sono troppo distanze dalla fotocamera.

11. Quando l'applicazione è in esecuzione, deve essere in grado di identificare gli oggetti all'interno della scena. A tale scopo, è necessario contrassegnare gli oggetti. Selezionare uno degli oggetti e  nel pannello Inspector (Controllo) fare clic su **Add Tag (Aggiungi** tag) per scambiare *Inspector* (Controllo) con il pannello **Tags (& Layer).**

    ![Configurare gli oggetti nella scena unity ](images/AzureLabs-Lab309-41.png)![](images/AzureLabs-Lab309-42.png)

12. Fare clic **sul simbolo + (segno più)** e quindi digitare il nome del tag **come ObjectInScene**.

    ![Configurare gli oggetti nella scena unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Se si usa un nome diverso per il tag, è necessario assicurarsi che questa modifica sia stata apportata anche agli script *DataFromAnalytics*, *ObjectTrigger* e *Gaze* in un secondo momento, in modo che gli oggetti siano trovati e rilevati all'interno della scena.

13. Dopo aver creato il tag, è necessario applicarlo a tutti e tre gli oggetti. Da *Hierarchy*(Gerarchia) tieni premuto MAIUSC, quindi fai clic sugli oggetti **Cube**, **Cube** e **Sphere**, quindi nell'inspector (Controllo) fai clic sul menu a discesa accanto a **Tag** e infine sul tag *ObjectInScene* creato. 

    ![Configurare gli oggetti nella scena unity ](images/AzureLabs-Lab309-44.png)![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capitolo 6- Creare la classe ApplicationInsightsTracker

Il primo script da creare è **ApplicationInsightsTracker,** responsabile di:

1.  Creazione di eventi in base alle interazioni dell'utente da inviare applicazione Azure Insights.

2. Creazione di nomi di evento appropriati, a seconda dell'interazione dell'utente.

3. Invio di eventi all'istanza del servizio Insights applicazione.

Per creare questa classe:

1.  Fare clic con il pulsante destro *del mouse nel Project e* quindi scegliere **Crea**  >  **cartella.** Assegnare alla cartella il **nome Scripts**.

    ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Dopo avere **creato la** cartella Script, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro **del mouse su Crea** script  >  **C#.** Assegnare allo script **il nome ApplicationInsightsTracker**.

3.  Fare doppio clic sul nuovo script **ApplicationInsightsTracker** per aprirlo con **Visual Studio**.

4.  Aggiornare gli spazi dei nomi all'inizio dello script come indicato di seguito:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Impostare i **valori instrumentationKey, applicationId e API_Key** in  modo appropriato, usando le chiavi di servizio del portale di Azure, come indicato nel capitolo [1,](#chapter-1---the-azure-portal)passaggio 9 in poi.

6.  Aggiungere quindi i **metodi Start()** **e Awake(),** che verranno chiamati quando la classe viene inizializzata:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Aggiungere i metodi responsabili dell'invio degli eventi e delle metriche registrati dall'applicazione:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-7---create-the-gaze-script"></a>Capitolo 7 - Creare lo script sguardo fisso

Lo script successivo da creare è lo script **Sguardo** fisso. Questo script è responsabile della creazione di *un raycast* che verrà proiettato in avanti dalla fotocamera principale *per* rilevare l'oggetto che l'utente sta esaminando. In questo caso, *Raycast* dovrà identificare se l'utente sta esaminando un oggetto con il tag  **ObjectInScene** e quindi contare per quanto tempo l'utente guarda l'oggetto.

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script il **nome Gaze**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  È ora necessario aggiungere il codice per i metodi **Awake()** e **Start().**

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  **All'interno della classe Gaze** aggiungere il codice seguente nel metodo **Update()** per proiettare *un raycast* e rilevare l'hit di destinazione:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Aggiungere il **metodo ResetFocusedObject()** per inviare dati all'applicazione **Insights** quando l'utente ha esaminato un oggetto.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  A questo punto è stato completato lo script **Sguardo** fisso. Salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capitolo 8 - Creare la classe ObjectTrigger

Lo script successivo da creare è **ObjectTrigger,** responsabile di:

- Aggiunta dei componenti necessari per la collisione alla fotocamera principale.
- Rilevamento se la fotocamera si trova vicino a un oggetto contrassegnato **come ObjectInScene.**

Per creare lo script:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script **il nome ObjectTrigger**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio. Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capitolo 9: Creare la classe DataFromAnalytics

È ora necessario creare lo script **DataFromAnalytics,** responsabile di:

- Recupero dei dati di analisi sull'oggetto che è stato maggiormente avvicinato dalla fotocamera.
- Usando le *chiavi di servizio*, che consentono la comunicazione con l'istanza applicazione Azure Insights Service.
- Ordinamento degli oggetti nella scena, in base al quale è presente il numero di eventi più elevato.
- Modifica del colore del materiale, dell'oggetto più avvicinato, in *verde.*

Per creare lo script:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script **il nome DataFromAnalytics**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  All'interno dello script inserire quanto segue:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  **All'interno della classe DataFromAnalytics,** subito dopo il metodo **Start(),** aggiungere il metodo **seguente denominato FetchAnalytics().** Questo metodo è responsabile del popolamento dell'elenco di coppie chiave-valore, con *un GameObject* e un numero di eventi segnaposto. Inizializza quindi la coroutine **GetWebRequest().** La struttura di query della chiamata a *Application Insights* è disponibile anche all'interno di questo metodo, come endpoint *dell'URL di* query.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Subito sotto il **metodo FetchAnalytics(),** aggiungere un metodo denominato **GetWebRequest()**, che restituisce un *oggetto IEnumerator.* Questo metodo è responsabile della richiesta del numero di volte in cui un evento, corrispondente a un *GameObject* specifico, è stato chiamato all'interno *dell'applicazione Insights*. Quando tutte le query inviate sono state restituite, viene chiamato il metodo **DetermineWinner().**

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  Il metodo successivo è **DetermineWinner(),** che ordina l'elenco di *coppie GameObject* e *Int,* in base al numero di eventi più elevato. Modifica quindi il colore del materiale di *tale GameObject* in *verde* (come feedback per il fatto che abbia il numero più alto). Verrà visualizzato un messaggio con i risultati dell'analisi.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Aggiungere la struttura della classe che verrà usata per deserializzare l'oggetto JSON, ricevuto da *Application Insights*. Aggiungere queste classi nella parte inferiore del file di classe **DataFromAnalytics,** **all'esterno** della definizione della classe.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-10---create-the-movement-class"></a>Capitolo 10 - Creare la classe Movement

Lo  script di spostamento è lo script successivo che sarà necessario creare. È responsabile di:

- Spostamento della fotocamera principale in base alla direzione verso cui la fotocamera sta guardando.
- Aggiunta di tutti gli altri script agli oggetti della scena.

Per creare lo script:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script il **nome Movement**.

3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.

4.  Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  All'interno della  classe **Movement,** sotto il metodo **Update()** vuoto, inserire i metodi seguenti che consentono all'utente di usare il controller manuale per spostarsi nello spazio virtuale:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Aggiungere infine la chiamata al metodo all'interno **del metodo Update().**

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capitolo 11 - Configurazione dei riferimenti agli script

In questo capitolo è necessario inserire lo script **di spostamento** nell'elemento padre della fotocamera e impostarne le destinazioni di riferimento.  Lo script gestirà quindi l'inserimento degli altri script dove devono essere.

1.  Dalla cartella **Scripts** (Script) nel *pannello Project ,* trascinare lo script **Movement** (Spostamento) nell'oggetto Camera **Parent (Padre** fotocamera) che si trova in *Hierarchy Panel (Pannello gerarchia).*

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-48.png)

2.  Fare clic su **Camera Parent (Padre fotocamera).** Nel pannello *Hierarchy (Gerarchia)* trascinare l'oggetto **Right Hand** (Mano destra) dal *pannello Hierarchy* (Gerarchia) alla destinazione di **riferimento, Controller,** nel *pannello Inspector (Controllo).* Impostare **User Speed (Velocità utente)** **su 5,** come illustrato nell'immagine seguente.

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capitolo 12 - Compilare il progetto Unity

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è il momento di compilarlo da Unity.

1.  Passare a **Build Impostazioni**(**File**  >  **Build Impostazioni**).

2.  Nella finestra **Build Impostazioni** (Compila) fare clic su **Build (Compila).**

    ![Compilare il Project Unity nella soluzione UWP](images/AzureLabs-Lab309-50.png)

3.  Verrà **Esplora file** una finestra di dialogo che richiede un percorso per la compilazione. Creare una nuova cartella (facendo clic **su Nuova cartella** nell'angolo in alto a sinistra) e assegnare alla cartella il nome **BUILDS**.

    ![Compilare il Project Unity nella soluzione UWP](images/AzureLabs-Lab309-51.png)

    1.  Aprire la nuova **cartella BUILDS** e  creare un'altra cartella (usando ancora una volta Nuova cartella) e assegnare alla cartella il nome **MR Azure Application \_ \_ \_ Insights**.

        ![Compilare il Project Unity nella soluzione UWP](images/AzureLabs-Lab309-52.png)

    2.  Con la **cartella MR Azure Application \_ \_ \_ Insights** selezionata, fare clic **su Select Folder (Seleziona cartella).** La compilazione del progetto potrebbe richiedere circa un minuto.

4.  Dopo *La* compilazione **Esplora file** verrà visualizzato il percorso del nuovo progetto.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>Capitolo 13: Distribuire MR_Azure_Application_Insights app nel computer

Per distribuire l'app **\_ mr Azure Application \_ \_ Insights** nel computer locale:

1.  Aprire il file della soluzione dell'app **mr Azure Application \_ \_ \_ Insights** in **Visual Studio**.

2.  In **Piattaforma soluzione selezionare** **x86, Computer locale.**

3.  In Configurazione **soluzione selezionare** **Debug.**

    ![Compilare il Project Unity nella soluzione UWP](images/AzureLabs-Lab309-53.png)

4.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer.

5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.

6. Avviare l'applicazione di realtà mista.

7. Spostarsi nella scena, avvicinando gli oggetti e osservandoli, quando il servizio Informazioni dettagliate di *Azure* ha raccolto dati di eventi sufficienti, imposta l'oggetto che è stato maggiormente avvicinato in verde.

> [!IMPORTANT] 
> Mentre il tempo medio  di attesa per la raccolta di eventi e metriche da parte del servizio richiede circa 15 minuti, in alcuni casi potrebbe essere necessario fino a 1 ora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capitolo 14: Portale del servizio Insights applicazioni

Dopo aver aggirato la scena e aver fisso diversi oggetti, è possibile visualizzare i dati raccolti nel portale del servizio Insights *applicazioni.*

1.  Tornare al portale di Application Insights Service.

2.  Fare clic *su Esplora metriche*.

    ![Visualizzazione dei dati raccolti](images/AzureLabs-Lab309-54.png)

3.  Verrà aperta in una scheda contenente il grafico che rappresenta gli *eventi e le metriche* correlati all'applicazione. Come accennato in precedenza, la visualizzazione dei dati nel grafico potrebbe richiedere tempo (fino a 1 ora)

    ![Visualizzazione dei dati raccolti](images/AzureLabs-Lab309-55.png)

4.  Fare clic sulla *barra Eventi* in Total *of Events* by Application Version (Totale eventi per versione applicazione) per visualizzare una suddivisione dettagliata degli eventi con i relativi nomi.

    ![Visualizzazione dei dati raccolti](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>L'applicazione application Insights Service è stata completata

È stata compilata un'app di realtà mista che sfrutta application Insights service per monitorare l'attività dell'utente all'interno dell'app.

![risultato del corso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

Provare a generare, anziché creare manualmente, gli oggetti ObjectInScene e impostarne le coordinate sul piano all'interno degli script. In questo modo, è possibile chiedere ad Azure qual è l'oggetto più  diffuso (dai risultati di sguardo fisso o prossimità) e generare un oggetto aggiuntivo.

**Esercizio 2**

Ordinare i risultati Insights'applicazione in base all'ora, in modo da ottenere i dati più rilevanti e implementare i dati sensibili all'ora nell'applicazione.