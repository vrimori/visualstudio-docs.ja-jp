---
title: "IDiaEnumDebugStreams::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Next メソッド"
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンスのデバッグのストリームから指定した数の要素を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] ユーザーが取得された列挙子のデバッグ ストリームの数値を付ける **T**。  
  
 rgelt  
 \[出力\] 取得されたデバッグのストリームを表す [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) のオブジェクトの配列を返します。  
  
 pceltFetched  
 \[出力\] 返されたデバッグ ストリームの数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` これ以上のストリームがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)