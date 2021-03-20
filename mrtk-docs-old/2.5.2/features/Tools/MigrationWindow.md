---
title: MigrationWindow
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a670a3c1fb68037a8ecf8989dd0a84f8e0407e62
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693858"
---
# <a name="migration-window"></a>Finestra di migrazione

Quando il MRTK subisce modifiche, è possibile che alcuni componenti vengano deprecati e che vengano introdotti sostituzioni.
La finestra migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.

![Finestra di migrazione](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Utilizzo

Per aprire la finestra, selezionare la finestra di migrazione utilità del *Toolkit di realtà mista*  >    >  . Una volta aperta la finestra di migrazione, è possibile abilitare le schede di navigazione in modalità selezione scegliendo l'implementazione specifica del componente del gestore di migrazione.  

![Modalità di selezione della migrazione](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modalità oggetto

Selezionando la scheda oggetti, viene abilitato il campo oggetto in cui l'utente può trascinare e rilasciare gli oggetti gioco dalla scena attualmente aperta o dai prefabbricati dalla cartella del progetto da migrare.
Premendo il pulsante Rimuovi *(-)* visualizzato a destra dell'oggetto elencato viene rimosso l'oggetto dall'elenco di selezione.

Una volta che tutti gli oggetti desiderati sono presenti nell'elenco, se si preme il pulsante *migra* verranno applicate le modifiche richieste dall'implementazione del gestore della migrazione scelta a tutti i componenti della selezione che corrispondono all'implementazione.

![Migrazione selezione](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modalità scena

Consente all'utente di trascinare e rilasciare asset della scena contenenti oggetti da migrare.

![Selezione di scene per la migrazione](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Modalità progetto

Quando si preme il pulsante *migra* , il componente di destinazione dell'implementazione del gestore della migrazione viene aggiornato per tutte le prefabbricate e le scene del progetto.

![Migrazione di un progetto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Vedi anche

- [Aggiornamento da versioni precedenti](../../updates-deployment/Updating.md)
- [Versioni di Microsoft Mixed Reality Toolkit](../../packages-releases/ReleaseNotes.md)
- [Roadmap MRTK](../../Roadmap.md)
