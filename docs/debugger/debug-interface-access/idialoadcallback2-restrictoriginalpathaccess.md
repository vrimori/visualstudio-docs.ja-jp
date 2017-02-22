---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictOriginalPathAccess メソッド"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

これは元の Debug ディレクトリの .pdb ファイルを検索することが適切かどうかを判定します。  
  
## 構文  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `S_OK` 以外のリターン コードは元の Debug ディレクトリの .pdb ファイルを検索するようにします。  元の Debug ディレクトリが実行可能ファイルにコンパイル シンボル ファイルをデバッグするとパスです。  このパスは実行可能ファイルが存在するパスと必ずしも同じではありません。  
  
## 参照  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)