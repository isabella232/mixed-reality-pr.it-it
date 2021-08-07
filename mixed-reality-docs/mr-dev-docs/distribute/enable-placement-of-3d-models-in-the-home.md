---
title: Abilitare il posizionamento di modelli 3D nello spazio iniziale
description: Informazioni su come inserire modelli 3D dal sito Web o dall'applicazione nella Windows Mixed Reality home page.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modello, luogo in casa, luogo, mondo, modellazione, ambiente iniziale, Web, app, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186797"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Abilitare il posizionamento di modelli 3D nell'ambiente iniziale

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte [dell'Windows 10 di aprile 2018.](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) Le versioni precedenti Windows non sono compatibili con questa funzionalità.

La [Windows Mixed Reality iniziale è il](../discover/navigating-the-windows-mixed-reality-home.md) punto di partenza da cui gli utenti atterrerà prima di avviare le applicazioni. In alcuni scenari, le app 2D(come l'app Ologrammi) consentono il posizionamento dei modelli 3D direttamente nel ambiente iniziale come decorazione o per un'ulteriore ispezione in 3D completo. Il  protocollo di aggiunta del modello consente di inviare un modello 3D dal sito Web o dall'applicazione direttamente nella home page di Windows Mixed Reality, dove verrà mantenuto come utilità di avvio di [app 3D,](3d-app-launcher-design-guidance.md)app 2D e ologrammi. 

Ad esempio, se si sta sviluppando un'applicazione che mette in primo piano  un catalogo di mobili 3D per la progettazione di uno spazio, usare il protocollo di aggiunta del modello per consentire agli utenti di inserire tali modelli di mobili 3D dal catalogo. Una volta inseriti nel mondo, gli utenti possono spostare, ridimensionare e rimuovere questi modelli 3D come altri ologrammi nella casa. Questo articolo offre una panoramica  dell'implementazione del protocollo di aggiunta del modello per consentire agli utenti di decorare il proprio mondo con oggetti 3D dall'app o dal Web.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Aggiungere il protocollo del modello</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Nozioni di base

Esistono due passaggi per abilitare il posizionamento dei modelli 3D nella home Windows Mixed Reality home:
1. [Verificare che il modello 3D sia compatibile con il Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implementare *il protocollo di aggiunta del* modello nell'applicazione o nella pagina Web (questo articolo).

## <a name="implementing-the-add-model-protocol"></a>Implementazione del *protocollo di aggiunta del modello*

Dopo aver creato un [modello 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)compatibile, è possibile implementare il protocollo di aggiunta del modello attivando l'URI seguente da qualsiasi pagina Web o applicazione: 

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se l'URI punta a una risorsa remota, verrà automaticamente scaricato e inserito nella home page. Le risorse locali verranno copiate nella ambiente iniziale dei dati dell'app prima di essere posizionate nella home page. È consigliabile progettare l'esperienza per gli scenari in cui l'utente potrebbe eseguire una versione precedente di Windows che non supporta questa funzionalità nascondendo il pulsante o disabilitandolo, se possibile. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Richiamo del protocollo *di aggiunta del modello* da un'app universal Windows Platform:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Richiamo del protocollo *di aggiunta del modello* da una pagina Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerazioni sui visori VR immersive

* Per i visori VR immersive, il Portale realtà mista non deve essere in esecuzione prima di richiamare il *protocollo di aggiunta del modello*. In questo caso, il protocollo di aggiunta del modello avvierà il Portale realtà mista e inserirà l'oggetto direttamente nel punto in cui il visore VR sta guardando quando si arriva al ambiente iniziale.  
* Quando si richiama il *protocollo di* aggiunta del modello dal desktop con il Portale realtà mista già in esecuzione, assicurarsi che il visore VR sia "attivo". In caso contrario, il posizionamento non avrà esito positivo. 

## <a name="see-also"></a>Vedi anche

* [Creazione di modelli 3D da usare nella home page Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)