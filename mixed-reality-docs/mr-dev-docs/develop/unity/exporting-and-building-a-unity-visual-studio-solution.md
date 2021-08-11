---
title: Esportazione e creazione di una soluzione di Visual Studio Unity
description: Questo articolo descrive l'esportazione del progetto di realtà mista da Unity per poter compilare e distribuire in Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, esportare, compilare, distribuire, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, UWP, distribuzione
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203613"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Esportazione e creazione di una soluzione di Visual Studio Unity

Se l'app non richiede la tastiera di sistema, è consigliabile usare *D3D* in modo che l'app usi una quantità di memoria leggermente inferiore e tempi di avvio più rapidi. Tuttavia, se si usa la tastiera di sistema tramite l'API TouchScreenKeyboard, è necessario esportare il progetto come *XAML.*

## <a name="how-to-export-from-unity"></a>Come esportare da Unity

![Impostazioni di compilazione di Unity](images/unitybuildsettings-300px.png)<br>
*Impostazioni di compilazione nell'editor di Unity*

1. Quando si è pronti per esportare il progetto da Unity, aprire il menu **File** e selezionare **Compila Impostazioni...**
2. Selezionare **Add Open Scenes (Aggiungi** scene aperte) per aggiungere la scena alla compilazione.
3. Nella finestra **di dialogo Impostazioni** compilazione scegliere le opzioni seguenti per l'esportazione per HoloLens:
   * **Piattaforma:** *piattaforma Windows universale* e assicurarsi di selezionare **Cambia** piattaforma per attivare la selezione.
   * **SDK:** *Universal 10*.
   * **Tipo di compilazione UWP:** *D3D.*
4. **Facoltativo:** **Progetti C# Unity:** selezionato.

>[!NOTE]
>Selezionando questa casella è possibile:
>* Eseguire il debug dell'app Visual Studio debugger remoto.
>* Modificare gli script nel progetto C# unity quando si usa IntelliSense per le API WinRT.

5. Nella finestra **Impostazioni...** aprire Player **Impostazioni...**
6. Selezionare la **Impostazioni della piattaforma Windows universali.**
7. Espandere il gruppo **Impostazioni XR**.
8. Nella sezione **XR Impostazioni** selezionare la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere un nuovo elenco **di** dispositivi di realtà virtuale e verificare che **"Windows Mixed Reality"** sia elencato come dispositivo supportato.
9. Tornare alla finestra **di dialogo Impostazioni** compilazione.
10. Selezionare **Compila**.
11. Nella finestra Windows Explorer visualizzata creare una nuova cartella per contenere l'output di compilazione di Unity. In genere, la cartella viene deno come "App".
12. Selezionare la cartella appena creata e selezionare **Seleziona cartella.**
13. Al termine della compilazione di Unity, verrà Windows finestra Esplora risorse nella directory radice del progetto. Passare alla cartella appena creata.
14. Aprire il file della Visual Studio generato che si trova all'interno di questa cartella.

## <a name="when-to-re-export-from-unity"></a>Quando esportare di nuovo da Unity

Selezionando la **casella di controllo C# Projects** (Progetti C#) quando si esporta l'app da Unity viene creata Visual Studio soluzione che include tutti i file di script Unity. La presenza di tutti gli script in un'unica posizione consente di eseguire l'iterazione senza esportare nuovamente da Unity. Tuttavia, se si apportano modifiche al progetto che non si stanno semplicemente modificando il contenuto degli script, sarà necessario esportare nuovamente da Unity. Alcuni esempi di volte in cui è necessario esportare nuovamente da Unity sono:
* È possibile aggiungere o rimuovere asset nella Project risorse.
* È possibile modificare qualsiasi valore nella scheda Inspector (Controllo).
* È possibile aggiungere o rimuovere oggetti dalla scheda Gerarchia .
* Si modificano le impostazioni del progetto Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilazione e distribuzione di una soluzione Visual Studio Unity

Il resto della compilazione e della distribuzione di app avviene in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). È necessario specificare una configurazione di compilazione Unity. Le convenzioni di denominazione di Unity possono differire da quella usata in Visual Studio:

|  Configurazione  |  Spiegazione | 
|----------|----------|
|  Debug  |  Tutte le ottimizzazioni sono disattivate e il profiler è abilitato. Usato per eseguire il debug degli script. | 
|  Master  |  Tutte le ottimizzazioni sono attivate e il profiler è disabilitato. Usato per inviare app a Store. | 
|  Versione  |  Tutte le ottimizzazioni sono attivate e il profiler è abilitato. Usato per valutare le prestazioni dell'app. | 

Si noti che l'elenco precedente è un subset dei trigger comuni che causeranno la Visual Studio del progetto. In generale, la modifica dei file con estensione cs dall'interno Visual Studio non richiederà la rigenerazione del progetto da Unity.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verifica che le modifiche ai file con estensione cs non vengono riconosciute nel progetto Visual Studio, assicurarsi che l'opzione **Progetti C# unity** sia selezionata quando si genera il progetto di Visual Studio dal menu Compila di Unity.
