---
title: 1. Guida introduttiva
description: Parte 1 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: efa0bc210fc20b9e639954a06e97eb78661d87e5
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712580"
---
# <a name="1-getting-started"></a>1. Guida introduttiva

Indipendentemente dal fatto che l'utente sia alle prime armi o un professionista esperto nell'ambito della realtà mista, questo è il punto di partenza ideale per esplorare [HoloLens 2](../../../index.yml) e [Unreal Engine](https://www.unrealengine.com/en-US/). Questa serie di esercitazioni offre una guida dettagliata su come creare un'app di scacchi interattiva con il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), che fa parte di [Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). Con il plug-in potrai aggiungere comuni funzionalità UX ai tuoi progetti con codice, progetti ed esempi. 

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

Alla fine della serie, l'utente avrà acquisito esperienza pratica su:
* Avvio di un nuovo progetto
* Configurazione per la realtà mista
* Gestione dell'input utente
* Aggiunta di pulsanti
* Riproduzione su un emulatore o dispositivo

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, è importante verificare che siano installati gli elementi seguenti:
* Windows 10 1809 o versioni successive
* Windows 10 SDK 10.0.18362.0 o versioni successive
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 o versione successiva
* Dispositivo Microsoft HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) o [emulatore](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* Visual Studio 2019 con i carichi di lavoro seguenti

### <a name="installing-visual-studio-2019"></a>Installazione di Visual Studio 2019

Assicurarsi, innanzitutto, che la configurazione venga eseguita con tutti i pacchetti di Visual Studio necessari:
1. Installa la versione più recente di [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
1. Installa i [carichi di lavoro](/visualstudio/install/modify-visual-studio#modify-workloads) seguenti:
    * Sviluppo per desktop con C++
    * Sviluppo per desktop .NET
    * Sviluppo per la piattaforma UWP
1. Espandere Sviluppo per la piattaforma UWP e selezionare: 
    * Connettività dispositivi USB
    * Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v142)

1. Installa i [componenti](/visualstudio/install/modify-visual-studio#modify-individual-components) seguenti:
    * Compilatori, strumenti di compilazione e runtime > MSVC versione 142 - VS 2019 C++ ARM64 Build Tools (versione più recente)

È possibile verificare l'installazione con l'immagine seguente:

![Segni di spunta importanti nel programma di installazione VS](images/unreal-uxt/1-install-the-tools.png)

Ecco fatto! Ora è tutto pronto per iniziare il progetto degli scacchi.

[Sezione successiva: 2. Inizializzazione del progetto e prima applicazione](unreal-uxt-ch2.md)