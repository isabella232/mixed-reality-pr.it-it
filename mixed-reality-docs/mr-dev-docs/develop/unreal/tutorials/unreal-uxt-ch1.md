---
title: 1. Guida introduttiva
description: Parte 1 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: aa6d90bebbbfc10b108b97d05931a9926118ba7c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679860"
---
# <a name="1-getting-started"></a>1. Guida introduttiva

Che tu sia alle prime armi o un professionista esperto, questo è il punto di partenza ideale per esplorare [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e [Unreal Engine](https://www.unrealengine.com/en-US/). Questa serie di esercitazioni ti offrirà una guida dettagliata su come creare un'app di scacchi interattiva con il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), che fa parte di [Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). Con il plug-in potrai aggiungere comuni funzionalità UX ai tuoi progetti con codice, progetti ed esempi. 

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

Alla fine della serie avrai acquisito esperienza pratica su:
* Avvio di un nuovo progetto
* Configurazione per la realtà mista
* Gestione dell'input utente
* Aggiunta di pulsanti
* Riproduzione su un emulatore o dispositivo


## <a name="prerequisites"></a>Prerequisiti
Prima di iniziare, è importante verificare che siano installati gli elementi seguenti:
* Windows 10 1809 o versioni successive
* Windows 10 SDK 10.0.18362.0 o versioni successive
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o versioni successive
* Dispositivo Microsoft HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) o emulatore
* Visual Studio 2019 con i carichi di lavoro seguenti

### <a name="installing-visual-studio-2019"></a>Installazione di Visual Studio 2019
Per verificare di avere a disposizione tutti i pacchetti di Visual Studio necessari, è necessario eseguire alcuni passaggi:
1. Installa la versione più recente di [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
2. Installa i [carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) seguenti:
    * Sviluppo per desktop con C++
    * Sviluppo per desktop .NET
    * Sviluppo per la piattaforma UWP

3. Installa i [componenti](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) seguenti:
    * Compilatori, strumenti di compilazione e runtime > MSVC versione 142 - VS 2019 C++ ARM64 Build Tools (versione più recente)

Ecco fatto! Ora è tutto pronto per iniziare il progetto degli scacchi.

[Sezione successiva: 2. Inizializzazione del progetto e prima applicazione](unreal-uxt-ch2.md)