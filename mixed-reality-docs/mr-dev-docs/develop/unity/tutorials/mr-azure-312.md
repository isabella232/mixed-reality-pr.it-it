---
title: HoloLens (prima generazione) e Azure 312 - Integrazione del bot
description: Completare questo corso per informazioni su come creare e distribuire un bot usando Microsoft Bot Framework v4 e comunicare con esso in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, visione computer, hololens, immersive, vr, microsoft bot framework v4, bot app Web, bot framework, microsoft bot, Windows 10, Visual Studio
ms.openlocfilehash: 61a39806c2b434cb85d39a9b208ea8659ec8cbc301d8955ee1330bda4149f0db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189811"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a>HoloLens (prima generazione) e Azure 312: integrazione del bot

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

In questo corso si apprenderà come creare e distribuire un bot usando la Microsoft Bot Framework V4 e comunicare con esso tramite un'Windows Mixed Reality virtuale. 

![](images/AzureLabs-Lab312-00.png)

La **Microsoft Bot Framework V4** è un set di API progettate per fornire agli sviluppatori gli strumenti per creare un'applicazione bot estendibile e scalabile. Per altre informazioni, visitare la [Microsoft Bot Framework o](https://dev.botframework.com/) il repository [Git V4.](https://github.com/Microsoft/botbuilder-dotnet/wiki)

Al termine di questo corso, sarà stata creata un'Windows Mixed Reality, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento tocco per** avviare il bot in ascolto della voce degli utenti.
2. Quando l'utente ha detto qualcosa, il bot tenterà di fornire una risposta.
3. Visualizzare la risposta dei bot come testo, posizionato vicino al bot, nella scena unity.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è progettato per illustrare come integrare un servizio di Azure con il progetto Unity. È compito dell'utente usare le conoscenze acquisite da questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 312: Integrazione di bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in HoloLens, è anche possibile applicare ciò che si apprende in questo corso per Windows Mixed Reality visori vr immersivi. Poiché i visori VR immersive non hanno fotocamere accessibili, è necessaria una fotocamera esterna connessa al PC. Man mano che si segue il corso, verranno visualizzati note sulle modifiche che potrebbe essere necessario applicare per supportare visori VR immersive.

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
- Accesso a Internet per Azure e per il recupero di bot di Azure. Per altre informazioni, [seguire questo collegamento.](https://dev.botframework.com/)

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione del HoloLens, visitare l'articolo HoloLens [setup .](/hololens/hololens-setup) 
3.  È buona idea eseguire calibrazione e ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (talvolta può essere utile per eseguire queste attività per ogni utente). 

Per informazioni sulla calibrazione, seguire questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo HoloLens Sensor Tuning](/hololens/hololens-updates).

## <a name="chapter-1--create-the-bot-application"></a>Capitolo 1: Creare l'applicazione Bot

Il primo passaggio consiste nel creare il bot come applicazione Web ASP.Net Core locale. Dopo aver completato e testato il test, lo si pubblicherà nel portale di Azure.

1.  Aprire Visual Studio. Creare un nuovo progetto, selezionare **Applicazione Web ASP NET Core** come tipo di progetto (nella sottosezione .NET Core) e chiamarla **MyBot**. Fare clic su **OK**.

2.  Nella finestra visualizzata selezionare **Vuoto.** Assicurarsi anche che la destinazione sia impostata su **ASP NET Core 2.0** e che l'opzione Autenticazione sia impostata su **Nessuna autenticazione**. Fare clic su **OK**.  

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-01.png)

