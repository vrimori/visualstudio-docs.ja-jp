---
title: "IDiaSectionContrib::get_notPaged | Microsoft Docs"
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
  - "IDiaSectionContrib::get_notPaged メソッド"
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_notPaged
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

セクションはメモリからページングできるかどうかを示すフラグを取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[out\] セクションを編集して場合はを返します `TRUE` ; それ以外の場合戻り `FALSE`。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)