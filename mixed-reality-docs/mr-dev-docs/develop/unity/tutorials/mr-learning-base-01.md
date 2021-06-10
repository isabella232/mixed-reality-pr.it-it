---
title: Introduzione alle esercitazioni di MRTK
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista da zero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, risolutori, tracciamento oculare, comandi vocali
ms.localizationpriority: high
ms.openlocfilehash: 0af75341aa1c90f38ac679dd1ff2db6ab2796839
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403342"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Introduzione alle esercitazioni di MRTK

Serie di esercitazioni introduttive Nel corso di queste esercitazioni, verranno fornite informazioni su Mixed Reality Toolkit (MRTK) e alcune delle funzionalità che offre. Sarà anche possibile creare un'esperienza di realtà mista in cui l'utente può esplorare un ologramma modellato in base a Mars Curiosity Rover della NASA. Al termine di questa serie, si disporrà di una solida conoscenza di MRTK e dell'utilizzo di questo strumento per accelerare il processo di sviluppo.

Le esercitazioni di questa serie sono sequenziali, consultarle quindi nell'ordine corretto:

1. [Introduzione](mr-learning-base-01.md) (l'esercitazione corrente)
2. [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md)
3. [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md)
4. [Posizionamento degli oggetti nella scena](mr-learning-base-04.md)
5. [Creazione di contenuto dinamico tramite risolutori](mr-learning-base-05.md)
6. [Creazione delle interfacce utente](mr-learning-base-06.md)
7. [Interazione con oggetti 3D](mr-learning-base-07.md)
8. [Uso del tracciamento oculare](mr-learning-base-08.md)
9. [Uso dei comandi vocali](mr-learning-base-09.md)

## <a name="objectives"></a>Obiettivi

* Imparare a configurare Unity per MRTK
* Imparare a compilare e distribuire nel dispositivo
* Imparare a usare alcune delle funzionalità chiave di MRTK
* Creare un'esperienza di realtà mista completa

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 o versioni successive
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020 LTS (attualmente 2020.3.x) o Unity 2019 LTS (attualmente 2019.4.x) installato e il modulo piattaforma UWP (Universal Windows Platform) Build Support aggiunto

Quando si installa Unity, assicurarsi di controllare i componenti seguenti in **"Piattaforme".**

* **piattaforma UWP (Universal Windows Platform) di compilazione**
* **Supporto per la compilazione di Windows (IL2CPP)**

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../../../develop/images/Unity_Install_Option_UWP.png)

Se Unity è stato installato senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub.

![Opzione Unity Windows Build Support (Supporto per la compilazione di Windows in Unity)](../../../develop/images/Unity_Install_Option_UWP2.png)

> [!Important]
> La versione consigliata di MRTK per questa serie di esercitazioni è MRTK 2.7.

> [!Important]
> Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin. Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md)
