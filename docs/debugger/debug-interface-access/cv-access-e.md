---
title: "CV_access_e | Microsoft Docs"
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
  - "CV_access_e 列挙型"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

メンバー関数と変数のアクセス レベル \(表示\) の範囲を指定します。  
  
## 構文  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elements  
 CV\_private  
 メンバーはプライベート アクセスできます。  
  
 CV\_protected  
 メンバーのアクセスを保護します。  
  
 CV\_public  
 メンバーはパブリック アクセスできます。  
  
## 解説  
 `friend` のアクセス指定子はクラスのプライベート メンバーとプロテクト要素の両方にアクセスできる非メンバー関数で一般的に使用されるためここでは説明していません。  `SymTagFriend` のアクセスを持つシンボルを検索するに [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) のメソッドを使用します。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)