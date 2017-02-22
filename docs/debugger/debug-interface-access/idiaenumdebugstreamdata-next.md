---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next メソッド"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列挙体シーケンス内の指定されたレコード数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### パラメーター  
 celt  
 \[入力\] 取得するレコード数。  
  
 cbData  
 byte \[入力\] バッファーのサイズ。  
  
 pcbData  
 \[出力\] 返されるバイト数を返します。  `data` が null の場合`pcbData` はすべての要求されたレコードのデータの合計バイト数。  
  
 \[データ\]  
 \[入力\] デバッグ ストリームのレコードのデータが格納されるバッファー。  
  
 pceltFetched  
 \[入力出力\] `data` のレコード数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 次のレコードがある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)