---
title: PROFILER_RELATIONSHIP_INFO 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e95b11537873d3bfe02bf3fa793b61ace10938aa
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095811"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO 列挙型
リレーションシップのオブジェクトに関する情報を表します。 使用される[PROFILER_HEAP_OBJECT_RELATIONSHIP 構造体](../../winscript/reference/profiler-heap-object-relationship-structure.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|[値]|説明|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|オブジェクトは、数値です。|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|オブジェクトは、文字列です。|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|オブジェクトは、ヒープのオブジェクトです。|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|オブジェクトは外部では、ガベージ コレクション ヒープにします。|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|オブジェクトは、BSTR です。|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|オブジェクトは、部分文字列です。|