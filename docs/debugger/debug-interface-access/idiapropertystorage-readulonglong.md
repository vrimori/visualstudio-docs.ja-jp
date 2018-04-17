---
title: IDiaPropertyStorage::ReadULONGLONG |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9235cc627ca63e97944f9346c87be7b4942e0dd6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 [in]読み込まれるプロパティの識別子 (`PROPID`として WTypes.h で定義された、 `ULONG`)。  
  
 `pValue`  
 [out]プロパティ値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。 返します`E_INVALIDARG`場合は、プロパティの型ではありません`ULONGLONG`です。  
  
## <a name="remarks"></a>コメント  
 A `ULONGLONG` 64 ビット符号なし整数としての Windows によって定義されます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)