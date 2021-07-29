---
title: Case study - Creazione di HoloSketch, un'app per il layout spaziale e lo sketch dell'esperienza utente per HoloLens
description: HoloSketch è uno strumento di layout spaziale e UX sketching per HoloLens per la creazione di esperienze olografiche.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, sketching, app
ms.openlocfilehash: 24929d38f97a3c02946a28184d7702c151dc22b2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757323"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Case study - Creazione di HoloSketch, un'app per il layout spaziale e lo sketch dell'esperienza utente per HoloLens

HoloSketch è uno strumento di layout spaziale e UX sketching per HoloLens per la creazione di esperienze olografiche. HoloSketch funziona con una combinazione Bluetooth tastiera e mouse, nonché con comandi vocali e movimenti. Lo scopo di HoloSketch è fornire un semplice strumento di layout dell'esperienza utente per la visualizzazione rapida e l'iterazione.

![HoloSketch: un'app per il layout spaziale e lo sketch dell'esperienza utente per HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout spaziale e app di sketch dell'esperienza utente per HoloLens*

![Un semplice strumento di layout dell'esperienza utente per la visualizzazione rapida e l'iterazione.](images/holosketch-image-02.png)<br>
*Un semplice strumento di layout dell'esperienza utente per la visualizzazione rapida e l'iterazione*

## <a name="features"></a>Funzionalità

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitive per gli studi rapidi e la creazione di prototipi di scala

![Uso di forme primitive](images/holosketch-primitives-giphy.gif)

Usare forme primitive per gli studi di massa rapida e la creazione di prototipi di scala.

### <a name="import-objects-through-onedrive"></a>Importare oggetti tramite OneDrive

![importazione di oggetti](images/holosketch-importobjects-giphy.gif)

Importare immagini PNG/JPG o oggetti FBX 3D (richiede la creazione di pacchetti in Unity) nello spazio di realtà mista tramite OneDrive.

### <a name="manipulate-objects"></a>Modificare gli oggetti

![modifica di oggetti](images/manipulate-objects-640px.jpg)

Manipolare gli oggetti (spostamento/rotazione/ridimensionamento) con un'interfaccia a oggetti 3D familiare.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/tastiera, movimenti e comandi vocali

![supporta l'Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch supporta Bluetooth mouse/tastiera, movimenti e comandi vocali.

## <a name="background"></a>Sfondo

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importanza di sperimentare la progettazione nel dispositivo

Quando si progetta qualcosa per HoloLens, è importante sperimentare la progettazione nel dispositivo. Una delle principali sfide nella progettazione di app di realtà mista è che è difficile ottenere il senso di scalabilità, posizione e profondità, soprattutto tramite gli sketch 2D tradizionali.

### <a name="cost-of-2d-based-communication"></a>Costo della comunicazione basata su 2D

Per comunicare in modo efficace i flussi e gli scenari dell'esperienza utente ad altri utenti, una finestra di progettazione può terminare con la creazione di asset usando gli strumenti 2D tradizionali, ad esempio Illustrator, Photoshop e PowerPoint. Queste progettazioni 2D richiedono spesso un impegno aggiuntivo per convertirle in 3D. Alcune idee vengono perse in questa traduzione da 2D a 3D.

### <a name="complex-deployment-process"></a>Processo di distribuzione complesso

Poiché la realtà mista è un nuovo canvas per noi, comporta molte iterazioni di progettazione, prove ed errori per sua natura. Per i progettisti che non hanno familiarità con strumenti come Unity e Visual Studio, non è facile mettere insieme qualcosa HoloLens. In genere è necessario eseguire il processo seguente per visualizzare la grafica 2D/3D nel dispositivo. Si tratta di una grande barriera per i progettisti che eseere rapidamente l'iter su idee e scenari.

![Processo di distribuzione complesso](images/holosketch-image-03-1000px.png)<br>
*Processo di distribuzione*

### <a name="simplified-process-with-holosketch"></a>Processo semplificato con HoloSketch

Con HoloSketch si è voluto semplificare questo processo senza coinvolgere gli strumenti di sviluppo e l'associazione del portale per dispositivi. Usando OneDrive, gli utenti possono inserire facilmente asset 2D/3D in HoloLens.

![Processo semplificato con HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo semplificato con HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Favorire il modo di pensare e le soluzioni di progettazione tridimensionale

Si è pensato che questo strumento offrisse ai progettisti l'opportunità di esplorare le soluzioni in uno spazio realmente tridimensionale e di non rimanere bloccati in 2D. Non devono pensare alla creazione di uno sfondo 3D per l'interfaccia utente, perché lo sfondo è il mondo reale nel caso di HoloLens. HoloSketch consente ai progettisti di esplorare facilmente la progettazione 3D HoloLens.

## <a name="get-started"></a>Introduzione

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Come importare immagini 2D (JPG/PNG) in HoloSketch

* Upload Immagini JPG/PNG nella OneDrive 'Documents/HoloSketch'.
* Dal menu OneDrive in HoloSketch sarà possibile selezionare e posizionare l'immagine nell'ambiente.

![Importazione di immagini 2D](images/import-2d-images-1000px.jpg)<br>
*Importazione di immagini e oggetti 3D tramite OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Come importare oggetti 3D in HoloSketch

Prima di caricare nella cartella OneDrive, seguire questa procedura per creare un pacchetto degli oggetti 3D in un bundle di asset Unity. Usando questo processo è possibile importare i file FBX/OBJ da software 3D come Maya, Cinema 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Attualmente, la creazione di bundle di asset è supportata con Unity versione 5.4.5f1.

1. Scaricare e aprire il progetto Unity ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Questo progetto Unity include lo script per la generazione di asset bundle.
2. Creare un nuovo GameObject.
3. Assegnare un nome all'oggetto GameObject in base al contenuto.
4. Nel pannello Inspector (Controllo) fare clic su "Add Component" (Aggiungi componente) e aggiungere "Box Collider". 

   ![Nel pannello Inspector (Controllo) fare clic su "Add Component" (Aggiungi componente) e aggiungere "Box Collider"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Nel pannello Inspector (Controllo) fare clic su "Add Component" (Aggiungi componente) e aggiungere "Box Collider" #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importare il file FBX 3D trascinandolo nel pannello del progetto.
6. Trascinare l'oggetto nel pannello Hierarchy **(Gerarchia) sotto il nuovo GameObject**.

   ![Trascinare l'oggetto nel pannello Hierarchy (Gerarchia) sotto il nuovo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Regolare la dimensione collisore se non corrisponde all'oggetto . Ruotare l'oggetto in modo che **faccia l'asse Z.**

   ![Regolare la dimensione del collisore se non corrisponde all'oggetto .](images/holosketch-13-assetbundles-1000px.png)

8. Trascinare l'oggetto dal pannello Gerarchia Project pannello per **renderlo prefab**.
9. Nella parte inferiore del pannello del controllo fare clic sull'elenco a discesa, creare e assegnare un nuovo nome univoco. Nell'esempio seguente viene illustrata l'aggiunta e l'assegnazione di "brownchair" per il nome AssetBundle. 

   ![Nella parte inferiore del pannello del controllo fare clic sull'elenco a discesa e assegnare un nuovo nome univoco.](images/holosketch-14-assetbundles-1000px.png)

10. Preparare un'immagine di anteprima per l'oggetto modello. 
   ![Trascinare un'immagine nel pannello del progetto e assegnare il nome usato per l'oggetto.](images/holosketch-15-assetbundles-1000px.png)

11. Creare una cartella denominata "Assetbundles" nella cartella "Asset" del progetto Unity.

12. Dal menu Asset selezionare "Build AssetBundles" (Compila assetBundles) per generare il file. 
   ![Dal menu Asset selezionare "Build AssetBundles" (Compila assetBundles) per generare il file.](images/holosketch-15a-assetbundles.png)


13. **Upload il file generato nella cartella /Files/Documents/HoloSketch OneDrive.** Upload solo asset_unique_name file. Non è necessario caricare file manifesto o file AssetBundles. <br>
![Aggiungere file alla cartella Files/Documents/HoloSketch/ Verrà visualizzato l'oggetto 3D aggiunto nel menu OneDrive ](images/holosketch-onedriveupload-1000px.png)
 ![ HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Come modificare gli oggetti

HoloSketch supporta l'interfaccia tradizionale ampiamente usata nel software 3D. È possibile usare lo spostamento, la rotazione, la scalabilità degli oggetti con movimenti e un mouse. È possibile passare rapidamente da una modalità all'altra con la voce o la tastiera.

### <a name="object-manipulation-modes"></a>Modalità di manipolazione degli oggetti

![Come modificare gli oggetti](images/holosketch-image-06-1000px.png)<br>
*Come modificare gli oggetti*

### <a name="contextual-and-tool-belt-menus"></a>Menu contestuali e della barra degli strumenti

**Uso del menu contestuale**

Toccare doppio air per aprire il menu contestuale. 

Voci di menu:
* **Superficie di layout:** Si tratta di un sistema a griglia 3D in cui è possibile eseguire il layout di più oggetti e gestirli come gruppo. Toccare due volte l'area di layout per aggiungere oggetti.
* **Primitive:** Usare cubi, sphere, cilindri e coni per gli studi di massa.
* **OneDrive:** Aprire il menu OneDrive per importare gli oggetti.
* **Guida:** Visualizza la schermata della Guida.

![Menu di scelta rapida](images/holosketch-image-07.png)<br>
*Menu di scelta rapida*

**Uso del menu a nastri degli strumenti**

Le opzioni Sposta, Ruota, Ridimensiona, Salva e Carica scena sono disponibili nel menu a nastri degli strumenti. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Uso di tastiera, movimenti e comandi vocali

![Tastiera, movimenti e comandi vocali](images/holosketch-image-08-1000px.png)<br>
*Tastiera, movimenti e comandi vocali*

## <a name="download-the-app"></a>Scarica l'app

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Scaricare e installare l'app HoloSketch gratuitamente dal Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemi noti
* La creazione del bundle di asset è attualmente supportata **con Unity versione 5.4.5f1.**
* A seconda della quantità di dati nel OneDrive, l'app potrebbe apparire come se fosse stata arrestata durante il caricamento OneDrive contenuto
* Attualmente, la funzionalità Salva e carica supporta solo oggetti primitivi
* I menu Testo, Audio, Video e Foto sono disabilitati nel menu di scelta rapida
* Il pulsante Play (Riproduci) nel menu Tool Belt (Nastro strumenti) cancella i gizmo di manipolazione

## <a name="sharing-your-sketches"></a>Condivisione degli sketch

È possibile usare la funzionalità di registrazione video in HoloLens pronunciare "Hey Cortana, Start/Stop recording" (Hey Cortana, Avvia/Arresta registrazione). Premere il tasto di volume su/giù insieme per scattare una foto dello sketch.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Designer di esperienza utente @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Sviluppatore @Microsoft</td>
</tr>
</table> 