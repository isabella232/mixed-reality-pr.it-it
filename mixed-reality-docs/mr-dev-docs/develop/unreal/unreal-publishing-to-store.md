---
title: Pubblicazione in Microsoft Store
description: Informazioni su come creare pacchetti, certificare e pubblicare le applicazioni di realtà mista Unreal in Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, visore VR realtà mista, visore VR di windows mixed reality, visore VR per realtà virtuale, pubblicazione, distribuzione, Microsoft Store
ms.openlocfilehash: 2e0e628439c187d787fe64902cbb9a17d617559623d90830ef4a57f6c7b34338
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226298"
---
# <a name="publishing-to-the-microsoft-store"></a>Pubblicazione in Microsoft Store

Quando l'app Unreal è pronta per essere pubblicata, è necessario aggiornare alcune impostazioni di progetto prima dell'invio a Microsoft Store. Tutte queste impostazioni hanno valori predefiniti. Per rappresentare l'applicazione in modo ottimale, tuttavia, devono essere modificate per la fase di produzione.

## <a name="project-settings-for-the-store-packaging"></a>Impostazioni di progetto per la creazione di pacchetti per lo Store

1. Selezionare prima **Project Settings > Description** (Impostazioni progetto > Descrizione) e aggiornare le informazioni sul gioco e sull'editore: 
    * **Game Name** (Nome gioco) verrà visualizzato nel riquadro dell'app in HoloLens
    * **Company Distinguished Name** (Nome distinto società) viene usato durante la generazione del certificato di progetto e deve avere il formato seguente: 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:

![Screenshot dell'editor di Unreal con la sezione relativa alla descrizione espansa nelle impostazioni di progetto](images/unreal-publishing-img-01.png)

2. Espandere la sezione **HoloLens** delle impostazioni di progetto e aggiornare le risorse per la creazione di pacchetti.  Questi nomi di risorse verranno visualizzati nella pagina dell'applicazione nello Store:

![Screenshot dell'editor di Unreal con la sezione relativa alla creazione di pacchetti espansa nelle impostazioni di progetto](images/unreal-publishing-img-02.png)

3. Espandere la sezione **Images** (Immagini) e aggiornare le immagini predefinite dello Store con le trame che rappresentano l'app dello Store.  Facoltativamente, selezionare la casella di controllo **3D Logo** (Logo 3D) per caricare un file con estensione glb da usare come cubo live 3D all'avvio dell'applicazione:

![Screenshot dell'editor di Unreal con la sezione relativa alle immagini espansa nelle impostazioni di progetto](images/unreal-publishing-img-03.png)

4. Infine, selezionare **Generate New** (Genera nuovo) per generare un certificato di firma dal nome del progetto e dal nome distinto della società  
    * Impostare un valore per **Tile Background Color** (Colore di sfondo riquadro), che verrà visualizzato al posto di eventuali pixel trasparenti nelle immagini dello Store.
    * Espandere l'elenco a discesa e abilitare **Use Retail Windows Store Environment** (Usa ambiente Windows Store retail) per l'esecuzione in dispositivi bloccati per utenti retail e non sbloccati per sviluppatori.

![Screenshot dell'editor di Unreal con la sezione relativa alla generazione del certificato espansa nelle impostazioni di progetto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>Programma di installazione app facoltativo

È possibile creare un file Programma di installazione app in **Project Settings > HoloLens** (Impostazioni progetto > HoloLens), che può essere usato per distribuire l'applicazione al di fuori dello Store.  Abilitare la casella di controllo **Should Create App Installer** (Devi creare Programma di installazione app) e impostare un URL o un percorso di rete nella posizione in cui si vuole archiviare il pacchetto appxbundle del gioco.  

![Screenshot dell'editor di Unreal con la sezione relativa al Programma di installazione app espansa nelle impostazioni di progetto](images/unreal-publishing-img-05.png)

Quando si crea il pacchetto dell'app, vengono generati sia appxbundle sia appinstaller.  Caricare appxbundle nell'URL di installazione e quindi avviare appinstaller per installare l'app dal percorso di rete.

## <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Windows 10 SDK viene fornito con il Kit di certificazione app Windows (WACK) per convalidare problemi comuni che possono influire sul caricamento di un pacchetto nello Store.  È possibile trovare WACK nella directory Windows Kits, in genere nel percorso seguente: 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. Dopo la creazione del pacchetto del file appx per la pubblicazione, eseguire **appcertui.exe** e seguire le istruzioni per eseguire la scansione di appx:

![Screenshot dell'app selezionata per la convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-06.png)

2. Selezionare **Convalida app di Store**:

![Screenshot della selezione della convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-07.png)

3. Individuare appx nella sezione superiore e selezionare **Avanti**:

![Screenshot della selezione di test nel Kit di certificazione app Windows](images/unreal-publishing-img-08.png)

4. Selezionare **Avanti** per eseguire i test e creare un report:
    * Tutti i test disponibili che possono essere eseguiti nel PC host saranno abilitati per impostazione predefinita

![Screenshot dello stato di avanzamento della convalida nel Kit di certificazione app Windows](images/unreal-publishing-img-09.png)

5. Attendere il completamento dei test. Al termine, nella finestra finale verrà indicato l'esito positivo o negativo, che può essere visualizzato nel report salvato.

![Screenshot dei risultati del report finale nel Kit di certificazione app Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>Errore noto di WACK nella versione 4.25

Il plug-in di Windows Mixed Reality in Unreal 4.25 non riuscirà a eseguire WACK perché vengono inclusi alcuni file binari x64 durante la creazione del pacchetto per HoloLens. L'errore sarà simile al seguente:

![Screenshot dell'errore dovuto all'analizzatore binario e alle API supportate dal Kit di certificazione app Windows](images/unreal-publishing-img-11.png)

Per correggere il problema:
1. Passare alla directory radice di installazione o di origine di Unreal aprendo un progetto di Unreal e facendo clic con il pulsante destro del mouse sull'icona di Unreal nella barra delle applicazioni.
2. Fare clic con il pulsante destro del mouse su UE4Editor, selezionare Properties (Proprietà) e passare al percorso indicato alla voce **Location** (Posizione):

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. In **WindowsMixedRealityHMD.Build.cs** modificare la **riga 32** da:

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

in:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Chiudere Unreal, riaprire il progetto e creare nuovamente il pacchetto per HoloLens.  Eseguire nuovamente WACK e l'errore verrà rimosso. 

## <a name="see-also"></a>Vedi anche

* [Invio di un'app a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [Creare un file del programma di installazione app manualmente](/windows/msix/app-installer/how-to-create-appinstaller-file)