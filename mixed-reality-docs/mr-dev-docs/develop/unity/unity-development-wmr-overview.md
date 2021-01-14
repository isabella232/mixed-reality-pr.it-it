---
title: Sviluppo in Unity per VR
description: Guida introduttiva alla creazione di app di realtà mista in Unity per VR e visori VR immersive di Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realtà mista, sviluppo, guida introduttiva, nuovo progetto, conversione, funzionalità, fotocamera, simulazione, emulazione, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, che cos'è la realtà virtuale, che cos'è la realtà aumentata, MRTK, mixed reality toolkit, input vocale, fotocamera individuabile, emulatore, Azure, esercitazioni
ms.openlocfilehash: ba63f137e90b68345f3e5bbb831aba6abd6fe538
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040579"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>Sviluppo in Unity per VR e Windows Mixed Reality

![Logo banner di Unity](../images/unity_logo_banner.png)

Se si usa Unity per la prima volta, prima di continuare è consigliabile esplorare le [esercitazioni](https://unity3d.com/learn/tutorials) di livello principiante nella piattaforma Unity Learn. È anche opportuno visitare i [forum di Unity sulla realtà mista](https://forum.unity3d.com/forums/hololens.102/) per partecipare alla community online impegnata nella creazione di app di realtà mista. In questi ambienti si scoprono spesso risorse o soluzioni estremamente interessanti. Per iniziare a usare MRTK, passare ai checkpoint di sviluppo illustrati di seguito.

> [!IMPORTANT]
> Se si ha a disposizione un progetto Unity da trasmettere a un visore VR immersive di Windows Mixed Reality, consultare le **[guide alla conversione](../porting-apps/porting-overview.md)** . 

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista. 

### <a name="1-getting-started"></a>1. Guida introduttiva

È presente piccolo set di impostazioni di Unity da modificare manualmente per Windows Mixed Reality e lo sviluppo per VR. Le impostazioni sono suddivise in due categorie: per progetto e per scena. Al termine di questa sezione, saranno disponibili le impostazioni di progetto e gli strumenti necessari per iniziare a creare le app personali.

|  Checkpoint  |  Risultato  |
| --- | --- |
| [Installare gli ultimi aggiornamenti](../install-the-tools.md) | Scaricare e installare il pacchetto Unity più recente e configurare il progetto per la realtà mista |
| [Configurazione del progetto per WMR](configure-unity-project.md) | Vedere le informazioni su come creare applicazioni che eseguono il rendering di contenuto digitale in dispositivi di visualizzazione olografici e VR |

### <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Dopo aver avviato un nuovo progetto immersivo, sono necessari alcuni blocchi predefiniti di base per sviluppare app immersive. Tutti i componenti di base per le applicazioni di realtà mista sono esposti in modo coerente con altre API di Unity Potrebbero non essere tutti necessari nell'immediato, ma è bene esaminarli nella fase iniziale. Dopo aver esaminato i blocchi predefiniti fondamentali indicati di seguito, si avrà a disposizione un insieme completo di funzionalità che è possibile integrare nei progetti VR.

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-platform-capabilities-and-apis"></a>3. API e funzionalità della piattaforma

Altre funzionalità chiave per le applicazioni immersive sono disponibili tramite le API di Unity senza la necessità di ulteriori pacchetti o configurazioni. Dopo aver esaminato le funzionalità più avanzate offerte da Unity, sarà possibile creare app VR più complesse.

|  Funzionalità  |  Capabilities  |
| --- | --- |
| [Perdita del tracciamento](tracking-loss-in-unity.md) | Gestire gli scenari in cui il dispositivo non è in grado di individuare la propria posizione nello spazio globale dell'applicazione |
| [Input da tastiera](keyboard-input-in-unity.md) | Ottenere input nelle app da tastiere reali e di realtà mista |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Distribuzione in un dispositivo o un emulatore

Non appena il progetto Unity olografico è pronto per il test, il passaggio successivo è quello di esportare e compilare una soluzione Unity di Visual Studio. Con questa soluzione di Visual Studio è possibile eseguire l'applicazione in dispositivi reali o simulati. Al termine di questa sezione, sarà possibile distribuire l'applicazione in un dispositivo o un emulatore adatto alle specifiche esigenze di sviluppo.

* [Visore VR immersive di Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Simulatore di visore VR immersive di Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>Passaggi successivi

Il lavoro degli sviluppatori non finisce mai, soprattutto per quanto riguarda la conoscenza di nuovi strumenti o SDK. Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati. Questi argomenti e queste risorse non sono presentati in ordine sequenziale e possono quindi essere esplorati liberamente.

### <a name="porting"></a>Conversione

Se si hanno a disposizione app di cui si vuole eseguire la conversione, sarà utile consultare gli articoli elencati di seguito:

* [Conversione di app VR in Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [Aggiornamento di app SteamVR per Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a>Risorse aggiuntive

Prima di entrare nel mondo della realtà mista in totale autonomia, è consigliabile esaminare la documentazione aggiuntiva indicata di seguito. 

* [Guida per appassionati di VR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity Asset Store](https://www.assetstore.unity3d.com)

## <a name="see-also"></a>Vedere anche 

* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
