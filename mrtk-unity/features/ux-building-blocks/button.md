---
title: Pulsanti
description: Panoramica sui pulsanti in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, pulsanti MRTK
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281850"
---
# <a name="buttons"></a>Pulsanti

![Pulsante principale](../images/button/MRTK_Button_Main.png)

Un pulsante offre all'utente un modo per attivare un'azione immediata. È uno dei componenti di base della realtà mista. MRTK offre vari tipi di prefab per i pulsanti.

## <a name="button-prefabs-in-mrtk"></a>Prefab dei pulsanti in MRTK

Esempi dei prefab dei pulsanti nella ``MRTK/SDK/Features/UX/Interactable/Prefabs`` cartella

### <a name="unity-ui-imagegraphic-based-buttons"></a>Pulsanti basati su immagine/grafica dell'interfaccia utente di Unity

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Pulsanti basati su collisori

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    HoloLens 2 pulsante in stile shell di HoloLens 2 con backplate che supporta vari commenti visivi, ad esempio luce del bordo, luce di prossimità e pappe anteriore compresso
    :::column-end:::
    :::column:::
    HoloLens 2 di stile della shell senza backplate
    :::column-end:::
    :::column:::
    HoloLens 2 in stile shell di HoloLens 2 con forma circolare
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Pulsante HoloLens 2 stile shell di Wide HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    Barra dei HoloLens 2 orizzontale con backplate condiviso
    :::column-end:::
    :::column:::
    Barra HoloLens 2 pulsante con backplate condiviso
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    HoloLens 2 della casella di controllo di tipo shell 32x32mm
    :::column-end:::
    :::column:::
    HoloLens 2 di tipo shell di HoloLens 2 32x32mm 
    :::column-end:::
    :::column:::
    HoloLens 2 radio in stile shell di HoloLens 2 32x32mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 2 di controllo di tipo shell di HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 di shell di HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 radio in stile shell di HoloLens 2 32x96mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Radiale ](../images/button/MRTK_Button_Radial.png) **radiale**
    :::column-end:::
    :::column:::
    ![Casella di controllo ](../images/button/MRTK_Button_Checkbox.png) **della casella di controllo**
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Pulsante radiale 
    :::column-end:::
    :::column:::
    Casella di controllo 
    :::column-end:::
    :::column:::
    Interruttore Attiva/Disattiva
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![Pulsante di base ](../images/button/MRTK_Button_Base.png) **del pulsante**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens pulsante di stile della shell di prima generazione
    :::column-end:::
    :::column:::
    Pulsante di selezione forma rotonda
    :::column-end:::
    :::column:::
    Pulsante Di base
    :::column-end:::
:::row-end:::

`Button`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) si basa sul concetto [interactable](interactable.md) per fornire controlli dell'interfaccia utente semplici per i pulsanti o altri tipi di superfici interattive. Il pulsante baseline supporta tutti i metodi di input disponibili, incluso l'input della mano articolato per le interazioni da vicino, nonché lo sguardo fisso e il tocco nell'aria per le interazioni da lontano. È anche possibile usare il comando vocale per attivare il pulsante.

`PressableButtonHoloLens2`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) è un pulsante di stile della shell di HoloLens 2 che supporta il movimento preciso del pulsante per l'input di tracciamento diretto della mano. Combina script `Interactable` con `PressableButton` script.

Per HoloLens 2, è consigliabile usare pulsanti con un backplate opaco. I pulsanti trasparenti non sono consigliati a causa di questi problemi di usabilità e stabilità:

* L'icona e il testo sono difficili da leggere con l'ambiente fisico
* È difficile comprendere quando viene attivato l'evento
* Ologrammi visualizzati tramite un piano trasparente possono essere instabili con la HoloLens 2 LSR di profondità del sistema