3.  La soluzione verrà ora aperta. Fare clic con il pulsante destro del mouse su **Solution Mybot** nel **Esplora soluzioni** e scegliere Gestisci NuGet pacchetti per **la soluzione**. 

    ![Creare l'applicazione Bot](images/AzureLabs-Lab312-02.png)

4.  Nella scheda **Sfoglia** cercare **Microsoft.Bot.Builder.Integration.AspNet.Core** (assicurarsi di aver selezionato Includi **versione non** definitiva). Selezionare il pacchetto versione **4.0.1-preview** e selezionare le caselle di progetto. Fare quindi clic su **Installa**. Sono state ora installate le librerie necessarie per **l'Bot Framework v4.** Chiudere la NuGet pagina.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-03.png)

5.  Fare clic con il pulsante destro *del Project,* **MyBot**, nella Esplora soluzioni **fare** clic su **Aggiungi** **|** **classe**.

    ![Creare l'applicazione Bot](images/AzureLabs-Lab312-04.png)

6.  Assegnare alla classe **il nome MyBot** e fare clic **su Aggiungi**.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-05.png)

7.  Ripetere il punto precedente per creare un'altra classe denominata **ConversationContext**. 

8.  Fare clic con il pulsante destro del mouse su **wwwroot** **nel Esplora soluzioni** e scegliere **Aggiungi** **|** **nuovo elemento**. Selezionare  **Pagina HTML** (è possibile trovarla nella sottosezione Web). Assegnare al file **default.html**. Fare clic su **Aggiungi**.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-06.png)

9.  L'elenco di classi/oggetti nel **Esplora soluzioni** dovrebbe essere simile all'immagine seguente.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-07.png)

10. Fare doppio clic sulla **classe ConversationContext.** Questa classe è responsabile della gestione delle variabili usate dal bot per mantenere il contesto della conversazione. Questi valori di contesto della conversazione vengono mantenuti in un'istanza di questa classe, perché qualsiasi istanza della **classe MyBot** verrà aggiornata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente alla classe :

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Fare doppio clic sulla **classe MyBot.** Questa classe ospiterà i gestori chiamati da qualsiasi attività in ingresso dal cliente. In questa classe si aggiungerà il codice usato per compilare la conversazione tra il bot e il cliente. Come accennato in precedenza, un'istanza di questa classe viene inizializzata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente a questa classe:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Fare doppio clic sulla **classe Startup.** Questa classe inizializza il bot. Aggiungere il codice seguente alla classe :

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Aprire il file **di** classe Program e verificare che il codice in esso sia identico al seguente:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Ricordarsi di salvare le modifiche. A tale scopo, passare a **File** Save All (Salva tutto) dalla barra degli strumenti nella  >  parte superiore Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capitolo 2: Creare il servizio Azure Bot

Dopo aver compilato il codice per il bot, è necessario pubblicarlo in un'istanza del servizio *Bot app Web* nel portale di Azure. Questo capitolo illustra come creare e configurare il servizio Bot in Azure e quindi pubblicarvi il codice.

