---
title: "PROFILER_HEAP_OBJECT_FLAGS 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96e05d67bedcf03c97edc1015c80b212b6021562
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS 列挙型
ヒープ オブジェクトの基本情報を表すフラグ。 使用される、 [PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|このヒープ オブジェクトは、前のヒープ列挙要求の後に割り当てられました。 [PROFILER_HEAP_OBJECT_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)オブジェクトが収集される場合は、値を再利用されることができます。|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|このヒープ オブジェクトは、オブジェクト グラフのルート オブジェクトです。|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|このヒープ オブジェクトは、閉じられたスクリプト サイトからです。|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|このヒープ オブジェクトは、JavaScript ガベージ コレクション ヒープ以外に割り当てられました。|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|このヒープ オブジェクトは、ガベージ コレクション ヒープと IUnknown の実装の外部に割り当てられました。|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|このヒープ オブジェクトは、ガベージ コレクション ヒープ以外が割り当てられたを IDISPATCH インターフェイスを実装します。|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|このヒープ オブジェクトのサイズは概算です。|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|このヒープ オブジェクトのサイズは使用できません。|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|ヒープ オブジェクトは、Windows ランタイム インスタンスです。|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|ヒープ オブジェクトは、Windows ランタイム ランタイム クラスです。|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|ヒープ オブジェクトは、Windows ランタイム デリゲートです。|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|ヒープ オブジェクトは、Windows ランタイム名前空間にあります。|