---
title: "IDiaEnumSourceFiles::Next | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Next メソッド"
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンスのソース ファイルの指定した数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[出力\] 取得された列挙子のソース ファイルの数。  
  
 rgelt  
 \[入力\] 目的のソース ファイルを表す [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) のオブジェクトが格納された配列。  
  
 pceltFetched  
 \[入力\] 列挙子のフェッチ ソース ファイル数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` これ以上のソース ファイルがない場合 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)