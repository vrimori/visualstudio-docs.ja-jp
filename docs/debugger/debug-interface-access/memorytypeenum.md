---
title: MemoryTypeEnum |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 616bae99a4cb3ffafa4cdf773bce63576ed04e7a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
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
 アクセスは、メモリのみをスタックします。  
  
 `MemTypeAny`  
 任意の種類のメモリにアクセスします。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値に渡され、 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)にさまざまな種類のメモリへのアクセスを制限する方法です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)