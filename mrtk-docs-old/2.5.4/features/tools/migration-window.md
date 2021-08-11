---
title: Finestra di migrazione
description: Documentazione su come eseguire la migrazione a un aggiornamento in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 655c35a750a2a247b497a7cb2b04f1708646913650ec9f1c95ba9f4b8a944c9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218997"
---
# <a name="migration-window"></a>Finestra di migrazione

Quando mrTK subisce modifiche, alcuni componenti potrebbero essere deprecati e verranno introdotte le sostituzioni.
La finestra di migrazione è uno strumento che consente agli utenti di eseguire automaticamente la migrazione di un subset di tali componenti deprecati alle nuove sostituzioni.

![Finestra di migrazione](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Utilizzo

Per aprire la finestra, selezionare *Mixed Reality Toolkit* Utilities Migration Window (Finestra di migrazione di Mixed Reality Toolkit  >    >  *Utilities).* Una volta aperta la finestra di migrazione, le schede di navigazione in modalità di selezione possono essere abilitate scegliendo l'implementazione specifica del componente del gestore della migrazione.  

![Modalità di selezione della migrazione](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Modalità oggetto

La selezione della scheda Oggetti consente all'oggetto Campo in cui l'utente può trascinare e rilasciare qualsiasi oggetto Game dalla scena o dai prefab attualmente aperti dalla cartella del progetto da migrare.
Se si preme *il pulsante rimuovi (-)* visualizzato sul lato destro dell'oggetto elencato, l'oggetto viene rimosso dall'elenco di selezione.

Quando tutti gli oggetti desiderati sono  presenti nell'elenco, premendo il pulsante Esegui migrazione le modifiche richieste dall'implementazione del gestore di migrazione scelta verranno applicate a tutti i componenti nella selezione corrispondenti all'implementazione.

![Migrazione della selezione](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Modalità scena

Consente all'utente di trascinare e rilasciare gli asset della scena contenenti oggetti di cui eseguire la migrazione.

![Selezione di scene per la migrazione](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project predefinita

Premendo il *pulsante Esegui* migrazione, il componente di destinazione dell'implementazione del gestore di migrazione verrà aggiornato per tutti i prefab e le scene nel progetto.

![Migrazione di un progetto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Vedi anche

- [Aggiornamento da versioni precedenti](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality Toolkit versioni](../../packages-releases/release-notes.md)
- [Roadmap di MRTK](../../roadmap.md)
