---
title: IDiaPropertyStorage::ReadBOOL |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 702a5c9f4558ad657c6a571b45298d62b011fb00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
読み取り`BOOL`プロパティ セット内の値。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 [in]読み込まれるプロパティの識別子 (`PROPID`として WTypes.h で定義された、 `ULONG`)。  
  
 `pValue`  
 [out]プロパティ値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。 返します`E_INVALIDARG`場合は、プロパティの型ではありません`BOOL`です。  
  
## <a name="remarks"></a>コメント  
 一貫性のある結果を得るには、次のように解釈します。、`BOOL`値の 0 以外の値が実行されるように`TRUE`0 で、`FALSE`です。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)