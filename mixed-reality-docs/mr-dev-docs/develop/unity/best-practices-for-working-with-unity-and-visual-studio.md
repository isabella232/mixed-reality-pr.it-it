---
title: Procedure consigliate Visual Studio Unity e
description: Suggerimenti e consigli per semplificare il flusso di lavoro di creazione di un'applicazione di realtà mista con Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, visore immersivo, procedure consigliate, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, UWP, Strumenti di Visual Studio, Windows SDK
ms.openlocfilehash: edd79b95d02cfeb1da4effc485fc57078e3d24a3
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042262"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedure consigliate per l'uso con Unity e Visual Studio

Quando si crea un'applicazione di realtà mista con Unity, è necessario passare da Unity a Visual Studio per compilare e distribuire il pacchetto dell'app in HoloLens o in un visore immersivo. Per impostazione predefinita, sono necessarie due istanze Visual Studio: un'istanza per modificare gli script di Unity e un'altra per la distribuzione nel dispositivo e il debug. Le istruzioni seguenti consentono di sviluppare usando una singola Visual Studio, riducendo la frequenza di esportazione dei progetti Unity e migliorando l'esperienza di debug.

## <a name="improving-iteration-time"></a>Miglioramento del tempo di iterazione

Il supporto per il back-end di scripting .NET in Unity è stato deprecato in Unity 2018 e rimosso a data di Unity 2019+, quindi è consigliabile passare a [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html) Tuttavia, è possibile che si verifichino tempi di compilazione più lunghi da Unity a Visual Studio. Per migliorare l'iterazione più rapida, configurare l'ambiente per ottenere risultati di compilazione ottimali:

1) Usare la compilazione incrementale compilando il progetto nella stessa directory ogni volta, riutilizzando i file predefiniti
2) Disabilitare le analisi software antimalware per il progetto & cartelle di compilazione
   - Aprire **Virus & protezione dalle minacce** nell'app impostazioni Windows 10 sicurezza
   - Selezionare **Gestisci impostazioni** in Impostazioni di protezione dalle minacce & **virus**
   - Selezionare **Aggiungi o rimuovi esclusioni** nella sezione **Esclusioni**
   - Selezionare **Aggiungi un'esclusione e** selezionare la cartella contenente il codice del progetto Unity e gli output di compilazione
3) Usare un SSD per la compilazione

Per [altre informazioni, vedere Ottimizzazione dei tempi di compilazione per IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) Vedere anche [Debug nel back-end di scripting IL2CPP.](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)

Provare a installare [ *l'estensione UnityScriptAnalyzer* Visual Studio .](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer) Questo strumento analizza gli script C# di Unity per il codice che può essere scritto in modo più ottimizzato.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity

Scaricare [Visual Studio Tools per Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Vantaggi della Visual Studio Tools per Unity**
* Eseguire il debug della modalità di riproduzione nell'editor di Unity Visual Studio inserendo punti di interruzione, valutando variabili ed espressioni complesse.
* Usare Esplora progetti unity per trovare lo script con la stessa gerarchia visualizzata da Unity.
* Ottenere la console di Unity direttamente all'interno Visual Studio.
* Usare le procedure guidate per creare o passare rapidamente agli script.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Esporre variabili di classe C# per una facile ottimizzazione

Esistono due modi per esporre le variabili di classe. Il modo consigliato è aggiungere l'attributo [SerializeField] alle variabili private. È possibile accedere ai campi serializzati dall'editor, ma non a livello di codice.  L'altra opzione è rendere pubbliche le variabili di classe C# per esporle nell'interfaccia utente dell'editor. 

Entrambi gli approcci rendono possibile modificare facilmente le variabili durante la riproduzione nell'editor, particolarmente utile per l'ottimizzazione delle proprietà del meccanismo di interazione.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Rigenerare le soluzioni UWP Visual Studio dopo l'Windows SDK o Unity

Le soluzioni Visual Studio UWP archiviate nel controllo del codice sorgente possono non essere aggiornate dopo l'aggiornamento a un nuovo motore Windows SDK o Unity. È possibile risolvere le soluzioni non aggiornate dopo creando una nuova soluzione UWP da Unity e unendo le differenze nella soluzione archiviata.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usare asset in formato testo per confrontare facilmente le modifiche al contenuto

L'archiviazione di asset in formato testo semplifica la revisione delle diff di modifica del contenuto Visual Studio. È possibile archiviare gli asset in formato testo selezionando Modifica > impostazioni progetto **> Editor** e impostando la modalità Serializzazione asset su Forza **testo**.  Tuttavia, l'unione delle modifiche ai file di asset di testo è erta e non consigliata, pertanto è consigliabile abilitare estrazioni binarie esclusive nel controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Visual Studio Tools per Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Ottimizzazione dei tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio estensione](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)