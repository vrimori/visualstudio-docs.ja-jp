---
title: "IDebugPortEx2 | Microsoft Docs"
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
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "IDebugPortEx2 インターフェイス"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャーが \(SDM\) ポートのプログラムおよび実行されているプロセスを制御できるようになります。  
  
## 構文  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートのサプライヤーが同じでこのインターフェイスを実装するオブジェクト [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 実行します。  
  
## 呼び出し元のメモ  
 SDM はこのインターフェイスを取得するに `IDebugPort2` のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPortEx2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|実行可能ファイルが起動されます。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|プロセスの実行を再開します。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|プロセスを終了できるかどうかを判定します。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|プロセスを終了します。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|ポートのプロセス ID 自体を取得します。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|プログラムをプログラムのノードに関連付けられているを取得します。|  
  
## 解説  
 このインターフェイスは通常 SDM とカスタム ポートのサプライヤー間でプライベートです。  
  
 必要に応じてデバッグ エンジンは \(DE\)[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) に渡される [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のこのインターフェイスのインターフェイスを検索しプログラムの起動に [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) を使用できます。  これは必須ではありませんがde\-DE がプログラムを起動する必要があるものを行うことができます。  
  
## 必要条件  
 ヘッダー : portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)