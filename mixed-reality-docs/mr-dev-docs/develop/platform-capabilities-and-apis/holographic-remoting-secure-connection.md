---
title: Abilitazione della sicurezza della connessione per la comunicazione remota olografica
description: Questa pagina illustra come configurare la comunicazione remota olografica per l'uso di connessioni crittografate e autenticate tra Player e app Remote.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale, sicurezza, autenticazione, da server a client
ms.openlocfilehash: 0881238bfca199958802598a3e1829a9de0d8e5b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006481"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Abilitazione della sicurezza della connessione per la comunicazione remota olografica

>[!IMPORTANT]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Questa pagina offre una panoramica della sicurezza di rete per la comunicazione remota olografica. Sono disponibili informazioni su

* sicurezza nel contesto di comunicazione remota olografica e perché potrebbe essere necessaria
* misure consigliate basate su diversi casi di utilizzo
* implementazione della sicurezza nella soluzione di comunicazione remota olografica

## <a name="holographic-remoting-security"></a>Sicurezza della comunicazione remota olografica

La comunicazione remota olografica scambia informazioni in una rete. Se non sono presenti misure di sicurezza, gli avversari nella stessa rete potrebbero compromettere l'integrità della comunicazione o accedere a informazioni riservate.

Le app di esempio e il lettore di comunicazione remota olografica in Windows Store sono con sicurezza disabilitata. Questa operazione rende gli esempi più facili da comprendere. Consente inoltre di iniziare più rapidamente con lo sviluppo.

Per il test dei campi o la produzione, si consiglia vivamente di abilitare la sicurezza nella soluzione di comunicazione remota olografica.

Sicurezza nella comunicazione remota olografica, quando è configurata correttamente per il caso d'uso, offre le seguenti garanzie:

* **Autenticità:** sia il lettore che l'app remota possono essere sicuri che l'altro lato sia quello che attestano
* **Riservatezza:** nessuna parte di terze parti può leggere le informazioni scambiate tra il lettore e l'app remota
* **Integrità:** il lettore e il computer remoto possono rilevare eventuali modifiche in transito alla comunicazione

>[!IMPORTANT]
>Per poter usare le funzionalità di sicurezza, è necessario implementare sia un [lettore personalizzato](holographic-remoting-create-player.md) che un'app remota personalizzata usando le API [OpenXR](holographic-remoting-create-remote-openxr.md) o di [realtà mista di Windows](holographic-remoting-create-remote-wmr.md) .

