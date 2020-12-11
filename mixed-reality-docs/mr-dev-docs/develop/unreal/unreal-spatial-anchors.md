---
title: Ancoraggi nello spazio locali in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: b517b1d89ddf7a35864db45a17336f4493816526
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609632"
---
# <a name="local-spatial-anchors-in-unreal"></a>Ancoraggi nello spazio locali in Unreal

Gli ancoraggi nello spazio salvano gli ologrammi nel mondo reale in più sessioni dell'applicazione come **ARPin**. Una volta salvati nell'archivio di ancoraggio di HoloLens, è possibile caricare ARPin in sessioni future e scegliere un'opzione di fallback ideale in assenza di connettività Internet.

> [!NOTE]
> Le funzioni di ancoraggio di UE 4.25 sono obsolete nella versione 4.26 e devono essere sostituite con funzioni più recenti. 

> [!IMPORTANT]
> Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud. Se si vuole usare i servizi cloud di Azure per archiviare gli ancoraggi, è disponibile un documento che fornisce informazioni dettagliate sull'integrazione di [Ancoraggi nello spazio di Azure](unreal-azure-spatial-anchors.md). Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.

## <a name="checking-the-anchor-store"></a>Verifica dell'archivio degli ancoraggi

Prima di salvare o caricare gli ancoraggi, verifica che l'archivio degli ancoraggi sia pronto.  Chiamando una delle funzioni di ancoraggio di HoloLens prima che l'archivio degli ancoraggi sia pronto, la chiamata avrà esito negativo.  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>Salvataggio degli ancoraggi

Quando l'applicazione dispone di un componente che si vuole aggiungere al mondo reale, è possibile salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito: 

[!INCLUDE[](includes/tabs-sa-2.md)]

Operazioni da eseguire:
1. Genera un attore in una posizione nota.
2. Crea un oggetto **ARPin** con quella posizione e un nome basato sulla classe dell'attore. 
3. Aggiungi l'attore all'oggetto **ARPin** e salva il segnaposto nell'archivio degli ancoraggi di HoloLens.  
    * Il nome dell'ancoraggio scelto deve essere univoco. In questo esempio è usato il timestamp corrente. 

4. Se l'ancoraggio viene salvato correttamente nell'archivio degli ancoraggi, è possibile ispezionarlo nel portale del dispositivo HoloLens in **System > Map manager > Anchor Files Saved On Device** (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo). 

## <a name="loading-anchors"></a>Caricamento degli ancoraggi

Quando un'applicazione viene avviata, puoi usare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:

[!INCLUDE[](includes/tabs-sa-3.md)]

Operazioni da eseguire:
1. Esegui l'iterazione di tutti gli ancoraggi nell'archivio degli ancoraggi. 
2. Genera un attore in corrispondenza dell'identità.
3. Blocca quell'attore sull'oggetto **ARPin** dall'archivio degli ancoraggi.  

    * È importante generare l'attore in corrispondenza dell'identità perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato. Qualsiasi trasformazione aggiunta qui aggiungerà un offset all'ancoraggio. 

Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio. 

## <a name="removing-anchors"></a>Rimozione degli ancoraggi 

Terminate le operazioni su un ancoraggio, è possibile eliminare singoli ancoraggi o l'intero archivio degli ancoraggi con i componenti **Remove ARPin from WMRAnchor Store** (Rimuovi ARPin dall'archivio WMRAnchor) e **Remove All ARPins from WMRAnchor Store** (Rimuovi tutti gli ARPin dall'archivio WMRAnchor).

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> Tieni presente che gli ancoraggi spaziali sono ancora in versione beta, quindi visualizza di nuovo questa pagina in futuro per verificare se sono presenti informazioni e funzionalità aggiornate.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK. Da qui, è possibile passare al blocco predefinito successivo: 

> [!div class="nextstepaction"]
> [Ancoraggi nello spazio di Azure](unreal-azure-spatial-anchors.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Ancoraggi nello spazio di Azure](unreal-azure-spatial-anchors.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Sistemi di coordinate](../../design/coordinate-systems.md)
