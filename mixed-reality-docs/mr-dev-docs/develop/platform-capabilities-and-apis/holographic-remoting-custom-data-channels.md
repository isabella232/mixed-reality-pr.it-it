---
title: Canali di dati di Holographic Remoting personalizzati
description: I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota olografica già stabilita.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, canali di dati
ms.openlocfilehash: 6fd2bbd8ce2dedc3b13674576a23a0484ebe1419
ms.sourcegitcommit: 99ae85159b7cf75f919021771ebb8299868beea9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2020
ms.locfileid: "97102906"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="5b7fc-104">Canali di dati di Holographic Remoting personalizzati</span><span class="sxs-lookup"><span data-stu-id="5b7fc-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="5b7fc-105">Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="5b7fc-106">Utilizzare canali di dati personalizzati per inviare dati personalizzati tramite una connessione remota consolidata.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5b7fc-107">I canali di dati personalizzati richiedono un'app remota personalizzata e un'app per lettore personalizzata, perché consente la comunicazione tra le due app personalizzate.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="5b7fc-108">È possibile trovare un semplice esempio di ping-pong negli esempi remote e Player all'interno del [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="5b7fc-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="5b7fc-109">Rimuovere il commento ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` dai file SampleRemoteMain. h/SamplePlayerMain. h per abilitare il codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="5b7fc-110">Creare un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="5b7fc-110">Create a custom data channel</span></span>


<span data-ttu-id="5b7fc-111">Per creare un canale di dati personalizzato, sono necessari i campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="5b7fc-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="5b7fc-112">Una volta stabilita una connessione, è possibile creare nuovi canali dati dal lato remoto, dal lato Player o da entrambi.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-112">After a connection is successfully established, you can create new data channels from either the remote side, the player side, or both.</span></span> <span data-ttu-id="5b7fc-113">Sia RemoteContext che PlayerContext forniscono un ```CreateDataChannel()``` metodo per la creazione di canali di dati.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method for creating data channels.</span></span> <span data-ttu-id="5b7fc-114">Il primo parametro è l'ID del canale, che viene usato per identificare il canale dati nelle operazioni successive.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-114">The first parameter is the channel ID, which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="5b7fc-115">Il secondo parametro è la priorità, che specifica la priorità con cui i dati di questo canale vengono trasferiti sull'altro lato.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-115">The second parameter is the priority, which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="5b7fc-116">Gli ID di canale validi sul lato remoto sono compresi tra 0 e 63 e 64 fino a e compreso 127 per il lato Player.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-116">Valid channel IDs on the remote side are from 0 up to and including 63, and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="5b7fc-117">Le priorità valide sono ```Low``` , ```Medium``` o ```High``` (su entrambi i lati).</span><span class="sxs-lookup"><span data-stu-id="5b7fc-117">Valid priorities are ```Low```, ```Medium```, or ```High``` (on both sides).</span></span>

<span data-ttu-id="5b7fc-118">Per avviare la creazione di un canale dati sul lato **remoto** :</span><span class="sxs-lookup"><span data-stu-id="5b7fc-118">To start the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="5b7fc-119">Per avviare la creazione di un canale dati sul lato **Player** :</span><span class="sxs-lookup"><span data-stu-id="5b7fc-119">To start the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="5b7fc-120">Per creare un nuovo canale di dati personalizzato, è necessario che il metodo venga chiamato da un solo lato (remoto o lettore) ```CreateDataChannel``` .</span><span class="sxs-lookup"><span data-stu-id="5b7fc-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="5b7fc-121">Gestione degli eventi del canale dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="5b7fc-121">Handling custom data channel events</span></span>

<span data-ttu-id="5b7fc-122">Per stabilire un canale di dati personalizzato, ```OnDataChannelCreated``` è necessario gestire l'evento (sia sul lettore che sul lato remoto).</span><span class="sxs-lookup"><span data-stu-id="5b7fc-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="5b7fc-123">Viene attivato quando un canale dati utente viene creato da entrambi i lati e fornisce un ```IDataChannel``` oggetto che può essere utilizzato per inviare e ricevere dati su questo canale.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="5b7fc-124">Per registrare un listener per l' ```OnDataChannelCreated``` evento:</span><span class="sxs-lookup"><span data-stu-id="5b7fc-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="5b7fc-125">Per ricevere una notifica quando vengono ricevuti i dati, effettuare la registrazione all' ```OnDataReceived``` evento nell' ```IDataChannel``` oggetto fornito dal ```OnDataChannelCreated``` gestore.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="5b7fc-126">Eseguire la registrazione all' ```OnClosed``` evento per ricevere una notifica quando il canale dati è stato chiuso.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="5b7fc-127">Invio di dati</span><span class="sxs-lookup"><span data-stu-id="5b7fc-127">Sending data</span></span>

<span data-ttu-id="5b7fc-128">Per inviare dati su un canale di dati personalizzato, utilizzare il ```IDataChannel::SendData()``` metodo.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="5b7fc-129">Il primo parametro è un oggetto ```winrt::array_view<const uint8_t>``` per i dati che devono essere inviati.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="5b7fc-130">Il secondo parametro specifica la posizione in cui i dati devono essere inviati di nuovo, fino a quando l'altro lato non riconosce la ricezione.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="5b7fc-131">In caso di condizioni di rete non valide, lo stesso pacchetto di dati potrebbe arrivare più di una volta.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="5b7fc-132">Il codice ricevente deve essere in grado di gestire questa situazione.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="5b7fc-133">Chiusura di un canale di dati personalizzato</span><span class="sxs-lookup"><span data-stu-id="5b7fc-133">Closing a custom data channel</span></span>

<span data-ttu-id="5b7fc-134">Per chiudere un canale di dati personalizzato, utilizzare il ```IDataChannel::Close()``` metodo.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="5b7fc-135">Entrambi i lati verranno informati dall' ```OnClosed``` evento dopo la chiusura del canale dati personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5b7fc-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="5b7fc-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5b7fc-136">See Also</span></span>
* [<span data-ttu-id="5b7fc-137">Scrittura di un'app remota olografica remota usando le API di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5b7fc-137">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="5b7fc-138">Scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR</span><span class="sxs-lookup"><span data-stu-id="5b7fc-138">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="5b7fc-139">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="5b7fc-139">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5b7fc-140">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="5b7fc-140">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="5b7fc-141">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="5b7fc-141">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5b7fc-142">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="5b7fc-142">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
