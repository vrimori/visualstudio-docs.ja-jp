---
title: PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d0159dd50d57aa77a62dc3b8536b50712b96df5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087140"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体
ヒープ オブジェクトに関するオプション情報を表します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|情報の種類|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列挙型](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|省略可能な情報の種類。|  
|プロトタイプ|[PROFILER_HEAP_OBJECT_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|ヒープ オブジェクトのプロトタイプ オブジェクトの ID。|  
|functionName|LPCWSTR|ヒープ オブジェクトの関数の名前。|  
|elementAttributesSize|UINT|ヒープ オブジェクトの要素の属性のサイズ。|  
|elementTextChildrenSize|UINT|ヒープ オブジェクトのテキストの子のサイズ。|  
|scopeList|[PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|ヒープ オブジェクトのスコープのリスト。|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)|ヒープ オブジェクトの内部プロパティです。|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトの名前のプロパティの一覧。|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトのインデックスのプロパティの一覧。|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトの関係の一覧。|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 構造体](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|ヒープ オブジェクトのイベントの一覧。|