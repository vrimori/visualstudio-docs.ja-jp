---
title: "IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド
指定 [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) の構造と [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) の関連する要素を解放します。  
  
## 構文  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### パラメーター  
 `celt`  
 空きオブジェクトの数。  
  
 `heapObjects`  
 [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) 構造体の配列。  
  
## 戻り値  
 HRESULT。