---
title: PROFILER_HEAP_ENUM_FLAGS 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c711dd3a4174f38bf2f3b3e163805e6cfa1c314
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091833"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS 列挙型
オブジェクト リレーションシップ内でヒープ オブジェクトが指すものに関する補足情報を、公開するかどうかを表すフラグです。 使用される、 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|[値]|説明|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|このヒープ オブジェクトはオブジェクト リレーションシップに関する補足情報を公開しません。 このヒープ オブジェクトの動作と同じ方法で[iactivescriptprofilercontrol 3::heapenum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)します。|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|このヒープ オブジェクトは、オブジェクト リレーションシップ内でオブジェクトが指しているものが、Getter または Setter メソッドであるかどうかの情報を公開します。 この情報は、の上位 2 バイト (16 ビット) に格納されますが、 [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md)フィールドの 1 つとして、 [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md)列挙値。|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|このヒープ オブジェクトは、部分文字列を正しく表示するために使用します。|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &AMP;#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|このヒープ オブジェクトは、部分文字列を正しく表示するために使用します。|