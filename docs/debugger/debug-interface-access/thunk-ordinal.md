---
title: THUNK_ORDINAL |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 7e139bceb9456e792ddf10d00d8b519a7677cc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834062"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
サンクの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
typedef enum THUNK_ORDINAL {   
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
 標準のサンクします。  
  
 THUNK_ORDINAL_ADJUSTOR  
 A`this`サンクの調整権限を保持します。  
  
 THUNK_ORDINAL_VCALL  
 仮想呼び出しサンクします。  
  
 THUNK_ORDINAL_PCODE  
 P コード サンクします。  
  
 THUNK_ORDINAL_LOAD  
 遅延読み込みのサンクします。  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 増分トランポリン サンクが (1 つのメモリ領域からの呼び出しを間跳ねるトランポリン サンクが使用されます)。  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 分岐ポイント トランポリン サンクします。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値が呼び出しから返される、 [idiasymbol::get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>「  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)