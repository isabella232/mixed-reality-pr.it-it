---
title: Procedure consigliate per Unity e Visual Studio
description: Suggerimenti e consigli per semplificare il flusso di lavoro di creazione di un'applicazione di realtà mista con Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, visore VR immersive, procedure consigliate, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, UWP, Strumenti di Visual Studio, Windows SDK
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186881"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedure consigliate per l'uso con Unity e Visual Studio

Quando crei un'applicazione di realtà mista con Unity, devi passare da Unity a Visual Studio per compilare e distribuire il pacchetto dell'app in HoloLens o in un visore VR immersive. Per impostazione predefinita, sono necessarie due istanze Visual Studio, una per modificare gli script unity e un'altra per la distribuzione nel dispositivo e il debug. Le istruzioni seguenti consentono di sviluppare usando una singola istanza Visual Studio, riducendo la frequenza di esportazione dei progetti Unity e migliorando l'esperienza di debug.

## <a name="improving-iteration-time"></a>Miglioramento del tempo di iterazione

Il supporto per il back-end di scripting .NET in Unity è stato deprecato in Unity 2018 e rimosso a livello di Unity 2019+, quindi è consigliabile passare a [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html) Tuttavia, è possibile che si verifichino tempi di compilazione più lunghi da Unity Visual Studio. Per migliorare l'iterazione più veloce, configurare l'ambiente per ottenere risultati di compilazione ottimali:

1) Usare la compilazione incrementale compilando ogni volta il progetto nella stessa directory, riutilizzando i file predefiniti
2) Disabilitare le analisi del software antimalware per il progetto & di compilazione
   - Aprire **Virus & protezione dalle minacce nell'app** impostazioni Windows 10 sicurezza
   - Selezionare **Gestisci Impostazioni** impostazioni di protezione dalle minacce & **virus**
   - Selezionare **Aggiungi o rimuovi esclusioni** nella sezione **Esclusioni**
   - Selezionare **Add an exclusion (Aggiungi un'esclusione)** e selezionare la cartella contenente il codice del progetto Unity e gli output di compilazione
3) Usare un'SSD per la compilazione

Per [altre informazioni, vedere Ottimizzazione dei tempi di compilazione per IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) Vedere anche [Debugging on IL2CPP Scripting Back-end (Debug nel back-end di scripting IL2CPP).](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)

Provare a installare [ *l'estensione unityScriptAnalyzer* Visual Studio .](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer) Questo strumento analizza gli script C# di Unity per il codice che può essere scritto in modo più ottimizzato.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity

Scaricare [Visual Studio Tools per Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Vantaggi dell'Visual Studio Tools per Unity**
* Eseguire il debug della modalità di riproduzione nell'editor di Unity Visual Studio inserendo punti di interruzione, valutando variabili ed espressioni complesse.
* Usare Unity Project Explorer per trovare lo script con la stessa gerarchia visualizzata da Unity.
* Ottenere la console di Unity direttamente all'interno Visual Studio.
* Usare le procedure guidate per creare o passare rapidamente agli script.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Esporre le variabili di classe C# per una facile ottimizzazione

Esistono due modi per esporre le variabili di classe. Il modo consigliato è aggiungere l'attributo [SerializeField] alle variabili private. I campi serializzati sono accessibili dall'editor, ma non esposti a livello di codice.  L'altra opzione è rendere pubbliche le variabili di classe C# per esporle nell'interfaccia utente dell'editor. 

Entrambi gli approcci rendono possibile modificare facilmente le variabili durante la riproduzione nell'editor, particolarmente utile per ottimizzare le proprietà del meccanismo di interazione.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Rigenerare le soluzioni UWP Visual Studio dopo l'aggiornamento Windows SDK o Unity

Le soluzioni Visual Studio UWP archiviate nel controllo del codice sorgente possono non essere aggiornate dopo l'aggiornamento a un nuovo sdk Windows o un motore Unity. È possibile risolvere le soluzioni non aggiornate compilando una nuova soluzione UWP da Unity e unendo le differenze nella soluzione archiviata.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usare asset in formato testo per confrontare facilmente le modifiche al contenuto

L'archiviazione degli asset in formato testo semplifica la revisione delle diff in caso di modifica del contenuto Visual Studio. È possibile archiviare gli asset in formato testo selezionando  Modifica > Project Impostazioni > **Editor** e impostando la modalità serializzazione asset **su Forza testo**. Tuttavia, l'unione delle modifiche ai file di asset di testo è erta e non consigliata, pertanto è consigliabile abilitare estrazioni binarie esclusive nel controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Visual Studio Tools per Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Ottimizzazione dei tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Estensione Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)