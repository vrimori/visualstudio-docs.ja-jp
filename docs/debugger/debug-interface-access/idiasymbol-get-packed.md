---
title: Idiasymbol::get_packed |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 088d9e5df0f7bf31526a5c4e7364dff235988f77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
ユーザー定義データ型 (UDT) がパックされているかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`; UDT がパックされる場合を返しますそれ以外の場合、`FALSE`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティが、シンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 メモリ境界に整列する中間の埋め込みはなしで、UDT のすべてのメンバーは、できるだけ近い配置されていることを意味をパックします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)