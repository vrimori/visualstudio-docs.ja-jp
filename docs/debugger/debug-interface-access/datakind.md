---
title: "DataKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DataKind 列挙型"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

データ値の特定の範囲が表示されます。  
  
## 構文  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elements  
 DataIsUnknown  
 データ シンボルが決定する必要があります。  
  
 DataIsLocal  
 データ項目をローカル変数と呼びます。  
  
 DataIsStaticLocal  
 データ項目は静的ローカル変数です。  
  
 DataIsParam  
 データ項目は仮パラメーターです。  
  
 DataIsObjectPtr  
 データ項目はオブジェクト ポインター \(`this`\) です。  
  
 DataIsFileStatic  
 データ項目はファイル スコープの変数です。  
  
 DataIsGlobal  
 データ項目はグローバル変数です。  
  
 DataIsMember  
 データ項目はオブジェクトのメンバー変数です。  
  
 DataIsStaticMember  
 データ項目はクラスの静的変数です。  
  
 DataIsConstant  
 データ項目は定数です。  
  
## 解説  
 この列挙体の値は [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) のメソッドによって返されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)