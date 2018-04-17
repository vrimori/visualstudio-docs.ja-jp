---
title: THUNK_ORDINAL |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c74d7d9f419a524ac7ef4c96d304c366f1a7c14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
サンクの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elements  
 THUNK_ORDINAL_NOTYPE  
 標準サンクはします。  
  
 THUNK_ORDINAL_ADJUSTOR  
 A`this`サンクを調整権限を保持します。  
  
 THUNK_ORDINAL_VCALL  
 仮想呼び出しサンクです。  
  
 THUNK_ORDINAL_PCODE  
 P コード サンクです。  
  
 THUNK_ORDINAL_LOAD  
 遅延読み込みサンクです。  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 増分トランポリン サンクを (別の呼び出しを 1 つのメモリ領域から跳ね返りますトランポリン サンクを使用します)。  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 ブランチ トランポリン サンクをポイントします。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値への呼び出しから返される、 [idiasymbol::get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)