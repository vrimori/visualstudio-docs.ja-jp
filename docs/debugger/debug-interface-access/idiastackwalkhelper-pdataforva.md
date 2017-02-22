---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::pdataByVA メソッド"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

仮想アドレスに関連付けられた PDATA のデータ ブロックを返します。  
  
## 構文  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### パラメーター  
 `va`  
 \[入力\] データの仮想アドレスを取得するように指定します。  
  
 `cbData`  
 \[入力\] 取得するバイト データのサイズ。  
  
 `pcbData`  
 \[出力\] 取得されたバイト データの実際のサイズを返します。  
  
 `pbData`  
 \[入力出力\] 要求されたデータが格納されるバッファー。  `NULL` にすることはできません。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 指定したアドレスの PDATA がある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 コンパイル単位 \(.pdata PDATA 「」というセクション\) は関数の例外処理に関する情報が含まれます。  
  
 呼び出し元はデータの量を呼び出す必要があるデータの量を返す必要があるので呼び出し元はないかを確認します。  したがって `pbData` のパラメーターが `NULL` 場合このメソッドは実装がエラーを返すことを指定できます。  
  
## 参照  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)