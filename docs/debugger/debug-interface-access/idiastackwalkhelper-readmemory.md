---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory メソッド"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

メモリの実行可能ファイルのイメージのデータのブロックを読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### パラメーター  
 `type`  
 \[入力\] 読み取るためのメモリの [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md) の種類を指定する列挙体の値。  
  
 VA  
 \[入力\] イメージの読み上げを開始する仮想アドレス。  
  
 `cbData`  
 byte \[入力\] バッファーのサイズ。  
  
 `pcbData`  
 \[出力\] 実際に読み込まれるバイト数を返します。  `pbData` が `NULL` である場合はデータの合計バイト数です。  
  
 `pbData`  
 \[入力出力\] 読み込まれたメモリが格納されるバッファー。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)