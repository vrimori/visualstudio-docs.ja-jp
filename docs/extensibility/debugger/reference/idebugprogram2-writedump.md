---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ダンプをファイルに書き込みます。  
  
## 構文  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### パラメーター  
 `DumpType`  
 \[入力\] たとえば短いダンプの種類はの [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) 指定する列挙体の値。  
  
 `pszDumpUrl`  
 \[入力\] ダンプの書き込み先 URL。  通常これは `file://c: パス \ \ filename.ext` の形式で有効な URL である場合があります。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 プログラムのダンプはプログラムには現在のスタック フレームとスタックで実行中のスレッドの一覧とプログラムが所有しているメモリが含まれます。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)