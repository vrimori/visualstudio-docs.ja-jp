---
title: "Idiasymbol::get_types |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a6074e3f91595883d5b9c546b8cbd05974af34b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)