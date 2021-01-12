---
title: Uso del plug-in OpenXR per la realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR per la realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: c5d312161b7d0f4f832e8d09dbacf5af700ffd8d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108884"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Uso del plug-in OpenXR per la realtà mista per Unity

A partire da Unity versione 2020,2, il pacchetto di plug-in per la realtà mista di Microsoft OpenXR è disponibile tramite Gestione pacchetti Unity (UPM).

## <a name="prerequisites"></a>Prerequisiti

* Unity 2020,2 o versione successiva
* Plug-in OpenXR Unity 0.1.2 o versione successiva
* Visual Studio 2019 o versione successiva
* Installare il supporto della piattaforma **UWP** in Unity per le app HoloLens 2

> [!NOTE]
> Se si stanno compilando applicazioni VR in PC Windows, il plug-in OpenXR per realtà mista non è necessariamente obbligatorio. Tuttavia, è necessario installare il plug-in se si sta personalizzando il mapping del controller per i controller HP Reverb G2 o la creazione di app che funzionano sia con le cuffie HoloLens 2 sia con le cuffie VR.

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Installare il plug-in OpenXR per la realtà mista

Il progetto deve installare il plug-in **OpenXR** e i pacchetti di **gestione dei plug** -in XR prima di usare il plug-in OpenXR realtà mista. Se sono già stati installati, In caso contrario, l'installazione del plug-in OpenXR per la realtà mista li installerà automaticamente come dipendenze:

1. Nell'editor di Unity passare a **modifica > impostazioni progetto > gestione pacchetti**
2. Espandere la sezione **registri con ambito** , immettere le informazioni seguenti e selezionare **Salva**:
    * Imposta il **nome** su **Microsoft Mixed Reality**
    * Imposta **URL** su **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * Imposta **ambito/i** su **com. Microsoft. mixedreality**

3. In **Impostazioni avanzate** selezionare **Abilita pacchetti di anteprima**

![Screenshot della finestra di gestione pacchetti Unity aperta in Impostazioni progetto](images/openxr-img-01.png)

Gestione pacchetti Unity usa un file manifesto denominato *manifest.json* per determinare i pacchetti da installare e i registri da cui possono essere installati.

> [!IMPORTANT]
> OpenXR è ancora sperimentale in Unity e questo processo può variare nel tempo mentre si lavora per ottimizzare l'esperienza degli sviluppatori.

### <a name="registering-the-mixed-reality-dependency"></a>Registrazione della dipendenza della realtà mista

Quando il registro con ambito Microsoft Mixed Reality è stato aggiunto al manifesto, è possibile specificare il pacchetto OpenXR.

Per aggiungere il pacchetto OpenXR:

1. Aprire **[projectRoot]/Packages/manifest.js** in un editor di testo, ad esempio Visual Studio Code
    1. Per ottenerlo, fare clic con il pulsante destro del mouse su **pacchetti** nel riquadro sinistro della finestra del progetto. Quindi, fare clic su **Mostra in Esplora**.
    ![Screenshot dell'elenco di pacchetti nella finestra del progetto](images/packages.png)
1. Modificare la sezione relativa alle dipendenze dei *pacchetti/manifest.jsnel* file come indicato di seguito:

    > [!IMPORTANT]
    > Nel file manifesto potrebbero essere presenti più dipendenze di quelle illustrate qui. Non eliminare alcun oggetto, ma è sufficiente aggiungere la dipendenza OpenXR all'elenco.

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.2",
      }
    ```

1. Salvare il file, tornare all'editor di Unity e aprire **Gestione pacchetti** per verificare che il plug-in sia installato:

    ![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con il plug-in di OpenXR realtà mista evidenziato](images/openxr-img-03.png)

    > [!Note]
    > Se il pacchetto OpenXR viene rimosso usando Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i passaggi descritti in precedenza.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configurazione della gestione dei plug-in XR per OpenXR

Per impostare OpenXR come runtime in Unity:

1. Nell'editor di Unity passare a **modifica > impostazioni progetto**
2. Nell'elenco delle impostazioni selezionare **Gestione plug** -in XR
3. Selezionare le caselle **Inizializza XR all'avvio** e **OpenXR (anteprima)**
4. Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il **set di funzionalità di Microsoft HoloLens**

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-img-05.png)

> [!IMPORTANT]
> Se viene visualizzata un'icona di avviso rossa accanto a plug-in **OpenXR (anteprima)**, fare clic sull'icona e selezionare **Correggi tutto** prima di continuare. Per rendere effettive le modifiche, potrebbe essere necessario riavviare l'editor di Unity.

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

A questo punto si è pronti per iniziare a sviluppare con OpenXR in Unity.  Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.

## <a name="optimization"></a>Optimization

Se si sta sviluppando per HoloLens 2, passare a **realtà mista> OpenXR > applicare le impostazioni di progetto consigliate per HoloLens 2** per ottenere prestazioni migliori per le app.

![Screenshot della voce di menu della realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Provare le scene di esempio di Unity

Per usare uno o più degli esempi, installare [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) da **Gestione pacchetti**:

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con AR Foundation evidenziato](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>Esempi di HoloLens 2

1. Nell'editor di Unity passare a **finestra > gestione pacchetti**
2. Nell'elenco dei pacchetti selezionare il plug-in **OpenXR realtà mista**
3. Individuare l'esempio nell'elenco degli **esempi** e selezionare **Importa** .

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con la realtà mista OpenXR plug-in selezionato ed esempi pulsante di importazione evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Quando viene aggiornato un pacchetto, Unity offre la possibilità di aggiornare gli esempi importati.  L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.

## <a name="using-mrtk-with-openxr-support"></a>Uso di MRTK con il supporto OpenXR

MRTK Unity supporta il plug-in OpenXR realtà mista a partire dalla versione 2.5.3.  I plug-in MRTK possono essere installati dagli stessi registri con ambito impostati quando si [installa il plug-in OpenXR realtà mista](#installing-the-mixed-reality-openxr-plugin). Per informazioni più dettagliate, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Aggiungere i pacchetti seguenti in **[projectRoot]/Packages/manifest.js** nel file:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
```

2. Passare allo script del componente MixedReality Toolkit nel controllo e passare al profilo **DefaultOpenXRConfigurationProfile** :

![Screenshot del cambio della configurazione di MRTK nel componente del Toolkit per realtà mista del controllo](images/openxr-img-11.png)

### <a name="known-issues"></a>Problemi noti 

Quando si usa la funzionalità di rilevamento della mano, aggiungere la riga seguente nel file **assets/MixedRealityToolkit. generated/link.xml** :

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a>Passaggi successivi

Ora che il progetto è stato configurato per OpenXR ed è possibile accedere agli esempi, vedere quali [funzionalità](openxr-supported-features.md) sono attualmente supportate nel plug-in OpenXR.

## <a name="have-feedback"></a>Inviare commenti e suggerimenti?

OpenXR è ancora in fase di sperimentazione, quindi saremmo lieti di ricevere commenti e suggerimenti per aiutarti a migliorarlo. Ci troviamo nei [Forum di Unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e **HoloLens 2** o la **realtà mista di Windows**.

## <a name="see-also"></a>Vedere anche

* [Configurazione del progetto senza MRTK](configure-unity-project.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
