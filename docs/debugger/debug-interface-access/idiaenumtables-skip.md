---
title: Idiaenumtables::skip |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2aadb5570b49c28502f837492657e5301b80616e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
列挙のシーケンス内のテーブルの指定した数をスキップします。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする列挙のシーケンス内のテーブルの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`ありませんをスキップするテーブルがある場合。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)