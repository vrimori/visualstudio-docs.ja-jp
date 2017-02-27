---
title: "IDebugEngineLaunch2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "IDebugEngineLaunch2 インターフェイス"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムを起動し終了するときにデバッグ エンジン \(DE\) によって使用されます。  
  
## 構文  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## 実装についてのメモ  
 このインターフェイスはカスタム de\-DE にカスタム ポートによって完全に処理できないプロセスを起動するための特別な要件がある場合実行されます。  これはインタープリターしますがプロセスのデバッグはスクリプトである場合に同じです : インタープリターが最初に起動する必要があります。にスクリプトが読み込まれ開始されます。  ポートはインタープリターに起動できますがスクリプト \(de\-DE にロールを持つ場合\) である特別な処理を必要とする場合があります。  このインターフェイスは処理するカスタム ポートができないプログラムを起動するための固有の要件がある場合にだけ実行されます。  
  
## 呼び出し元のメモ  
 このインターフェイスはデバッグ セッションのマネージャー \(SDM\) によって SDM が [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) のインターフェイスからこのインターフェイスを取得できますが呼び出されます \(QueryInterface を使用します。  このインターフェイスを取得できますがSDM は de\-DE には特別な要件があることを確認しポートの起動が表示される代わりにプログラムを起動するにはこのインターフェイスをにを呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEngineLaunch2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|でプロセスを開始します。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|再開が実行を処理します。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|プロセスを終了できるかどうかを判定します。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|プロセスを終了します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)