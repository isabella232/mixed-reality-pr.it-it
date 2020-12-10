---
title: Esportazione e creazione di una soluzione di Visual Studio Unity
description: Questo articolo illustra come esportare il progetto di realtà mista da Unity, in modo da poter compilare e distribuire in Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, Export, Build, deploy, HoloLens, multireality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, UWP, Deploying
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010412"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Esportazione e creazione di una soluzione di Visual Studio Unity

Se l'app non richiede la tastiera di sistema, si consiglia di usare *D3D* in modo che l'app usi un minor numero di memoria e un tempo di avvio più veloce. Tuttavia, se si usa la tastiera di sistema tramite l'API TouchScreenKeyboard, è necessario esportare il progetto come *XAML*.

## <a name="how-to-export-from-unity"></a>Come esportare da Unity

![Impostazioni di compilazione Unity](images/unitybuildsettings-300px.png)<br>
*Impostazioni di compilazione nell'editor di Unity*

1. Quando si è pronti per esportare il progetto da Unity, aprire il menu **file** e selezionare **impostazioni di compilazione...**
2. Selezionare **Aggiungi scene aperte** per aggiungere la scena alla compilazione.
3. Nella finestra di dialogo **impostazioni di compilazione** scegliere le opzioni seguenti per esportare per HoloLens:
   * **Piattaforma:** *piattaforma UWP (Universal Windows Platform)* e assicurarsi di selezionare **Switch Platform (Cambia piattaforma** ) per rendere effettive le selezioni.
   * **SDK:** *universale 10*.
   * **Tipo di compilazione UWP:** *D3D*.
4. **Facoltativo**: **progetti C# di Unity:** selezionati.

>[!NOTE]
>Selezionando questa casella è possibile:
>* Eseguire il debug dell'app in Visual Studio Remote Debugger.
>* Modificare gli script nel progetto Unity C# usando IntelliSense per le API WinRT.

5. Dalla finestra **impostazioni di compilazione...** aprire **lettore impostazioni...**
6. Selezionare le **impostazioni per** la scheda piattaforma UWP (Universal Windows Platform).
7. Espandere il gruppo **Impostazioni XR**.
8. Nella sezione **impostazioni di XR** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco di **dispositivi di realtà virtuale** e confermare che la **realtà mista di Windows** è elencata come un dispositivo supportato.
9. Tornare alla finestra di dialogo **impostazioni di compilazione** .
10. Selezionare **Compila**.
11. Nella finestra di dialogo Esplora risorse visualizzata creare una nuova cartella che contenga l'output di compilazione di Unity. In genere, la cartella "app" viene denominata.
12. Selezionare la cartella appena creata e fare clic su **Seleziona cartella**.
13. Una volta completata la compilazione di Unity, viene visualizzata una finestra di Esplora risorse per la directory radice del progetto. Passare alla cartella appena creata.
14. Aprire il file della soluzione di Visual Studio generato che si trova all'interno di questa cartella.

## <a name="when-to-re-export-from-unity"></a>Quando eseguire nuovamente l'esportazione da Unity

Controllo della casella di controllo **progetti C#** quando si esporta l'app da Unity crea una soluzione di Visual Studio che include tutti i file di script Unity. La presenza di tutti gli script in un'unica posizione consente di eseguire l'iterazione senza riesportare da Unity. Tuttavia, se si apportano modifiche al progetto che non cambiano solo il contenuto degli script, sarà necessario eseguire di nuovo l'esportazione da Unity. Di seguito sono riportati alcuni esempi di casi in cui è necessario eseguire di nuovo l'esportazione da Unity:
* È possibile aggiungere o rimuovere asset nella scheda progetto.
* È possibile modificare qualsiasi valore nella scheda Inspector (controllo).
* Si aggiungono o rimuovono oggetti dalla scheda gerarchia.
* Modificare le impostazioni del progetto Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilazione e distribuzione di una soluzione Unity di Visual Studio

Il resto della compilazione e della distribuzione delle app avviene in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Sarà necessario specificare una configurazione di compilazione Unity. Le convenzioni di denominazione di Unity possono essere diverse da quelle usate in Visual Studio:

|  Configurazione  |  Spiegazione | 
|----------|----------|
|  Debug  |  Tutte le ottimizzazioni disattivate e il profiler è abilitato. Utilizzato per eseguire il debug degli script. | 
|  Master  |  Tutte le ottimizzazioni sono attivate e il profiler è disabilitato. Usato per inviare app allo Store. | 
|  Versione  |  Tutte le ottimizzazioni sono attivate e il profiler è abilitato. Usato per valutare le prestazioni dell'app. | 

Si noti che l'elenco precedente è un subset dei trigger comuni che comporteranno la generazione del progetto di Visual Studio. In generale, la modifica dei file con estensione cs da Visual Studio non richiede la rigenerazione del progetto dall'interno di Unity.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se le modifiche apportate ai file con estensione cs non vengono riconosciute nel progetto di Visual Studio, assicurarsi che i **progetti C# di Unity** vengano controllati quando si genera il progetto vs dal menu Compila di Unity.
