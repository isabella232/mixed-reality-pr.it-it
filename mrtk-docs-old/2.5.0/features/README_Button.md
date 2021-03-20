---
title: README_Butons
description: Panoramica sui pulsanti in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MRTK pulsanti
ms.openlocfilehash: a321aff683710f53b555b321c4f0a97e3cdd9047
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695228"
---
# <a name="button"></a>Button

![Button](Images/Button/MRTK_Button_Main.png)

Un pulsante offre all'utente un modo per attivare un'azione immediata. È uno dei componenti più fondamentali in realtà mista. MRTK fornisce vari tipi di prefabbricati di pulsanti.

## <a name="button-prefabs-in-mrtk"></a>Prefabbricati di pulsanti in MRTK

Esempi di prefabbricati dei pulsanti nella ``MRTK/SDK/Features/UX/Interactable/Prefabs`` cartella

### <a name="unity-ui-imagegraphic-based-buttons"></a>Icona dell'interfaccia utente di Unity/pulsanti basati su grafica

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Pulsanti basati su Collider

|  ![PressableButtonHoloLens2](Images/Button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 | ![PressableButtonHoloLens2Unplated](Images/Button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated | ![PressableButtonHoloLens2Circular](Images/Button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular |
|:--- | :--- | :--- |
| Pulsante di tipo Shell di HoloLens 2 con backplate che supporta vari commenti visivi, ad esempio la luce del bordo, la luce di prossimità e il pannello anteriore compresso | Pulsante di tipo Shell di HoloLens 2 senza backplat  | Pulsante di tipo Shell di HoloLens 2 con forma circolare  |
|  ![PressableButtonHoloLens2_32x96 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96** | ![](Images/Button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H** PressableButtonHoloLens2Bar3H | ![](Images/Button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V** PressableButtonHoloLens2Bar3V |
| Pulsante di tipo Shell HoloLens 2 Wide 32x96mm | Barra del pulsante orizzontale HoloLens 2 con backplate condiviso | Barra dei pulsanti verticale HoloLens 2 con backplate condiviso |
|  ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** | ![PressableButtonHoloLens2ToggleSwitch_32x32 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32** | ![PressableButtonHoloLens2ToggleRadio_32x32 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32** |
| Casella di controllo di tipo Shell di HoloLens 2 32x32mm | 32x32mm switch di tipo Shell di HoloLens 2 | 32x32mm radio in stile shell di HoloLens 2 |
|  ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96** | ![PressableButtonHoloLens2ToggleSwitch_32x96 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** | ![PressableButtonHoloLens2ToggleRadio_32x96 ](Images/Button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** |
| Casella di controllo di tipo Shell di HoloLens 2 32x96mm | 32x96mm switch di tipo Shell di HoloLens 2 | 32x96mm radio in stile shell di HoloLens 2 |
|  ![](Images/Button/MRTK_Button_Radial.png) **Radiale** radiale | ![Casella di controllo](Images/Button/MRTK_Button_Checkbox.png) **Casella di controllo** | ![](Images/Button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch** ToggleSwitch |
| Pulsante radiale | Casella di controllo  | Interruttore Attiva/Disattiva |
|  ![](Images/Button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1** ButtonHoloLens1 | ![](Images/Button/MRTK_Button_Round.png) **PressableRoundButton** PressableRoundButton | ![Pulsante ](Images/Button/MRTK_Button_Base.png)  pulsante |
| Pulsante dello stile della shell di HoloLens 1st Gen | Pulsante di push forma arrotondata | Pulsante di base |

Il `Button` (assets/MRTK/SDK/features/UX/Interactive/precases/Button. prefabbricate) si basa sul concetto di [interazione](README_Interactable.md) per fornire semplici controlli dell'interfaccia utente per i pulsanti o altri tipi di superfici interattive. Il pulsante Baseline supporta tutti i metodi di input disponibili, tra cui l'input manuale articolato per le interazioni near, nonché lo sguardo e il tocco aereo per le interazioni. Per attivare il pulsante, è anche possibile usare il comando Voice.

`PressableButtonHoloLens2` (Assets/MRTK/SDK/features/UX/interactable/precases/PressableButtonHoloLens2. prefabriced) è il pulsante di tipo Shell di HoloLens 2 che supporta lo spostamento preciso del pulsante per l'input di rilevamento a mano diretta. Combina `Interactable` script con `PressableButton` script.

Per HoloLens 2, è consigliabile usare i pulsanti con una contropiastra opaca. Non è consigliabile usare pulsanti trasparenti a causa di questi problemi di usabilità e stabilità:

- L'icona e il testo sono difficili da leggere con l'ambiente fisico
- È difficile capire quando viene attivato l'evento
- Gli ologrammi visualizzati tramite un piano trasparente possono essere instabili con la stabilizzazione LSR di HoloLens 2

![Pulsante](Images/Button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Come usare i pulsanti stampabili

### <a name="unity-ui-based-buttons"></a>Pulsanti basati sull'interfaccia utente di Unity

Creare un'area di disegno nella scena (GameObject-> interfaccia utente-> Canvas). Nel pannello Inspector per l'area di disegno:

* Fare clic su "Converti in MRTK Canvas"
* Fare clic su "Aggiungi NearInteractionTouchableUnityUI"
* Impostare la scala X, Y e Z del componente trasformazione Rect su 0,001

Quindi, trascinare `PressableButtonUnityUI` (assets/MRTK/SDK/features/UX/interactable/prefabrics/PressableButtonUnityUI. precaset), `PressableButtonUnityUICircular` (assets/MRTK/SDK/features/UX/interactable/precases/PressableButtonUnityUICircular. prefabbricate) o `PressableButtonHoloLens2UnityUI` (assets/MRTK/SDK/features/UX/interactable/precases/

### <a name="collider-based-buttons"></a>Pulsanti basati su Collider

È sufficiente trascinare `PressableButtonHoloLens2` (assets/MRTK/SDK/features/UX/interactable/precases/PressableButtonHoloLens2. precasel) o `PressableButtonHoloLens2Unplated` (assets/MRTK/SDK/features/UX/interactable/precases/PressableButtonHoloLens2Unplated. prefabbricate) nella scena. Questi prefabbricati di pulsanti sono già configurati in modo da ottenere feedback audio-visivi per i vari tipi di input, tra cui l'input e lo sguardo a mano articolata.

Per attivare azioni aggiuntive, è possibile usare gli eventi esposti nell'oggetto prefabbricato stesso nonché il componente [Interactabile](README_Interactable.md) . I pulsanti stampabili nella [scena HandInteractionExample](README_HandInteractionExamples.md) utilizzano l'evento *OnClick* di Interact per attivare una modifica nel colore di un cubo. Questo evento viene attivato per diversi tipi di metodi di input come lo sguardo, il tocco aereo, il raggio di mano, nonché le pressioni dei pulsanti fisici tramite lo script del pulsante stampabile.

<img src="Images/Button/MRTK_Button_HowToUse_Interactable.png" width="450">

È possibile configurare quando il pulsante stampabile genera l'evento *OnClick* tramite l'oggetto `PhysicalPressEventRouter` sul pulsante. Ad esempio, è possibile impostare *OnClick* per attivare quando il pulsante viene premuto per la prima volta, anziché essere premuto e rilasciato, impostando *interactable su clic* per l' *evento alla pressione*.

<img src="Images/Button/MRTK_Button_HowTo_Events.png" width="450">

Per sfruttare le informazioni specifiche sullo stato di input della mano, è possibile usare i pulsanti stampabili eventi- *inizio tocco*, *tocco finale*, *pulsante premuto*, *pulsante rilasciato*. Tuttavia, questi eventi non vengono attivati in risposta agli input aria, a mano o a occhio. **Per supportare entrambe le interazioni in prossimità e in gran parte, è consigliabile usare l'evento *OnClick* interattivo.**

<img src="Images/Button/MRTK_Button_HowTo_PressableButton.png" width="450">

## <a name="interaction-states"></a>Stati di interazione

Nello stato inattivo, il pannello anteriore del pulsante non è visibile. Con l'avvicinarsi di un dito o un cursore dall'input di sguardi alla superficie, il bordo illuminante della piastra anteriore diventa visibile. È presente un'evidenziazione aggiuntiva della posizione della punta sulla superficie anteriore. Quando viene eseguito il push con un dito, il pannello anteriore si sposta con la punta. Quando la punta tocca la superficie del pannello anteriore, Mostra un effetto di impulso sottile per dare un feedback visivo del punto di tocco.

Nel pulsante di tipo Shell HoloLens 2 sono disponibili molti indicatori visivi e affordances per aumentare la confidenza dell'utente sull'interazione.

|  ![Luce vicina](Images/Button/ux_button_affordance_proximitylight.jpg) | ![Evidenziazione dello stato attivo](Images/Button/ux_button_affordance_focushighlight.jpg)  | ![Compressione Cage](Images/Button/ux_button_affordance_compression.jpg) | ![Pulse on trigger](Images/Button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Luce vicina | Evidenziazione dello stato attivo | Compressione Cage | Pulse on trigger |

L'effetto di impulso sottile viene attivato dal pulsante stampabile, che cerca *ProximityLight (s)* che risiedono nel puntatore che interagisce attualmente. Se vengono rilevati indicatori di prossimità, `ProximityLight.Pulse` viene chiamato il metodo, che aggiunge automaticamente un'animazione ai parametri dello shader per visualizzare un impulso.

## <a name="inspector-properties"></a>Proprietà di Inspector

![Pulsante](Images/Button/MRTK_Button_Structure.png)

**Box Collider** 
 `Box Collider` per il pannello anteriore del pulsante.

**Pulsante stampabile** Logica del movimento del pulsante con l'interazione con la pressione della mano.

**Router di eventi di stampa fisico** Questo script consente di inviare gli eventi dall'interazione con la pressione [all'interazione.](README_Interactable.md)

**Interactabile** 
 [Interactable](README_Interactable.md) gestisce vari tipi di Stati ed eventi di interazione. HoloLens lo sguardo, il movimento e l'input vocale e l'input del controller di movimento per auricolari immersivi vengono gestiti direttamente da questo script.

**Origine audio** Origine audio Unity per i clip di feedback audio.

*NearInteractionTouchable. cs* necessario per rendere qualsiasi oggetto ritoccabile con input della mano articolata.

## <a name="prefab-layout"></a>Layout prefabbricato

L'oggetto *ButtonContent* contiene il pannello anteriore, l'etichetta di testo e l'icona. Il *coperchio* risponde alla prossimità del dito dell'indice usando il *Button_Box* shader. Mostra bordi luminosi, luce di prossimità e effetto di impulso sul tocco. L'etichetta di testo viene creata con TextMesh Pro. La visibilità di *SeeItSayItLabel* è controllata dal tema di [Interact](README_Interactable.md).

![Pulsante](Images/Button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Come modificare l'icona e il testo

I pulsanti MRTK usano un `ButtonConfigHelper` componente per facilitare la modifica dell'icona, del testo e dell'etichetta del pulsante. Si noti che alcuni campi possono essere assenti se gli elementi non sono presenti sul pulsante selezionato.

![Pulsante](Images/Button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Creazione e modifica di set di icone

Un **set di icone** è un set condiviso di asset icona usati dal `ButtonConfigHelper` componente. Sono supportati tre *stili* di icona.

* Viene eseguito il rendering delle icone **Quad** su un quad usando `MeshRenderer` . Si tratta dello stile di icona predefinito.
* Il rendering delle icone **sprite** viene eseguito utilizzando un oggetto `SpriteRenderer` . Questa opzione è utile se si preferisce importare le icone come foglio sprite o se si vuole che le risorse dell'icona vengano condivise con i componenti dell'interfaccia utente di Unity. Per utilizzare questo stile, è necessario installare il pacchetto dell'editor sprite **(gestione pacchetti Windows->-> sprite 2D)**
* Il rendering delle icone **char** viene eseguito usando un `TextMeshPro` componente. Questa opzione è utile se si preferisce usare un tipo di carattere icona. Per usare il tipo di carattere dell'icona HoloLens, è necessario creare un `TextMeshPro` asset del tipo di carattere.

Per modificare lo stile usato dal pulsante, espandere l'elenco a discesa *Icone* in ButtonConfigHelper e selezionare nell'elenco a discesa *stile icona* .

È possibile creare una nuova icona del pulsante impostata con il menu asset: **create > Mixed Reality Toolkit > set di icone.** Per aggiungere icone quad e sprite, è sufficiente trascinarle nelle rispettive matrici. Per aggiungere le icone char, è innanzitutto necessario creare e assegnare un asset del tipo di carattere.

In MRTK 2,4 e versioni successive, è consigliabile spostare le trame delle icone personalizzate in un valore di icone.
Per aggiornare gli asset in tutti i pulsanti di un progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit-> Utilities-> finestra di migrazione > selezione del gestore della migrazione-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

Importazione del pacchetto Microsoft. MixedRealityToolkit. Unity. Tools necessario per aggiornare i pulsanti.

![Finestra di dialogo Aggiorna finestra](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se un'icona non viene trovata nel set di icone predefinito durante la migrazione, viene creato un set di icone personalizzato in MixedRealityToolkit. generated/CustomIconSets. Una finestra di dialogo indicherà che questa operazione è stata eseguita.

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Creazione di un asset del tipo di carattere dell'icona HoloLens

Importare prima di tutto il tipo di carattere dell'icona in Unity. Nei computer Windows è possibile trovare il tipo di carattere HoloLens predefinito in *Windows/Fonts/holomdl2. ttf.* Copiare e incollare il file nella cartella assets.

A questo punto, aprire il TextMeshPro font asset Creator tramite la **finestra > TextMeshPro > font asset Creator.** Ecco le impostazioni consigliate per la generazione di un Atlante dei tipi di carattere HoloLens. Per includere tutte le icone, incollare l'intervallo Unicode seguente nel campo *sequenza di caratteri* :

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Pulsante](Images/Button/MRTK_Font_Asset_Creation_1.png)

Una volta generato l'asset del tipo di carattere, salvarlo nel progetto e assegnarlo al campo del *tipo di carattere dell'icona char* del set di icone. Il menu a discesa *icone disponibili* verrà ora popolato. Per rendere un'icona disponibile per l'uso da un pulsante, fare clic su di essa. Verrà aggiunto all'elenco a discesa delle *icone selezionate* e ora verrà visualizzato in `ButtonConfigHelper.` è possibile assegnare facoltativamente all'icona un tag. Questo consente di impostare l'icona in fase di esecuzione.

![Button](Images/Button/MRTK_Font_Asset_Creation_3.png)

![Button](Images/Button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Per usare il set di icone selezionare un pulsante, espandere l'elenco a discesa icone in `ButtonConfigHelper` e assegnarlo al campo del *set* di icone.

![Pulsante](Images/Button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Come modificare le dimensioni di un pulsante

Le dimensioni del pulsante di tipo Shell di HoloLens 2 sono 32x32mm. Per personalizzare la dimensione, modificare la dimensione di questi oggetti nel prefabbricato Button:

1. **Coperchio**
2. **Quad** sotto il pannello
3. **Box Collider** nella radice

Quindi, fare clic sul pulsante **Correggi limiti** nello script NearInteractionTouchable che si trova nella radice del pulsante.

Aggiornare le dimensioni del pulsante coperchio ![](Images/Button/MRTK_Button_SizeCustomization1.png)

Aggiornare le dimensioni del pulsante Quad ![](Images/Button/MRTK_Button_SizeCustomization2.png)

Aggiornare le dimensioni del pulsante box Collider ![](Images/Button/MRTK_Button_SizeCustomization3.png)

Fare clic sul pulsante ' Correggi limiti ' ![](Images/Button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>Comando vocale (' See-it, Say-it ')

**Gestore di input vocale** Lo script [interagibile](README_Interactable.md) è già implementato in un pulsante stampabile `IMixedRealitySpeechHandler` . Qui è possibile impostare una parola chiave del comando Voice.

<img src="Images/Button/MRTK_Button_Speech1.png" width="450">

**Profilo di input vocale** Inoltre, è necessario registrare la parola chiave del comando Voice nel *profilo dei comandi di sintesi vocale* globale.

<img src="Images/Button/MRTK_Button_Speech2.png" width="450">

**Vedere l'etichetta it, Say-it** Il prefabbricato del pulsante stampabile dispone di un'etichetta segnaposto TextMesh Pro nell'oggetto *SeeItSayItLabel* . È possibile usare questa etichetta per comunicare all'utente la parola chiave del comando Voice per il pulsante.

<img src="Images/Button/MRTK_Button_Speech3.png" width="450">

## <a name="how-to-make-a-button-from-scratch"></a>Come creare un pulsante da zero

È possibile trovare gli esempi di questi pulsanti nella scena **PressableButtonExample** .

<img src="Images/Button/MRTK_PressableButtonCube0.png">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. creazione di un pulsante stampabile con Cube (solo near Interaction)

1. Creare un cubo Unity (GameObject > oggetto 3D > Cube)
2. Aggiungi `PressableButton.cs` script
3. Aggiungi `NearInteractionTouchable.cs` script

Nel `PressableButton` pannello Inspector di, assegnare l'oggetto Cube agli oggetti **visivi del pulsante di trasferimento**.

<img src="Images/Button/MRTK_PressableButtonCube3.png" width="450">

Quando si seleziona il cubo, nell'oggetto vengono visualizzati più livelli colorati. Vengono visualizzati i valori di distanza in **impostazioni di pressione**. Utilizzando gli handle, è possibile configurare quando iniziare a premere (spostare l'oggetto) e quando attivare l'evento.

<img src="Images/Button/MRTK_PressableButtonCube1.jpg" width="450">

<img src="Images/Button/MRTK_PressableButtonCube2.png" width="450">

Quando si preme il pulsante, si spostano e generano eventi appropriati esposti nello `PressableButton.cs` script, ad esempio TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().

<img src="Images/Button/MRTK_PressableButtonCubeRun1.jpg">

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. aggiunta di commenti visivi al pulsante di base del cubo

MRTK standard shader offre diverse funzionalità che semplificano l'aggiunta di commenti visivi. Creare un materiale e selezionare shader `Mixed Reality Toolkit/Standard` . In alternativa, è possibile usare o duplicare uno dei materiali esistenti in `/SDK/StandardAssets/Materials/` che usa MRTK standard shader.

<img src="Images/Button/MRTK_PressableButtonCube4.png" width="450">

Controllare `Hover Light` e `Proximity Light` in **Opzioni Fluent**. Questo consente il feedback visivo per le interazioni a breve (luce di prossimità) e puntatore (luce del passaggio del mouse).

<img src="Images/Button/MRTK_PressableButtonCube5.png" width="450">

<img src="Images/Button/MRTK_PressableButtonCubeRun2.jpg">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. aggiunta di commenti audio al pulsante Basic Cube

Poiché `PressableButton.cs` lo script espone eventi come TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), è possibile assegnare facilmente il feedback audio. È sufficiente aggiungere Unity `Audio Source` all'oggetto Cube e quindi assegnare clip audio selezionando audiosource. PlayOneShot (). È possibile usare MRTK_Select_Main e MRTK_Select_Secondary le clip audio nella `/SDK/StandardAssets/Audio/` cartella.

<img src="Images/Button/MRTK_PressableButtonCube7.png" width="450">

<img src="Images/Button/MRTK_PressableButtonCube6.png" width="450">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. aggiunta degli stati visivi e gestione degli eventi di interazione

[Interactable](README_Interactable.md) è uno script che semplifica la creazione di uno stato di visualizzazione per i vari tipi di interazioni di input. Gestisce anche gli eventi di interazione di gran lunga. Aggiungere `Interactable.cs` e trascinare l'oggetto cubo nel campo **destinazione** sotto **profili**. Quindi, creare un nuovo tema con un tipo **ScaleOffsetColorTheme**. In questo tema è possibile specificare il colore dell'oggetto per gli Stati di interazione specifici, ad esempio lo **stato attivo** e quello **premuto**. È anche possibile controllare scala e offset. Controllare l' **interpolazione** e impostare Duration per rendere la transizione visiva uniforme.

![Selezionare il tema del profilo](Images/Button/mrtk_button_profiles.gif)

Si noterà che l'oggetto risponde a entrambe le interazioni (raggio di mano o cursore a occhi) e vicino (mano).

<img src="Images/Button/MRTK_PressableButtonCubeRun3.jpg">
<img src="Images/Button/MRTK_PressableButtonCubeRun4.jpg">

## <a name="custom-button-examples"></a>Esempi di pulsanti personalizzati

Nella [scena HandInteractionExample](README_HandInteractionExamples.md)vedere gli esempi di pulsanti di piano e arrotondamento che usano entrambi `PressableButton` .

<img src="Images/Button/MRTK_Button_Custom1.png" width="450">

<img src="Images/Button/MRTK_Button_Custom2.png" width="450">

A ogni chiave del piano sono `PressableButton` assegnati un e uno `NearInteractionTouchable` script. È importante verificare che la direzione *in avanti locale* di `NearInteractionTouchable` sia corretta. È rappresentato da una freccia bianca nell'editor. Assicurarsi che la freccia si trovi fuori dalla faccia anteriore del pulsante:

<img src="Images/Button/MRTK_Button_Custom3.png" width="450">

## <a name="see-also"></a>Vedi anche

* [Con cui](README_Interactable.md)
* [Temi visivi](VisualThemes.md)
