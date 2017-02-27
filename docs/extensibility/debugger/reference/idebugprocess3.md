---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "IDebugProcess3 インターフェイス"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは実行中のプロセスとプログラムを表します。  このインターフェイスは [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) インターフェイスの複数のメソッドに代わるものとします。  これはプロセス内のすべてのプログラム\] コントロールを提供します。  
  
> [!NOTE]
>  [続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md) [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) と [ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md) のメソッドの使用は推奨されていません。今後は使用しないでください。  `IDebugProcess3` インターフェイスの対応するメソッドを使用します。  
  
## 構文  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## 実装についてのメモ  
 このインターフェイスはカスタム ポートの仕入先によってグループとしてプログラムを管理するために実装されます。  プログラムをグループとして管理すると実行を制御し式エバリュエーターの言語を設定できます。  このインターフェイスはポートの仕入先に実装する必要があります。  
  
## 呼び出し元のメモ  
 このインターフェイスはデバッグ セッションのマネージャー \(SDM\) によってこのプロセスで識別されるプログラムのグループと対話するため主に呼び出されます。  
  
 このインターフェイスを取得するに [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出します。  
  
## Vtable の順序でメソッド  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) から継承されたメソッドに加えて `IDebugProcess3` は次のメソッドを実装します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|実行されるプロセスのステップ実行を続けます。|  
|[実行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|プロセスの実行を開始します。|  
|[ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md)|プロセスの手順に進みます命令またはステートメントの 1 つが。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|プロセスのデバッグの開始理由を取得します。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|デバッグ エンジンは適切な式エバリュエーターを読み込むためにホストの言語を設定します。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|現在の言語を設定してこのプロセスで取得します。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|このプロセスを無効にするためにENC\) 編集します。<br /><br /> カスタム ポートの業者はこのメソッド \(`E_NOTIMPL` を常に返す必要があります\) を実装していません。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|このプロセスの ENC の状態を取得します。<br /><br /> カスタム ポートの業者はこのメソッド \(`E_NOTIMPL` を常に返す必要があります\) を実装していません。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|使用可能なデバッグ エンジンの一意の識別子の配列を取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)