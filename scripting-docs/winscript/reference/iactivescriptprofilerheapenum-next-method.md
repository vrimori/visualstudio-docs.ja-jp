---
title: "IActiveScriptProfilerHeapEnum::Next メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next メソッド
次のオブジェクトを取得またはヒープのセット オブジェクトは、[IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)から取得します。  
  
## 構文  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### パラメーター  
 `celt`  
 返されるオブジェクトの数。  
  
 `heapObjects`  
 \[入力\] [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) の次の構造。  
  
 `pceltFetched`  
 \[入力\]オブジェクトの数は、返された  
  
## 戻り値  
 HRESULT。