---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum メソッド"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

チェックサムのバイトを取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### パラメーター  
 `cbData`  
 byte \[入力\] バッファーのサイズ。  
  
 `pcbData`  
 \[出力\] チェックサムのバイト数を返します。  このパラメーターには、`NULL` は指定できません。  
  
 `data`  
 \[入力出力\] チェックサムのバイトが格納されるバッファー。  このパラメーターがの場合`NULL``pcbData` に必要なバイト数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 チェックサムのバイトを生成するために使用されるチェックサム アルゴリズムの種類を確認するには [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) のメソッドを呼び出します。  
  
 ソース ファイルのチェックサムがイメージからその生成されチェックサムのバイトのソース ファイルに変更が反映されます。  チェックサムのバイトがファイルから読み込まれたイメージの生成されたチェックサムと一致しないファイルは影響が及ぶ場合または改竄されていないと考えてください。  
  
 一般的なチェックサムが32 バイトを超えるで想定していませんがチェックサムの最大サイズです。  チェックサムを取得するのに必要なバイト数を取得するに `NULL` に `data` のパラメーターを設定します。  次に適したサイズのバッファーの割り当てとコピー先のバッファーを指定してこのメソッドを再度呼び出します。  
  
## 参照  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)