---
title: Idiasymbol::get_types |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcfde6e7824fa0df315cb843eedb92e4d249b618
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965147"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
このシンボルをコンパイラに固有の型の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cTypes`  
 [in]データを保持するバッファーのサイズ。  
  
 `pcTypes`  
 [out]記述された、型の数を返しますまたは、`types`パラメーターが`NULL`、利用可能なタイプの合計数、します。  
  
 `types[]`  
 [out]格納する配列、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)このシンボルのすべての型を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)