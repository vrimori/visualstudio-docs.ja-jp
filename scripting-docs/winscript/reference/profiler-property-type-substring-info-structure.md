---
title: "PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 構造 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: ba7c0c865ae875d22fa82e48557eb2ed8b170e65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilerpropertytypesubstringinfo-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 構造体
リレーションシップで使用される部分文字列の種類に関する情報を表します。 使用される[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|長さ|UINT|オブジェクトは、UINT です。|  
|値|LPCWSTR|オブジェクトは、LPCWSTR です。|