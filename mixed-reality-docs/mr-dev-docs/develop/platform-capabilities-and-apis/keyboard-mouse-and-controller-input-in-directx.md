---
title: Input da tastiera, mouse e controller in DirectX
description: Viene illustrato come creare un'app per Windows Mixed Reality che usa tastiera, mouse e controller di gioco.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, tastiera, mouse, controller di gioco, controller xbox, HoloLens, desktop, procedura dettagliata, codice di esempio
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244174"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Input da tastiera, mouse e controller in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](../native/openxr-getting-started.md)**.

Tastiere, mouse e controller di gioco possono essere tutte forme di input utili per Windows Mixed Reality dispositivi. Bluetooth tastiere e mouse sono entrambi supportati in HoloLens, per l'uso con il debug dell'app o come forma alternativa di input. Windows Mixed Reality supporta anche visori immersivi collegati a PC, dove topi, tastiere e controller di gioco sono stati la norma.

Per usare l'input da tastiera HoloLens, associare una tastiera Bluetooth al dispositivo o usare l'input virtuale tramite il Windows Portale di dispositivi. Per usare l'input da tastiera mentre si indossa un visore immersivo Windows Mixed Reality, assegnare lo stato attivo per l'input alla realtà mista inserendo il dispositivo o usando la combinazione di tasti Windows Tasto + Y. Tenere presente che le app destinate HoloLens devono fornire funzionalità senza questi dispositivi collegati.
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'uso di C++/CX anziché C++17 conforme a C++/WinRT come usato nel modello di progetto [olografico C++.](../native/creating-a-holographic-directx-project.md)  I concetti sono equivalenti per un progetto C++/WinRT, anche se è necessario tradurre il codice.

## <a name="subscribe-for-corewindow-input-events"></a>Sottoscrivere eventi di input CoreWindow

### <a name="keyboard-input"></a>Input da tastiera

Nel modello Windows'app Holographic è incluso un gestore eventi per l'input da tastiera come qualsiasi altra app UWP. L'app usa i dati di input della tastiera nello stesso modo in Windows Mixed Reality.

Da AppView.cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Input da tastiera virtuale
Per i visori desktop immersivi, è possibile supportare le tastiere virtuali di cui Windows sulla visualizzazione immersiva implementando **CoreTextEditContext.** In questo modo Windows lo stato delle caselle di testo di cui è stato eseguito il rendering dell'app, in modo che la tastiera virtuale possa contribuire correttamente al testo.

Per altre informazioni sull'implementazione del supporto CoreTextEditContext, vedere [l'esempio CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Mouse Input

È anche possibile usare l'input del mouse, anche in questo caso tramite i gestori eventi di input UWP CoreWindow. Ecco come modificare il modello Windows'app Holographic per supportare i clic del mouse nello stesso modo dei movimenti premuti. Dopo aver apportato questa modifica, un clic del mouse mentre si indossa un dispositivo vr immersivo riposiziona il cubo.

> [!NOTE]
> Le app UWP possono anche ottenere dati XY non elaborati per il mouse usando l'API [MouseDevice.](/uwp/api/Windows.Devices.Input.MouseDevice)

Iniziare dichiarando un nuovo gestore OnPointerPressed in AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

In AppView.cpp aggiungere questo codice a SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Inserire quindi questa definizione per OnPointerPressed nella parte inferiore del file:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

Il gestore eventi appena aggiunto è un pass-through alla classe main del modello. Modificare la classe principale per supportare questo pass-through. Aggiungere questa dichiarazione di metodo pubblico al file di intestazione:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sarà necessaria anche questa variabile membro privata:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Infine, si aggiornerà la classe principale con una nuova logica per supportare i clic del mouse. Per iniziare, aggiungere questo gestore eventi. Assicurarsi di aggiornare il nome della classe:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

A questo punto, nel metodo Update sostituire la logica esistente per ottenere una posizione di puntatore con questa:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Ricompilare e ridistribuire. Si noti che il clic del mouse riposiziona ora il cubo nel visore immersivo o HoloLens con il mouse Bluetooth collegato.

### <a name="game-controller-support"></a>Supporto del controller di gioco

I controller di gioco possono essere un modo divertente e pratico per consentire all'utente di controllare un'esperienza Windows Mixed Reality immersiva.

 Aggiungere le dichiarazioni di membro private seguenti alla classe di intestazione per il file principale:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Inizializzare gli eventi del gamepad e tutti i gamepad attualmente associati nel costruttore per la classe principale:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Aggiungere questi gestori eventi alla classe principale. Assicurarsi di aggiornare il nome della classe:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Infine, aggiornare la logica di input per riconoscere le modifiche nello stato del controller. In questo caso viene utilizzata la stessa m_pointerPressed illustrata nella sezione precedente per aggiungere eventi del mouse. Aggiungere questo elemento al metodo Update, subito prima del punto in cui viene verificata la presenza di SpatialPointerPose:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Non dimenticare di annullare la registrazione degli eventi durante la pulizia della classe principale:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Ricompilare e ridistribuire. È ora possibile collegare o associare un controller di gioco e usarlo per riposizionare il cubo di rotazione.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Linee guida importanti per l'input da tastiera e mouse

Esistono alcune differenze principali nel modo in cui questo codice può essere usato in Microsoft HoloLens, ovvero un dispositivo basato principalmente sull'input naturale dell'utente, rispetto a ciò che è disponibile in un PC abilitato per Windows Mixed Reality.
* Non è possibile fare affidamento sull'input della tastiera o del mouse per essere presenti. Tutte le funzionalità dell'app devono funzionare con lo sguardo, i movimenti e l'input vocale.
* Quando una Bluetooth tastiera è collegata, può essere utile abilitare l'input da tastiera per qualsiasi testo che l'app potrebbe richiedere. Questo può essere un ottimo integratore per la dettatura, ad esempio.
* Quando si tratta di progettare l'app, non affidarsi (ad esempio) ai controlli WASD e di aspetto del mouse per il gioco. HoloLens è progettato per consentire all'utente di spostarsi nella stanza. In questo caso, l'utente controlla direttamente la fotocamera. Un'interfaccia per guidare la fotocamera intorno alla stanza con controlli di spostamento/aspetto non offrirà la stessa esperienza.
* L'input da tastiera è un modo eccellente per controllare il debug dell'app o del motore di gioco, soprattutto perché l'utente non deve usare la tastiera. Il cablaggio è identico a quello usato con le API di evento CoreWindow. In questo scenario è possibile scegliere di implementare un modo per configurare l'app per indirizzare gli eventi della tastiera a una modalità "solo input di debug" durante le sessioni di debug.
* Bluetooth anche i controller di rete funzionano.

## <a name="see-also"></a>Vedi anche
* [Accessori hardware](../../discover/hardware-accessories.md)