1.  Accedere prima di tutto al portale di Azure ( https://portal.azure.com) . 

    1. Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di laboratorio, chiedere all'insegnante o a uno dei protori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su Crea una risorsa nell'angolo in alto **a** sinistra, cercare *Bot app Web* e fare clic su **Invio.**

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  La nuova pagina fornirà una descrizione del *servizio Bot app Web.* Nella parte inferiore sinistra di questa pagina selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  Dopo aver fatto clic su **Crea:**

    1. Inserire il nome **desiderato per** questa istanza del servizio.
    2. Selezionare una **Sottoscrizione**.
    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi corsi) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, [seguire questo collegamento](/azure/azure-resource-manager/resource-group-portal)

    4. Determinare la località per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione si trova idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.
    5. Selezionare il **piano tariffario** appropriato. Se è la prima volta che si crea un servizio Bot app *Web,* dovrebbe essere disponibile un livello gratuito (denominato F0).
    6. **Il nome** dell'app può essere lasciato uguale al *nome del bot*. 
    7. Lasciare il *modello bot* come **Basic (C#).**
    8. *Il piano di servizio app o la* località devono essere stati compilati automaticamente per l'account.
    9. Impostare il **Archiviazione di Azure** che si vuole usare per ospitare il bot. Se non è già presente, è possibile crearlo qui.
    10. È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.
    11. Fare clic su Crea.
 
        ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-10.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio di Azure. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  A questo punto è necessario configurare una funzionalità denominata **Direct Line** consentire all'applicazione client di comunicare con questo servizio Bot. Fare clic **su Canali** e quindi nella sezione Aggiungi un canale **in primo** piano fare clic su Configura **Direct Line canale**.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-14.png)

10. In questa pagina sono presenti le chiavi segrete **che** consentiranno all'app client di eseguire l'autenticazione con il bot. Fare clic **sul pulsante** Mostra ed eseguire una copia di una delle chiavi visualizzate, in quanto sarà necessaria più avanti nel progetto. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capitolo 3: Pubblicare il bot nel servizio Azure Web App Bot

Ora che il servizio è pronto, è necessario pubblicare il codice del bot creato in precedenza nel servizio Bot app Web appena creato.

> [!NOTE] 
> Sarà necessario pubblicare il bot nel servizio di Azure ogni volta che si apportano modifiche alla soluzione/al codice del bot.

1.  Tornare alla soluzione Visual Studio creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse sul progetto **MyBot,** **nella Esplora soluzioni** fare clic su **Publish (Pubblica).**

    ![Pubblicare il bot nel servizio Bot app Web di Azure](images/AzureLabs-Lab312-16.png)

3.  Nella pagina Selezionare una destinazione di pubblicazione fare clic su  Servizio **app,** quindi su Seleziona esistente e infine su Crea profilo. Se non è visibile, potrebbe essere necessario fare clic sulla freccia *a* discesa accanto al pulsante Pubblica.  

    ![Pubblicare il bot nel servizio Bot app Web di Azure](images/AzureLabs-Lab312-17.png)

4. Se non si è ancora connessi all'account Microsoft, è necessario farlo qui.
5. Nella pagina **Pubblica** è necessario impostare la  stessa sottoscrizione usata per la creazione *del servizio Bot app Web.* Impostare quindi **Visualizza come** Gruppo **di** risorse e, nella struttura di cartelle a discesa, selezionare il gruppo **di** risorse creato in precedenza. Fare clic su **OK**. 

    ![Pubblicare il bot nel servizio Bot app Web di Azure](images/AzureLabs-Lab312-18.png)

6.  Fare clic sul **pulsante Publish** (Pubblica) e attendere che il bot venga pubblicato (l'operazione potrebbe richiedere alcuni minuti).

    ![Pubblicare il bot nel servizio Bot app Web di Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capitolo 4: Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity e* fare clic su New **(Nuovo).** 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-20.png)

2.  È ora necessario specificare un nome di progetto Unity. Inserire **HoloLens bot**. Assicurarsi che il modello di progetto sia impostato su **3D.** Impostare Il **percorso su** un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica > preferenze** e quindi dalla nuova finestra passare a Strumenti **esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-22.png)

4.  Passare quindi a **File > Build Impostazioni** e selezionare Universal Windows **Platform** e quindi fare clic sul pulsante **Switch Platform** (Cambia piattaforma) per applicare la selezione.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-23.png)

5.  Sempre in **File > Build Impostazioni** e assicurarsi che:

    1.  **Dispositivo di destinazione** impostato su **HoloLens**

        > Per i visori VR immersive, impostare **Dispositivo di destinazione** su Qualsiasi *dispositivo.*

    2.  **Il tipo di** compilazione è impostato **su D3D**

    3.  **L'SDK** è impostato su **Più recente installato**

    4.  **Visual Studio versione è** impostata su **Versione più recente installata**

    5.  **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**

    6.  Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.
        
            ![Configurare il progetto Unity](images/AzureLabs-Lab312-24.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

             ![Configurare il progetto Unity](images/AzureLabs-Lab312-25.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file*: digitare **BotScene** e quindi fare clic su **Salva.**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-26.png)

    7. Le impostazioni rimanenti, in **Build Impostazioni**, per il momento devono essere lasciato come predefinite.

6. Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova *il controllo.* 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-27.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1. **La versione del runtime di** scripting deve essere sperimentale (equivalente a NET **4.6)**; La modifica di questa impostazione richiederà il riavvio dell'editor.
        2. **Il back-end di** scripting deve **essere .NET**
        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-28.png)
      
    2. **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:

        - **InternetClient**
        - **Microfono**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-29.png)

    3. Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Configurare il progetto Unity](images/AzureLabs-Lab312-30.png)

