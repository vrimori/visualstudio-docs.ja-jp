---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyDebugDir メソッド"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ ディレクトリは .exe ファイルにあるときに呼び出されます。  
  
## 構文  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### パラメーター  
 `fExecutable`  
 \(.dbg ファイル\) ではなく \[入力\] デバッグ ディレクトリが実行可能ファイルから読まれれば `TRUE`。  
  
 `cbData`  
 \[入力\] デバッグ ディレクトリにデータのバイト数。  
  
 `data[]`  
 \[入力\] デバッグ ディレクトリが格納された配列。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  リターン コードは通常は無視されます。  
  
## 解説  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) のメソッドは実行可能ファイルの処理中にデバッグ ディレクトリを検索するときにこのメソッドを呼び出します。  
  
 このメソッドは.pdb ファイルに含まれるまたサポートのデバッグ情報をリバース エンジニアリングするクライアントの要件を実行可能ファイルまたはファイルのデバッグ削除します。  このデータを使用してクライアントは実行可能ファイルまたは .dbg ファイルに存在するかどうかをデバッグに使用できる情報の種類を認識します。  
  
 ほとんどのクライアントからシンボルを実行するために必要なとき `IDiaDataSource::loadDataForExe` のメソッドを透過的に .pdb および .dbg ファイルを開くためこのコールバックは不要です。  
  
## 参照  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)