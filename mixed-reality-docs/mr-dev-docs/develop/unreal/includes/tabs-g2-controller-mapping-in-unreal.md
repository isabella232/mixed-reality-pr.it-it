---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204271"
---
# <a name="all-platforms"></a>[Tutte le piattaforme](#tab/all)

Le stesse azioni e gli stessi mapping degli assi nelle impostazioni del progetto di input del gioco possono essere usati da C++.

1. Creare una nuova classe C++ con File/Nuova classe C++...

![Creazione di una nuova classe C++](../images/reverb-g2-img-11.png)

2. Creare un pedone

![Creazione di un pedone](../images/reverb-g2-img-12.png)

3. Nella soluzione del progetto Visual Studio trovare la nuova classe Pawn e configurarla per l'input.
* Innanzitutto, nel costruttore impostare AutoPossessPlayer sul primo lettore per indirizzare l'input al pedone.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* In SetupPlayerInputComponent associare quindi azioni ed eventi asse ai nomi delle azioni dalle impostazioni di input del progetto.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Aggiungere le funzioni di callback alla classe :

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

* Aggiornare l'intestazione del pedone con le definizioni di funzione di callback:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Compilare da Visual Studio per avviare l'editor con il nuovo pedone. Trascinare e rilasciare il pedone dal browser del contenuto nel gioco e il pedone eseguirà ora i callback quando viene premuto l'input.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Quando si usano gli eventi dell'asse delle leve, il nome dell'evento dell'asse deve terminare con "_X" o "_Y" corrispondente alla chiave usata.

![Uso degli eventi di identificazione personale](../images/reverb-g2-img-09.png)

Registrare infine le azioni nel gioco con  SteamVR usando i pulsanti Rigenera manifesto azione e Rigenera associazioni **controller** in Project Impostazioni >'input VR di Steam.

![Registrazione di azioni nelle impostazioni del progetto](../images/reverb-g2-img-10.png)

