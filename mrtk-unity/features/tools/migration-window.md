---
title: Finestra di migrazione
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647118"
---
# <a name="migration-window"></a>Finestra di migrazione

Quando MRTK subisce modifiche, alcuni componenti potrebbero essere deprecati e verranno introdotte sostituzioni.
La finestra di migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.

![Finestra di migrazione](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Utilizzo

Per aprire la finestra, selezionare **Mixed Reality** Toolkit Utilities Migration  >  Window (Finestra di migrazione delle utilità di Mixed Reality  >    >  Toolkit). Una volta aperta la finestra di migrazione, le schede di navigazione in modalità di selezione possono essere abilitate scegliendo l'implementazione specifica del componente del gestore della migrazione.  

![Modalità di selezione della migrazione](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modalità oggetto

La selezione della scheda Oggetti consente all'oggetto Campo in cui l'utente può trascinare e rilasciare tutti gli oggetti Game dalla scena o dai prefab attualmente aperti dalla cartella del progetto da migrare.
Se si preme *il pulsante rimuovi (-)* visualizzato a destra dell'oggetto elencato, l'oggetto viene rimosso dall'elenco di selezione.

Quando tutti gli oggetti desiderati sono  presenti nell'elenco, premendo il pulsante Migrate (Esegui migrazione) verranno applicate le modifiche richieste dall'implementazione del gestore di migrazione scelta a tutti i componenti nella selezione che corrispondono all'implementazione.

![Migrazione della selezione](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modalità scena

Consente all'utente di trascinare e rilasciare gli asset della scena contenenti oggetti di cui eseguire la migrazione.

![Selezione di scene per la migrazione](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Modalità progetto

Se si *preme il pulsante* Esegui migrazione, il componente di destinazione dell'implementazione del gestore di migrazione verrà aggiornato per tutti i prefab e le scene nel progetto.

![Migrazione di un progetto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Vedi anche

- [Aggiornamento da versioni precedenti](../../updates-deployment/updating.md)
- [Versioni di Microsoft Mixed Reality Toolkit](../../release-notes/mrtk-26-release-notes.md)
- [Guida di orientamento a MRTK](../../roadmap.md)
