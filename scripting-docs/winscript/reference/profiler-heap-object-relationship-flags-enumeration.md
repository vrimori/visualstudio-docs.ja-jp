---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列挙型
オブジェクト リレーションシップ内でこのヒープ オブジェクトが指しているものが、Getter または Setter メソッドであることを表すフラグです。  PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS の値が `enumFlags` パラメーターで指定されている場合に [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) メソッドで使用されます。  
  
## 構文  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|オブジェクト リレーションシップ内でこのヒープ オブジェクトが指しているものは、Getter メソッド、Setter メソッドのいずれとしても認識されません。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|オブジェクト リレーションシップ内でヒープ オブジェクトは Getter メソッドを指しています。  この情報は、[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) フィールドの上位 2 バイト \(16 ビット\) に格納されます。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|オブジェクト リレーションシップ内でヒープ オブジェクトは Setter メソッドを指しています。  この情報は、`PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` フィールドの上位 2 バイト \(16 ビット\) に格納されます。|