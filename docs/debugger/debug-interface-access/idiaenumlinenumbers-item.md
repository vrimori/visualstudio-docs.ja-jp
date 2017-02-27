---
title: "IDiaEnumLineNumbers::Item | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Item メソッド"
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

インデックスで行数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### パラメーター  
 index  
 \[入力\] 取得する [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) のオブジェクトのインデックス。  インデックスは 0 ~ \-1 `count` に `count` が [IDiaEnumLineNumbers::get\_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) のメソッドによって返される場合になります。  
  
 lineNumber  
 \[入力\] [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) に目的の行番号を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)