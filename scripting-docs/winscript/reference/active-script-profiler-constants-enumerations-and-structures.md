---
title: "アクティブ スクリプト プロファイラーの定数、列挙型、および構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# アクティブ スクリプト プロファイラーの定数、列挙型、および構造体
次の列挙型は、アクティブ スクリプトのプロファイラーのインターフェイスで使用されます。  
  
## 定数、列挙型、および構造体  
  
|定数|説明|  
|--------|--------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 型](../../winscript/reference/profiler-external-object-address-type.md)|プロファイラーの外部オブジェクトのアドレス。  [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) および [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md) で使用されます。|  
|[PROFILER\_HEAP\_OBJECT\_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ オブジェクトの ID。  [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)、[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)、および [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md) で使用されます。|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)|ヒープ オブジェクトの名前の ID。  [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) で使用されます。|  
  
|列挙型|説明|  
|---------|--------|  
|[PROFILER\_EVENT\_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)|プロファイルが必要なイベントの種類を示します。|  
|[PROFILER\_HEAP\_ENUM\_FLAGS 列挙型](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|オブジェクト リレーションシップ内でヒープ オブジェクトが指すものに関する補足情報を、公開するかどうかを表すフラグです。  [IActiveScriptProfilerControl5::EnumHeap2 メソッド](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) で使用されます。|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS 列挙型](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|ヒープ オブジェクトの基本情報を表すフラグ。  [PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md) で使用されます。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE 列挙型](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|別の種類のオプション情報を表します。  [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md) で使用されます。|  
|[PROFILER\_RELATIONSHIP\_INFO 列挙型](../../winscript/reference/profiler-relationship-info-enumeration.md)|リレーションシップのオブジェクトに関する情報を表します。  [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md) で使用されます。|  
|[PROFILER\_SCRIPT\_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)|スクリプトの種類を指定します。|  
  
|構造体|説明|  
|---------|--------|  
|[PROFILER\_HEAP\_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)|[IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) によって収集されたヒープ オブジェクトを表します。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|ヒープ オブジェクトに関するオプション情報を表します。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)|ヒープ オブジェクトのリレーションシップを表します。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトに属するリレーションシップの一覧を表します。|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|この構造体は、関数オブジェクトにだけ関連付けられます。  スコープの一覧は、各スコープがそれぞれ特定のスコープ内の変数を表す関連プロパティの一覧を持つヒープ オブジェクトであるスコープの一覧として関数のクロージャを表します。  場合によっては、そのスコープ内のオブジェクトの名前は使用できないことがあります。|  
  
## 参照  
 [アクティブ スクリプト プロファイラーのインターフェイス](../../winscript/reference/active-script-profiler-interfaces.md)