---
title: Visualizzazione del feedback su Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come visualizzare feedback da Ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, sessioni, elementi di feedback
ms.localizationpriority: high
ms.openlocfilehash: 65a814019909ecacffdd454171075c68497dae1b2123804e07ced1d7e100fdd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215672"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Visualizzazione del feedback su Ancoraggi nello spazio di Azure

In questa esercitazione si apprenderà come fornire agli utenti feedback su individuazione, eventi e stato degli ancoraggi con Ancoraggi nello spazio di Azure (ASA).

## <a name="objectives"></a>Obiettivi

* Imparare a configurare un riquadro dell'interfaccia utente in cui vengono visualizzate informazioni fondamentali sulla sessione ASA corrente
* Imparare ed esplorare gli elementi di feedback che ASA SDK mette a disposizione degli utenti

## <a name="setting-up-asa-feedback-panel"></a>Configurazione del riquadro per il feedback di ASA

Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse sull'oggetto **Instructions** (Istruzioni)  > **TextContent**. Selezionare **3D Object** (Oggetto 3D)  > **Text (Testo) - TextMeshPro** per creare un oggetto testo TextMeshPro come figlio dell'oggetto Instructions (Istruzioni) > TextContent:

![Unity con l'oggetto TextMeshPro appena creato selezionato](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Per rendere più agevole l'uso della scena, disattiva la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità</a> per l'oggetto ParentAnchor facendo clic sull'icona a forma di occhio a sinistra dell'oggetto. In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco.

Rinominare l'oggetto Text (TMP) appena creato **Feedback** e quindi, modificare la relativa dimensione e posizione nella finestra Inspector (Controllo), in modo che l'oggetto venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:

* Modificare il valore di **Pos Y** (Posizione Y) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su -0,24.
* Modificare il valore di **Width** (Larghezza) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su 0,555.
* Modificare il valore di **Height** (Altezza) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su -0,1.

Scegliere quindi le proprietà del tipo di carattere, in modo da adattare bene il testo all'interno dell'area di testo, ad esempio:

* Modificare il valore di **Font Style** (Stile carattere) per il componente TextMeshPro - Text (Testo) impostandolo su Bold (Grassetto).
* Modificare il valore di **Font Size** (Dimensioni carattere) per il componente TextMeshPro - Text (Testo) impostandolo su 0,17.
* Modificare il valore di **Alignment** (Allineamento) per il componente TextMeshPro - Text (Testo) impostandolo su Center (Al centro verticalmente) e Middle (Al centro orizzontalmente).

![Unity con l'oggetto Feedback configurato](images/mr-learning-asa/asa-04-section1-step1-2.png)

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Feedback** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente), per aggiungere il componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script) e configuralo come indicato di seguito:

* Assegnare l'oggetto **Feedback** stesso al campo **Feedback Text** (Testo feedback) del componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script).

![Unity con il componente Anchor Feedback Script configurato](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come creare un pannello dell'interfaccia utente. Questo pannello visualizza lo stato corrente dell'esperienza di Ancoraggi nello spazio di Azure per fornire agli utenti feedback in tempo reale.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 5. Ancoraggi nello spazio di Azure per Android e iOS](mr-learning-asa-05.md)
