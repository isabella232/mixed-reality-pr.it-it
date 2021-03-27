---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636314"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La [finestra di dialogo di configurazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tenterà di impostare le impostazioni del buffer di profondità per XR SDK e il WSA legacy, ma è opportuno verificare le schede e verificare le impostazioni in Unity.

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per specificare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **modifica**  >  **Impostazioni progetto**  >  **Gestione plug-in di XR** e verificare che la voce di menu sia espansa.
2. Fare clic sulla voce di menu corrispondente al runtime XR scelto, ovvero la realtà mista di Windows o OpenXR. Assicurarsi inoltre che sia selezionata la piattaforma di compilazione corretta, in quanto le schede per Windows autonomo e piattaforma UWP (Universal Windows Platform) sono disponibili.
3. Per abilitare e configurare:
    1. Per OpenXR selezionare un formato di profondità o "None" nell'elenco a discesa **modalità di invio profondità** .
    2. Per la realtà mista di Windows, selezionare o deselezionare la casella di controllo **buffer di profondità condivisa** . Selezionare quindi un formato nell'elenco a discesa **formato buffer di profondità** .

![Impostazioni di profondità del plug-in Windows XR ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR impostazioni di profondità](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> È in genere consigliabile usare buffer a 16 bit di profondità per migliorare le prestazioni. Tuttavia, se si usa il formato di profondità a 16 bit, gli effetti necessari sul buffer dello stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il *formato di profondità a 24 bit,* in genere viene creato un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile sulla piattaforma grafica dell'endpoint.

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per specificare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **Edit**  >  **Project Settings**  >  **Player**  >  **piattaforma UWP (Universal Windows Platform) Tab**  >  **XR Settings**.
2. Espandere l'elemento **SDK di realtà mista di Windows** .
3. Selezionare o deselezionare la casella di controllo **Abilita condivisione buffer di profondità** . Per impostazione predefinita, l'opzione Abilita condivisione buffer di profondità è selezionata nei nuovi progetti, ma potrebbe essere stata deselezionata per impostazione predefinita nei progetti precedenti.

![Impostazioni di profondità XR legacy](../../images/wmr-depth.png)

Un buffer di profondità può migliorare la qualità visiva, purché Windows possa mappare accuratamente i valori di profondità per pixel normalizzati nel buffer di profondità a distanza in metri, usando i piani vicini e lontani impostati in Unity sulla fotocamera principale. Se il rendering passa i valori di profondità di gestione in modi tipici, in genere è opportuno eseguire questa procedura, sebbene i passaggi di rendering traslucidi che scrivono nel buffer di profondità durante la visualizzazione dei pixel di colore esistenti possano confondere la riproiezione.  Se si è certi che i passaggi di rendering lasceranno molti dei pixel di profondità finali con valori di profondità non corretti, è probabile che si ottenga una qualità visiva migliore deselezionando "Abilita condivisione buffer di profondità".

> [!NOTE]
> È in genere consigliabile usare buffer a 16 bit di profondità per migliorare le prestazioni. Tuttavia, se si usa il formato di profondità a 16 bit, gli effetti necessari sul buffer dello stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il *formato di profondità a 24 bit,* in genere viene creato un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile sulla piattaforma grafica dell'endpoint.