>[!NOTE]
> A partire dalla versione [2.4.0](holographic-remoting-version-history.md#v2.4.0) è possibile creare app Remote con l' [API OpenXR](../native/openxr.md) . Una panoramica su come stabilire una connessione sicura in un ambiente OpenXR è disponibile di [seguito](#secure-connection-using-the-openxr-api).

## <a name="planning-the-security-implementation"></a>Pianificazione dell'implementazione della sicurezza

Quando si Abilita la sicurezza nella comunicazione remota olografica, la libreria .NET Remoting Abilita automaticamente la crittografia e i controlli di integrità per tutti i dati scambiati sulla rete.

Per garantire che l'autenticazione appropriata richieda comunque alcune operazioni aggiuntive. Ciò che è necessario fare dipende dal caso d'uso e la parte restante di questa sezione consiste nel comprendere i passaggi necessari.

>[!IMPORTANT]
> Questo articolo può fornire solo indicazioni generali. Se non si è certi, è consigliabile consultare un esperto di sicurezza che possa fornire indicazioni specifiche per il caso d'uso.

Prima di tutto la terminologia: quando si descrivono le connessioni di rete, verranno usati i termini _client_ e _Server_ . Il server è il lato in ascolto delle connessioni in ingresso su un indirizzo endpoint noto e il client è quello che si connette all'endpoint del server.

>[!NOTE]
> I ruoli client e server non sono collegati a se un'app funge da lettore o come remoto. Mentre gli esempi hanno il lettore nel ruolo del server, è facile invertire i ruoli se si adatta meglio al caso d'uso.

### <a name="planning-the-server-to-client-authentication"></a>Pianificazione dell'autenticazione da server a client

Il server utilizza certificati digitali per dimostrare la propria identità al client. Il client convalida il certificato del server durante la fase di handshake della connessione. Se il client non considera attendibile il server, la connessione verrà terminata a questo punto.

Il modo in cui il client convalida il certificato del server e i tipi di certificati del server possono essere utilizzati, a seconda del caso d'uso.

**Caso d'uso 1:** Il nome host del server non è fisso oppure il server non è risolto dal nome host.

In questo caso d'uso, non è pratico (o addirittura possibile) emettere un certificato per il nome host del server. Si consiglia di convalidare invece l'identificazione personale del certificato. Analogamente a un'impronta digitale umana, l'identificazione personale identifica in modo univoco un certificato.

È importante comunicare l'identificazione personale al client fuori banda. Ciò significa che non è possibile inviarlo tramite la stessa connessione di rete usata per la comunicazione remota. È invece possibile immetterlo manualmente nella configurazione del client o fare in modo che il client analizzi un codice a matrice.

**Caso d'uso 2:** Il server può essere raggiunto tramite un nome host stabile.

In questo caso di utilizzo, il server dispone di un nome host specifico e si è certi che questo nome non cambierà. È quindi possibile usare un certificato emesso per il nome host del server. La relazione di trust verrà stabilita in base al nome host e alla catena di certificati del certificato.

Se si sceglie questa opzione, il client deve verificare in anticipo il nome host del server e il certificato radice.

### <a name="planning-the-client-to-server-authentication"></a>Pianificazione dell'autenticazione da client a server

I client eseguono l'autenticazione nel server usando un token in formato libero. Ciò che questo token deve contenere dipenderà da un caso d'uso:

**Caso d'uso 1:** È sufficiente verificare l'identità dell'app client.

In questo caso di utilizzo, un segreto condiviso può essere sufficiente. Questo segreto deve essere sufficientemente complesso da non poter essere indovinato.

Un segreto condiviso valido è un GUID casuale, che viene immesso manualmente nella configurazione del server e del client. Per crearne uno è possibile, ad esempio, usare il `New-Guid` comando in PowerShell.

Verificare che il segreto condiviso non venga mai comunicato su canali non sicuri. La libreria .NET Remoting garantisce che il segreto condiviso venga sempre inviato crittografato e solo ai peer attendibili.

**Caso d'uso 2:** È anche necessario verificare l'identità dell'utente dell'app client.

Un segreto condiviso non sarà sufficiente per coprire il caso d'uso. È invece possibile usare i token creati da un provider di identità. Un flusso di lavoro di autenticazione che usa un provider di identità avrà un aspetto simile al seguente:

* Il client autorizza il provider di identità e richiede un token
* Il provider di identità genera un token e lo invia al client
* Il client invia questo token al server tramite la comunicazione remota olografica
* Il server convalida il token del client rispetto al provider di identità

Un esempio di provider di identità è la [piattaforma di identità Microsoft](https://docs.microsoft.com/azure/active-directory/develop/).

Come nel caso di utilizzo precedente, assicurarsi che questi token non vengano inviati tramite canali non protetti o altrimenti esposti.

## <a name="implementing-holographic-remoting-security"></a>Implementazione della sicurezza di comunicazione remota olografica

Tenere presente che è necessario implementare app Remote e Player personalizzate se si vuole abilitare la sicurezza della connessione. È possibile usare gli esempi forniti come punti di partenza per le proprie app.

Per abilitare la sicurezza, chiamare `ListenSecure()` anziché `Listen()` e `ConnectSecure()` anziché `Connect()` per stabilire la connessione remota.

Per queste chiamate è necessario fornire implementazioni di determinate interfacce per fornire e convalidare le informazioni relative alla sicurezza:

* Il server deve implementare un provider di certificati e un validator di autenticazione
* Il client deve implementare un provider di autenticazione e un validator del certificato.

Tutte le interfacce dispongono di una funzione che richiede di eseguire un'azione, che riceve un oggetto callback come parametro. Utilizzando questo oggetto, è possibile implementare facilmente la gestione asincrona della richiesta. Mantiene un riferimento a questo oggetto e chiama la funzione di completamento quando l'azione asincrona è completa. La funzione di completamento può essere chiamata da qualsiasi thread.

>[!TIP]
>L'implementazione di interfacce WinRT può essere eseguita facilmente con C++/WinRT. Il capitolo [API autore con C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) descrive in modo dettagliato questo aspetto.

>[!IMPORTANT]
>Il contenuto del `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` pacchetto NuGet contiene la documentazione dettagliata per l'API relativa alle connessioni protette.

### <a name="implementing-a-certificate-provider"></a>Implementazione di un provider di certificati

I provider di certificati forniscono all'applicazione server il certificato da utilizzare. L'implementazione di è costituita da due parti:

1) Oggetto Certificate, che implementa l' `ICertificate` interfaccia:

    * `GetCertificatePfx()` deve restituire il contenuto binario di un `PKCS#12` archivio certificati. Un `.pfx` file contiene `PKCS#12` dati, quindi il relativo contenuto può essere usato direttamente qui.
    * `GetSubjectName()` deve restituire il nome descrittivo che identifica il certificato da utilizzare. Se al certificato non è assegnato alcun nome descrittivo, questa funzione deve restituire il nome del soggetto del certificato.
    * `GetPfxPassword()` deve restituire la password necessaria per aprire l'archivio certificati o una stringa vuota se non è necessaria alcuna password.

2) Un provider di certificati che implementa l' `ICertificateProvider` interfaccia:
    * `GetCertificate()` deve costruire un oggetto certificato e restituirlo chiamando `CertificateReceived()` sull'oggetto callback.

