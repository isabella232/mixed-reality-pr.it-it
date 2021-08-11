---
title: Progettare ambienti immersivi personalizzati
description: Informazioni su come Windows Mixed Reality ambienti home personalizzati.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, realtà mista, realtà virtuale, REALTÀ VIRTUALE, MR, Home, ambienti personalizzati, luoghi, casa di servizio, skyloft, utente, creare, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: c0f006d3e05cb0892a0a9b2014a4d46a0668f628cf369e38c63c83756148d778
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198602"
---
# <a name="design-your-own-immersive-environments"></a>Progettare ambienti immersivi personalizzati

>[!NOTE]
>Si tratta di una funzionalità sperimentale. Provare a farlo, ma non c'è da aspettarsi se tutto non funziona come previsto. Microsoft sta valutando la fattibilità di questa funzionalità e l'interesse a usarla, quindi è possibile segnalare l'esperienza (e gli eventuali bug rilevati) nei forum per [sviluppatori](https://forums.hololens.com/categories/custom-home-environments).

A partire dall'aggiornamento di Windows 10 aprile [2018,](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)è stata abilitata una funzionalità sperimentale che consente di aggiungere ambienti personalizzati alla selezione Località (nel menu Start) da usare come home [Windows Mixed Reality.](../discover/navigating-the-windows-mixed-reality-home.md) Windows Mixed Reality ha due ambienti predefiniti, Casa sulla scogliera e Skyloft, è possibile scegliere come casa. La creazione di ambienti personalizzati consente di espandere l'elenco con le proprie creazioni. Questa funzionalità verrà presto disponibile per valutare l'interesse di autori e sviluppatori. Vedere quali tipi di mondo si creano e comprendere come si lavora con diversi strumenti di creazione.

Quando si usa un ambiente personalizzato, si noterà che il teletrasporto, l'interazione con le app e il posizionamento di ologrammi funzionano esattamente come in Casa sulla scogliera e Skyloft. È possibile esplorare il Web in un panorama circostante o riempire una città con ologrammi. Le possibilità sono infinite.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Ambienti home personalizzati</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Prova di un ambiente di esempio

