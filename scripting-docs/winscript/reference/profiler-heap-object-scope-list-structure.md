---
title: PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 114b1a55fce34908c4274877583164aff4ec8dba
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344825"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST 構造体
この構造体は、関数オブジェクトにだけ関連付けられます。 スコープの一覧は、各スコープがそれぞれ特定のスコープ内の変数を表す関連プロパティの一覧を持つヒープ オブジェクトであるスコープの一覧として関数のクロージャを表します。 場合によっては、スコープが使用できないこと、内のオブジェクトとプロパティの一覧に、インデックスのみの名前は使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|count|UINT|スコープの数|  
|scopes|[PROFILER_HEAP_OBJECT_ID 型](../../winscript/reference/profiler-heap-object-id-type.md)|スコープの配列。|