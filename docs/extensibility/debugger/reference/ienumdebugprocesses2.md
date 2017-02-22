---
title: "IEnumDebugProcesses2 | Microsoft Docs"
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
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ ポートで実行されているプロセスを列挙します。  
  
## 構文  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者はポートで実行されているプロセスの一覧を表示するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 Visual Studio はこのインターフェイスを取得するに [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugProcesses2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|列挙体シーケンス内の指定したプロセスの数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|列挙体シーケンスのプロセスの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../Topic/IEnumDebugProcesses2::Clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|プロセスの列挙子の数を取得します。|  
  
## 解説  
 Visual Studio には\[出力\] ウィンドウ ENT0ENT を取得するためこのインターフェイスを使用します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)