È stato creato un ambiente di esempio che illustra alcune delle possibilità creative degli ambienti domestici personalizzati. Per provarlo, seguire questa procedura:
1. [Scaricare l'ambiente dell'isola Islande di esempio](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (punti di collegamento all'eseguibile autoestraente).

    ![Ambiente di esempio dell'isola Dell'Isola Del Nord](images/FantasyLand.jpg)<br>
    *Ambiente di esempio dell'isola Dell'Isola Del Nord*<br>

2. Eseguire il **fileFantasy_Island.exe** scaricato.

    > [!NOTE]
    > Quando si tenta di eseguire un file .exe scaricato dal Web (come questo), è possibile che venga visualizzato un popup "Windows protetto il PC". Per eseguire Fantasy_Island.exe da questo popup, selezionare **Altre informazioni** e quindi **Esegui comunque.** Questa impostazione di sicurezza ha lo scopo di proteggere l'utente dal download di file che potrebbero non essere attendibili, quindi scegliere questa opzione solo quando si considera attendibile l'origine del file.

3. Aprire **Esplora file** e passare alla cartella environments incollando il percorso del file seguente nella barra degli indirizzi: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` .
4. Copiare l'ambiente di esempio scaricato in questa cartella.
5. Riavviare **Portale realtà mista** per aggiornare l'elenco degli ambienti nella selezione Località.
6. Inserire il visore VR. Quando si è nella home page, aprire il **menu Start** usando il pulsante Windows il controller.
7. Selezionare **l'icona** Luoghi sopra l'elenco delle app aggiunte per scegliere un ambiente principale.
8. È possibile trovare l'ambiente dell'isola Islanda Disartie scaricata nell'elenco di località. Selezionare **Isola Del Sud** per accedere al nuovo ambiente domestico personalizzato.

## <a name="creating-your-own-custom-environment"></a>Creazione di un ambiente personalizzato

Oltre a usare gli ambienti di esempio, è possibile esportare i propri ambienti personalizzati usando il software di modifica 3D preferito. 

### <a name="modeling-guidelines"></a>Linee guida per la modellazione

Quando si modella l'ambiente, tenere presenti le raccomandazioni seguenti in modo che gli utenti creino l'orientamento corretto in un mondo di dimensioni notevolmente grandi:

1. Gli utenti generano a 0,0,0 in modo da centrare la posizione di generazione intorno all'origine.
2. Le unità di lavoro devono essere impostate su contatori in modo che gli asset possano essere creati su scala globale.
3. L'asse in su deve essere impostato su "Y".
4. L'asset deve essere "in avanti" verso l'asse Z positivo.
5. Non è necessario combinare tutte le mesh, ma è consigliabile scegliere come destinazione dispositivi con risorse limitate.

### <a name="exporting-your-environment"></a>Esportazione dell'ambiente

Windows Mixed Reality si basa su glTF binario (.glb) come formato di distribuzione degli asset per gli ambienti. glTF è uno standard aperto gratuito per la distribuzione di asset 3D gestito dal gruppo Khronos. Il supporto di Microsoft per il formato nelle app Windows e nelle esperienze crescerà con l'evoluzione di glTF come standard di settore per i contenuti 3D interoperativi.

Il primo passaggio per l'esportazione di asset da usare come ambienti home personalizzati consiste nella generazione di un modello glTF 2.0. Il gruppo di lavoro glTF gestisce un [elenco di](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) convertitori e esportatori supportati per creare un modello glTF 2.0. Per iniziare, usare uno dei programmi elencati in questa pagina per creare ed esportare un modello glTF 2.0 o convertire un modello esistente usando uno dei convertitori supportati.

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>Limiti dell'ambiente

Tutti gli ambienti devono avere < 256 MB. Gli ambienti di dimensioni superiori a 256 MB non riusciranno a caricare ed eseguire il fall back in un ambiente vuoto con solo il skybox predefinito che circonda l'utente. Tenere presente questo limite di dimensioni dei file durante la creazione dei modelli. Inoltre, se si prevede di ottimizzare l'ambiente usando WindowsMRAssetConverter come descritto di seguito, è importante essere concisi che le dimensioni della trama aumenteranno man appena l'utilità di ottimizzazione crea trame con dimensioni di file maggiori, ma il caricamento sarà più veloce. 

### <a name="optimizing-your-environment"></a>Ottimizzazione dell'ambiente

Windows Mixed Reality supporta molte ottimizzazioni facoltative che possono ridurre significativamente i tempi di caricamento dell'ambiente. Prestare particolare attenzione con gli ambienti con molte trame, perché a volte si timeout durante il caricamento. In generale, è consigliabile eseguire questo passaggio per tutti gli asset, tuttavia gli ambienti più piccoli con trame di dimensioni ridotte o a bassa risoluzione non lo richiedono sempre. 

Per semplificare questo processo, è stato creato il Windows Mixed Reality [Asset Converter (disponibile](https://github.com/Microsoft/glTF-Toolkit/releases) in GitHub) per eseguire le ottimizzazioni. Questo strumento usa un set di utilità disponibili in Microsoft glTF Toolkit per ottimizzare qualsiasi glTF standard 2.0 o.glb eseguendo una compressione, una compressione e una risoluzione aggiuntive per il ridimensionamento. 

Il convertitore supporta attualmente diversi flag per modificare il comportamento esatto delle ottimizzazioni. Per ottenere risultati ottimali, è consigliabile eseguire con i flag seguenti:

Flag|Valori consigliati|Descrizione
---|---|---
-max-texture-size|1024 o 2048| Modificare il valore per migliorare la qualità delle trame. Il valore predefinito è 512x512. Un valore maggiore incide in modo significativo sulle dimensioni del file dell'ambiente, quindi tenere presente il limite di 256 MB
-min-version|1803|Gli ambienti personalizzati sono supportati solo nelle versioni di Windows >= 1803. Questo flag rimuoverà le trame per le versioni precedenti e ridurrà le dimensioni del file dell'asset finale

Ad esempio:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Test dell'ambiente

Dopo aver creato l'ambiente final.glb, è possibile testarlo nel visore VR. Iniziare dal passaggio 2 della sezione ["Prova di un](#trying-a-sample-environment) ambiente di esempio" per usare l'ambiente personalizzato come ambiente iniziale. 

## <a name="sending-feedback"></a>Invio di feedback

Anche se si sta valutando questa funzionalità sperimentale, microsoft è interessata a scoprire come si usano gli ambienti personalizzati, eventuali bug trovati e come si desidera la funzionalità. Condividere commenti e suggerimenti per la creazione e l'uso di ambienti home personalizzati nei [forum per sviluppatori.](https://forums.hololens.com/categories/custom-home-environments)

## <a name="troubleshooting-and-tips"></a>Risoluzione dei problemi e suggerimenti

### <a name="how-do-i-change-the-name-of-the-environment"></a>Ricerca per categorie modificare il nome dell'ambiente?

Il nome del file nella cartella environments verrà usato nel selettore Località. Per modificare il nome dell'ambiente, rinominare il nome file dell'ambiente e quindi riavviare Portale realtà mista.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Ricerca per categorie rimuovere gli ambienti personalizzati dal selettore Località?

Per rimuovere un ambiente personalizzato, aprire la cartella environments nel PC ( `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ) ed eliminare l'ambiente. Dopo il riavvio Portale realtà mista, questo ambiente non verrà più visualizzato nella selezione Località. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Ricerca per categorie impostazione predefinita è l'ambiente personalizzato preferito?

Non è attualmente possibile modificare l'ambiente predefinito. Ogni volta che si Portale realtà mista, si torna all'ambiente di Casa sulla scogliera. 

### <a name="i-spawn-into-a-blank-space"></a>Genera in uno spazio vuoto

Windows Mixed Reality [non supporta ambienti che superano i 256 MB.](#environment-limits) Quando un ambiente supera questo limite, verrà visualizzato il sky box vuoto senza modello.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Il caricamento dell'ambiente richiede molto tempo

È possibile aggiungere ottimizzazioni facoltative all'ambiente per velocizzare il caricamento. Per [informazioni dettagliate, vedere "Ottimizzazione](#optimizing-your-environment) dell'ambiente".

### <a name="the-scale-of-my-environment-is-incorrect"></a>La scalabilità dell'ambiente non è corretta

Windows Mixed Reality converte le unità glTF in 1 contatore durante il caricamento degli ambienti. Se l'ambiente carica una scala imprevista, controllare l'esportatore per assicurarsi di eseguire la modellazione su una scala di 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>La posizione di generazione nell'ambiente non è corretta

Il percorso di generazione predefinito si trova in 0,0,0 nell'ambiente. Non è attualmente possibile personalizzare questa posizione, quindi è necessario modificare il punto di generazione esportando l'ambiente con l'origine posizionata nel punto di generazione desiderato.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>L'audio non sembra corretto nell'ambiente

Quando si crea l'ambiente personalizzato, verrà utilizzata una simulazione di rendering dell'acustica che non corrisponde allo spazio fisico creato. Il suono può derivare da direzioni erre e può sembrare ovattato. 

## <a name="see-also"></a>Vedi anche
* [Windows Mixed Reality Asset Converter (in GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)