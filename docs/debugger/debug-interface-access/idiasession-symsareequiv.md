---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv メソッド"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

2 個のシンボルが等しいかどうかを確認します。  
  
## 構文  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### パラメーター  
 `symbolA`  
 \[入力\] 比較する [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) の最初のオブジェクト。  
  
 `symbolB`  
 \[入力\] 比較する `IDiaSymbol` の 2 番目のオブジェクト。  
  
## 戻り値  
 シンボルが同じである場合は戻り `S_OK`; それ以外の場合戻り `S_FALSE` はシンボル同等ではありません。  それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)