8.  Tornare alla *compilazione Impostazioni* i _progetti C# Unity_ non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).
10. Salvare la scena e il progetto **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).


## <a name="chapter-5--camera-setup"></a>Capitolo 5: Configurazione della fotocamera

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il codice, è possibile scaricare il [](https://docs.unity3d.com/Manual/AssetPackages.html)file [Azure-MR-312-Package.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [7.](#chapter-8--create-the-botobjects-class)

1.  Nel pannello *Hierarchy (Gerarchia)* selezionare **Main Camera (Fotocamera principale).** 
2.  Dopo la selezione, sarà possibile visualizzare tutti i componenti della fotocamera **principale** nel *pannello Inspector (Controllo).*

    1. **L'oggetto Camera** deve essere denominato **Main Camera (si** noti l'ortografia)
    2. Il tag della **fotocamera principale** deve essere impostato su **MainCamera** (si noti l'ortografia)
    3. Assicurarsi che **Posizione trasformazione** sia impostato su **0, 0, 0**
    4. Impostare **Cancella flag** su Colore a **tinta unita.**
    5. Impostare Il **colore di** sfondo del componente Fotocamera **su Nero, Alfa 0 (codice esadecimale: #00000000)**

    ![configurazione della fotocamera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capitolo 6: Importare la libreria Newtonsoft

Per facilitare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio Bot, è necessario scaricare **la libreria Newtonsoft.** Una versione compatibile già organizzata con la struttura di cartelle unity corretta è disponibile [qui.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage) 

Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.

1.  Aggiungere il *file con estensione unitypackage* a Unity usando l'opzione di menu **Assets**  >  **Import Package** Custom  >  **Package (Importa** pacchetto personalizzato di asset).

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  Nella casella **Import Unity Package (Importa** pacchetto Unity) visualizzata verificare che sia selezionato tutto il contenuto di Plugins (e including) Plugins (Plug-in inclusi). 

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Fare clic **sul** pulsante Importa per aggiungere gli elementi al progetto.

4.  Passare alla **cartella Newtonsoft** in **Plugins (Plug-in)** nella visualizzazione del progetto e selezionare il plug-in Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Dopo avere selezionato il plug-in Newtonsoft, assicurarsi che l'opzione **Any Platform** (Qualsiasi piattaforma) sia deselezionata, quindi assicurarsi che anche **WSAPlayer** sia deselezionato, quindi fare clic su Apply **(Applica).** Questa operazione viene eseguita solo per verificare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Contrassegnare questi plug-in per configurarli in modo che siano usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la **cartella WSA** all'interno della **cartella Newtonsoft.** Verrà visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nel controllo verificare che
    -   **Qualsiasi piattaforma** **è deselezionata** 
    -   **È selezionato** **solo WSAPlayer** 
    -   **L'opzione Dont process** (Non **processo) è selezionata**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capitolo 7: Creare il BotTag

1.  Creare un nuovo **oggetto Tag** denominato **BotTag.** Selezionare la fotocamera principale nella scena. Fare clic sul menu a discesa Tag nel pannello Inspector (Controllo). Fare clic **su Aggiungi tag.**

    ![configurazione della fotocamera](images/AzureLabs-Lab312-32.png)
 
2.  Fare clic sul **+** simbolo. Assegnare al nuovo **tag il** nome **BotTag** e *salvare*.

    ![configurazione della fotocamera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Non applicare** **botTag** alla fotocamera principale. Se questa operazione è stata accidentalmente eseguita, assicurarsi di modificare di nuovo il tag Main Camera (Fotocamera principale) in *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capitolo 8: Creare la classe BotObjects

Il primo script che è necessario creare è la classe **BotObjects,** che è una classe vuota creata in modo che una serie di altri oggetti classe possa essere archiviata all'interno dello stesso script e accessibile da altri script nella scena.

La creazione di questa classe è esclusivamente una scelta a livello di architettura. Questi oggetti potrebbero invece essere ospitati nello script bot che verrà creato più avanti in questo corso.

Per creare questa classe: 

1.  Fare clic con il pulsante destro *del mouse nel Project e* quindi scegliere > **cartella**. Assegnare alla cartella il **nome Scripts**. 

    ![Creare la cartella scripts.](images/AzureLabs-Lab312-36.png)

2.  Fare doppio clic sulla **cartella Script** per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse **e scegliere > script C#.** Assegnare allo script **il nome BotObjects**. 

3.  Fare doppio clic sul nuovo script **BotObjects** per aprirlo con **Visual Studio**.

4.  Eliminare il contenuto dello script e sostituirlo con il codice seguente:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-9--create-the-gazeinput-class"></a>Capitolo 9: Creare la classe GazeInput

La classe successiva che si creerà è **la classe GazeInput.** Questa classe è responsabile di:

- Creazione di un cursore che rappresenterà *lo sguardo* fisso del lettore.
- Rilevamento di oggetti rilevati dallo sguardo fisso del giocatore e con un riferimento agli oggetti rilevati.

Per creare questa classe: 

1.  Passare alla cartella **Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse **all'interno della cartella Create > C# Script**. Chiamare lo script **GazeInput**. 
3.  Fare doppio clic sul nuovo script **GazeInput** per aprirlo con **Visual Studio**.
4.  Inserire la riga seguente a destra sopra il nome della classe:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Aggiungere quindi le variabili seguenti all'interno **della classe GazeInput,** sopra il **metodo Start():**

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  È necessario **aggiungere il codice** per il metodo Start(). Verrà chiamato quando la classe inizializza:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implementare un metodo che crea un'istanza e configura il cursore sguardo fisso: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implementare i metodi che configurano il raycast dalla fotocamera principale e tengono traccia dell'oggetto attivo corrente.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-10--create-the-bot-class"></a>Capitolo 10: Creare la classe Bot

Lo script che si creerà ora è denominato **Bot**. Questa è la classe principale dell'applicazione, che archivia: 

- Credenziali del bot app Web
- Metodo che raccoglie i comandi vocali dell'utente
- Metodo necessario per avviare conversazioni con il bot app Web 
- Metodo necessario per inviare messaggi al bot app Web 

Per inviare messaggi al servizio Bot, la coroutine **SendMessageToBot()** compila un'attività, ovvero un oggetto riconosciuto dal Bot Framework come dati inviati dall'utente. 
 
Per creare questa classe: 

1. Fare doppio clic sulla **cartella Script** per aprirla. 
2. Fare clic con il pulsante destro del **mouse all'interno** della **cartella Script e scegliere > script C#.** Assegnare allo script il **nome Bot**. 
3. Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4. Aggiornare gli spazi dei nomi in modo che siano uguali ai seguenti, all'inizio della **classe** Bot:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. **All'interno della** classe Bot aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Assicurarsi di inserire la **chiave privata del bot** nella variabile **botSecret.** All'inizio di questo corso si noterà la chiave privata del **bot,** nel **[capitolo 2,](#chapter-2---create-the-azure-bot-service)passaggio 10.**

7. È ora necessario aggiungere il codice per **Awake()** e **Start().** 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Aggiungere i due gestori chiamati dalle librerie di riconoscimento vocale all'inizio e alla fine dell'acquisizione vocale. *DictationRecognizer interromperà automaticamente* l'acquisizione della voce dell'utente quando l'utente smette di parlare.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. Il gestore seguente raccoglie il risultato dell'input vocale dell'utente e chiama la coroutine responsabile dell'invio del messaggio al servizio Bot app Web.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. La coroutine seguente viene chiamata per avviare una conversazione con il bot. Si noterà che una volta completata la chiamata di conversazione, chiamerà **SendMessageToCoroutine()** passando una serie di parametri che impostano l'attività da inviare al servizio Bot come messaggio vuoto. Questa operazione viene eseguita per richiedere al servizio Bot di avviare il dialogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. La coroutine seguente viene chiamata per compilare l'attività da inviare al servizio Bot. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. La coroutine seguente viene chiamata per richiedere una risposta dopo l'invio di un'attività al servizio Bot. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. L'ultimo metodo da aggiungere a questa classe è necessario per visualizzare il messaggio nella scena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > È possibile che venga visualizzato un errore nella console dell'editor di Unity, in caso di mancanza **della classe SceneOrganiser.** Ignorare questo messaggio, poiché questa classe verrà creata più avanti nell'esercitazione.

14.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-11--create-the-interactions-class"></a>Capitolo 11: Creare la classe Interactions

La classe che si creerà ora è denominata **Interazioni.** Questa classe viene usata per rilevare l HoloLens'input tocco dell'utente. 

Se l'utente tocca mentre esamina l'oggetto *Bot* nella scena e il bot è pronto per  l'ascolto degli input vocali, l'oggetto Bot cambierà colore in rosso e inizierà ad ascoltare gli input vocali. 

Questa classe eredita dalla classe **GazeInput** e quindi è in grado di fare riferimento al metodo **Start()** e alle variabili da tale classe, denotato dall'uso di **base**. 
 
Per creare questa classe:

1.  Fare doppio clic sulla **cartella Script** per aprirla. 
2.  Fare clic con il pulsante destro del **mouse nella cartella Script** e scegliere Crea > script **C#.** Assegnare allo script **il nome Interactions**. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi e l'ereditarietà della classe in modo che siano uguali ai seguenti, nella parte superiore della **classe Interactions:**

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  **All'interno della classe Interactions** aggiungere la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Aggiungere quindi il **metodo Start():**

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Aggiungere il gestore che verrà attivato quando l'utente esegue il movimento di tocco davanti alla HoloLens fotocamera

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capitolo 12: Creare la classe SceneOrganiser

L'ultima classe richiesta in questo lab è denominata **SceneOrganiser**. Questa classe configura la scena a livello di codice, aggiungendo componenti e script alla fotocamera principale e creando gli oggetti appropriati nella scena.
 
Per creare questa classe:

1.  Fare doppio clic sulla **cartella Script** per aprirla. 
2.  Fare clic con il pulsante destro del **mouse nella cartella Script** e scegliere Crea > script **C#.** Assegnare allo script **il nome SceneOrganiser**. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  **All'interno della classe SceneOrganiser** aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Aggiungere quindi i **metodi Awake()** **e Start():**

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto Bot nella scena e della configurazione dei parametri e dei componenti:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto dell'interfaccia utente nella scena, che rappresenta le risposte dal bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*
9.  Nell'editor unity trascinare lo script **SceneOrganiser** dalla cartella Script alla fotocamera principale. Il componente SceneElettura dovrebbe ora essere visualizzato nell'oggetto Fotocamera principale, come illustrato nell'immagine seguente.

    ![Creare la servizio Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capitolo 13 - Prima della compilazione

Per eseguire un test approfondito dell'applicazione, è necessario eseguire il sideload dell'applicazione HoloLens.
Prima di procedere, assicurarsi che:

-   Tutte le impostazioni indicate nel [**capitolo 4**](#chapter-4--set-up-the-unity-project) sono impostate correttamente. 
-   Lo script **SceneOrganiser** è collegato **all'oggetto Fotocamera** principale. 
-   Nella classe **Bot** assicurarsi di aver inserito la chiave privata **bot** nella **variabile botSecret.**

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capitolo 14: Compilare e eseguire il sideload nel HoloLens

Tutto il necessario per la sezione Unity di questo progetto è stato completato, quindi è il momento di compilarlo da Unity.

1.  Passare a **Build Impostazioni**, File > **Build Impostazioni...**.
2.  Nella finestra **Compila Impostazioni** fare clic su **Compila**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab312-38.png)

3.  Se non è già presente, selezionare **Unity C# Projects**.
4.  Fare clic su **Compila**. Unity avvierà una **Esplora file,** in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome **App**. Quindi, con la **cartella App** selezionata, fare clic su **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella **cartella App.** 
6.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una finestra **Esplora file** nel percorso della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà notificata l'aggiunta di una nuova finestra).

## <a name="chapter-15--deploy-to-hololens"></a>Capitolo 15: Distribuire in HoloLens

Per eseguire la distribuzione HoloLens:

1.  Sarà necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore.** Per eseguire questa operazione:

    1. Mentre si indossa il HoloLens, aprire il **Impostazioni**.
    2. Passare a **Impostazioni & Internet > Wi-Fi > opzioni avanzate**
    3. Prendere nota **dell'indirizzo IPv4.**
    4. Tornare quindi a Impostazioni **e** quindi a Update & Security > for Developers (Aggiorna & Sicurezza > **per sviluppatori)** 
    5. Impostare la modalità sviluppatore attivata.

2.  Passare alla nuova build di Unity (cartella **App)** e aprire il file di soluzione con **Visual Studio**.
3.  In **Configurazione soluzione selezionare** **Debug**.
4.  In **Piattaforma soluzione selezionare** **x86**, **Computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.
6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel HoloLens, pronto per l'avvio.

    > [!NOTE]
    > Per eseguire la distribuzione in visore vr immersivo, impostare Piattaforma **soluzione** su *Computer* locale e impostare Configurazione su *Debug*, con *x86* come **Piattaforma**.  Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capitolo 16: Uso dell'applicazione nel HoloLens

- Dopo aver avviato l'applicazione, il bot verrà visualizzato come una sfera blu davanti.

- Usare il **movimento tocco** mentre si guarda la sfera per avviare una conversazione. 
 
- Attendere l'avvio della conversazione .L'interfaccia utente visualizza un messaggio quando si verifica. Dopo aver ricevuto il messaggio introduttivo dal bot, toccare di nuovo il bot in modo che si trasformi in rosso e inizi ad ascoltare la voce. 

- Quando si smette di parlare, l'applicazione invierà il messaggio al bot e si riceverà una risposta che verrà visualizzata nell'interfaccia utente. 

- Ripetere il processo per inviare altri messaggi al bot (è necessario toccare ogni volta che si vuole inviare un messaggio).

Questa conversazione illustra come il bot può conservare le informazioni (nome), fornendo allo stesso tempo informazioni note (ad esempio gli articoli stoccati).

#### <a name="some-questions-to-ask-the-bot"></a>Alcune domande da porre al bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Applicazione Bot app Web (v4) completata

È stata creata un'app di realtà mista che sfrutta il bot dell'app Web di Azure, Microsoft Bot Framework v4.

![Prodotto finale](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

La struttura della conversazione in questo lab è molto semplice. Usare Microsoft LUIS per offrire al bot funzionalità di comprensione del linguaggio naturale.

### <a name="exercise-2"></a>Esercizio 2

Questo esempio non include l'interruzione di una conversazione e il riavvio di una nuova conversazione. Per completare la funzionalità Bot, provare a implementare la chiusura della conversazione.