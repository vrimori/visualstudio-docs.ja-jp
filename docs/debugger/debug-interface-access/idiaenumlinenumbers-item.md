---
title: Idiaenumlinenumbers::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4733756a8de69348623049d3ae4997847eb32bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925566"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
インデックスを使用して、行番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックス、 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)を取得するオブジェクト。 インデックスは 0 ~ の範囲内で、 `count`-1 の場合、`count`によって返される、 [idiaenumlinenumbers::get_count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)メソッド。  
  
 lineNumber  
 [out]返します、 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)目的の行番号を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)