---
title: Stabilire una connessione sicura con Holographic Remoting
description: Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683645"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Stabilire una connessione sicura con Holographic Remoting

>[!IMPORTANT]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.

Quando si esegue lo streaming di contenuto in HoloLens 2 su una rete non sicura, ad esempio un Wi-Fi aperto o Internet, è consigliabile usare una connessione crittografata.

>[!IMPORTANT]
>È consigliabile prendere in considerazione anche quando si usa un Wi-Fi locale attendibile usando una connessione crittografata.

Per poter usare una connessione crittografata, sarà necessario implementare sia un [lettore personalizzato](holographic-remoting-create-player.md) che un' [app remota personalizzata](holographic-remoting-create-host.md).

La crittografia viene eseguita tramite l'implementazione TLS delle piattaforme sottostanti.

## <a name="basics-of-an-encrypted-connection"></a>Nozioni di base su una connessione crittografata

Per consentire uno scambio di certificati, è necessario implementare gli oggetti seguenti.

>[!TIP]
>L'implementazione di interfacce WinRT può essere eseguita facilmente con C++/WinRT. Il capitolo [API autore con C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) descrive in modo dettagliato questo aspetto.

>[!IMPORTANT]
>Il contenuto del ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` pacchetto NuGet contiene la documentazione dettagliata per l'API relativa alle connessioni protette.

1) Oggetto Certificate, che deve implementare l' ```ICertificate``` interfaccia.

    * Restituisce il contenuto binario del certificato PFX tramite il ```GetCertificatePfx``` metodo. Uguale al contenuto binario di un file con estensione pfx.
    * Restituisce il nome del soggetto del certificato tramite ```GetSubjectName``` .
    * Restituire la password PFX tramite ```GetPfxPassword``` . Restituisce una stringa vuota per un PFX non protetto.

2) Provider di certificati che implementa l' ```ICertificateProvider``` interfaccia che fornisce un certificato quando viene richiesto tramite il ```GetCertificate``` metodo.

3) Validator del certificato che implementa l' ```ICertificateValidator``` interfaccia. L'attività consiste nel verificare i certificati in ingresso.
    * Il ```PerformSystemValidation``` metodo deve restituire ```true``` quando la piattaforma sottostante deve convalidare la catena di certificati in ingresso; ```false``` in caso contrario,.
    * ```ValidateCertificate``` viene chiamato dal contesto client per richiedere la convalida di un certificato. Questo metodo accetta la catena di certificati (con il primo certificato che è il certificato oggetto), il nome del server con cui viene stabilita la connessione e se deve essere forzato un controllo di revoca. Il risultato della convalida del sistema verrà fornito se è stata richiesta la convalida dal sistema sottostante. Per continuare l'elaborazione ```CertificateValidated``` con il risultato appropriato o ```Cancel``` per annullare la convalida, è necessario chiamare sull'oggetto passato ```ICertificateValidationCallback``` .

Inoltre, per consentire lo scambio di un token protetto, è necessario implementare gli oggetti seguenti.

1) Un provider di autenticazione che implementa l' ```IAuthenticationProvider``` interfaccia. Il ```GetToken``` metodo viene chiamato dal contesto client per richiedere un token per l'autenticazione client. Per continuare ```TokenReceived``` a fornire il token di autenticazione e continuare il processo di connessione oppure ```Cancel``` per annullare il processo, è necessario chiamare sull'oggetto passato ```IAuthenticationProviderCallback``` .
2) Ricevitore di autenticazione che implementa l' ```IAuthenticationReceiver``` interfaccia. La relativa attività consiste nel convalidare i token in ingresso.
    * Il ```GetRealm``` metodo deve restituire il nome dell'area di autenticazione.
    * Il ```ValidateToken``` metodo viene chiamato dal contesto di rete del server per richiedere la convalida di un token di autenticazione client. Per continuare, chiamare il ```ValidationCompleted``` completamento del segnale della convalida o ```Cancel``` rifiutare la connessione client. La connessione client verrà accettata o rifiutata in base al risultato della convalida passato a ```ValidationCompleted``` . 

Una volta implementati questi oggetti, è ```ListenSecure``` necessario chiamare anziché ```Listen``` e ```ConnectSecure``` anziché ```Connect``` nel contesto remoto e nel contesto del lettore rispettivamente. ```ListenSecure``` richiede un provider di certificati e un ricevitore di autenticazione aggiuntivi ```Listen``` . ```ConnectSecure``` richiede un provider di autenticazione e un validator del certificato aggiuntivi ```Connect``` .

## <a name="see-also"></a>Vedere anche
* [Scrivere un'app remota Holographic Remoting](holographic-remoting-create-host.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
