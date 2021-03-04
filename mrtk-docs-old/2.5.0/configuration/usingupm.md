---
title: usingupm
description: Uso di MRTK in Unity pakage Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK pakages,
ms.openlocfilehash: 7868612d02d9ed0e5d944768de9dd7356912b5b1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782370"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Toolkit per realtà mista e gestione pacchetti Unity

A partire dalla versione 2.5.0, Microsoft Mixed Reality Toolkit è disponibile tramite Gestione pacchetti Unity (UPM), in Unity 2019,4 e versioni successive.

## <a name="installing-mixed-reality-features-using-the-unity-package-manager"></a>Installazione delle funzionalità della realtà mista tramite Gestione pacchetti Unity

Gestione pacchetti Unity usa un [file manifesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) per determinare i pacchetti da installare e i registri (Server) da cui possono essere installati.

> [!Note]
> A partire dalla versione 2.5.0 di MRTK, la registrazione iniziale del server e dei pacchetti è una procedura manuale per progetto. per istruzioni dettagliate, vedere le sezioni seguenti.
>
> Questo processo è necessario a causa dell'uso di UPM per la funzionalità di ricerca NPM legacy (/-/All) non supportata da Azure DevOps.

### <a name="registering-the-mixed-reality-component-server"></a>Registrazione del server del componente realtà mista

Per ogni progetto che utilizzerà Microsoft Mixed Reality Toolkit, il `manifest.json` file (nella cartella Pacchetti) dovrà aggiungere il registro di sistema con ambito di realtà misto. Di seguito viene illustrato come modificare correttamente `manifest.json` per supportare la realtà mista.

1. Aprire `<projectRoot>/Packages/manifest.json` in un editor di testo, ad esempio [Visual Studio Code](https://code.visualstudio.com/).
1. Nella parte superiore del file manifesto aggiungere il server di realtà misto alla sezione del registro di sistema con ambito e salvare il file.

```
{
  "scopedRegistries": [
    {
      "name": "Microsoft Mixed Reality",
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/",
      "scopes": [
        "com.microsoft.mixedreality",
        "com.microsoft.spatialaudio"
      ]
    }
  ],
```

### <a name="adding-mrtk-packages"></a>Aggiunta di pacchetti MRTK

Quando il registro con ambito Microsoft Mixed Reality è stato aggiunto al manifesto, è possibile specificare i pacchetti MRTK.

La sezione relativa a [Gestione pacchetti Unity](../packages-releases/MRTK_Packages.md#unity-package-manager) dell'articolo relativo al [pacchetto del Toolkit di realtà mista](../packages-releases/MRTK_Packages.md) descrive i pacchetti MRTK disponibili, il relativo contenuto e gli scenari per l'uso.

Per aggiungere un pacchetto MRTK, modificare la sezione dipendenze del `Packages/manifest.json` file. Nell'esempio seguente viene illustrato come aggiungere i pacchetti Foundation, Tools ed examples, il pacchetto di asset standard verrà aggiunto automaticamente come dipendenza della base.

```
  "dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.0",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.0",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.0",
```

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gestione delle funzionalità della realtà mista con gestione pacchetti Unity

Una volta aggiunto al manifesto del pacchetto, un pacchetto del Toolkit di realtà mista può essere gestito tramite l'interfaccia utente di gestione pacchetti Unity.

![Pacchetto UPM MRTK Foundation](../features/Images/Packaging/MRTK_FoundationUPM.png)

> [!Note]
> Se un pacchetto del Toolkit di realtà mista viene rimosso tramite Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i [passaggi descritti in precedenza](#adding-mrtk-packages).

### <a name="using-mixed-reality-toolkit-examples"></a>Esempi di utilizzo del Toolkit di realtà mista

Diversamente da quando si usano i file di pacchetto asset (con estensione file unitypackage Tools), `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` non vengono importati automaticamente gli asset e le scene di esempio.

Per usare uno o più degli esempi, attenersi alla procedura seguente:

1. Nell'editor di Unity passare a `Window` > `Package Manager`
1. Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`
1. Individuare gli esempi desiderati nell' `Samples` elenco
1. Fare clic su`Import into Project`.

![Importazione di esempi](../features/Images/Packaging/MRTK_ExamplesUpm.png)

Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.

> [!Note]
> L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.

## <a name="see-also"></a>Vedere anche

- [Pacchetti Toolkit per realtà mista](../packages-releases/MRTK_Packages.md)
