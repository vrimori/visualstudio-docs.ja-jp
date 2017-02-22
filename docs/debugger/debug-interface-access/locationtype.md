---
title: "LocationType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocationType 列挙型"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルに含まれている場所情報の種類を示します。  
  
## 構文  
  
```cpp#  
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
  
## Elements  
 `LocIsNull`  
 位置情報は使用できません。  
  
 `LocIsStatic`  
 場所は静的です。  
  
 `LocIsTLS`  
 場所はスレッド ローカル ストレージにあります。  
  
 `LocIsRegRel`  
 場所は登録相対的です。  
  
 `LocIsThisRel`  
 場所は `this`\- 相対パスです。  
  
 `LocIsEnregistered`  
 位置がレジスタにあります。  
  
 `LocIsBitField`  
 位置がビット フィールドです。  
  
 `LocIsSlot`  
 場所は Microsoft Intermediate Language \(MSIL\) のスロットです。  
  
 `LocIsIlRel`  
 場所は MSIL 相対的です。  
  
 `LocInMetaData`  
 場所はメタデータにあります。  
  
 `LocIsConstant`  
 場所は定数値に設定されます。  
  
 `LocTypeMax`  
 この列挙体の場所の種類の数。  
  
## 解説  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) のインターフェイスで使用できるプロパティはイメージ ファイル内のシンボルの位置によって決まります。  詳細については、「[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)」を参照してください。  
  
 この列挙体の値は [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)