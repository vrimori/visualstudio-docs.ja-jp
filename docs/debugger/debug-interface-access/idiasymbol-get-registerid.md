---
title: Idiasymbol::get_registerid |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 0acc6d79e1e5da810e2f2da699df5d4def424df9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861469"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
場所のレジスタの指定子を取得するときに、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsEnregistered`します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]場所のレジスタの指定子を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>Remarks  
 記号がつまりがレジスタを基準とした場合、場合、シンボルの[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsRegRel`を使用して、`get_registerId`メソッドへの呼び出しに続けて、 [idiasymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)記号が配置されているレジスタからのオフセットを取得するメソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)