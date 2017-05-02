---
title: "IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド
指定されたオブジェクトのオプション情報を取得します \([IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) から返されるヒープ オブジェクトのセットから\)。  
  
 返されたオブジェクトに割り当てられている返されたメモリを解放する必要はありません。  代わりに、[IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md) を呼び出します。  
  
## 構文  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### パラメーター  
 `heapObject`  
 情報を返す対象となる [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)。  
  
 `celt`  
 返される [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 構造体の数。  
  
 `optionalInfo`  
 \[出力\] 指定されたオブジェクトの [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 構造体の配列。  
  
## 戻り値  
 HRESULT。