---
title: "IDebugProgramEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "IDebugProgramEx2 インターフェイス"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションの管理により\(SDM\) プログラムにアタッチされプログラムのノードをプログラムに関連付けられた取得できるようにします。  
  
## 構文  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートのサプライヤーが同時にポートがサプライヤーのすべてのセッションを追跡できるようにすることがプログラムにアタッチしますがインターフェイスの [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) SDM のアタッチをプログラムで使用するとこのインターフェイスを実装します。  カスタム ポートのサプライヤーを選択するとこのインターフェイスを実装できます。  
  
## 呼び出し元のメモ  
 SDM はプログラムにアタッチするセッションを追跡するにはこのインターフェイスを取得するために `IDebugProgram2` のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgramEx2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|セッションにプログラムをアタッチします。|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|プログラムのノードをプログラムに関連付けられているを取得します。|  
  
## 解説  
 このインターフェイスはSDM のプログラム間でプライベートです。  
  
## 必要条件  
 ヘッダー : Portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)