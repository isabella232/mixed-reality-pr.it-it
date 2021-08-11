---
title: WinRT in Unreal
description: Informazioni su come scrivere e gestire funzionalità WinRT personalizzate nelle app di realtà mista Unreal per HoloLens dispositivi.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, introduzione, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, WinRT, DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198381"
---
# <a name="winrt-in-unreal"></a>WinRT in Unreal

Nel corso dell'HoloLens sviluppo potrebbe essere necessario scrivere una funzionalità usando WinRT. Ad esempio, l'apertura di una finestra di dialogo file in HoloLens'applicazione potrebbe avere bisogno di FileSavePicker in winrt/Windows. Archiviazione. File di intestazione Pickers.h. WinRT è supportato nel sistema di compilazione di Unreal a partire dalla versione 4.26.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso per lo sviluppo con Unreal che è stato delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui è possibile passare a [qualsiasi](unreal-development-overview.md#3-advanced-features) argomento o passare direttamente alla distribuzione dell'app in un dispositivo o un emulatore.

> [!div class="nextstepaction"]
> [Distribuzione nel dispositivo](unreal-deploying.md)

## <a name="see-also"></a>Vedi anche

* [API C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Librerie di terze parti Unreal](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)