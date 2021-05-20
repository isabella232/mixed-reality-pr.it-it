---
title: Finestra di compilazione MRTK
description: Documentazione sull'uso della finestra di compilazione in MRTK per Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, compilazione, finestra di compilazione, strumenti
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196868"
---
# <a name="build-window"></a>Finestra Di compilazione
![Compilare & flusso di distribuzione](images/MRTK_BuildWindow0.png)

La finestra di compilazione di MRTK semplifica la compilazione & distribuire i MRTK-Unity progetto. Con un solo clic del pulsante, è possibile compilare il progetto Unity e generare Visual Studio soluzione(. SLN), pacchetto app UWP(. APPX) e installare il pacchetto dell'app nel dispositivo. 


## <a name="unity-build-options"></a>Opzioni di compilazione di Unity
![Finestra di compilazione - Opzioni di compilazione di Unity 1](images/MRTK_BuildWindow1.png)

Queste scene sono tratta dalle impostazioni di compilazione di Unity. È possibile modificare il tipo di dispositivo di destinazione usando il menu a discesa.

## <a name="appx-build-options"></a>Opzioni di compilazione appx
![Finestra Di compilazione - Opzioni di compilazione di Appx 2](images/MRTK_BuildWindow2.png)

Questa scheda mostra la configurazione per la Visual Studio soluzione. Per HoloLens 2 funzionalità di input di tracciamento oculare, selezionare **l'opzione Funzionalità di input sguardo** fisso. 

È possibile assegnare il file con estensione glb nel campo Modello di avvio app **3D** per l'icona di avvio di app 3D personalizzata. Per altre informazioni, vedere Linee guida per la progettazione dell'utilità di avvio di app [3D.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)

Per impostazione predefinita, **l'incremento** automatico è selezionato in Opzioni di controllo delle versioni. Le versioni di AppX verranno incrementate automaticamente.


## <a name="deploy-options"></a>Opzioni di distribuzione
![Finestra Di compilazione - Opzioni di distribuzione 3](images/MRTK_BuildWindow3.png)

In questa scheda è possibile connettersi al dispositivo immettendo nome utente e password per il Portale di dispositivi. 

Nella parte inferiore della pagina è possibile trovare l'elenco dei pacchetti dell'app creati. 

