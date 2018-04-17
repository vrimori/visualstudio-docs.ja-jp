---
title: Idiasymbol::get_registerid |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ffbfb06336b19f9b7c9840e891eae9171d2c513
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
場所のレジスタ指定子を取得するときに、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsEnregistered`です。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]場所のレジスタ指定子を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティが、シンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 シンボルは、レジスタ、に対して相対的だ場合場合シンボルの[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsRegRel`を使用して、`get_registerId`メソッドへの呼び出しに続けて、 [idiasymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)シンボルが配置されているレジスタからのオフセットを取得するメソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)