---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110631489"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La finestra di dialogo di configurazione di [MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tenterà di impostare le impostazioni del buffer di profondità sia per XR SDK che per WSA legacy, ma è bene controllare queste schede e verificare le impostazioni in Unity.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per impostare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **Modifica**  >  **impostazioni progetto** Gestione  >  **plug-in XR** e verificare che la voce di menu sia espansa.
2. Fare clic sulla voce di menu corrispondente al runtime XR scelto, Windows Mixed Reality o OpenXR. Assicurarsi inoltre che sia selezionata la piattaforma di compilazione corretta, in quanto sono disponibili schede sia per Windows autonomo che per piattaforma UWP (Universal Windows Platform).
3. Per abilitare e configurare:
    1. Per OpenXR, selezionare un formato di profondità o "Nessuno" nell'elenco a discesa **Modalità di invio** della profondità.
    2. Per Windows Mixed Reality, selezionare o deselezionare la casella di controllo **Buffer profondità** condivisa. Selezionare quindi un formato nell'elenco a **discesa Formato buffer** di profondità.

![Impostazioni di profondità del plug-in Windows XR ](../../images/xrsdk-winxr-depth.png)
 ![ Impostazioni di profondità OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> È in genere consigliabile usare buffer di profondità a 16 bit per migliorare le prestazioni. Tuttavia, se si usa un formato di profondità a 16 bit, gli effetti necessari del buffer di stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile nella piattaforma grafica dell'endpoint.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per impostare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **Edit** Project Settings Player (Modifica impostazioni  >    >    >  **progetto) piattaforma UWP (Universal Windows Platform) scheda**  >  **XR Settings (Impostazioni XR).**
2. Espandere **l'Windows Mixed Reality SDK.**
3. Selezionare o deselezionare la **casella di controllo Abilita condivisione buffer** di profondità. L'opzione Abilita condivisione buffer di profondità è selezionata per impostazione predefinita nei nuovi progetti, ma potrebbe essere stata deselezionata per impostazione predefinita nei progetti precedenti.

![Impostazioni di profondità XR legacy](../../images/wmr-depth.png)

Un buffer di profondità può migliorare la qualità visiva, purché Windows sia in grado di eseguire in modo accurato il mapping dei valori di profondità normalizzati per pixel nel buffer di profondità alle distanze in metri, usando i piani vicino e lontano impostati in Unity nella fotocamera principale. Se i passaggi di rendering gestiscono i valori di profondità in modo tipico, è in genere consigliabile usare questa opzione, anche se i passaggi di rendering traslucidi che scrivono nel buffer di profondità durante la visualizzazione nei pixel di colore esistenti possono confondere la riproiezione.  Se si sa che i passaggi di rendering lasciano molti dei pixel di profondità finali con valori di profondità non accurati, è probabile che si otterrà una migliore qualità visiva deselezionando "Abilita condivisione buffer di profondità".

> [!NOTE]
> È in genere consigliabile usare buffer di profondità a 16 bit per migliorare le prestazioni. Tuttavia, se si usa un formato di profondità a 16 bit, gli effetti necessari del buffer di stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile nella piattaforma grafica dell'endpoint.