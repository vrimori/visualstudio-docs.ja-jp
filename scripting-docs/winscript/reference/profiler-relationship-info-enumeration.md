---
title: "PROFILER_RELATIONSHIP_INFO 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO 列挙型
リレーションシップのオブジェクトに関する情報を表します。  [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md) で使用されます。  
  
## 構文  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|オブジェクトは、数値です。|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|オブジェクトは文字列です。|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|オブジェクトは、ヒープ上のオブジェクトです。|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|オブジェクトは、ガベージ コレクション ヒープで外部つまり、ありません。|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|オブジェクトは、BSTR です。|