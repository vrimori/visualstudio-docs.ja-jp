---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign メソッド"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

イメージの配置を設定します。  
  
## 構文  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### パラメーター  
 NewVal  
 \[入力\] 実行可能ファイルに対して新しいイメージの配置の値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 読み込まれたイメージ \(実行可能ファイル\) は指定したメモリの境界に配置します。  この配置は現在のシステムのアーキテクチャおよびリンク時のオプションの影響を受ける可能性があります。  イメージの配置をバイト境界上に常にです。  次のイメージの位置の値が有効です : 12481632および 64 バイト境界。  
  
 現在のイメージの配置を [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) のメソッドを呼び出すことで取得できます。  
  
> [!NOTE]
>  イメージはこのメソッドを呼び出すことができるまでに読み込まれます。  `put_imageAlign` のメソッドはイメージが新しい配置に必要な移動されたまたは変更され使用されます。  
  
## 参照  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)