---
title: "IDiaSourceFile::get_uniqueId | Microsoft Docs"
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
  - "IDiaSourceFile::get_uniqueId メソッド"
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このイメージに対して一意である単純な整数のキー値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[出力\] このイメージに対して一意である単純な整数のキー値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 文字列ではなくキーを比較すると行番号の処理を短縮できます。  
  
## 参照  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)