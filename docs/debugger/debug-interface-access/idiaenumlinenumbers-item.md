---
title: Idiaenumlinenumbers::item |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f4e65e8b5ec336d403ae9ec3f8a2c67c63e874d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 [in]インデックス、 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)を取得するオブジェクト。 インデックスが範囲 0 `count`-1 で、ここで`count`によって返される、 [idiaenumlinenumbers::get_count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)メソッドです。  
  
 lineNumber  
 [out]返します、 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)目的の行番号を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)