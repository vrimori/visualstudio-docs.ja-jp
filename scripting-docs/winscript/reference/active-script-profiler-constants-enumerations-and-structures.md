---
title: アクティブ スクリプト Profiler の定数、列挙型および構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d367374e4402da2d30cd8a855a509299363f882
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349128"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>アクティブ スクリプト プロファイラーの定数、列挙型、および構造体
次の列挙型は、アクティブ スクリプトのプロファイラーのインターフェイスで使用されます。  
  
## <a name="constants-enumerations-and-structures"></a>定数、列挙型、および構造体  
  
|定数|説明|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 型](../../winscript/reference/profiler-external-object-address-type.md)|プロファイラーの外部オブジェクトのアドレス。 使用される[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)と[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)します。|  
|[PROFILER_HEAP_OBJECT_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ オブジェクトの ID。 使用される[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)、 [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)、および[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)します。|  
|[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)|ヒープ オブジェクトの名前の ID。 使用される[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)します。|  
  
|列挙|説明|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)|プロファイルが必要なイベントの種類を示します。|  
|[PROFILER_HEAP_ENUM_FLAGS 列挙型](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|オブジェクト リレーションシップ内でヒープ オブジェクトが指すものに関する補足情報を、公開するかどうかを表すフラグです。 使用される、 [iactivescriptprofilercontrol 5::enumheap2 メソッド](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)します。|  
|[PROFILER_HEAP_OBJECT_FLAGS 列挙型](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|ヒープ オブジェクトの基本情報を表すフラグ。 使用される、 [PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)します。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列挙型](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|別の種類のオプション情報を表します。 使用される[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)します。|  
|[PROFILER_RELATIONSHIP_INFO 列挙型](../../winscript/reference/profiler-relationship-info-enumeration.md)|リレーションシップのオブジェクトに関する情報を表します。 使用される[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)します。|  
|[PROFILER_SCRIPT_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)|スクリプトの種類を指定します。|  
  
|構造体|説明|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)|によって収集されたヒープのオブジェクトを表します[iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)します。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|ヒープ オブジェクトに関するオプション情報を表します。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)|ヒープ オブジェクトのリレーションシップを表します。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトに属するリレーションシップの一覧を表します。|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|この構造体は、関数オブジェクトにだけ関連付けられます。 スコープの一覧は、各スコープがそれぞれ特定のスコープ内の変数を表す関連プロパティの一覧を持つヒープ オブジェクトであるスコープの一覧として関数のクロージャを表します。 場合によっては、そのスコープ内のオブジェクトの名前は使用できないことがあります。|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 構造体](../../winscript/reference/profiler-property-type-substring-info-structure.md)|部分文字列の種類に関する情報を表します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)