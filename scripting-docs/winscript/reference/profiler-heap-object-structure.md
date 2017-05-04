---
title: "PROFILER_HEAP_OBJECT 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT 構造体
[IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)によって収集されたヒープにオブジェクトを表します。  
  
## 構文  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## メンバー  
  
|メンバー|型|説明|  
|----------|-------|--------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ内のオブジェクトの ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 型](../../winscript/reference/profiler-external-object-address-type.md)|C\+\+.などのオブジェクトの外部オブジェクトのアドレスは、JavaScript ヒープの外部にあるオブジェクトを C\+\+ 代入します。|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)|[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)から取得されたヒープ内のオブジェクトの種類名の ID。  `externalObjectAddress` か `typeName` の 1 ビットのみが `flags` の値です。|  
|フラグ|[PROFILER\_HEAP\_OBJECT\_FLAGS 列挙型](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|ヒープのオブジェクトについての基本情報を含むフラグ。|  
|optionalInfoCount|USHORT|ヒープのオブジェクトで使用できる [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) のレコードの数。|