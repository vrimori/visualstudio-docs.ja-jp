---
title: MemoryTypeEnum |Microsoft Docs
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
ms.openlocfilehash: 4a8dcf657933cf62f3f2173bb89dadd1366b0cec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822944"
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
  
## <a name="remarks"></a>Remarks  
 この列挙体の値を渡す、 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)にさまざまな種類のメモリへのアクセスを制限する方法。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)