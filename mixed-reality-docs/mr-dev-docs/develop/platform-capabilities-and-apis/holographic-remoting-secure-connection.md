---
title: Abilitazione della sicurezza della connessione per Holographic Remoting
description: Questa pagina illustra come configurare Holographic Remoting per l'uso di connessioni crittografate e autenticate tra il lettore e le app remote.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, sicurezza, autenticazione, da server a client
ms.openlocfilehash: 6ac5284bdf9e5984fcf091b6502fb62a494e4fe8
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184648"
---
# <a name="enabling-connection-security-for-holographic-remoting-c"></a>Abilitazione della sicurezza della connessione per Holographic Remoting (C++)

>[!IMPORTANT]
>Queste linee guida sono specifiche di Holographic Remoting HoloLens 2.

Questa pagina offre una panoramica della sicurezza di rete per Holographic Remoting. Sono disponibili informazioni su

* sicurezza nel contesto di Holographic Remoting e perché potrebbe essere necessario
* misure consigliate in base a casi d'uso diversi
* implementazione della sicurezza nella soluzione Holographic Remoting

## <a name="holographic-remoting-security"></a>Sicurezza della comunicazione remota olografica

Holographic Remoting scambia informazioni su una rete. Se non sono presenti misure di sicurezza, gli avversari nella stessa rete possono compromettere l'integrità della comunicazione o accedere a informazioni riservate.

Le app di esempio e Holographic Remoting Player in Windows Store sono con sicurezza disabilitata. In questo modo, gli esempi sono più facili da comprendere. Consente anche di iniziare più rapidamente a usare lo sviluppo.

Per il test sul campo o la produzione, è consigliabile abilitare la sicurezza nella soluzione Holographic Remoting.

La sicurezza in Holographic Remoting, se configurata correttamente per il caso d'uso, offre le garanzie seguenti:

* **Autenticità:** sia il lettore che l'app remota possono essere certi che l'altro lato sia l'utente che dichiara di essere
* **Riservatezza: nessuna** terza parte può leggere le informazioni scambiate tra il lettore e l'app remota
* **Integrità: il** lettore e il remoto possono rilevare eventuali modifiche in transito alla comunicazione

>[!IMPORTANT]
>Per poter usare le funzionalità di sicurezza, [](holographic-remoting-create-player.md) è necessario implementare sia un lettore personalizzato che un'app remota personalizzata usando le API [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) [o OpenXR.](holographic-remoting-create-remote-openxr.md)

