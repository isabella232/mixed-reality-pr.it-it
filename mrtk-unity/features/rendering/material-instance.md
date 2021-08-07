---
title: Istanza material
description: Documentazione sull'istanza material e i relativi usi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MaterialInstance,
ms.openlocfilehash: 6d9a2a35a009bfce1fcfae15000ea02c47be637a8c5a483254ea30d9948922e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210051"
---
# <a name="material-instance"></a>Istanza material

Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di tenere traccia della durata del materiale dell'istanza e di eliminare automaticamente i materiali di istanza per l'utente. Questo componente dell'utilità può essere usato come sostituzione di [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [Renderer.materials.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)

> [!NOTE]
> [Gli oggetti MaterialPropertyBlock sono](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) preferibili rispetto alle istanze dei materiali, ma non sono sempre disponibili in tutti gli scenari.

Perché [l'uso di Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) può essere un problema? Se si aggiunge il codice seguente a una scena Unity e si preme l'utilizzo della memoria di riproduzione, l'uso della memoria continuerà a essere molto familiare:

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
> Il comportamento di perdita precedente **arresterà in modo** anomalo Unity se eseguito per troppo tempo.

In alternativa, provare a usare il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento :

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

## <a name="usage"></a>Utilizzo

Quando si richiama [renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)di Unity, Unity crea automaticamente un'istanza di nuovi materiali. È responsabilità del chiamante eliminare i materiali quando un materiale non è più necessario o l'oggetto gioco viene eliminato. Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di evitare perdite di materiale e mantiene coerenti i percorsi di allocazione dei materiali durante la modifica e la fase di esecuzione.

Quando non [è possibile usare MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) e è necessario creare istanze di un materiale, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) è possibile usare come indicato di seguito:

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

Se più oggetti necessitano della proprietà dell'istanza material, è meglio assumere la proprietà esplicita per il rilevamento dei riferimenti. Esiste un'interfaccia [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) facoltativa denominata per il controllo della proprietà. Di seguito è riportato un esempio di utilizzo:

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

Per altre informazioni, vedere l'esempio di utilizzo illustrato all'interno del [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.

## <a name="see-also"></a>Vedi anche

* [MRTK Standard Shader](mrtk-standard-shader.md)
