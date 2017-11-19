---
title: "PROFILER_HEAP_OBJECT 構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT 構造体
によって収集されたヒープのオブジェクトを表す[iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ オブジェクトの ID。|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS 型](../../winscript/reference/profiler-external-object-address-type.md)|など、C++ に割り当てられたオブジェクトを JavaScript ヒープ以外は、オブジェクトの外部オブジェクトのアドレス。|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)|ヒープ オブジェクトの型名の ID から取得[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)です。 1 つのみ`externalObjectAddress`または`typeName`異なりますが、`flags`値。|  
|フラグ|[PROFILER_HEAP_OBJECT_FLAGS 列挙型](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|ヒープ オブジェクトに関する基本的な情報を格納するフラグ。|  
|optionalInfoCount|USHORT|数[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)ヒープ オブジェクトで利用可能なレコード。|