>[!NOTE]
> A partire dalla [versione 2.4.0](holographic-remoting-version-history.md#v2.4.0) è possibile creare app remote usando l'API [OpenXR.](../native/openxr.md) Una panoramica su come stabilire una connessione sicura in un ambiente OpenXR è disponibile [di seguito.](#secure-connection-using-the-openxr-api)

## <a name="planning-the-security-implementation"></a>Pianificazione dell'implementazione della sicurezza

Quando si abilita la sicurezza in Holographic Remoting, la libreria remota abiliterà automaticamente i controlli di crittografia e integrità per tutti i dati s scambiati in rete.

Per garantire un'autenticazione appropriata, tuttavia, è necessario eseguire alcune operazioni aggiuntive. Le operazioni da eseguire dipendono dal caso d'uso e il resto di questa sezione riguarda la procedura necessaria.

>[!IMPORTANT]
> Questo articolo può fornire solo indicazioni generali. In caso di dubbi, è consigliabile consultare un esperto di sicurezza in grado di fornire indicazioni specifiche per il caso d'uso.

Prima di tutto, quando si descrivono le connessioni di rete, verranno usati i termini _client_ e _server._ Il server è il lato in ascolto delle connessioni in ingresso su un indirizzo endpoint noto e il client è quello che si connette all'endpoint del server.

>[!NOTE]
> I ruoli client e server non sono legati a se un'app funge da lettore o da remoto. Anche se gli esempi hanno il ruolo del server, è facile invertire i ruoli se si adatta meglio al caso d'uso.

### <a name="planning-the-server-to-client-authentication"></a>Pianificazione dell'autenticazione da server a client

Il server usa i certificati digitali per dimostrare la propria identità al client. Il client convalida il certificato del server durante la fase di handshake della connessione. Se il client non considera attendibile il server, terminerà la connessione a questo punto.

Il modo in cui il client convalida il certificato server e quali tipi di certificati server possono essere usati dipende dal caso d'uso.

**Caso d'uso 1:** Il nome host del server non è fisso o il server non è affatto indirizzato in base al nome host.

In questo caso d'uso, non è pratico (o nemmeno possibile) rilasciare un certificato per il nome host del server. È consigliabile convalidare invece l'identificazione personale del certificato. Come un'impronta digitale umana, l'identificazione personale identifica in modo univoco un certificato.

È importante comunicare l'identificazione personale al client fuori banda. Ciò significa che non è possibile inviarlo tramite la stessa connessione di rete usata per la comunicazione remota. È invece possibile immetterlo manualmente nella configurazione del client o fare in modo che eseere il client a eseguire l'analisi di un codice a qr.

**Caso d'uso 2:** Il server può essere raggiunto tramite un nome host stabile.

In questo caso d'uso, il server ha un nome host specifico e si sa che non è probabile che questo nome cambi. È quindi possibile usare un certificato rilasciato al nome host del server. L'attendibilità verrà stabilita in base al nome host e alla catena di attendibilità del certificato.

Se si sceglie questa opzione, il client deve conoscere in anticipo il nome host del server e il certificato radice.

### <a name="planning-the-client-to-server-authentication"></a>Pianificazione dell'autenticazione da client a server

I client eseguono l'autenticazione nel server usando un token in formato libero. Ciò che questo token deve contenere dipenderà di nuovo dal caso d'uso:

**Caso d'uso 1:** È necessario solo verificare l'identità dell'app client.

In questo caso d'uso, un segreto condiviso può essere sufficiente. Questo segreto deve essere sufficientemente complesso da non essere intuito.

Un segreto condiviso valido è un GUID casuale, che viene immesso manualmente nella configurazione del server e del client. Per crearne uno è possibile, ad esempio, usare `New-Guid` il comando in PowerShell.

Assicurarsi che questo segreto condiviso non sia mai comunicato tramite canali non sicuri. La libreria remota garantisce che il segreto condiviso sia sempre inviato crittografato e solo a peer attendibili.

**Caso d'uso 2:** È anche necessario verificare l'identità dell'utente dell'app client.

Un segreto condiviso non sarà sufficiente per coprire questo caso d'uso. È invece possibile usare i token creati da un provider di identità. Un flusso di lavoro di autenticazione che usa un provider di identità sarà simile al seguente:

* Il client autorizza il provider di identità e richiede un token
* Il provider di identità genera un token e lo invia al client
* Il client invia questo token al server tramite Holographic Remoting
* Il server convalida il token del client rispetto al provider di identità

Un esempio di provider di identità è [l'Microsoft Identity Platform](/azure/active-directory/develop/).

Come nel caso d'uso precedente, assicurarsi che questi token non siano inviati tramite canali non sicuri o esposti in altro modo.

## <a name="implementing-holographic-remoting-security"></a>Implementazione della sicurezza remota olografica

Tenere presente che è necessario implementare app remote e lettore personalizzate se si vuole abilitare la sicurezza della connessione. È possibile usare gli esempi forniti come punti di partenza per le proprie app.

Per abilitare la sicurezza, `ListenSecure()` chiamare invece di e invece di per stabilire la connessione `Listen()` `ConnectSecure()` `Connect()` remota.

Queste chiamate richiedono di fornire implementazioni di determinate interfacce per fornire e convalidare informazioni relative alla sicurezza:

* Il server deve implementare un provider di certificati e un validator di autenticazione
* Il client deve implementare un provider di autenticazione e un validator del certificato.

Tutte le interfacce hanno una funzione che richiede di intervenire, che riceve un oggetto callback come parametro. Questo oggetto consente di implementare facilmente la gestione asincrona della richiesta. Mantenere un riferimento a questo oggetto e chiamare la funzione di completamento al termine dell'azione asincrona. La funzione di completamento può essere chiamata da qualsiasi thread.

>[!TIP]
>L'implementazione di interfacce WinRT può essere eseguita facilmente usando C++/WinRT. Il [capitolo Author APIs with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) (Creare API con C++/WinRT) descrive questo argomento in dettaglio.

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`All'interno NuGet pacchetto contiene la documentazione dettagliata per l'API correlata alle connessioni protette.

### <a name="implementing-a-certificate-provider"></a>Implementazione di un provider di certificati

I provider di certificati forniscono all'applicazione server il certificato da usare. L'implementazione è costituita da due parti:

1) Oggetto certificato che implementa `ICertificate` l'interfaccia :

    * `GetCertificatePfx()` deve restituire il contenuto binario di un `PKCS#12` archivio certificati. Un `.pfx` file contiene `PKCS#12` dati, quindi il relativo contenuto può essere usato direttamente qui.
    * `GetSubjectName()` deve restituire il nome descrittivo che identifica il certificato da usare. Se al certificato non viene assegnato alcun nome descrittivo, questa funzione deve restituire il nome soggetto del certificato.
    * `GetPfxPassword()` deve restituire la password necessaria per aprire l'archivio certificati o una stringa vuota se non è richiesta alcuna password.

2) Provider di certificati che implementa `ICertificateProvider` l'interfaccia :
    * `GetCertificate()` deve costruire un oggetto certificato e restituirlo chiamando `CertificateReceived()` sull'oggetto di callback.

### <a name="implementing-an-authentication-validator"></a>Implementazione di un validator di autenticazione

I validator di autenticazione ricevono il token di autenticazione inviato dal client e rispondono con il risultato della convalida.

Implementare `IAuthenticationReceiver` l'interfaccia come indicato di seguito:

* `GetRealm()` deve restituire il nome dell'area di autenticazione (un'area di autenticazione HTTP usata durante l'handshake di connessione remota).
* `ValidateToken()` deve convalidare il token di autenticazione client e `ValidationCompleted()` chiamare sull'oggetto callback con il risultato della convalida.

### <a name="implementing-an-authentication-provider"></a>Implementazione di un provider di autenticazione

I provider di autenticazione generano o recuperano il token di autenticazione da inviare al server.

Implementare `IAuthenticationProvider` l'interfaccia come segue:

* `GetToken()` deve generare o recuperare il token di autenticazione da inviare. Quando il token è pronto, chiamare il `TokenReceived()` metodo sull'oggetto callback.

### <a name="implementing-a-certificate-validator"></a>Implementazione di un validator del certificato

I validator del certificato ricevono la catena di certificati inviata dal server e determinano se il server può essere considerato attendibile.

Per convalidare i certificati, è possibile usare la logica di convalida del sistema sottostante. Questa convalida di sistema può supportare la propria logica di convalida o sostituirla completamente. Se non si passa il proprio validator del certificato quando si richiede una connessione sicura, verrà usata automaticamente la convalida del sistema.

In Windows, la convalida del sistema verifica la presenza di:

* Integrità della catena di certificati: i certificati formano una catena coerente che termina con un certificato radice attendibile
* Validità del certificato: il certificato del server rientra nell'intervallo di validità e viene emesso per l'autenticazione del server
* Revoca: il certificato non è stato revocato
* Corrispondenza nome: il nome host del server corrisponde a uno dei nomi host per cui è stato emesso il certificato

Implementare `ICertificateValidator` l'interfaccia come segue:

 * `PerformSystemValidation()` deve restituire `true` se deve essere eseguita una convalida di sistema come descritto in precedenza. In questo caso, il risultato della convalida di sistema viene passato come input al `ValidateCertificate()` metodo .
* `ValidateCertificate()` deve convalidare la catena di certificati e quindi `CertificateValidated()` chiamare sul callback passato con il risultato della convalida finale. Questo metodo accetta la catena di certificati, il nome del server con cui viene stabilita la connessione e se è necessario forzare un controllo di revoca. Se la catena di certificati contiene più certificati, il primo è il certificato del soggetto.

>[!NOTE]
>Se il caso d'uso richiede una forma di convalida diversa (vedere il caso d'uso del certificato #1 precedente), ignorare completamente la convalida del sistema. Usare invece qualsiasi API o libreria in grado di gestire certificati X.509 con codifica DER per decodificare la catena di certificati ed eseguire i controlli necessari per il caso d'uso.

## <a name="secure-connection-using-the-openxr-api"></a>Proteggere la connessione con l'API OpenXR

Quando si usa [l'API OpenXR,](../native/openxr.md) tutte le API correlate alla connessione sicura sono disponibili come parte dell'estensione `XR_MSFT_holographic_remoting` OpenXR.

>[!IMPORTANT]
>Per informazioni sull'API dell'estensione OpenXR di [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) Holographic Remoting, vedere la specifica disponibile nel repository github degli esempi di [Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

Gli elementi chiave per la connessione protetta tramite `XR_MSFT_holographic_remoting` l'estensione OpenXR sono i callback seguenti.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, genera o recupera il token di autenticazione da inviare.
- `xrRemotingValidateServerCertificateCallbackMSFT`, convalida la catena di certificati.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, convalida il token di autenticazione client.
- `xrRemotingRequestServerCertificateCallbackMSFT`, fornire all'applicazione server il certificato da usare.

Questi callback possono essere forniti al runtime OpenXR remoto tramite `xrRemotingSetSecureConnectionClientCallbacksMSFT` e `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Inoltre, la connessione protetta deve essere abilitata tramite il parametro secureConnection nella struttura o nella struttura a seconda che si `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` utilizzi o `xrRemotingConnectMSFT` `xrRemotingListenMSFT` .

Questa API è simile all'API basata su IDL descritta in Implementazione della sicurezza [remota olografica.](#implementing-holographic-remoting-security) Tuttavia, invece di implementare le interfacce, è necessario fornire implementazioni di callback. È possibile trovare un esempio dettagliato [nell'app di esempio OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Vedere anche
* [Panoramica di Holographic Remoting](holographic-remoting-overview.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con le API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)