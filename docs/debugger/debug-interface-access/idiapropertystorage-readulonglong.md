---
title: IDiaPropertyStorage::ReadULONGLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dea61b14cdee1ac260e4a21db0056abbdcad74f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977383"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
読み取り`ULONGLONG`プロパティ セット内の値。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 [in]読み取るプロパティの識別子 (`PROPID`として WTypes.h で定義されている、 `ULONG`)。  
  
 `pValue`  
 [out]プロパティ値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。 返します`E_INVALIDARG`型のプロパティがない場合`ULONGLONG`します。  
  
## <a name="remarks"></a>コメント  
 A `ULONGLONG` 64 ビット符号なし整数としての Windows によって定義されます。  
  
## <a name="see-also"></a>「  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)