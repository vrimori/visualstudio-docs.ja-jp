---
title: "BasicType | Microsoft Docs"
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
  - "BasicType 列挙型"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルの基本型を指定します。  
  
## 構文  
  
```cpp#  
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
   btHresult  = 31  
};  
```  
  
## Elements  
 btNoType  
 基本型が指定されていません。  
  
 btVoid  
 基本型は `void` です。  
  
 btChar  
 基本型は `char` \(C\/C\+\+\) の型です。  
  
 btWChar  
 基本的な種類はワイド \(Unicode\) 文字 \(`WCHAR`\) です。  
  
 btInt  
 基本型は `signed int` \(C\/C\+\+\) の型です。  
  
 btUInt  
 基本型は `unsigned int` \(C\/C\+\+\) の型です。  
  
 btFloat  
 基本型浮動小数点数 \(`FLOAT`\) です。  
  
 btBCD  
 基本的な種類は進化 2 \(10 進数\)`BCD` です。  
  
 btBool  
 基本的な種類はブール型 \(\)`BOOL` です。  
  
 btLong  
 基本型は `long int` \(C\/C\+\+\) の型です。  
  
 btULong  
 基本型は `unsigned long int` \(C\/C\+\+\) の型です。  
  
 btCurrency  
 基本的な種類は数字です。  
  
 btDate  
 基本型は日付 \/ 時刻 \(\)`DATE` です。  
  
 btVariant  
 基本型は変数の型の構造体 \(`VARIANT`\) です。  
  
 btComplex  
 基本型は複合型です。  
  
 btBit  
 基本的な種類は少し異なります。  
  
 btBSTR  
 基本型は基本型またはバイナリ文字列 \(`BSTR`\) です。  
  
 btHresult  
 基本型は `HRESULT` です。  
  
## 解説  
 この列挙体の値は [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) のメソッドによって返されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)