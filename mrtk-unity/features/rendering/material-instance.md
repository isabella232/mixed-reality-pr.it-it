---
title: Istanza material
description: Documentazione sull'istanza material e i relativi usi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MaterialInstance,
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145209"
---
# <a name="material-instance"></a><span data-ttu-id="3ceab-104">Istanza material</span><span class="sxs-lookup"><span data-stu-id="3ceab-104">Material instance</span></span>

<span data-ttu-id="3ceab-105">Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di tenere traccia della durata del materiale dell'istanza e di eliminare automaticamente i materiali di istanza per l'utente.</span><span class="sxs-lookup"><span data-stu-id="3ceab-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="3ceab-106">Questo componente dell'utilità può essere usato come sostituzione di [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)</span><span class="sxs-lookup"><span data-stu-id="3ceab-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="3ceab-107">[Gli oggetti MaterialPropertyBlock sono](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) preferibili rispetto alle istanze di materiale, ma non sono sempre disponibili in tutti gli scenari.</span><span class="sxs-lookup"><span data-stu-id="3ceab-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="3ceab-108">Perché [l'uso di Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) può essere un problema?</span><span class="sxs-lookup"><span data-stu-id="3ceab-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="3ceab-109">Se si aggiunge il codice seguente a una scena Unity e si preme l'uso della memoria di riproduzione, l'uso della memoria continuerà a essere molto familiare:</span><span class="sxs-lookup"><span data-stu-id="3ceab-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

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
> <span data-ttu-id="3ceab-110">Il comportamento di perdita precedente **arresterà in modo** anomalo Unity se eseguito per troppo tempo.</span><span class="sxs-lookup"><span data-stu-id="3ceab-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="3ceab-111">In alternativa, provare a usare il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento :</span><span class="sxs-lookup"><span data-stu-id="3ceab-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

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

## <a name="usage"></a><span data-ttu-id="3ceab-112">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="3ceab-112">Usage</span></span>

<span data-ttu-id="3ceab-113">Quando si richiama [renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)di Unity, Unity crea automaticamente un'istanza di nuovi materiali.</span><span class="sxs-lookup"><span data-stu-id="3ceab-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="3ceab-114">È responsabilità del chiamante eliminare i materiali quando un materiale non è più necessario o l'oggetto gioco viene eliminato.</span><span class="sxs-lookup"><span data-stu-id="3ceab-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="3ceab-115">Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di evitare perdite di materiale e mantiene coerenti i percorsi di allocazione dei materiali durante la fase di modifica e di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="3ceab-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="3ceab-116">Quando non [è possibile usare MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) e è necessario creare istanze di un materiale, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) è possibile usare come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="3ceab-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

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

<span data-ttu-id="3ceab-117">Se più oggetti necessitano della proprietà dell'istanza material, è meglio assumere la proprietà esplicita per il rilevamento dei riferimenti.</span><span class="sxs-lookup"><span data-stu-id="3ceab-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="3ceab-118">Esiste un'interfaccia [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) facoltativa denominata per il controllo della proprietà. Di seguito è riportato un esempio di utilizzo:</span><span class="sxs-lookup"><span data-stu-id="3ceab-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

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

<span data-ttu-id="3ceab-119">Per altre informazioni, vedere l'esempio di utilizzo illustrato all'interno del [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.</span><span class="sxs-lookup"><span data-stu-id="3ceab-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ceab-120">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3ceab-120">See also</span></span>

* [<span data-ttu-id="3ceab-121">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="3ceab-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
