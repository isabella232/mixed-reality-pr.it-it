---
title: Informazioni di riferimento sulle API di Portale di dispositivi
description: Informazioni di riferimento sulle API per il portale per dispositivi Windows in HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portale per dispositivi Windows, API, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677970"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="3c3bb-104">Informazioni di riferimento sulle API di Portale di dispositivi</span><span class="sxs-lookup"><span data-stu-id="3c3bb-104">Device portal API reference</span></span>

<span data-ttu-id="3c3bb-105">Tutti gli elementi del [portale per dispositivi Windows](using-the-windows-device-portal.md) sono basati sulle API REST che è possibile usare per accedere ai dati e controllare il dispositivo a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="3c3bb-106">Deloyment app</span><span class="sxs-lookup"><span data-stu-id="3c3bb-106">App deloyment</span></span>

<span data-ttu-id="3c3bb-107">**/API/app/PackageManager/Package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="3c3bb-108">Disinstalla un'app</span><span class="sxs-lookup"><span data-stu-id="3c3bb-108">Uninstalls an app</span></span>

<span data-ttu-id="3c3bb-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-109">Parameters</span></span>
* <span data-ttu-id="3c3bb-110">Package: nome file del pacchetto da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="3c3bb-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="3c3bb-112">Installa un'app</span><span class="sxs-lookup"><span data-stu-id="3c3bb-112">Installs an App</span></span>

<span data-ttu-id="3c3bb-113">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-113">Parameters</span></span>
* <span data-ttu-id="3c3bb-114">Package: nome file del pacchetto da installare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="3c3bb-115">Payload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-115">Payload</span></span>
* <span data-ttu-id="3c3bb-116">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="3c3bb-116">multi-part conforming http body</span></span>

<span data-ttu-id="3c3bb-117">**/API/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="3c3bb-118">Recupera l'elenco delle app installate nel sistema con i dettagli</span><span class="sxs-lookup"><span data-stu-id="3c3bb-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="3c3bb-119">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-119">Return data</span></span>
* <span data-ttu-id="3c3bb-120">Elenco dei pacchetti installati con i dettagli</span><span class="sxs-lookup"><span data-stu-id="3c3bb-120">List of installed packages with details</span></span>

<span data-ttu-id="3c3bb-121">**/API/app/PackageManager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="3c3bb-122">Ottiene lo stato dell'installazione dell'app in corso</span><span class="sxs-lookup"><span data-stu-id="3c3bb-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="3c3bb-123">Raccolta dei dump</span><span class="sxs-lookup"><span data-stu-id="3c3bb-123">Dump collection</span></span>

