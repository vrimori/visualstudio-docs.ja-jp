---
title: "PROFILER_HEAP_ENUM_FLAGS 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS 列挙型
オブジェクト リレーションシップ内でヒープ オブジェクトが指すものに関する補足情報を、公開するかどうかを表すフラグです。 使用される、 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|このヒープ オブジェクトはオブジェクト リレーションシップに関する補足情報を公開しません。 このヒープ オブジェクトの動作と同じ方法で[iactivescriptprofilercontrol 3::heapenum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)です。|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|このヒープ オブジェクトは、オブジェクト リレーションシップ内でオブジェクトが指しているものが、Getter または Setter メソッドであるかどうかの情報を公開します。 この情報は、の上位 2 バイト (16 ビット) に格納されます、 [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md)フィールドの 1 つとして、 [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md)列挙型値。|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|このヒープ オブジェクトは、部分文字列が正しく表示に使用されます。|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124;です。PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|このヒープ オブジェクトは、部分文字列が正しく表示に使用されます。|