---
title: THUNK_ORDINAL |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf4a6f96eda9a44e10975ffc1a8262030180b302
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534687"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[THUNK_ORDINAL](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/thunk-ordinal)します。  
  
サンクの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="remarks"></a>Remarks  
 この列挙体の値が呼び出しから返される、 [idiasymbol::get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)



