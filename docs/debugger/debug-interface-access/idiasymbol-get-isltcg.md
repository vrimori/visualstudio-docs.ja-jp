---
title: Idiasymbol::get_isltcg |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7eb1d7308eb03d396ca8a08f915a294ec1debd82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877739"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
指定するフラグを取得するかどうか、[コンパイル単位](../../debugger/debug-interface-access/compiland.md)リンカー スイッチにリンクされている[/LTCG (リンク時コード生成)](/cpp/build/reference/ltcg-link-time-code-generation)、プログラム全体の最適化を支援します。 このスイッチは、マネージ コードにのみ適用されます。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pFlag  
 [out]返します`TRUE`場合、 `compiland` /LTCG リンカー スイッチを使用してリンクされました。 それ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)