---
title: Documentazione del pacchetto di dati spaziali della realtà mista
description: Lo strumento di pacchetto di dati spaziali per la realtà mista è ora deprecato e non funziona più in alcuna piattaforma. È invece consigliabile lo strumento Gestione mappe.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 93d598a6add8350850faadab241b254e9cb341aa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583646"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="151d1-105">Documentazione del pacchetto di dati spaziali della realtà mista</span><span class="sxs-lookup"><span data-stu-id="151d1-105">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="151d1-106">DEPRECATO</span><span class="sxs-lookup"><span data-stu-id="151d1-106">DEPRECATED</span></span> 
> 
> <span data-ttu-id="151d1-107">A partire da 8/1/2020, questo strumento è ora deprecato e non funziona più in alcuna piattaforma.</span><span class="sxs-lookup"><span data-stu-id="151d1-107">As of 8/1/2020 this tool is now deprecated and no longer functions on any platform.</span></span> <span data-ttu-id="151d1-108">Si consiglia invece di utilizzare lo strumento [Gestione mappe](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) nel portale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="151d1-108">We recommend using the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool in the Device Portal instead.</span></span> 
> 
> <span data-ttu-id="151d1-109">Questo strumento e le relative operazioni sono offerti così come sono.</span><span class="sxs-lookup"><span data-stu-id="151d1-109">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="151d1-110">È soggetta a modifiche senza preavviso e potrebbe non essere compatibile con le versioni future di Windows o Windows Mixed Reality HMD.</span><span class="sxs-lookup"><span data-stu-id="151d1-110">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span> 


