---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列挙型
オプション情報の種類を表します。  [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) で使用されます。  
  
## 構文  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## メンバー  
  
|メンバー|価値|説明|  
|----------|--------|--------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_PROTOTYPE|0x00000001|ヒープ内のオブジェクトのプロトタイプに関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_FUNCTION\_NAME|0x00000002|ヒープ内のオブジェクトの関数名に関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_SCOPE\_LIST|0x00000003|ヒープ内のオブジェクトの [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)に関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_INTERNAL\_PROPERTY|0x00000004|ヒープ内のオブジェクトの内部プロパティに関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_NAME\_PROPERTIES|0x00000005|ヒープのオブジェクト名のプロパティに関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_INDEX\_PROPERTIES|0x00000006|ヒープ内のオブジェクトのインデックスのプロパティに関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_ELEMENT\_ATTRIBUTES\_SIZE|0x00000007|DOM 要素に関連付けられた属性のサイズ。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|DOM 要素に関連付けられているテキストのサイズ。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_RELATIONSHIPS|0x00000009|ヒープ内のオブジェクトの関係について説明します。|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_WINRTEVENTS|0x0000000A|ヒープ内のオブジェクトの Windows のランタイム イベントに関する情報。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_WINRTEVENTS|この列挙体の最大値。|