![Pulsante con i toni](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Come usare i pulsanti a pressione

### <a name="unity-ui-based-buttons"></a>Pulsanti basati sull'interfaccia utente di Unity

Creare un'area di disegno nella scena (GameObject -> UI -> Canvas). Nel pannello Inspector (Controllo) per Canvas:

* Fare clic su "Convert to MRTK Canvas" (Converti in canvas MRTK)
* Fare clic su "Add NearInteractionTouchableUnityUI" (Aggiungi NearInteractionTouchableUnityUI)
* Impostare la scala X, Y e Z del componente Rect Transform su 0,001

Trascinare `PressableButtonUnityUI` quindi (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab) o `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) nell'area di disegno.

### <a name="collider-based-buttons"></a>Pulsanti basati su collisori

È sufficiente trascinare `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) o `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) nella scena. Questi prefab dei pulsanti sono già configurati per fornire feedback audio-visivo per i vari tipi di input, tra cui input con mano articolata e sguardo fisso.

Gli eventi esposti nel prefab stesso e nel componente [Interactable](interactable.md) possono essere usati per attivare azioni aggiuntive. I pulsanti a pressione nella scena [HandInteractionExample](../example-scenes/hand-interaction-examples.md) usano l'evento *OnClick* di Interactable per attivare una modifica nel colore di un cubo. Questo evento viene attivato per diversi tipi di metodi di input, ad esempio sguardo fisso, tocco d'aria, raggio della mano e pressione di pulsanti fisici tramite lo script del pulsante a pressione.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

È possibile configurare quando il pulsante a pressione genera *l'evento OnClick* tramite `PhysicalPressEventRouter` sul pulsante. Ad esempio, è possibile impostare *OnClick* in modo che venga generato quando il pulsante viene premuto per la prima volta, anziché essere premuto e rilasciato, impostando *Interactable On Click* su *Event On Press*.

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Per sfruttare informazioni specifiche sullo stato di input della mano articolata, è possibile usare gli eventi dei pulsanti a pressione: *Inizio* tocco, *Fine* tocco, *Pulsante* premuto, *Pulsante rilasciato.* Questi eventi, tuttavia, non verranno generati in risposta al tocco, al raggio della mano o agli input oculare. **Per supportare le interazioni da vicino e da lontano, è consigliabile usare l'evento *OnClick di Interactable.***

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Stati di interazione

Nello stato di inattività, il pannello anteriore del pulsante non è visibile. Quando un dito si avvicina o un cursore dall'input dello sguardo fisso si rivolge alla superficie, il bordo incandescente della superficie diventa visibile. È disponibile un'evidenziazione aggiuntiva della posizione della punta del dito sulla superficie della piana anteriore. Quando viene premuto con un dito, il piano anteriore si sposta con la punta del dito. Quando la punta del dito tocca la superficie della lastra anteriore, mostra un effetto di pulsazione sottile per fornire un feedback visivo del punto di tocco.

In HoloLens 2 di tipo shell, sono disponibili molti suggerimenti visivi e suggerimenti per aumentare la fiducia dell'utente nell'interazione.

|  ![Luce di prossimità](../images/button/ux_button_affordance_proximitylight.jpg) | ![Evidenziazione dello stato attivo](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compressione della compressa](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on trigger](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Luce di prossimità | Evidenziazione dello stato attivo | Compressione della compressa | Pulse on trigger |

L'effetto di pulsazione sottile viene attivato dal pulsante a pressione, che cerca *proximityLight(s)* che si trovano sul puntatore che interagisce attualmente. Se vengono trovate luci di prossimità, viene chiamato il metodo , che aggiunge automaticamente un'animazione ai parametri `ProximityLight.Pulse` dello shader per visualizzare un'animazione.

## <a name="inspector-properties"></a>Proprietà del controllo

![Struttura dei pulsanti](../images/button/MRTK_Button_Structure.png)

**Box Collisore** 
 `Box Collider` per la barra anteriore del pulsante.

**Pulsante a pressione** Logica per lo spostamento del pulsante con l'interazione con la pressione della mano.

**Router eventi di stampa fisica** Questo script invia eventi dall'interazione con la pressione manuale a [Interactable.](interactable.md)

**Interagibile** 
 [L'interazione](interactable.md) gestisce vari tipi di stati ed eventi di interazione. HoloLens lo sguardo, il movimento e l'input vocale e l'input del controller di movimento vr immersivo vengono gestiti direttamente da questo script.

**Origine audio** Origine audio Unity per le clip di feedback audio.

*NearInteractionTouchable.cs* Obbligatorio per rendere toccabile qualsiasi oggetto con input manuale articolato.

## <a name="prefab-layout"></a>Layout prefab

*L'oggetto ButtonContent* contiene la barra anteriore, l'etichetta di testo e l'icona. *FrontPlate* risponde alla prossimità della punta dell'indice usando Button_Box *shader.* Mostra bordi incandescenti, luce di prossimità e un effetto di impulso sul tocco. L'etichetta di testo viene fatta con TextMesh Pro. *La visibilità di SeeItSayItLabel* è controllata dal tema di [Interactable.](interactable.md)

![Layout dei pulsanti](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Come modificare l'icona e il testo

I pulsanti MRTK usano un componente per facilitare la modifica dell'icona, del testo e `ButtonConfigHelper` dell'etichetta del pulsante. Si noti che alcuni campi potrebbero essere assenti se gli elementi non sono presenti nel pulsante selezionato.

![Helper di configurazione dei pulsanti](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Creazione e modifica di set di icone

Un **set di** icone è un set condiviso di asset icona usati dal `ButtonConfigHelper` componente. Sono supportati *tre stili* icona.

* **Il rendering** delle icone quadre viene eseguito su un quad usando `MeshRenderer` un oggetto . Questo è lo stile predefinito dell'icona.
* **Il rendering delle icone sprite** viene eseguito usando `SpriteRenderer` un oggetto . Ciò è utile se si preferisce importare le icone come foglio sprite o se si vuole che gli asset delle icone siano condivisi con i componenti dell'interfaccia utente di Unity. Per usare questo stile è necessario installare il pacchetto Sprite Editor **(Windows -> Gestione pacchetti -> 2D Sprite)**
* **Il rendering** delle icone char viene eseguito usando un `TextMeshPro` componente . Ciò è utile se si preferisce usare un tipo di carattere icona. Per usare il tipo HoloLens tipo di carattere dell'icona, è necessario creare un `TextMeshPro` asset del tipo di carattere.

Per modificare lo stile utilizzato  dal pulsante, espandere l'elenco a discesa Icone nell'elenco a discesa ButtonConfigHelper e selezionare dall'elenco a discesa *Stile* icona.

È possibile creare un nuovo set di icone pulsante con il menu asset: Creare > **realtà mista Toolkit > set di icone.** Per aggiungere icone quad e sprite, è sufficiente trascinarle nelle rispettive matrici. Per aggiungere icone Char, è prima necessario creare e assegnare un asset del tipo di carattere.

In MRTK 2.4 e oltre è consigliabile spostare trame di icone personalizzate in un oggetto IconSet.
Per aggiornare gli asset in tutti i pulsanti di un progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)

Importazione del pacchetto Microsoft.MixedRealityToolkit.Unity.Tools necessario per aggiornare i pulsanti.

![Finestra di dialogo Aggiorna](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se non viene trovata un'icona nel set di icone predefinito durante la migrazione, verrà creato un set di icone personalizzato in MixedRealityToolkit.Generated/CustomIconSets. Una finestra di dialogo indicherà che l'operazione è stata eseguita.

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Creazione di un asset HoloLens carattere dell'icona

Per prima cosa, importare il tipo di carattere dell'icona in Unity. Nei Windows è possibile trovare il tipo di carattere HoloLens predefinito in *Windows/Fonts/holomdl2.ttf.* Copiare e incollare questo file nella cartella Assets.

Aprire quindi TextMeshPro Font Asset Creator tramite **Window > TextMeshPro > Font Asset Creator.Next,** open the TextMeshPro Font Asset Creator via Window > TextMeshPro > Font Asset Creator. Ecco le impostazioni consigliate per la generazione di un at atlas HoloLens tipo di carattere. Per includere tutte le icone, incollare l'intervallo Unicode seguente nel *campo Sequenza di* caratteri:

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creazione del pulsante 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Dopo aver generato l'asset del tipo di carattere, salvarlo nel progetto e assegnarlo al campo Carattere icona del set *di* icone. *L'elenco a discesa* Icone disponibili verrà ora popolato. Per rendere disponibile un'icona per l'uso da parte di un pulsante, fare clic su di essa. Verrà aggiunto all'elenco a discesa *Icone* selezionate e verrà ora visualizzato in È possibile assegnare all'icona `ButtonConfigHelper.` un tag. In questo modo è possibile impostare l'icona in fase di esecuzione.

![Creazione del pulsante 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creazione del pulsante 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Per usare il set di icone, selezionare un pulsante, espandere l'elenco a discesa Icone in `ButtonConfigHelper` e assegnarlo al *campo Set di* icone.

![Set di icone dei pulsanti](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Come modificare le dimensioni di un pulsante

HoloLens 2 dimensioni del pulsante in stile shell è di 32 x 32 mm. Per personalizzare la dimensione, modificare le dimensioni di questi oggetti nel prefab del pulsante:

1. **FrontPlate**
2. **Quad** in BackPlate
3. **Box Collisore** nella radice

Fare quindi **clic sul pulsante Correggi** limiti nello script NearInteractionTouchable che si trova nella radice del pulsante.

Aggiornare le dimensioni della personalizzazione di FrontPlate ![ Button Size 1](../images/button/MRTK_Button_SizeCustomization1.png)

Aggiornare le dimensioni della personalizzazione di Quad ![ Button Size 2](../images/button/MRTK_Button_SizeCustomization2.png)

Aggiornare le dimensioni della personalizzazione di Box Collider ![ Button Size 3](../images/button/MRTK_Button_SizeCustomization3.png)

Fare clic su "Correggi limiti" ![ Personalizzazione dimensioni pulsante 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>Comando vocale ('see-it, say-it')

**Gestore input vocale** Lo script [Interactable](interactable.md) in Pressable Button implementa già `IMixedRealitySpeechHandler` . Qui è possibile impostare una parola chiave di comando vocale.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Profilo di input vocale** Inoltre, è necessario registrare la parola chiave del comando vocale nel profilo *comandi vocali globale.*

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**Etichetta See-it, Say-it** Il prefab del pulsante selezionabile ha un segnaposto TextMesh Pro'etichetta sotto *l'oggetto SeeItSayItLabel.* È possibile usare questa etichetta per comunicare all'utente la parola chiave del comando vocale per il pulsante.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Come creare un pulsante da zero

Gli esempi di questi pulsanti sono disponibili nella **scena PressableButtonExample.**

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. Creazione di un pulsante pressabile con cubo (solo vicino all'interazione)

1. Creare un cubo Unity (GameObject > 3D Object > Cube)
2. Aggiungere `PressableButton.cs` uno script
3. Aggiungere `NearInteractionTouchable.cs` uno script

Nel pannello `PressableButton` Inspector (Controllo) assegnare l'oggetto cubo agli **oggetti visivi pulsante di spostamento**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Quando si seleziona il cubo, sull'oggetto verranno visualizzati più livelli colorati. In questo modo vengono visualizzati i valori della distanza **in Press Impostazioni**. Usando gli handle, è possibile configurare quando iniziare a premere (spostare l'oggetto) e quando attivare l'evento.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Quando si preme il pulsante, questo si sposterà e genererà gli eventi adeguati esposti nello script, ad esempio `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Risoluzione dei problemi