## <a name="download"></a><span data-ttu-id="151d1-111">Scarica</span><span class="sxs-lookup"><span data-stu-id="151d1-111">Download</span></span>
 <span data-ttu-id="151d1-112">Scarica [MixedRealitySpatialDataPackager qui](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="151d1-112">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="151d1-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="151d1-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="151d1-114"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="151d1-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="151d1-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="151d1-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="151d1-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="151d1-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="151d1-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="151d1-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="151d1-118">Pacchetto di dati spaziali della realtà mista</span><span class="sxs-lookup"><span data-stu-id="151d1-118">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="151d1-119">✔️</span><span class="sxs-lookup"><span data-stu-id="151d1-119">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="151d1-120">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="151d1-120">Quickstart</span></span>

<span data-ttu-id="151d1-121">Lo strumento di combinazione dei dati spaziali della realtà mista copia i dati spaziali di un'app di destinazione da un PC a un altro tramite un processo di esportazione e importazione in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="151d1-121">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="151d1-122">Lo strumento deve essere eseguito con privilegi di amministratore ed Elimina i dati spaziali esistenti durante l'importazione.</span><span class="sxs-lookup"><span data-stu-id="151d1-122">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="151d1-123">L'esportazione lascia intatti i dati spaziali esistenti.</span><span class="sxs-lookup"><span data-stu-id="151d1-123">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="151d1-124">Requisiti e limitazioni principali:</span><span class="sxs-lookup"><span data-stu-id="151d1-124">Key requirements and limitations:</span></span>

1. <span data-ttu-id="151d1-125">Lo strumento deve essere eseguito con privilegi di amministratore</span><span class="sxs-lookup"><span data-stu-id="151d1-125">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="151d1-126">Potrebbe essere necessario riavviare il computer se il portale per la realtà mista è instabile dopo l'esecuzione dello strumento</span><span class="sxs-lookup"><span data-stu-id="151d1-126">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="151d1-127">Lo strumento non verrà eseguito in caso di mancata corrispondenza delle versioni dei dati spaziali o di incompatibilità</span><span class="sxs-lookup"><span data-stu-id="151d1-127">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="151d1-128">Lo strumento cancellerà i dati spaziali esistenti durante l'importazione</span><span class="sxs-lookup"><span data-stu-id="151d1-128">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="151d1-129">Se il processo di importazione ha esito negativo, non è possibile ripristinare i dati precedenti a meno che non sia stato eseguito il backup esportando precedentemente</span><span class="sxs-lookup"><span data-stu-id="151d1-129">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="151d1-130">Funzionalità di importazione di qualità che condizionano la modalità di "sola lettura" per i dati della mappa spaziale</span><span class="sxs-lookup"><span data-stu-id="151d1-130">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="151d1-131">Procedure consigliate per il mapping</span><span class="sxs-lookup"><span data-stu-id="151d1-131">Mapping Best Practices</span></span>

1. <span data-ttu-id="151d1-132">Cancellare le mappe esistenti dal pannello di controllo (impostazioni-> realtà mista-> ambiente-> cancellare i dati dell'ambiente)</span><span class="sxs-lookup"><span data-stu-id="151d1-132">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="151d1-133">Assicurarsi che l'illuminazione sia sufficiente per un corretto rilevamento e se l'esecuzione della modalità Mappa bloccata tenti di mantenere la stessa illuminazione</span><span class="sxs-lookup"><span data-stu-id="151d1-133">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="151d1-134">Quando possibile, evitare di ridurre l'intervallo dinamico di illuminazione evitando aree di illuminazione elevata accanto a aree ombreggiate scure</span><span class="sxs-lookup"><span data-stu-id="151d1-134">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="151d1-135">Ridurre al minimo le superfici senza trama, ad esempio inserire un intervallo di poster diversi sui muri bianchi</span><span class="sxs-lookup"><span data-stu-id="151d1-135">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="151d1-136">Mappare lo spazio senza oggetti dinamici nella scena, ad esempio lo stato di trasferimento di persone</span><span class="sxs-lookup"><span data-stu-id="151d1-136">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="151d1-137">Blocca la mappa durante l'importazione (disponibile tramite l'anteprima di Insider)</span><span class="sxs-lookup"><span data-stu-id="151d1-137">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="151d1-138">Sbloccare la mappa e ripetere l'analisi dell'ambiente quando si verificano peggioramenti della qualità e/o sono presenti modifiche nell'ambiente (illuminazione o modifiche nel layout degli oggetti) \* \* _</span><span class="sxs-lookup"><span data-stu-id="151d1-138">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout) \*\*_</span></span>

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="151d1-139">Esecuzione di pacchetti di dati spaziali di realtà mista con script complementare</span><span class="sxs-lookup"><span data-stu-id="151d1-139">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="151d1-140">È stato fornito MRSpatialPackagerHelperScript.ps1 che esegue gli strumenti della mappa.</span><span class="sxs-lookup"><span data-stu-id="151d1-140">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="151d1-141">I parametri dello script sono definiti di seguito:</span><span class="sxs-lookup"><span data-stu-id="151d1-141">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="151d1-142">Esempio di utilizzo e output di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="151d1-142">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="151d1-143">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName Administrator-mode Export-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="151d1-143">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="151d1-144">Come esportare usando MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="151d1-144">How to Export using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="151d1-145">L'esportazione delle mappe dal dispositivo genera due file MapX, het. MapX e sa. MapX.</span><span class="sxs-lookup"><span data-stu-id="151d1-145">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="151d1-146">Durante il processo di esportazione tutti gli ancoraggi spaziali vengono rimossi tranne l'app specificata e il limite creato dall'utente (se esistente).</span><span class="sxs-lookup"><span data-stu-id="151d1-146">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="151d1-147">Il nome della famiglia di pacchetti di origine deve corrispondere a un'app installata esistente o il file exe non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="151d1-147">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="151d1-148">Come importare utilizzando MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="151d1-148">How to Import using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="151d1-149">L'importazione Elimina i dati spaziali esistenti e li sostituisce con i dati della directory specificata.</span><span class="sxs-lookup"><span data-stu-id="151d1-149">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="151d1-150">L'input del nome dell'app specifica il nome del pacchetto dell'app di destinazione per cui devono essere importati gli ancoraggi spaziali e il SID utente di destinazione specifica l'utente che deve avere accesso agli ancoraggi spaziali importati.</span><span class="sxs-lookup"><span data-stu-id="151d1-150">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="151d1-151">Il nome della famiglia di pacchetti di destinazione e i SID utente devono corrispondere ai valori esistenti nel PC oppure il file exe avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="151d1-151">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


<span data-ttu-id="151d1-152">_\*\*</span><span class="sxs-lookup"><span data-stu-id="151d1-152">_\*\*</span></span>
## <a name="error-messages"></a><span data-ttu-id="151d1-153">messaggi di errore</span><span class="sxs-lookup"><span data-stu-id="151d1-153">Error Messages</span></span>
<span data-ttu-id="151d1-154">Inoltre, i messaggi di errore che seguono gli errori saranno associati a un HRESULT</span><span class="sxs-lookup"><span data-stu-id="151d1-154">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="151d1-155">Se si è verificato un errore di argomenti non validi</span><span class="sxs-lookup"><span data-stu-id="151d1-155">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="151d1-156">Se il file eseguibile non è stato eseguito in modalità amministratore</span><span class="sxs-lookup"><span data-stu-id="151d1-156">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="151d1-157">Se si è verificato un errore durante l'abilitazione o la disabilitazione del driver</span><span class="sxs-lookup"><span data-stu-id="151d1-157">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="151d1-158">Se si è verificato un errore durante la convalida della versione del database spaziale</span><span class="sxs-lookup"><span data-stu-id="151d1-158">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="151d1-159">Se si è verificato un errore durante la convalida del nome della famiglia di pacchetti fornito per l'app di importazione/esportazione di destinazione</span><span class="sxs-lookup"><span data-stu-id="151d1-159">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="151d1-160">Se si è verificato un errore durante la convalida del SID utente</span><span class="sxs-lookup"><span data-stu-id="151d1-160">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="151d1-161">Se si è verificato un errore relativo ai file di dati spaziali di origine o di destinazione</span><span class="sxs-lookup"><span data-stu-id="151d1-161">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="151d1-162">Se si è verificato un errore relativo all'avvio e all'arresto dello spettro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="151d1-162">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```