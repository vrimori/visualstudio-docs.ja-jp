---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この interfac現在のデバッグ セッションで実行中のスレッドを列挙します。  
  
## 構文  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはプログラム \(DE\) のスレッド一覧を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 プロセスで実行しているすべてのプログラムのスレッド一覧を表すこのインターフェイスを取得するに [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) を呼び出します。  プログラムで実行中のスレッドの一覧を表すこのインターフェイスを取得するに [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugThreads2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../Topic/IEnumDebugThreads2::Next.md)|列挙体シーケンス内の指定した数のスレッドを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|列挙体シーケンス内の指定した数のスレッドをスキップします。|  
|[リセット](../Topic/IEnumDebugThreads2::Reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|現在の列挙状態と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|列挙子スレッドの数を取得します。|  
  
## 解説  
 Visual Studio は\[ENT0ENT\] ウィンドウを更新するには[実行](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 取得するためにこのインターフェイスを [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md) と [ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md) を呼び出すにはリスト内の最初のスレッドを取得します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [実行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)