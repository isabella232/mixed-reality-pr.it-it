---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638728"
---
# <a name="all-platforms"></a>[Tutte le piattaforme](#tab/all)

Gli stessi mapping di azione e asse nelle impostazioni del progetto di input del gioco possono essere usati da C++.

1. Crea una nuova classe C++ con file/nuova classe C++...

![Creazione di una nuova classe C++](../images/reverb-g2-img-11.png)

2. Creare un Pawn

![Creazione di un Pawn](../images/reverb-g2-img-12.png)

3. Nella soluzione Visual Studio del progetto individuare la nuova classe Pawn e configurarla per l'input.
* Per prima cosa, nel costruttore impostare AutoPossessPlayer sul primo giocatore per indirizzare l'input al pedone.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* In SetupPlayerInputComponent associare quindi gli eventi Action e AXIS ai nomi di azione dalle impostazioni di input del progetto.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Aggiungere le funzioni di callback alla classe:

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

* Aggiornare l'intestazione del Pawn con le definizioni della funzione di callback:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Compilare da Visual Studio per avviare l'editor con il nuovo pedone. Trascinare il pedone dal browser contenuto al gioco e il pedone eseguirà i callback quando viene premuto l'input.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Quando si usano gli eventi dell'asse levetta, il nome dell'evento dell'asse deve terminare con "_X" o "_Y" corrispondenti alla chiave usata.

![Uso degli eventi levetta](../images/reverb-g2-img-09.png)

Infine, registrare le azioni nel gioco con SteamVR usando il manifesto dell' **azione di rigenerazione** e **rigenerare i pulsanti associazioni controller** in Impostazioni progetto > input di Steam VR.

![Registrazione delle azioni nelle impostazioni del progetto](../images/reverb-g2-img-10.png)

