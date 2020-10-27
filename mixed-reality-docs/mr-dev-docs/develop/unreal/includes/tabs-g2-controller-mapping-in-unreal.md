---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638728"
---
# <a name="all-platforms"></a>[<span data-ttu-id="a8a11-101">Tutte le piattaforme</span><span class="sxs-lookup"><span data-stu-id="a8a11-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="a8a11-102">Gli stessi mapping di azione e asse nelle impostazioni del progetto di input del gioco possono essere usati da C++.</span><span class="sxs-lookup"><span data-stu-id="a8a11-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="a8a11-103">Crea una nuova classe C++ con file/nuova classe C++...</span><span class="sxs-lookup"><span data-stu-id="a8a11-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Creazione di una nuova classe C++](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="a8a11-105">Creare un Pawn</span><span class="sxs-lookup"><span data-stu-id="a8a11-105">Create a pawn</span></span>

![Creazione di un Pawn](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="a8a11-107">Nella soluzione Visual Studio del progetto individuare la nuova classe Pawn e configurarla per l'input.</span><span class="sxs-lookup"><span data-stu-id="a8a11-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="a8a11-108">Per prima cosa, nel costruttore impostare AutoPossessPlayer sul primo giocatore per indirizzare l'input al pedone.</span><span class="sxs-lookup"><span data-stu-id="a8a11-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="a8a11-109">In SetupPlayerInputComponent associare quindi gli eventi Action e AXIS ai nomi di azione dalle impostazioni di input del progetto.</span><span class="sxs-lookup"><span data-stu-id="a8a11-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="a8a11-110">Aggiungere le funzioni di callback alla classe:</span><span class="sxs-lookup"><span data-stu-id="a8a11-110">Add the callback functions to the class:</span></span>

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* <span data-ttu-id="a8a11-111">Aggiornare l'intestazione del Pawn con le definizioni della funzione di callback:</span><span class="sxs-lookup"><span data-stu-id="a8a11-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="a8a11-112">Compilare da Visual Studio per avviare l'editor con il nuovo pedone.</span><span class="sxs-lookup"><span data-stu-id="a8a11-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="a8a11-113">Trascinare il pedone dal browser contenuto al gioco e il pedone eseguirà i callback quando viene premuto l'input.</span><span class="sxs-lookup"><span data-stu-id="a8a11-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="a8a11-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="a8a11-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="a8a11-115">Quando si usano gli eventi dell'asse levetta, il nome dell'evento dell'asse deve terminare con "_X" o "_Y" corrispondenti alla chiave usata.</span><span class="sxs-lookup"><span data-stu-id="a8a11-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Uso degli eventi levetta](../images/reverb-g2-img-09.png)

<span data-ttu-id="a8a11-117">Infine, registrare le azioni nel gioco con SteamVR usando il manifesto dell' **azione di rigenerazione** e **rigenerare i pulsanti associazioni controller** in Impostazioni progetto > input di Steam VR.</span><span class="sxs-lookup"><span data-stu-id="a8a11-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Registrazione delle azioni nelle impostazioni del progetto](../images/reverb-g2-img-10.png)

