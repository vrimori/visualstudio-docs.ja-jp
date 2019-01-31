---
title: LocationType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e844438f5262b6a218a5feb355e78fc8a2cd1da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005359"
---
# <a name="locationtype"></a>LocationType
シンボルの場所の情報の種類を示します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elements  
 `LocIsNull`  
 場所の情報は、ご利用いただけません。  
  
 `LocIsStatic`  
 場所は静的です。  
  
 `LocIsTLS`  
 場所は、スレッド ローカル ストレージにです。  
  
 `LocIsRegRel`  
 場所は、レジスタの相対です。  
  
 `LocIsThisRel`  
 場所は`this`-相対します。  
  
 `LocIsEnregistered`  
 場所は、レジスタでです。  
  
 `LocIsBitField`  
 場所は、ビット フィールドでです。  
  
 `LocIsSlot`  
 場所は、Microsoft Intermediate Language (MSIL) のスロットです。  
  
 `LocIsIlRel`  
 場所は、MSIL 相対パスです。  
  
 `LocInMetaData`  
 メタデータ内の場所は。  
  
 `LocIsConstant`  
 場所は、定数値でです。  
  
 `LocTypeMax`  
 この列挙体の場所の種類の数。  
  
## <a name="remarks"></a>コメント  
 使用できるプロパティ、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)インターフェイスは、イメージ ファイル内のシンボルの場所によって異なります。 詳細については、次を参照してください。[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)します。  
  
 この列挙体の値が呼び出しによって返される、 [idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>「  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)