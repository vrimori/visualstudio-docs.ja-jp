---
title: Idiaenumtables::next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27d9811fe55a3b942cd020ae8038f07df8bf7a2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949409"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
列挙体シーケンス内のテーブルの指定した数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得する列挙子内のテーブルの数。  
  
 `rgelt`  
 [out]格納する配列、 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)目的のテーブルを表すオブジェクト。  
  
 `pceltFetched`  
 [out]フェッチされた列挙子では、テーブルの数を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`ない複数のテーブルがある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)