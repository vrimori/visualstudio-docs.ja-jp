---
title: BasicType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fb6000da7ab5d9ff17f78cacf87608432b839e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030935"
---
# <a name="basictype"></a>BasicType
シンボルの基本的な型を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum BasicType {   
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
   btHresult  = 31,  
   btChar16   = 32,  // char16_t
   btChar32   = 33,  // char32_t
};  
```  
  
## <a name="elements"></a>Elements  
 btNoType  
 基本的な型が指定されていません。  
  
 btVoid  
 基本的な型は、`void`します。  
  
 btChar  
 基本的な型は、 `char` (C と C++ の型)。  
  
 btWChar  
 基本的な型は、ワイド (Unicode) 文字 (`WCHAR`)。  
  
 btInt  
 基本的な型が`signed int`(C と C++ の型)。  
  
 btUInt  
 基本的な型が`unsigned int`(C と C++ の型)。  
  
 btFloat  
 基本的な型は、浮動小数点数 (`FLOAT`)。  
  
 btBCD  
 基本的な型がバイナリ コード化された 10 進数 (`BCD`)。  
  
 btBool  
 基本的な型がブール (`BOOL`)。  
  
 btLong  
 基本的な型は、 `long int` (C と C++ の型)。  
  
 btULong  
 基本的な型は、 `unsigned long int` (C と C++ の型)。  
  
 btCurrency  
 基本的な型は、通貨です。  
  
 btDate  
 基本的な型は日付/時刻 (`DATE`)。  
  
 btVariant  
 基本的な型が変数の型の構造 (`VARIANT`)。  
  
 btComplex  
 基本的な型は、複雑な数値です。  
  
 btBit  
 基本的な型は、少しです。  
  
 btBSTR  
 基本的な型が基本またはバイナリ文字列 (`BSTR`)。  
  
 btHresult  
 基本的な型は、`HRESULT`します。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値がによって返される、 [idiasymbol::get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
