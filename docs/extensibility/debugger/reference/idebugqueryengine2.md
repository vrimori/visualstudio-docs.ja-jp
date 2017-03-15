---
title: "IDebugQueryEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "IDebugQueryEngine2 インターフェイス"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションの管理に \(SDM\) デバッグ エンジンを表すインターフェイスを取得できるように \(DE\) なります。  
  
## 構文  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements します [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) のインターフェイス自体へのアクセスを許可するように共通の interfaces de\-DE \([IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) と [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) など\)このインターフェイスを実装するオブジェクト。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得する一般的なインターフェイスの呼び出し [QueryInterface](/visual-cpp/atl/queryinterface) します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugQueryEngine2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|カスタムのデバッグ エンジン \(DE\) インターフェイスを取得します。|  
  
## 解説  
 このインターフェイスはオブジェクトで実装で関数によって [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイス サポートする手順を因果関係する命令に実行します ; つまりデバッガーが関数にステップ インする場合実行する次の関数はスタックの前の関数別のスレッドのすべての関数ではない場合があります。  「因果関係の定義については」[Visual Studio デバッガーの用語集](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) を参照してください。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)