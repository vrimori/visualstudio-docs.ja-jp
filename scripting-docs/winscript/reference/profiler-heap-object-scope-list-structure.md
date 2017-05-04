---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体
この構造体は、関数オブジェクトだけに関連付けられます。  範囲のリストには、スコープは、の特定範囲の変数を表す関連するプロパティ リストを持つヒープのオブジェクトである範囲のリストとして関数の終了を表します。  場合によっては、その範囲オブジェクトの名前は使用できない場合があります。プロパティ リストへのインデックスのみ使用できます。  
  
## 構文  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## メンバー  
  
|メンバー|型|説明|  
|----------|-------|--------|  
|count|UINT|範囲の数|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|範囲の配列。|