---
title: Integrazione di Visione personalizzata di Azure
description: In questo corso viene illustrato come implementare Visione personalizzata di Azure in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, visione personalizzata di azure, servizi cognitivi di azure, servizi cloud di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: e5914b99e83df0c8ed7bf5aa26f11bf5b224b64107a6ca8e05994bc6ee41147f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190465"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Integrazione di Visione personalizzata di Azure

In questa esercitazione si imparerà a usare **Visione personalizzata di Azure**. Si caricherà un set di foto per associarle a un *oggetto tracciato*, caricarle nel servizio **Visione personalizzata** e avviare il processo di training. Si userà quindi il servizio per rilevare l'*oggetto tracciato* acquisendo foto dal feed della webcam.

## <a name="objectives"></a>Obiettivi

* Acquisire nozioni di base su Visione personalizzata di Azure
* Imparare a impostare la scena per usare il servizio Visione personalizzata di Azure nel progetto
* Scoprire come caricare, eseguire il training e rilevare le immagini

## <a name="understanding-azure-custom-vision"></a>Informazioni su Visione personalizzata di Azure

**Visione personalizzata di Azure** fa parte della famiglia di **Servizi cognitivi** e viene usato per il training dei classificatori di immagini. Il classificatore di immagini è un servizio di intelligenza artificiale che usa il modello con training per applicare tag corrispondenti. Questa funzionalità di classificazione verrà usata dall'applicazione per rilevare gli *oggetti tracciati*.

Altre informazioni su [Visione personalizzata di Azure](/azure/cognitive-services/custom-vision-service/home).

## <a name="preparing-azure-custom-vision"></a>Preparazione di Visione personalizzata di Azure

Prima di iniziare, è necessario creare un progetto di visione personalizzata. Il modo più rapido consiste nell'usare il portale Web.

Seguire questa [esercitazione introduttiva](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) per configurare l'account e il progetto fino alla sezione *Caricare e taggare le immagini*.

> [!WARNING]
> Per eseguire il training di un modello, è necessario disporre di almeno 2 tag e 5 immagini per ogni tag. Per usare questa applicazione, è necessario creare almeno un tag con 5 immagini, affinché il processo di training non abbia esito negativo in un secondo momento.

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**.

![Unity con la finestra Project che mostra il percorso del prefab ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

Da qui, trascinare il prefab **ObjectDetectionManager** nella gerarchia della scena.

![Unity con i campi di configurazione del componente script ObjectDetectionManager visualizzati in Inspector](images/mr-learning-azure/tutorial3-section4-step1-2.png)

Nella finestra Hierarchy (Gerarchia) individuare l'oggetto **ObjectDetectionManager** e selezionarlo.
Il prefab **ObjectDetectionManager** contiene il componente **ObjectDetectionManager (script)** e, come si può vedere dalla finestra Di controllo, dipende dalle impostazioni di Azure e Project predefinite.

## <a name="retrieving-azure-api-resource-credentials"></a>Recupero delle credenziali delle risorse API di Azure

Le credenziali necessarie per le impostazioni **ObjectDetectionManager (script)** possono essere recuperate dal portale di Azure e dal portale del servizio Visione personalizzata.

### <a name="retrieving-azure-settings-credentials"></a>Recupero delle credenziali Impostazioni Azure

Trovare e individuare la risorsa  visione personalizzata di tipo Servizi cognitivi creata nella sezione Preparazione della *scena* di questa esercitazione (selezionare il nome delle risorse di visione personalizzate seguito da *-Prediction).* Fare clic su *Panoramica* o *Chiavi ed endpoint* per recuperare le credenziali necessarie.

### <a name="retrieving-project-settings-credentials"></a>Recupero di Project Impostazioni credenziali

Nel dashboard [Visione personalizzata](https://www.customvision.ai/projects) aprire il progetto creato per questa esercitazione e fare clic sull'icona a forma di ingranaggio nell'angolo in alto a destra della pagina per aprire la pagina delle impostazioni. Qui nella sezione *Resources* (Risorse) a destra sono riportate le credenziali necessarie.

Dopo avere configurato correttamente **ObjectDetectionManager (script)** , trovare l'oggetto **SceneController** nella gerarchia della scena e selezionarlo.

![Unity con i campi di configurazione del componente script SceneController visualizzati in Inspector](images/mr-learning-azure/tutorial3-section4-step1-3.png)

Si noterà che il campo *Object Detection Manager* (Gestione rilevamento oggetti) nel componente **SceneController** è vuoto; trascinare **ObjectDetectionManager** dalla gerarchia a quel campo e salvare la scena.

![Unity con il componente script SceneController configurato](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>Acquisire e caricare immagini

Eseguire la scena e fare clic su **Set Object** (Imposta oggetto), quindi digitare il nome di uno degli **oggetti tracciati** creati nella [lezione precedente](mr-learning-azure-02.md). A questo punto, fare clic sul pulsante **Computer Vision** (Visione artificiale) nella parte inferiore della **Object Card** (Scheda oggetto).

Verrà aperta una nuova finestra in cui è necessario scattare sei foto per eseguire il training del modello per il riconoscimento delle immagini. Fare clic sul pulsante **Camera** (Fotocamera) ed eseguire un AirTap quando si osserva l'oggetto da tracciare e ripetere sei volte.

> [!TIP]
> Per migliorare il training del modello, provare ad acquisire ogni immagine da diverse angolazioni e in condizioni di illuminazione.

Quando le immagini sono sufficienti, fare clic sul pulsante **Train** (Esegui training) per avviare il processo di training del modello nel cloud. L'attivazione del training caricherà tutte le immagini e quindi inizierà il training. Questa operazione può richiedere un minuto o più. Un messaggio all'interno del menu indica lo stato di avanzamento e, quando risulta completato, è possibile arrestare l'applicazione

> [!TIP]
> **ObjectDetectionManager (script)** carica direttamente le immagini acquisite nel servizio Visione personalizzata. In alternativa, l'API di visione personalizzata accetta gli URL delle immagini; come esercizio, è possibile modificare **ObjectDetectionManager (script)** per caricare le immagini in un archivio BLOB.

## <a name="detect-objects"></a>Rilevare oggetti

A questo punto è possibile testare il modello con training, eseguire l'applicazione e dal *menu principale* fare clic su **Search Object** (Cerca oggetto) e digitare il nome dell'**oggetto tracciato** in questione. Quando viene visualizzata la **Object Card** (Scheda oggetto), fare clic sul pulsante **Custom Vision** (Visione personalizzata). Da qui, **ObjectDetectionManager** inizierà ad acquisire immagini in background dalla fotocamera e lo stato di avanzamento verrà indicato nel menu. Puntare la fotocamera sull'oggetto usato per eseguire il training del modello. Si noterà che dopo un breve periodo di tempo rileverà l'oggetto.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come usare Visione personalizzata di Azure per eseguire il training delle immagini e usare il servizio di classificazione per rilevare le immagini che corrispondono all'**oggetto tracciato** associato.

Nell'esercitazione successiva verrà spiegato come usare Ancoraggi nello spazio di Azure per collegare un *oggetto tracciato* a una posizione nel mondo fisico e come visualizzare una freccia che guiderà l'utente per tornare alla posizione collegata dell'oggetto tracciato.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Integrazione di Ancoraggi nello spazio di Azure](mr-learning-azure-04.md)