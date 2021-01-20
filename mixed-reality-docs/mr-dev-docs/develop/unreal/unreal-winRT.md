---
title: WinRT in Unreal
description: Informazioni su come scrivere e gestire funzionalità WinRT personalizzate in app Real realtà miste per dispositivi HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, Guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, WinRT, DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580414"
---
# <a name="winrt-in-unreal"></a>WinRT in Unreal

Nel corso dello sviluppo di HoloLens potrebbe essere necessario scrivere una funzionalità usando WinRT. Se ad esempio si apre una finestra di dialogo di file in un'applicazione HoloLens, è necessario FileSavePicker nel file di intestazione WinRT/Windows. storage. Pickers. h. WinRT è supportato nel sistema di compilazione Unreal dalla versione 4,26 e successive.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso per lo sviluppo con Unreal che è stato delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui è possibile passare a qualsiasi [argomento](unreal-development-overview.md#3-advanced-features) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.

> [!div class="nextstepaction"]
> [Distribuzione nel dispositivo](unreal-deploying.md)

## <a name="see-also"></a>Vedere anche

* [API C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Librerie di terze parti non reali](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)