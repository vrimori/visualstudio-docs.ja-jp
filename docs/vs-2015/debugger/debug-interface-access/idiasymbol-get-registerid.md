---
title: Idiasymbol::get_registerid |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c56467426840fe9bd9cbb62c77b6f0889126647
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537929"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiasymbol::get_registerid](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-registerid)します。  
  
場所のレジスタの指定子を取得するときに、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)に設定されている`LocIsEnregistered`します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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