### <a name="implementing-an-authentication-validator"></a>Implementazione di un validator di autenticazione

I validator di autenticazione ricevono il token di autenticazione inviato dal client e rispondono con il risultato della convalida.

Implementare l' `IAuthenticationReceiver` interfaccia come segue:

* `GetRealm()` deve restituire il nome dell'area di autenticazione (area di autenticazione HTTP utilizzata durante l'handshake della connessione remota).
* `ValidateToken()` deve convalidare il token di autenticazione client e chiamare `ValidationCompleted()` sull'oggetto callback con il risultato della convalida.

### <a name="implementing-an-authentication-provider"></a>Implementazione di un provider di autenticazione

I provider di autenticazione generano o recuperano il token di autenticazione da inviare al server.

Implementare l' `IAuthenticationProvider` interfaccia come segue:

* `GetToken()` deve generare o recuperare il token di autenticazione da inviare. Quando il token è pronto, chiamare il `TokenReceived()` metodo sull'oggetto callback.

### <a name="implementing-a-certificate-validator"></a>Implementazione di un validator del certificato

I validator dei certificati ricevono la catena di certificati inviata dal server e determinano se il server può essere considerato attendibile.

Per convalidare i certificati, è possibile usare la logica di convalida del sistema sottostante. Questa convalida del sistema può supportare una logica di convalida personalizzata o sostituirla. Se non si passa il proprio validator del certificato quando si richiede una connessione protetta, la convalida del sistema verrà usata automaticamente.

In Windows, la convalida del sistema verificherà quanto segue:

* Integrità della catena di certificati: i certificati formano una catena coerente che termina in corrispondenza di un certificato radice attendibile
* Validità del certificato: il certificato del server è compreso nell'intervallo di validità e viene emesso per l'autenticazione server
* Revoca: il certificato non è stato revocato
* Nome corrispondenza: il nome host del server corrisponde a uno dei nomi host per i quali è stato emesso il certificato

Implementare l' `ICertificateValidator` interfaccia come segue:

 * `PerformSystemValidation()` deve restituire `true` se deve essere eseguita una convalida del sistema come descritto in precedenza. In questo caso, il risultato della convalida del sistema viene passato come input al `ValidateCertificate()` metodo.
* `ValidateCertificate()` deve convalidare la catena di certificati e quindi chiamare `CertificateValidated()` sul callback passato con il risultato di convalida finale. Questo metodo accetta la catena di certificati, il nome del server con cui viene stabilita la connessione e il fatto che sia necessario forzare un controllo di revoca. Se la catena di certificati contiene più certificati, il primo è il certificato soggetto.

>[!NOTE]
>Se il caso d'uso richiede una forma diversa di convalida (vedere il caso d'uso del certificato #1 sopra), ignorare completamente la convalida del sistema. Usare invece qualsiasi API o libreria in grado di gestire i certificati X. 509 con codifica DER per decodificare la catena di certificati ed eseguire i controlli necessari per il caso d'uso.

## <a name="secure-connection-using-the-openxr-api"></a>Connessione sicura tramite l'API OpenXR

Quando si usa l' [API OpenXR](../native/openxr.md) , tutte le API correlate alla connessione sicura sono disponibili come parte dell' `XR_MSFT_holographic_remoting` estensione OpenXR.

>[!IMPORTANT]
>Per informazioni sull'API dell'estensione OpenXR per la comunicazione remota olografica, vedere la [specifica](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) che si trova nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Gli elementi chiave per la connessione sicura mediante l' `XR_MSFT_holographic_remoting` estensione OpenXR sono i callback seguenti.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, genera o Recupera il token di autenticazione da inviare.
- `xrRemotingValidateServerCertificateCallbackMSFT`, convalida la catena di certificati.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, convalida il token di autenticazione del client.
- `xrRemotingRequestServerCertificateCallbackMSFT`, fornire l'applicazione server con il certificato da utilizzare.

Questi callback possono essere forniti al runtime OpenXR di comunicazione remota tramite `xrRemotingSetSecureConnectionClientCallbacksMSFT` e `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Inoltre, la connessione protetta deve essere abilitata tramite il parametro secureConnection nella `XrRemotingConnectInfoMSFT` struttura o la `XrRemotingListenInfoMSFT` struttura a seconda che si stia usando `xrRemotingConnectMSFT` o `xrRemotingListenMSFT` .

Questa API è simile all'API basata su IDL descritta in [implementazione della sicurezza della comunicazione remota olografica](#implementing-holographic-remoting-security). Tuttavia, invece di implementare le interfacce, si dovrebbe fornire implementazioni di callback. È possibile trovare un esempio dettagliato nell' [app di esempio OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app remota olografica remota usando le API di realtà mista di Windows](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