<span data-ttu-id="3c3bb-124">**/API/debug/dump/usermode/CrashControl (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="3c3bb-125">Disabilita la raccolta dei dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="3c3bb-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-126">Parameters</span></span>
* <span data-ttu-id="3c3bb-127">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-127">packageFullname : package name</span></span>

<span data-ttu-id="3c3bb-128">**/API/debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="3c3bb-129">Ottiene le impostazioni per la raccolta di dump di arresto anomalo di sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="3c3bb-130">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-130">Parameters</span></span>
* <span data-ttu-id="3c3bb-131">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-131">packageFullname : package name</span></span>

<span data-ttu-id="3c3bb-132">**/API/debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="3c3bb-133">Abilita e imposta le impostazioni di controllo dump per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="3c3bb-134">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-134">Parameters</span></span>
* <span data-ttu-id="3c3bb-135">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-135">packageFullname : package name</span></span>

<span data-ttu-id="3c3bb-136">**/API/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="3c3bb-137">Elimina un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="3c3bb-138">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-138">Parameters</span></span>
* <span data-ttu-id="3c3bb-139">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-139">packageFullname : package name</span></span>
* <span data-ttu-id="3c3bb-140">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="3c3bb-140">fileName : dump file name</span></span>

<span data-ttu-id="3c3bb-141">**/API/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="3c3bb-142">Recupera un dump di arresto anomalo del sistema per un'app sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="3c3bb-143">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-143">Parameters</span></span>
* <span data-ttu-id="3c3bb-144">packageFullname: nome pacchetto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-144">packageFullname : package name</span></span>
* <span data-ttu-id="3c3bb-145">fileName: dump nome file</span><span class="sxs-lookup"><span data-stu-id="3c3bb-145">fileName : dump file name</span></span>

<span data-ttu-id="3c3bb-146">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-146">Return data</span></span>
* <span data-ttu-id="3c3bb-147">File dump.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-147">Dump file.</span></span> <span data-ttu-id="3c3bb-148">Esaminare con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3c3bb-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="3c3bb-149">**/API/debug/dump/usermode/Dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="3c3bb-150">Restituisce l'elenco di tutti i dump di arresto anomalo del sistema per le app sideload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="3c3bb-151">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-151">Return data</span></span>
* <span data-ttu-id="3c3bb-152">Elenco dei dump di arresto anomalo del sistema per app caricata sul lato</span><span class="sxs-lookup"><span data-stu-id="3c3bb-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="3c3bb-153">ETW</span><span class="sxs-lookup"><span data-stu-id="3c3bb-153">ETW</span></span>

<span data-ttu-id="3c3bb-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="3c3bb-155">Enumera i provider registrati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-155">Enumerates registered providers</span></span>

<span data-ttu-id="3c3bb-156">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-156">Return data</span></span>
* <span data-ttu-id="3c3bb-157">Elenco di provider, nome descrittivo e GUID</span><span class="sxs-lookup"><span data-stu-id="3c3bb-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="3c3bb-158">**/API/ETW/Session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="3c3bb-159">Crea una sessione ETW in tempo reale. gestito tramite WebSocket.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="3c3bb-160">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-160">Return data</span></span>
* <span data-ttu-id="3c3bb-161">Eventi ETW dai provider abilitati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="3c3bb-162">Sistema operativo olografico</span><span class="sxs-lookup"><span data-stu-id="3c3bb-162">Holographic OS</span></span>

<span data-ttu-id="3c3bb-163">**/API/Holographic/OS/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="3c3bb-164">Restituisce un elenco di provider ETW specifici di HoloLens non registrati con il sistema</span><span class="sxs-lookup"><span data-stu-id="3c3bb-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="3c3bb-165">**/API/Holographic/OS/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="3c3bb-166">Restituisce gli Stati di tutti i servizi in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-166">Returns the states of all services running.</span></span>

<span data-ttu-id="3c3bb-167">**/API/Holographic/OS/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="3c3bb-168">Ottiene il dip archiviato (distanza interpupillare) in millimetri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="3c3bb-169">**/API/Holographic/OS/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="3c3bb-170">Imposta il dpi</span><span class="sxs-lookup"><span data-stu-id="3c3bb-170">Sets the IPD</span></span>

<span data-ttu-id="3c3bb-171">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-171">Parameters</span></span>
* <span data-ttu-id="3c3bb-172">dpi: nuovo valore di DPI da impostare in millimetri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="3c3bb-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="3c3bb-174">Ottenere richieste HTTPS per Device Portal</span><span class="sxs-lookup"><span data-stu-id="3c3bb-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="3c3bb-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="3c3bb-176">Imposta i requisiti HTTPS per il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="3c3bb-177">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-177">Parameters</span></span>
* <span data-ttu-id="3c3bb-178">obbligatorio: Sì, no o default</span><span class="sxs-lookup"><span data-stu-id="3c3bb-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="3c3bb-179">Percezione olografica</span><span class="sxs-lookup"><span data-stu-id="3c3bb-179">Holographic Perception</span></span>

<span data-ttu-id="3c3bb-180">**/API/Holographic/Perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="3c3bb-181">Accetta gli aggiornamenti WebSocket ed esegue un client di percezione che invia gli aggiornamenti a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="3c3bb-182">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-182">Parameters</span></span>
* <span data-ttu-id="3c3bb-183">ClientMode: "Active" forza la modalità di rilevamento visivo quando non può essere stabilita passivamente</span><span class="sxs-lookup"><span data-stu-id="3c3bb-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="3c3bb-184">Termica olografica</span><span class="sxs-lookup"><span data-stu-id="3c3bb-184">Holographic Thermal</span></span>

<span data-ttu-id="3c3bb-185">**/API/Holographic/Thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="3c3bb-186">Ottenere la fase termica del dispositivo (0 normale, 1 caldo, 2 critico)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="3c3bb-187">Map Manager (Gestore mappe)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-187">Map Manager</span></span>

<span data-ttu-id="3c3bb-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="3c3bb-189">Ottiene l'elenco dei file di mappa disponibili (con estensione MapX).</span><span class="sxs-lookup"><span data-stu-id="3c3bb-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="3c3bb-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="3c3bb-191">Ottiene l'elenco dei file di ancoraggio disponibili (con estensione ANCX).</span><span class="sxs-lookup"><span data-stu-id="3c3bb-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="3c3bb-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="3c3bb-193">Ottiene l'elenco dei file di database di ricostruzione spaziale disponibili (con estensione srdb).</span><span class="sxs-lookup"><span data-stu-id="3c3bb-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="3c3bb-194">**/API/Holographic/MapManager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="3c3bb-195">Ottiene l'elenco di ancoraggi salvati in permanenza per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="3c3bb-196">Scaricare/caricare/eliminare file</span><span class="sxs-lookup"><span data-stu-id="3c3bb-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="3c3bb-197">**/API/Holographic/MapManager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="3c3bb-198">Scarica un file di database di mapping, ancoraggio o ricostruzione spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="3c3bb-199">Il file deve essere stato caricato o esportato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="3c3bb-200">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-200">Parameters</span></span>
* <span data-ttu-id="3c3bb-201">FileName: nome del file da scaricare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="3c3bb-202">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="3c3bb-203">**/API/Holographic/MapManager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="3c3bb-204">Carica un file di database di mapping, ancoraggio o ricostruzione spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="3c3bb-205">Una volta caricato, un file può essere importato in un secondo momento per l'uso da parte del sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="3c3bb-206">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-206">Parameters</span></span>
* <span data-ttu-id="3c3bb-207">file: nome del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="3c3bb-208">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="3c3bb-209">**/API/Holographic/MapManager/Delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="3c3bb-210">Elimina un file di database di mapping, ancoraggio o ricostruzione spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="3c3bb-211">Il file deve essere stato caricato o esportato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="3c3bb-212">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-212">Parameters</span></span>
* <span data-ttu-id="3c3bb-213">FileName: nome del file da eliminare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="3c3bb-214">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="3c3bb-215">Esportazione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-215">Export</span></span>

<span data-ttu-id="3c3bb-216">**/API/Holographic/MapManager/Export (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="3c3bb-217">Esporta la mappa attualmente utilizzata dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="3c3bb-218">Una volta esportata, è possibile scaricarla.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="3c3bb-219">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="3c3bb-220">**/API/Holographic/MapManager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="3c3bb-221">Esporta la mappa attualmente utilizzata dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="3c3bb-222">Una volta esportata, è possibile scaricarla.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="3c3bb-223">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="3c3bb-224">**/API/Holographic/MapManager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="3c3bb-225">Esporta la mappa e gli ancoraggi attualmente in uso dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="3c3bb-226">Una volta esportate, è possibile scaricarle.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="3c3bb-227">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="3c3bb-228">**/API/Holographic/MapManager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="3c3bb-229">Esporta la mappa e il database di ricostruzione spaziale attualmente in uso dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="3c3bb-230">Una volta esportate, è possibile scaricarle.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="3c3bb-231">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="3c3bb-232">Importa</span><span class="sxs-lookup"><span data-stu-id="3c3bb-232">Import</span></span>

<span data-ttu-id="3c3bb-233">**/API/Holographic/MapManager/Import (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="3c3bb-234">Indica al sistema quale mappa deve essere utilizzata attualmente.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="3c3bb-235">Può essere chiamato sui file che sono stati esportati o caricati.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="3c3bb-236">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-236">Parameters</span></span>
* <span data-ttu-id="3c3bb-237">FileName: nome della mappa da usare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="3c3bb-238">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="3c3bb-239">**/API/Holographic/MapManager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="3c3bb-240">Indica al sistema che devono essere usati gli ancoraggi attualmente in uso.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="3c3bb-241">Può essere chiamato sui file che sono stati esportati o caricati.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="3c3bb-242">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-242">Parameters</span></span>
* <span data-ttu-id="3c3bb-243">FileName: nome degli ancoraggi da usare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="3c3bb-244">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="3c3bb-245">**/API/Holographic/MapManager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="3c3bb-246">Indica al sistema quale database di ricostruzione spaziale usare attualmente.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="3c3bb-247">Può essere chiamato sui file che sono stati esportati o caricati.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="3c3bb-248">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-248">Parameters</span></span>
* <span data-ttu-id="3c3bb-249">FileName: nome del database di mapping spaziale da usare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="3c3bb-250">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="3c3bb-251">Altro</span><span class="sxs-lookup"><span data-stu-id="3c3bb-251">Other</span></span>

<span data-ttu-id="3c3bb-252">**/API/Holographic/MapManager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="3c3bb-253">Ripristinare il sistema mappa, ancoraggi e database di ricostruzione spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="3c3bb-254">Esempio:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="3c3bb-255">**/API/Holographic/MapManager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="3c3bb-256">Ottiene lo stato del sistema, inclusi i file di database di mapping, ancoraggi e ricostruzione spaziali che sono stati importati l'ultima volta.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="3c3bb-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="3c3bb-257">Mixed Reality Capture</span></span>

<span data-ttu-id="3c3bb-258">**/API/Holographic/MRC/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="3c3bb-259">Scarica un file di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="3c3bb-260">Usare il parametro di query op = Stream per il flusso.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="3c3bb-261">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-261">Parameters</span></span>
* <span data-ttu-id="3c3bb-262">filename: Name, hex64 codificato del file video da ottenere</span><span class="sxs-lookup"><span data-stu-id="3c3bb-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="3c3bb-263">op: Stream</span><span class="sxs-lookup"><span data-stu-id="3c3bb-263">op : stream</span></span>

<span data-ttu-id="3c3bb-264">**/API/Holographic/MRC/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="3c3bb-265">Elimina una registrazione di realtà mista dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="3c3bb-266">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-266">Parameters</span></span>
* <span data-ttu-id="3c3bb-267">filename: Name, hex64 codificato del file da eliminare</span><span class="sxs-lookup"><span data-stu-id="3c3bb-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="3c3bb-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="3c3bb-269">Restituisce l'elenco dei file di realtà mista archiviati nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="3c3bb-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="3c3bb-271">Accetta una foto della realtà mista e crea un file nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="3c3bb-272">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-272">Parameters</span></span>
* <span data-ttu-id="3c3bb-273">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-274">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-275">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="3c3bb-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="3c3bb-277">Ottiene le impostazioni predefinite di acquisizione della realtà mista</span><span class="sxs-lookup"><span data-stu-id="3c3bb-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="3c3bb-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="3c3bb-279">Imposta le impostazioni predefinite di acquisizione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="3c3bb-280">Alcune di queste impostazioni vengono applicate all'acquisizione di foto e video di MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="3c3bb-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="3c3bb-282">Ottiene lo stato dell'acquisizione di realtà mista all'interno del portale del dispositivo Windows.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="3c3bb-283">\**_Risposta_* _</span><span class="sxs-lookup"><span data-stu-id="3c3bb-283">\**_Response_* _</span></span>

<span data-ttu-id="3c3bb-284">La risposta contiene una proprietà JSON che indica se il portale del dispositivo Windows sta registrando o meno il video.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="3c3bb-285">_ */API/Holographic/MRC/Thumbnail (Get)*\*</span><span class="sxs-lookup"><span data-stu-id="3c3bb-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="3c3bb-286">Ottiene l'immagine di anteprima per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="3c3bb-287">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-287">Parameters</span></span>
* <span data-ttu-id="3c3bb-288">filename: Name, hex64 codificato, del file per il quale viene richiesta l'anteprima</span><span class="sxs-lookup"><span data-stu-id="3c3bb-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="3c3bb-289">**/API/Holographic/MRC/video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="3c3bb-290">Avvia una registrazione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="3c3bb-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="3c3bb-291">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-291">Parameters</span></span>
* <span data-ttu-id="3c3bb-292">Holo: Acquisisci ologrammi: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-293">PV: Capture PV fotocamera: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-294">MIC: Acquisisci microfono: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-295">loopback: Acquisisci audio dell'app: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-296">RenderFromCamera: (solo HoloLens 2) Render dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="3c3bb-297">Vstab: (solo HoloLens 2) Abilita stabilizzazione video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="3c3bb-298">vstabbuffer: (solo HoloLens 2) latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="3c3bb-299">**/API/Holographic/MRC/video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="3c3bb-300">Arresta la registrazione della realtà mista corrente</span><span class="sxs-lookup"><span data-stu-id="3c3bb-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="3c3bb-301">Flusso di realtà mista</span><span class="sxs-lookup"><span data-stu-id="3c3bb-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="3c3bb-302">HoloLens supporta l'anteprima in tempo reale della realtà mista tramite il download in blocchi di un MP4 frammentato.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="3c3bb-303">I flussi di realtà mista condividono lo stesso set di parametri per controllare gli elementi acquisiti:</span><span class="sxs-lookup"><span data-stu-id="3c3bb-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="3c3bb-304">Holo: acquisire gli ologrammi: true o false</span><span class="sxs-lookup"><span data-stu-id="3c3bb-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="3c3bb-305">PV: acquisire la fotocamera PV: true o false</span><span class="sxs-lookup"><span data-stu-id="3c3bb-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="3c3bb-306">MIC: Acquisisci microfono: true o false</span><span class="sxs-lookup"><span data-stu-id="3c3bb-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="3c3bb-307">loopback: Acquisisci audio dell'app: true o false</span><span class="sxs-lookup"><span data-stu-id="3c3bb-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="3c3bb-308">Se non viene specificato alcun valore, verranno acquisiti gli ologrammi, la fotocamera foto/video e l'audio dell'app.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="3c3bb-309">Se viene specificato any: i parametri non specificati verranno impostati su false.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="3c3bb-310">Parametri facoltativi (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="3c3bb-311">RenderFromCamera: rendering dal punto di vista della fotocamera Photo/video: true o false (il valore predefinito è true)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="3c3bb-312">Vstab: Abilita stabilizzazione video: true o false (il valore predefinito è false)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="3c3bb-313">vstabbuffer: latenza buffer di stabilizzazione video: da 0 a 30 fotogrammi (il valore predefinito è 15 fotogrammi)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="3c3bb-314">**live.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="3c3bb-315">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="3c3bb-316">**live_high.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="3c3bb-317">Flusso di 5Mbit 1280x720p 30 fps.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="3c3bb-318">**live_med.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="3c3bb-319">Un flusso 854x480p 30 fps da 2 MB.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="3c3bb-320">**live_low.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="3c3bb-321">Flusso 428x240p 15fps 0.6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="3c3bb-322">Rete</span><span class="sxs-lookup"><span data-stu-id="3c3bb-322">Networking</span></span>

<span data-ttu-id="3c3bb-323">**/API/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="3c3bb-324">Ottiene la configurazione IP corrente</span><span class="sxs-lookup"><span data-stu-id="3c3bb-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="3c3bb-325">Informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-325">OS Information</span></span>

<span data-ttu-id="3c3bb-326">**/API/OS/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="3c3bb-327">Ottiene le informazioni sul sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-327">Gets operating system information</span></span>

<span data-ttu-id="3c3bb-328">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="3c3bb-329">Ottiene il nome del computer</span><span class="sxs-lookup"><span data-stu-id="3c3bb-329">Gets the machine name</span></span>

<span data-ttu-id="3c3bb-330">**/API/OS/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="3c3bb-331">Imposta il nome del computer</span><span class="sxs-lookup"><span data-stu-id="3c3bb-331">Sets the machine name</span></span>

<span data-ttu-id="3c3bb-332">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-332">Parameters</span></span>
* <span data-ttu-id="3c3bb-333">Nome: nome del nuovo computer, hex64 codificato, per impostare su</span><span class="sxs-lookup"><span data-stu-id="3c3bb-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="3c3bb-334">Controllo della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-334">Perception Simulation Control</span></span>

<span data-ttu-id="3c3bb-335">**/API/Holographic/Simulation/Control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="3c3bb-336">Ottenere la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-336">Get the simulation mode</span></span>

<span data-ttu-id="3c3bb-337">**/API/Holographic/Simulation/Control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="3c3bb-338">Impostare la modalità di simulazione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-338">Set the simulation mode</span></span>

<span data-ttu-id="3c3bb-339">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-339">Parameters</span></span>
* <span data-ttu-id="3c3bb-340">Mode: modalità simulazione: predefinita, simulazione, remota, Legacy</span><span class="sxs-lookup"><span data-stu-id="3c3bb-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="3c3bb-341">**/API/Holographic/Simulation/Control/Stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="3c3bb-342">Eliminare un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-342">Delete a control stream.</span></span>

<span data-ttu-id="3c3bb-343">**/API/Holographic/Simulation/Control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="3c3bb-344">Aprire una connessione Web socket per un flusso di controllo.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="3c3bb-345">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="3c3bb-346">Creare un flusso di controllo (priorità obbligatoria) o pubblicare i dati in un flusso creato (streamId richiesto).</span><span class="sxs-lookup"><span data-stu-id="3c3bb-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="3c3bb-347">È previsto che i dati inviati siano di tipo ' Application/ottetto-Stream '.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="3c3bb-348">**/API/Holographic/Simulation/Display/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="3c3bb-349">Richiedere un flusso video di simulazione contenente il contenuto di cui è stato eseguito il rendering nella visualizzazione del sistema in modalità "simulazione".</span><span class="sxs-lookup"><span data-stu-id="3c3bb-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="3c3bb-350">Inizialmente verrà inviata un'intestazione di descrittore di formato semplice, seguita da trame con codifica H. 264, ognuna preceduta da un'intestazione che indica l'indice degli occhi e le dimensioni della trama.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="3c3bb-351">Riproduzione della simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-351">Perception Simulation Playback</span></span>

<span data-ttu-id="3c3bb-352">**/API/Holographic/Simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="3c3bb-353">Eliminare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-353">Delete a recording.</span></span>

<span data-ttu-id="3c3bb-354">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-354">Parameters</span></span>
* <span data-ttu-id="3c3bb-355">registrazione: nome della registrazione da eliminare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="3c3bb-356">**/API/Holographic/Simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="3c3bb-357">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-357">Upload a recording.</span></span>

<span data-ttu-id="3c3bb-358">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="3c3bb-359">Ottenere tutte le registrazioni.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-359">Get all recordings.</span></span>

<span data-ttu-id="3c3bb-360">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="3c3bb-361">Ottenere lo stato di riproduzione corrente di una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="3c3bb-362">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-362">Parameters</span></span>
* <span data-ttu-id="3c3bb-363">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-363">recording : Name of recording.</span></span>

<span data-ttu-id="3c3bb-364">**/API/Holographic/Simulation/playback/Session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="3c3bb-365">Scaricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-365">Unload a recording.</span></span>

<span data-ttu-id="3c3bb-366">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-366">Parameters</span></span>
* <span data-ttu-id="3c3bb-367">registrazione: nome della registrazione da scaricare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="3c3bb-368">**/API/Holographic/Simulation/playback/Session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="3c3bb-369">Caricare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-369">Load a recording.</span></span>

<span data-ttu-id="3c3bb-370">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-370">Parameters</span></span>
* <span data-ttu-id="3c3bb-371">registrazione: nome della registrazione da caricare.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="3c3bb-372">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="3c3bb-373">Ottenere tutte le registrazioni caricate.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-373">Get all loaded recordings.</span></span>

<span data-ttu-id="3c3bb-374">**/API/Holographic/Simulation/playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="3c3bb-375">Sospendere la registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-375">Pause a recording.</span></span>

<span data-ttu-id="3c3bb-376">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-376">Parameters</span></span>
* <span data-ttu-id="3c3bb-377">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-377">recording : Name of recording.</span></span>

<span data-ttu-id="3c3bb-378">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="3c3bb-379">Riprodurre una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-379">Play a recording.</span></span>

<span data-ttu-id="3c3bb-380">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-380">Parameters</span></span>
* <span data-ttu-id="3c3bb-381">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-381">recording : Name of recording.</span></span>

<span data-ttu-id="3c3bb-382">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="3c3bb-383">Arrestare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-383">Stop a recording.</span></span>

<span data-ttu-id="3c3bb-384">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-384">Parameters</span></span>
* <span data-ttu-id="3c3bb-385">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-385">recording : Name of recording.</span></span>

<span data-ttu-id="3c3bb-386">**/API/Holographic/Simulation/playback/Session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="3c3bb-387">Ottenere i tipi di dati in una registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="3c3bb-388">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-388">Parameters</span></span>
* <span data-ttu-id="3c3bb-389">registrazione: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="3c3bb-390">Registrazione della simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-390">Perception Simulation Recording</span></span>

<span data-ttu-id="3c3bb-391">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="3c3bb-392">Avviare una registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-392">Start a recording.</span></span> <span data-ttu-id="3c3bb-393">Solo una singola registrazione può essere attiva in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="3c3bb-394">È necessario impostare una delle intestazioni Head, Hands, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="3c3bb-395">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-395">Parameters</span></span>
* <span data-ttu-id="3c3bb-396">Head: impostare su 1 per registrare i dati Head.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="3c3bb-397">Hands: impostare su 1 per registrare i dati della mano.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="3c3bb-398">spatialMapping: impostare su 1 per registrare il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="3c3bb-399">ambiente: impostare su 1 per registrare i dati dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="3c3bb-400">Nome: nome della registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-400">name : Name of the recording.</span></span>
* <span data-ttu-id="3c3bb-401">singleSpatialMappingFrame: impostare su 1 per registrare un singolo frame di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="3c3bb-402">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="3c3bb-403">Ottenere lo stato di registrazione.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-403">Get recording state.</span></span>

<span data-ttu-id="3c3bb-404">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="3c3bb-405">Arrestare la registrazione corrente.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-405">Stop the current recording.</span></span> <span data-ttu-id="3c3bb-406">La registrazione verrà restituita come file.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="3c3bb-407">Dati sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="3c3bb-407">Performance data</span></span>

<span data-ttu-id="3c3bb-408">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="3c3bb-409">Restituisce l'elenco dei processi in esecuzione con i dettagli</span><span class="sxs-lookup"><span data-stu-id="3c3bb-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="3c3bb-410">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-410">Return data</span></span>
* <span data-ttu-id="3c3bb-411">JSON con elenco di processi e dettagli per ogni processo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="3c3bb-412">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="3c3bb-413">Restituisce le statistiche sulle prestazioni di sistema (lettura/scrittura di I/O, statistiche sulla memoria e così via.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="3c3bb-414">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-414">Return data</span></span>
* <span data-ttu-id="3c3bb-415">JSON con informazioni di sistema: CPU, GPU, memoria, rete, IO</span><span class="sxs-lookup"><span data-stu-id="3c3bb-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="3c3bb-416">Elettricità</span><span class="sxs-lookup"><span data-stu-id="3c3bb-416">Power</span></span>

<span data-ttu-id="3c3bb-417">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="3c3bb-418">Ottiene lo stato corrente della batteria</span><span class="sxs-lookup"><span data-stu-id="3c3bb-418">Gets the current battery state</span></span>

<span data-ttu-id="3c3bb-419">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="3c3bb-420">Controlla se il sistema è in uno stato di alimentazione basso</span><span class="sxs-lookup"><span data-stu-id="3c3bb-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="3c3bb-421">Controllo remoto</span><span class="sxs-lookup"><span data-stu-id="3c3bb-421">Remote Control</span></span>

<span data-ttu-id="3c3bb-422">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="3c3bb-423">Riavvia il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-423">Restarts the target device</span></span>

<span data-ttu-id="3c3bb-424">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="3c3bb-425">Arresta il dispositivo di destinazione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="3c3bb-426">Gestione attività</span><span class="sxs-lookup"><span data-stu-id="3c3bb-426">Task Manager</span></span>

<span data-ttu-id="3c3bb-427">**/API/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="3c3bb-428">Arresta un'app moderna</span><span class="sxs-lookup"><span data-stu-id="3c3bb-428">Stops a modern app</span></span>

<span data-ttu-id="3c3bb-429">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-429">Parameters</span></span>
* <span data-ttu-id="3c3bb-430">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="3c3bb-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="3c3bb-431">forcestop: forza l'arresto di tutti i processi (= Yes)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="3c3bb-432">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="3c3bb-433">Avvia un'app moderna</span><span class="sxs-lookup"><span data-stu-id="3c3bb-433">Starts a modern app</span></span>

<span data-ttu-id="3c3bb-434">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-434">Parameters</span></span>
* <span data-ttu-id="3c3bb-435">AppID: PRAID dell'app da avviare, hex64 codificato</span><span class="sxs-lookup"><span data-stu-id="3c3bb-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="3c3bb-436">pacchetto: nome completo del pacchetto dell'app, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="3c3bb-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="3c3bb-437">Gestione Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="3c3bb-437">WiFi Management</span></span>

<span data-ttu-id="3c3bb-438">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="3c3bb-439">Enumera le interfacce di rete wireless</span><span class="sxs-lookup"><span data-stu-id="3c3bb-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="3c3bb-440">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-440">Return data</span></span>
* <span data-ttu-id="3c3bb-441">Elenco di interfacce wireless con dettagli (GUID, descrizione e così via)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="3c3bb-442">**/API/WiFi/Network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="3c3bb-443">Elimina un profilo associato a una rete in un'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="3c3bb-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="3c3bb-444">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-444">Parameters</span></span>
* <span data-ttu-id="3c3bb-445">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="3c3bb-445">interface : network interface guid</span></span>
* <span data-ttu-id="3c3bb-446">profilo: nome profilo</span><span class="sxs-lookup"><span data-stu-id="3c3bb-446">profile : profile name</span></span>

<span data-ttu-id="3c3bb-447">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="3c3bb-448">Enumera le reti wireless sull'interfaccia di rete specificata</span><span class="sxs-lookup"><span data-stu-id="3c3bb-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="3c3bb-449">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-449">Parameters</span></span>
* <span data-ttu-id="3c3bb-450">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="3c3bb-450">interface : network interface guid</span></span>

<span data-ttu-id="3c3bb-451">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-451">Return data</span></span>
* <span data-ttu-id="3c3bb-452">Elenco di reti wireless disponibili nell'interfaccia di rete con i dettagli</span><span class="sxs-lookup"><span data-stu-id="3c3bb-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="3c3bb-453">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="3c3bb-454">Si connette o si disconnette a una rete sull'interfaccia specificata</span><span class="sxs-lookup"><span data-stu-id="3c3bb-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="3c3bb-455">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-455">Parameters</span></span>
* <span data-ttu-id="3c3bb-456">interfaccia: GUID dell'interfaccia di rete</span><span class="sxs-lookup"><span data-stu-id="3c3bb-456">interface : network interface guid</span></span>
* <span data-ttu-id="3c3bb-457">SSID: SSID, hex64 codificato, per la connessione a</span><span class="sxs-lookup"><span data-stu-id="3c3bb-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="3c3bb-458">op: connessione o disconnessione</span><span class="sxs-lookup"><span data-stu-id="3c3bb-458">op : connect or disconnect</span></span>
* <span data-ttu-id="3c3bb-459">CreateProfile: Sì o no</span><span class="sxs-lookup"><span data-stu-id="3c3bb-459">createprofile : yes or no</span></span>
* <span data-ttu-id="3c3bb-460">chiave: chiave condivisa, codificato in hex64</span><span class="sxs-lookup"><span data-stu-id="3c3bb-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="3c3bb-461">Registratore prestazioni Windows</span><span class="sxs-lookup"><span data-stu-id="3c3bb-461">Windows Performance Recorder</span></span>

<span data-ttu-id="3c3bb-462">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="3c3bb-463">Carica un profilo WPR e avvia la traccia usando il profilo caricato.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="3c3bb-464">Payload</span><span class="sxs-lookup"><span data-stu-id="3c3bb-464">Payload</span></span>
* <span data-ttu-id="3c3bb-465">corpo HTTP conforme a più parti</span><span class="sxs-lookup"><span data-stu-id="3c3bb-465">multi-part conforming http body</span></span>

<span data-ttu-id="3c3bb-466">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-466">Return data</span></span>
* <span data-ttu-id="3c3bb-467">Restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-467">Returns the WPR session status.</span></span>

<span data-ttu-id="3c3bb-468">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="3c3bb-469">Recupera lo stato della sessione WPR</span><span class="sxs-lookup"><span data-stu-id="3c3bb-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="3c3bb-470">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-470">Return data</span></span>
* <span data-ttu-id="3c3bb-471">Stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-471">WPR session status.</span></span>

<span data-ttu-id="3c3bb-472">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="3c3bb-473">Arresta una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="3c3bb-474">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-474">Return data</span></span>
* <span data-ttu-id="3c3bb-475">Restituisce il file ETL di traccia</span><span class="sxs-lookup"><span data-stu-id="3c3bb-475">Returns the trace ETL file</span></span>

<span data-ttu-id="3c3bb-476">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="3c3bb-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="3c3bb-477">Avvia una sessione di traccia WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="3c3bb-478">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c3bb-478">Parameters</span></span>
* <span data-ttu-id="3c3bb-479">profilo: nome profilo.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-479">profile : Profile name.</span></span> <span data-ttu-id="3c3bb-480">I profili disponibili vengono archiviati in perfprofiles/profiles.jsin</span><span class="sxs-lookup"><span data-stu-id="3c3bb-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="3c3bb-481">Restituisce i dati</span><span class="sxs-lookup"><span data-stu-id="3c3bb-481">Return data</span></span>
* <span data-ttu-id="3c3bb-482">All'avvio, restituisce lo stato della sessione WPR.</span><span class="sxs-lookup"><span data-stu-id="3c3bb-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c3bb-483">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3c3bb-483">See also</span></span>
* [<span data-ttu-id="3c3bb-484">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="3c3bb-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="3c3bb-485">Informazioni di riferimento sulle API del portale per dispositivi (UWP)</span><span class="sxs-lookup"><span data-stu-id="3c3bb-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
