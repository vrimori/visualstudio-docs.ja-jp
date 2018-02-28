---
title: "Idiasymbol::get_typeids |Microsoft ドキュメント"
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
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b186c9f2f8b3ad49808669c1fd04b1fdefe3b82d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
このシンボルにコンパイラ固有の型識別子の値の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cTypeIds`  
 [in]データを保持するバッファーのサイズ。  
  
 `pcTypeIds`  
 [out]数を返します`typeIds`書き込まれると、または、`typeIds`は`NULL`、し、型識別子が利用可能な数の合計。  
  
 `typeIds[]`  
 [out]型識別子を使用する入力となる配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)