---
title: "IActiveScriptProfilerHeapEnum インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum インターフェイス
[IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)で収集されたスクリプト エンジンに関連付けられているヒープ上のオブジェクトの反復子。  
  
## 構文  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## メソッド  
 [IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 [IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)によって収集されたヒープのオブジェクトのセットで次のオブジェクトを取得します。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 [IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)によって収集されたヒープのオブジェクトのセットの指定したオブジェクトの情報を取得します。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 指定 [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) の構造と [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) の関連する要素を解放します。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 [PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md) の値に対応する文字列の名前を返します。