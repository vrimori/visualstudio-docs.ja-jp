---
title: LocationType |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb46eb1c7477f93ed63dfc4424d881886c8d0c8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="locationtype"></a>LocationType
シンボルの場所の情報の種類を示します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum LocationType {   
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
 場所の情報は使用できません。  
  
 `LocIsStatic`  
 場所は静的です。  
  
 `LocIsTLS`  
 場所は、スレッド ローカル ストレージです。  
  
 `LocIsRegRel`  
 場所は、レジスタの相対です。  
  
 `LocIsThisRel`  
 場所は`this`-相対します。  
  
 `LocIsEnregistered`  
 場所は、レジスタでです。  
  
 `LocIsBitField`  
 場所は、ビット フィールドです。  
  
 `LocIsSlot`  
 場所は、Microsoft Intermediate Language (MSIL) のスロットです。  
  
 `LocIsIlRel`  
 場所は、MSIL relative です。  
  
 `LocInMetaData`  
 場所は、メタデータでです。  
  
 `LocIsConstant`  
 場所は、定数値です。  
  
 `LocTypeMax`  
 この列挙体の場所の種類の数。  
  
## <a name="remarks"></a>コメント  
 使用できるプロパティ、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)インターフェイスは、イメージ ファイル内のシンボルの場所によって異なります。 詳細については、次を参照してください。[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)です。  
  
 この列挙体の値がへの呼び出しによって返される、 [idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol::get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)