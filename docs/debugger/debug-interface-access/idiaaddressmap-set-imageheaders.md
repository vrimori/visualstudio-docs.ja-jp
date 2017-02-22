---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders メソッド"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

イメージのヘッダーを相対仮想アドレスの移動を有効にするように設定します。  
  
## 構文  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### パラメーター  
 cbData  
 \[入力\] ヘッダー データのバイト数。  `n` が実行可能ファイルのセクション ヘッダーの番号です。`n*sizeof(IMAGE_SECTION_HEADER)` にする必要があります。  
  
 \[データ\]  
 \[入力\] イメージのヘッダーとして使用する `IMAGE_SECTION_HEADER` の構造体の配列。  
  
 originalHeaders  
 \[入力\] アップグレード前に元のイメージを反映するイメージのヘッダーが新しいイメージの場合 `FALSE``TRUE` に設定します。  通常これは [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) のメソッドの呼び出しと組み合わせてのみ `TRUE` に設定されます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `IMAGE_SECTION_HEADER` の構造はWinnt.h で宣言され実行可能イメージのヘッダー ファイルのセクションの書式を表します。  
  
 相対仮想アドレスの計算は `IMAGE_SECTION_HEADER` の値によって異なります。  通常DIAプログラム データベース \(.pdb\) ファイルでこれらを取得します。  これらの値がない場合DIA は相対仮想アドレスと [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) のメソッド `FALSE` を計算することはできません。  クライアントはイメージから足りないイメージのヘッダー自体を入力したら相対仮想アドレスの計算を有効にするに [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) のメソッドを呼び出す必要があります。  
  
## 参照  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)