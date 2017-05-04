---
title: "PROFILER_HEAP_ENUM_FLAGS 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_ENUM_FLAGS 列挙型
オブジェクト リレーションシップ内でヒープ オブジェクトが指すものに関する補足情報を、公開するかどうかを表すフラグです。  [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) メソッドで使用されます。  
  
## 構文  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|このヒープ オブジェクトはオブジェクト リレーションシップに関する補足情報を公開しません。  このヒープ オブジェクトは、[IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) と同じように機能します。|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|このヒープ オブジェクトは、オブジェクト リレーションシップ内でオブジェクトが指しているものが、Getter または Setter メソッドであるかどうかの情報を公開します。  この情報は、[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) フィールドの上位 2 バイト \(16 ビット\) に [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) 列挙値の 1 つとして格納されます。|