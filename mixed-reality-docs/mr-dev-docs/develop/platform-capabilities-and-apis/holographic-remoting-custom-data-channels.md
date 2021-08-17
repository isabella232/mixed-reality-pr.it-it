---
title: Canali di dati di Holographic Remoting personalizzati
description: I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione Holographic Remoting già stabilita.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, canali dati
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184712"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>Canali di dati di Holographic Remoting personalizzati (C++)

>[!NOTE]
>Queste linee guida sono specifiche per Holographic Remoting in HoloLens 2.

Usare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota stabilita.

>[!IMPORTANT]
>I canali di dati personalizzati richiedono un'app remota personalizzata e un'app lettore personalizzata, in quanto consente la comunicazione tra le due app personalizzate.

>[!TIP]
>Un semplice esempio di ping-pong è disponibile negli esempi remoti e del lettore all'interno del repository github degli esempi di [Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) Rimuovere il commento ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` all'interno dei file SampleRemoteMain.h/SamplePlayerMain.h per abilitare il codice di esempio.


## <a name="create-a-custom-data-channel"></a>Creare un canale dati personalizzato


Per creare un canale dati personalizzato, sono necessari i campi seguenti:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Dopo aver stabilito una connessione, è possibile creare nuovi canali di dati dal lato remoto, dal lato lettore o da entrambi. Sia RemoteContext che PlayerContext forniscono un metodo ```CreateDataChannel()``` per la creazione di canali di dati. Il primo parametro è l'ID del canale, usato per identificare il canale dati nelle operazioni successive. Il secondo parametro è la priorità, che specifica la priorità con cui i dati di questo canale vengono trasferiti all'altro lato. Gli ID canale validi sul lato remoto sono compresi tra 0 e 63 e 64 fino a 127 per il lato lettore. Le priorità valide sono ```Low``` ```Medium``` , o ```High``` (su entrambi i lati).

Per avviare la creazione di un canale dati sul **lato** remoto:
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Per avviare la creazione di un canale dati sul **lato lettore:**
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Per creare un nuovo canale dati personalizzato, solo un lato (remoto o lettore) deve chiamare il ```CreateDataChannel``` metodo .

## <a name="handling-custom-data-channel-events"></a>Gestione degli eventi del canale dati personalizzato

Per stabilire un canale dati personalizzato, l'evento deve essere gestito (sia sul ```OnDataChannelCreated``` lettore che sul lato remoto). Viene attivato quando un canale dati utente è stato creato da entrambi i lati e fornisce un oggetto , che può essere usato per inviare e ricevere ```IDataChannel``` dati su questo canale.

Per registrare un listener ```OnDataChannelCreated``` sull'evento:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Per ricevere una notifica quando vengono ricevuti i dati, registrarsi ```OnDataReceived``` all'evento ```IDataChannel``` sull'oggetto fornito dal ```OnDataChannelCreated``` gestore. Registrarsi ```OnClosed``` all'evento per ricevere una notifica quando il canale dati è stato chiuso.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Invio di dati

Per inviare dati tramite un canale dati personalizzato, usare il ```IDataChannel::SendData()``` metodo . Il primo parametro è ```winrt::array_view<const uint8_t>``` un oggetto ai dati da inviare. Il secondo parametro specifica dove inviare di nuovo i dati, fino a quando l'altro lato non conferma la ricezione. 

>[!IMPORTANT]
>In caso di condizioni di rete non ottimali, lo stesso pacchetto di dati potrebbe arrivare più di una volta. Il codice ricevente deve essere in grado di gestire questa situazione.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Chiusura di un canale dati personalizzato

Per chiudere un canale dati personalizzato, usare il ```IDataChannel::Close()``` metodo . Entrambi i lati riceveranno una notifica ```OnClosed``` dall'evento dopo la chiusura del canale dati personalizzato.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Vedere anche
* [Panoramica di Holographic Remoting](holographic-remoting-overview.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con le API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)