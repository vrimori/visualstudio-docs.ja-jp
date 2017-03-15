---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
  - "IDiaSession::put_loadAddress メソッド"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このシンボル ストア内のシンボルに対応する実行形式の読み込みアドレスを設定します。  
  
## 構文  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### パラメーター  
 `NewVal`  
 \[入力\] 実行可能ファイルのアドレスを読み込みます。  
  
## 解説  
 シンボル用の仮想アドレスの \(VA\) プロパティはこのメソッドの値を使用して計算されます。  仮想アドレスはこのプロパティを以外の値に設定されている計算されません。  
  
> [!NOTE]
>  シンボル用の仮想プロパティを使用する必要がある場合 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) のオブジェクトを取得するとオブジェクトを使用して開始する前にこのメソッドを呼び出す必要があります。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)