---
title: "プログラムの制御 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "実行の [デバッグ SDK] コントロールのデバッグ"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# プログラムの制御
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio のデバッグでは次のステップ実行や継続ルーチンはすべてプログラムレベルで実行されます :  
  
-   特定のフレームの環境で実行される次の命令にコンピューターを設定する次のステートメントをつまり設定します  
  
-   つまりステップの実行モードを終了します。  
  
-   次の手順について  
  
-   現在のステップ モードで継続  
  
-   プログラムに含まれるスレッドを中断します  
  
-   プログラムに含まれるスレッドを再開します  
  
> [!NOTE]
>  呼び出し履歴を表示するにはスレッド レベルで実行されます。  スレッドの呼び出し履歴を表示する[IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) インターフェイスのすべてのメソッドを実装する必要があるときにフレームの情報を列挙します。  
  
## プログラムの制御のメソッド  
 次の表は最小限の機能デバッグ エンジン \(DE\) および実行制御するために必要な [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDebugProgram2:: 実行](../../extensibility/debugger/reference/idebugprogram2-execute.md)|プログラムに含まれる停止状態からすべてのスレッドを実行する Continues。  実行制御の場合に必要です。|  
|[IDebugProgram2:: 続行](../../extensibility/debugger/reference/idebugprogram2-continue.md)|プログラムに含まれる停止状態からすべてのスレッドを実行する Continues。  実行制御の場合に必要です。|  
|[IDebugProgram2:: 手順](../../extensibility/debugger/reference/idebugprogram2-step.md)|特定のスレッドの手順を実行します。  プログラムに含まれる他のすべてのスレッドを実行する Continues。  実行制御の場合に必要です。|  
  
 マルチスレッド プログラムでは[IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) のインターフェイス [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) のすべてのメソッドとメソッドを実装する必要があります。  
  
## 参照  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)