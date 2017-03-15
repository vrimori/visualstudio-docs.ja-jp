---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプロセスの境界を越えてプログラムに関連するインターフェイスをマーシャリングします。  
  
## 構文  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)プロセスの境界を越えてマーシャリング インターフェイスをサポートするために同じオブジェクトこのインターフェイスを実装する [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 実行します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugProgramNode2` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  このインターフェイスを取得できない場合はde\-DE インターフェイスのマーシャリングをサポートしていません。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|プロセスの境界を越えて指定されたインターフェイスを取得します。|  
  
## 解説  
 このインターフェイスはデバッグ対象プログラムとは別のプロセス空間の de\-DE runs ときに実行されます : たとえばde\-DE がデバッグ対象のプロセス領域ではなく Visual Studio のプロセス空間で実行している場合。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)