---
title: "IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::GetNameIdMap
[PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md) の値に対応する文字列の名前を返します。  
  
## 構文  
  
```  
HRESULT GetNameIdMap (  
    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],   
    [out] UINT *pcelt);  
```  
  
#### パラメーター  
 `pNameList`  
 \[入力\] [PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md) の値に関連付けられた名前の配列。  
  
 `pcelt`  
 \[入力\]配列の名前の数。  
  
## 戻り値  
 HRESULT。