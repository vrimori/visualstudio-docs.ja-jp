---
title: "BasicType |Microsoft ドキュメント"
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
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 302e935c1b9f772735612e731503f84ccc3e468f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basictype"></a>BasicType
シンボルの基本的な型を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elements  
 btNoType  
 基本的な型が指定されていません。  
  
 btVoid  
 基本型は、`void`です。  
  
 btChar  
 基本型は、 `char` (C と C++ 型)。  
  
 btWChar  
 基本の種類はワイド (Unicode) 文字 (`WCHAR`)。  
  
 btInt  
 基本型は`signed int`(C と C++ 型)。  
  
 btUInt  
 基本型は`unsigned int`(C と C++ 型)。  
  
 btFloat  
 基本型は、浮動小数点数 (`FLOAT`)。  
  
 btBCD  
 基本型は、バイナリ コード化された 10 進数 (`BCD`)。  
  
 btBool  
 基本的な型がブール値 (`BOOL`)。  
  
 btLong  
 基本型は、 `long int` (C と C++ 型)。  
  
 btULong  
 基本型は、 `unsigned long int` (C と C++ 型)。  
  
 btCurrency  
 基本型は、通貨です。  
  
 btDate  
 基本型は日付/時刻 (`DATE`)。  
  
 btVariant  
 基本型は変数の型構造体 (`VARIANT`)。  
  
 btComplex  
 基本型は、複雑な番号です。  
  
 btBit  
 基本型は、ビットです。  
  
 btBSTR  
 基本的な型が基本またはバイナリ文字列 (`BSTR`)。  
  
 btHresult  
 基本型は、`HRESULT`です。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値が返された、 [idiasymbol::get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>参照  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)