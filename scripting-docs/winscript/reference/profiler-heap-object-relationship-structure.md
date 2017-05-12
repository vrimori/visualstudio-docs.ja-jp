---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体
ヒープ内のオブジェクトの関係を表します。  
  
## 構文  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)|[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)のリレーションシップ名の ID。|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO 列挙型](../../winscript/reference/profiler-relationship-info-enumeration.md)|リレーションシップに関する情報。|  
|numberValue|double|数値。  `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` の 1 ビットのみが `relationshipInfo` の値に基づいて、設定されます。|  
|stringValue|LPCWSTR|オブジェクトに格納されている文字列を返します。|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ内のオブジェクトの ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 型](../../winscript/reference/profiler-external-object-address-type.md)|外部オブジェクトのアドレス。|