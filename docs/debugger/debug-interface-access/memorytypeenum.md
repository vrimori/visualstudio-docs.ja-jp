---
title: MemoryTypeEnum |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a83a37a3aa454885d714be667ca7678ae543ff09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875917"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
アクセスするメモリの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 `MemTypeCode`  
 アクセスには、メモリがコードのみです。  
  
 `MemTypeData`  
 アクセスのデータまたはスタックのメモリ。  
  
 `MemTypeStack`  
 アクセスにはスタック メモリのみ。  
  
 `MemTypeAny`  
 任意の種類のメモリにアクセスします。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値を渡す、 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)にさまざまな種類のメモリへのアクセスを制限する方法。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>「  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)