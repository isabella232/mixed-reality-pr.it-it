---
title: MaterialInstance
description: Documentazione sull'istanza del materiale e sui relativi usi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MaterialInstance,
ms.openlocfilehash: f804c62ac3655fbe754f4f268dd14d46497e4b51
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782263"
---
# <a name="material-instance"></a>Istanza del materiale

Gli [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) assistenti di comportamento nel rilevamento della durata del materiale dell'istanza ed eliminano automaticamente i materiali di istanza per l'utente. Questo componente utilità può essere utilizzato come sostituzione di [renderer. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) o [renderer. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html).

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) sono preferiti rispetto alle istanze del materiale ma non sono sempre disponibili in tutti gli scenari.

Perché è possibile utilizzare [renderer. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ? Se si aggiunge il codice seguente a una scena Unity e l'utilizzo della memoria di hit Play continuerà ad arrampicarsi:

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
> Il comportamento della perdita precedente **arresterà l'arresto anomalo di Unity se viene** eseguito per troppo tempo.

In alternativa, provare a usare il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento:

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

Quando si richiama il [renderer. Materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html)di Unity, Unity crea automaticamente un'istanza di nuovi materiali. È responsabilità del chiamante eliminare i materiali quando un materiale non è più necessario o l'oggetto gioco viene eliminato definitivamente. Il [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportamento consente di evitare perdite di materiale e di mantenere coerenti i percorsi di allocazione del materiale durante la modifica e la fase di esecuzione.

Quando non è possibile usare un [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) e un materiale deve essere sottoposto a un'istanza, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) può essere usato come indicato di seguito:

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

Se più oggetti richiedono la proprietà dell'istanza del materiale, è preferibile assumere la proprietà esplicita per il rilevamento dei riferimenti. (Esiste un'interfaccia facoltativa denominata [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) Exists per aide con proprietà). Di seguito è riportato un esempio di utilizzo:

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

Per ulteriori informazioni, vedere l'esempio di utilizzo illustrato nel [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamento.

## <a name="see-also"></a>Vedi anche

* [Shader standard MRTK](MRTKStandardShader.md)
