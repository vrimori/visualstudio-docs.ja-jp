---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap メソッド"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

サポートのイメージの移動に Address マップを提供します。  
  
## 構文  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### パラメーター  
 `cbData`  
 \[入力\] `data` のパラメーターの要素数。  
  
 `data[]`  
 \[移動\] マップを定義する [DiaAddressMapEntry 構造体](../../debugger/debug-interface-access/diaaddressmapentry.md) の構造体の配列。  
  
 `imagetoSymbols`  
 \(デバッグ シンボル\) と\[入力\] `data` のパラメーターが新しいイメージのレイアウトから元のレイアウトにマップを定義する `TRUE`。  `data` が元のレイアウトから取得される新しいイメージのレイアウトにマップされて `FALSE`。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 通常DIAプログラム データベース \(.pdb\) ファイルからアドレス変換 \(マップを取得します。  これらの値がない場合[IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) のメソッドは `TRUE` への `imagetoSymbols` 設定されたパラメーター `FALSE` 一度に `imagetoSymbols` のパラメーター セットに重複して一度だけ呼び出されます。  Address マップの移動は [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md) のメソッドを使用して移動のマップが両方とも提供する有効にできません。  
  
## 参照  
 [DiaAddressMapEntry 構造体](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)