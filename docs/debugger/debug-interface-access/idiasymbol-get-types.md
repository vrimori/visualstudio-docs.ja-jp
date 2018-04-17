---
title: Idiasymbol::get_types |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7340e7b0c3512c8a453dc9af8cc9915235a425be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
このシンボルにコンパイラに固有の型の配列を取得します。  
  
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
 [out]記述された、型の数を返しますまたはの場合、`types`パラメーターは`NULL`、使用可能な型の合計数、します。  
  
 `types[]`  
 [out]格納するのには配列を[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)このシンボルのすべての型を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)