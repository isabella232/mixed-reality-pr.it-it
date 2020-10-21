---
title: Collegare il visore VR
description: Informazioni su come connettere il dispositivo auricolare per la realtà mista di Windows a USB 3,0 e HDMI e su come connettere le cuffie alla cuffia.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, auricolare, installazione, introduzione
appliesto:
- Windows 10
ms.openlocfilehash: 16c06e14566671e44b1424447b02493ba1ff1a83
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2020
ms.locfileid: "92292978"
---
# <a name="plug-in-your-headset"></a>Collegare il visore VR

## <a name="connect-your-headset-to-your-pcs-usb-30-port"></a>Connettere l'auricolare alla porta USB 3,0 del PC

Identificare la porta USB 3,0 nel computer e collegare il cavo USB. Le porte USB 3,0 contengono SS (Super Speed) scritte accanto ad esse. Spesso (ma non sempre) blu.

Se non si dispone di un numero sufficiente di porte USB aperte nel PC, è possibile usare un [hub usb 3,0 esterno alimentato da AC](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets).

## <a name="connect-your-headset-to-your-pcs-hdmi-out-port"></a>Connettere l'auricolare alla porta di uscita HDMI del PC

Identificare la porta HDMI out del computer e collegare il cavo HDMI dell'auricolare. Assicurarsi che **non** si stia effettuando il collegamento a HDMI in porta.

## <a name="connect-headphones-to-your-headset"></a>Connettere le cuffie all'auricolare

A meno che non sia stato acquistato un auricolare Samsung HMD Odyssey, HP Reverb o HP reverbi G2 (che hanno integrato cuffie AKG e un microfono dual array integrato), è necessario connettere le cuffie (preferibilmente con un microfono in linea) in grado di collegarsi ai jack audio da 3,5 mm dell'auricolare.

## <a name="common-issues"></a>Problemi comuni

* È stato collegato il cavo HDMI prima di collegare il cavo USB 3,0.  Assicurarsi di collegare il cavo USB 3,0 **prima** di collegare il cavo HDMI.
* È stata inserita una scheda Bluetooth accanto al cavo USB di HMD.  Se si usa una scheda Bluetooth, non **collegare il** cavo USB dell'auricolare accanto alla scheda perché l'interferenza radio risultante può influire negativamente sulle prestazioni Bluetooth.
* Il cavo HDMI è stato collegato alla porta iGPU HDMI anziché alla porta dGPU HDMI (per i PC con entrambi). Alcuni PC desktop dispongono di un'unità di elaborazione grafica integrata (iGPU) e di un'unità di elaborazione grafica (dGPU) discreta e spesso le porte iGPU verranno disabilitate. Se il PC dispone di un dGPU, è necessario collegare l'auricolare al dGPU.  
* Se il PC non dispone di una porta HDMI, potrebbe essere necessario un adapter. Per [visualizzare l'elenco completo degli adapter consigliati, vedere qui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
* Si sta connettendo l'auricolare a un dispositivo Surface. Leggere [usando Surface con la realtà mista di Windows](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="see-also"></a>Vedere anche

* [Risoluzione dei problemi di connettività auricolare](headset-connectivity.md)
* [Installare Windows Mixed Reality](install-windows-mixed-reality.md)
* [Adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* [Linee guida per l'hardware minimo](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
