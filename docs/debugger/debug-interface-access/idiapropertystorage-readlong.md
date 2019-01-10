---
title: IDiaPropertyStorage::ReadLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aefa38870d3639b2277dd4af2c38d04b8fbb7c00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889979"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
読み取り`LONG`プロパティ セット内の値。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 [in]読み取るプロパティの識別子 (`PROPID`として WTypes.h で定義されている、 `ULONG`)。  
  
 `pValue`  
 [out]プロパティ値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。 返します`E_INVALIDARG`型のプロパティがない場合`LONG`します。  
  
## <a name="remarks"></a>コメント  
 A `LONG` 32 ビット符号付き整数としての Windows によって定義されます。  
  
## <a name="see-also"></a>「  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)