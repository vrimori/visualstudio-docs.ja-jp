---
title: PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 5f873cdf2ebd394e48c1513135f1acdcd700c283
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345644"
---
# <a name="profilerpropertytypesubstringinfo-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 構造体
リレーションシップで使用する部分文字列の種類に関する情報を表します。 使用される[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|長さ|UINT|オブジェクトは、UINT です。|  
|値|LPCWSTR|オブジェクトを LPCWSTR です。|