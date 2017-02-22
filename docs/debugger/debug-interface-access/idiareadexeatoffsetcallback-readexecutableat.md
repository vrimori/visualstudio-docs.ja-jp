---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt メソッド"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

実行可能ファイルの指定したオフセット位置から開始して指定したバイト数を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### パラメーター  
 fileOffset  
 \[入力\] 読み上げを開始する実行可能ファイルのオフセット。  
  
 cbData  
 \[入力\] 読み取るバイト数。  
  
 pcbData  
 \[入力\] 読み取るバイト数を返します。  
  
 \[データ\]  
 \[入力出力\] のバイト数が格納された配列はファイルから読み取った。  
  
## 解説  
 このメソッドは絶対ファイルのオフセットを使用して実行可能ファイルからデータを読み込むバイトの DIA のサポート コードによって呼び出されます。  このメソッドは [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) ためのメソッドが呼び出されます。  
  
## 参照  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)