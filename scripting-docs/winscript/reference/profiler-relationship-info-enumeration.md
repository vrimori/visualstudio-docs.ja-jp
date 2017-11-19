---
title: "PROFILER_RELATIONSHIP_INFO 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO 列挙型
リレーションシップのオブジェクトに関する情報を表します。 使用される[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|オブジェクトは、番号です。|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|オブジェクトは、文字列です。|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|オブジェクトは、ヒープ オブジェクトです。|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|オブジェクトは外部では、ガベージ コレクション ヒープにします。|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|オブジェクトは BSTR です。|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|オブジェクトは、部分文字列です。|