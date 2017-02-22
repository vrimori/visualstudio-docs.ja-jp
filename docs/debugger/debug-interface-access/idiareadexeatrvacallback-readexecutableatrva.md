---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA メソッド"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

実行可能ファイルから指定した相対仮想アドレスから始まる指定 \(RVA\) したバイト数を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### パラメーター  
 `relativeVirtualAddress`  
 \[入力\] 読み上げを開始する実行可能ファイルの RVA。  
  
 `cbData`  
 \[入力\] 読み取るバイト数。  
  
 `pcbData`  
 \[入力\] 読み取るバイト数を返します。  
  
 `data[]`  
 \[入力出力\] のバイト数が格納された配列はファイルから読み取った。  
  
## 解説  
 このメソッドは相対仮想アドレスを使用して実行可能ファイルからデータを読み込むバイトの DIA のサポート コードによって呼び出されます。  このメソッドは [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) ためのメソッドが呼び出されます。  
  
## 参照  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)