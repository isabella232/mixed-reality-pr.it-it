---
title: MaterialInstance
description: Documentazione sull'istanza del materiale e sui relativi usi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MaterialInstance,
ms.openlocfilehash: 27f411b13e796c99b0b881bdf46c5825dd985a01
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691328"
---
# <a name="material-instance"></a><span data-ttu-id="4fbf3-104">Istanza del materiale</span><span class="sxs-lookup"><span data-stu-id="4fbf3-104">Material instance</span></span>

<span data-ttu-id="4fbf3-105">Gli [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) assistenti di comportamento nel rilevamento della durata del materiale dell'istanza ed eliminano automaticamente i materiali di istanza per l'utente.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="4fbf3-106">Questo componente utilità può essere utilizzato come sostituzione di [renderer. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [renderer. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html).</span><span class="sxs-lookup"><span data-stu-id="4fbf3-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html).</span></span>

> [!NOTE]
> <span data-ttu-id="4fbf3-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) sono preferiti rispetto alle istanze del materiale ma non sono sempre disponibili in tutti gli scenari.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="4fbf3-108">Perché è possibile utilizzare [renderer. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ?</span><span class="sxs-lookup"><span data-stu-id="4fbf3-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="4fbf3-109">Se si aggiunge il codice seguente a una scena Unity e l'utilizzo della memoria di hit Play continuerà ad arrampicarsi:</span><span class="sxs-lookup"><span data-stu-id="4fbf3-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="4fbf3-110">Il comportamento della perdita precedente **arresterà l'arresto anomalo di Unity se viene** eseguito per troppo tempo.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="4fbf3-111">In alternativa, provare a usare il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento:</span><span class="sxs-lookup"><span data-stu-id="4fbf3-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="4fbf3-112">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="4fbf3-112">Usage</span></span>

<span data-ttu-id="4fbf3-113">Quando si richiama il [renderer. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html)di Unity, Unity crea automaticamente un'istanza di nuovi materiali.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="4fbf3-114">È responsabilità del chiamante eliminare i materiali quando un materiale non è più necessario o l'oggetto gioco viene eliminato definitivamente.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="4fbf3-115">Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di evitare perdite di materiale e di mantenere coerenti i percorsi di allocazione del materiale durante la modifica e la fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="4fbf3-116">Quando non è possibile usare un [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) e un materiale deve essere sottoposto a un'istanza, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) può essere usato come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="4fbf3-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="4fbf3-117">Se più oggetti richiedono la proprietà dell'istanza del materiale, è preferibile assumere la proprietà esplicita per il rilevamento dei riferimenti.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="4fbf3-118">(Esiste un'interfaccia facoltativa denominata [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) Exists per aide con proprietà). Di seguito è riportato un esempio di utilizzo:</span><span class="sxs-lookup"><span data-stu-id="4fbf3-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="4fbf3-119">Per ulteriori informazioni, vedere l'esempio di utilizzo illustrato nel [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.</span><span class="sxs-lookup"><span data-stu-id="4fbf3-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fbf3-120">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4fbf3-120">See also</span></span>

* [<span data-ttu-id="4fbf3-121">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="4fbf3-121">MRTK Standard Shader</span></span>](MRTKStandardShader.md)