Se il pulsante esegue una doppia pressione, assicurarsi che la proprietà Imponi push frontale sia attiva e che il piano **Start Push Distance** sia posizionato davanti al piano Near Interaction **Touchable.**  Il **piano Near Interaction Touchable** è indicato dal piano blu posizionato davanti all'origine della freccia bianca nella gif seguente:

![Componente script pulsante a pressione con la proprietà Imponi front push evidenziata](../images/button/MRTK_Button_Enforce_Push.png)

![Esempio animato di spostamento della distanza di push iniziale davanti al piano toccabile vicino all'interazione](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. Aggiunta di commenti e suggerimenti visivi al pulsante cubo di base

MrTK Standard Shader offre varie funzionalità che semplificano l'aggiunta di commenti e suggerimenti visivi. Creare un materiale e selezionare shader `Mixed Reality Toolkit/Standard` . Oppure è possibile usare o duplicare uno dei materiali esistenti in `/SDK/StandardAssets/Materials/` che usa MRTK Standard Shader.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Selezionare `Hover Light` e in Fluent `Proximity Light` **opzioni**. Ciò consente un feedback visivo sia per le interazioni vicino alla mano (luce di prossimità) che per le interazioni con puntatore lontano (Luce del passaggio del mouse).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. Aggiunta di commenti audio al pulsante cubo di base

Poiché lo script espone eventi come `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), è possibile assegnare facilmente commenti audio. È sufficiente aggiungere Unity `Audio Source` all'oggetto cubo e quindi assegnare clip audio selezionando AudioSource.PlayOneShot(). È possibile usare MRTK_Select_Main e MRTK_Select_Secondary clip audio nella `/SDK/StandardAssets/Audio/` cartella .

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Aggiunta di stati di visualizzazione e gestione di eventi di interazione lontano

[Interactable](interactable.md) è uno script che semplifica la creazione di uno stato di visualizzazione per i vari tipi di interazioni di input. Gestisce anche eventi di interazione lontano. Aggiungere `Interactable.cs` e trascinare l'oggetto cubo nel **campo Destinazione** in **Profili**. Creare quindi un nuovo tema con un tipo **ScaleOffsetColorTheme.** In questo tema è possibile specificare il colore dell'oggetto per gli stati di interazione specifici, ad esempio **Stato attivo** e **Premuto.** È anche possibile controllare Scale e Offset. Selezionare **Easing e** impostare la durata per rendere uniforme la transizione visiva.

![Selezionare il tema del profilo](../images/button/mrtk_button_profiles.gif)

L'oggetto risponde sia alle interazioni lontano (raggio della mano o sguardo fisso) che alle interazioni near(hand).

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Esempi di pulsanti personalizzati

Nella scena [HandInteractionExample](../example-scenes/hand-interaction-examples.md)vedere gli esempi di pulsanti piano e tondo che usano entrambi `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

A ogni chiave del piano sono `PressableButton` assegnati un e uno `NearInteractionTouchable` script. È importante verificare che la *direzione in* avanti locale di `NearInteractionTouchable` sia corretta. È rappresentato da una freccia bianca nell'editor. Assicurarsi che la freccia punti lontano dal lato anteriore del pulsante:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Vedi anche

* [Interagibile](interactable.md)
* [Temi visivi](visual-themes.md)
