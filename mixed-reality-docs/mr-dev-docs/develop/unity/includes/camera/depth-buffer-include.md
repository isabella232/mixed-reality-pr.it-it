---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212275"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La finestra di dialogo di configurazione di [MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tenterà di impostare le impostazioni del buffer di profondità sia per XR SDK che per WSA legacy, ma è bene controllare queste schede e verificare le impostazioni in Unity.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per impostare se l'app Unity fornirà un buffer di profondità per Windows:

1. Passare a  >  **Modifica Project Impostazioni** gestione  >  **plug-in XR** e verificare che la voce di menu sia espansa.
2. Fare clic sulla voce di menu corrispondente al runtime XR scelto, Windows Mixed Reality o OpenXR. Assicurarsi inoltre che sia selezionata la piattaforma di compilazione corretta, in quanto sono disponibili schede sia per Windows autonoma che per la piattaforma Windows universale.
3. Per abilitare e configurare:
    1. Per OpenXR, selezionare un formato di profondità o "Nessuno" nell'elenco a discesa **Modalità di invio** della profondità.
    2. Per Windows Mixed Reality, selezionare o deselezionare la casella di controllo **Buffer di profondità** condivisa. Selezionare quindi un formato nell'elenco a **discesa Formato buffer** di profondità.

![Windows Impostazioni di profondità del plug-in ](../../images/xrsdk-winxr-depth.png)
 ![ XR Impostazioni di profondità OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> È in genere consigliabile usare buffer di profondità a 16 bit per migliorare le prestazioni. Tuttavia, se si usa un formato di profondità a 16 bit, gli effetti necessari del buffer di stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile nella piattaforma grafica dell'endpoint.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Per impostare se l'app Unity fornirà un buffer di profondità per Windows:

1. Passare alla **scheda**  >  **Edit Project Impostazioni**  >  **Player** Universal Windows Platform  >    >  **XR Impostazioni**.
2. Espandere **l'Windows Mixed Reality SDK.**
3. Selezionare o deselezionare la **casella di controllo Abilita condivisione buffer** di profondità. L'opzione Abilita condivisione buffer di profondità è selezionata per impostazione predefinita nei nuovi progetti, ma potrebbe essere stata deselezionata per impostazione predefinita nei progetti precedenti.

![Impostazioni di profondità XR legacy](../../images/wmr-depth.png)

Un buffer di profondità può migliorare la qualità visiva purché Windows sia in grado di eseguire il mapping accurato dei valori di profondità normalizzati per pixel nel buffer di profondità alle distanze in metri, usando i piani vicino e lontano impostati in Unity nella fotocamera principale. Se i passaggi di rendering gestiscono i valori di profondità in modo tipico, è in genere consigliabile usare questa opzione, anche se i passaggi di rendering traslucidi che scrivono nel buffer di profondità durante la visualizzazione nei pixel di colore esistenti possono confondere la riproiezione.  Se si sa che i passaggi di rendering lasciano molti dei pixel di profondità finali con valori di profondità non accurati, è probabile che si otterrà una migliore qualità visiva deselezionando "Abilita condivisione buffer di profondità".

> [!NOTE]
> È in genere consigliabile usare buffer di profondità a 16 bit per migliorare le prestazioni. Tuttavia, se si usa un formato di profondità a 16 bit, gli effetti necessari del buffer di stencil (come alcuni pannelli di scorrimento dell'interfaccia utente di Unity) non funzioneranno perché Unity non crea un [buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in questa impostazione. Se si seleziona il formato di profondità a *24 bit,* in genere verrà creato un buffer di stencil a [8 bit,](https://docs.unity3d.com/Manual/SL-Stencil.html) se applicabile nella piattaforma grafica dell'endpoint.