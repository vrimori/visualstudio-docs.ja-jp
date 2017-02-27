---
title: "IDiaFrameData::get_lengthSavedRegisters | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthSavedRegisters メソッド"
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_lengthSavedRegisters
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

スタックにプッシュされるレジスタ格納されているバイト数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] 保存したレジスタのバイト数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドの戻り値はプログラムの文字列の解釈で使われます \(プログラムの文字列の定義については [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) のメソッドを参照\)。  
  
## 参照  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)