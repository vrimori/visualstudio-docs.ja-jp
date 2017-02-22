---
title: "操作モード | Microsoft Docs"
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
  - "デバッグ エンジンは、モード"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 操作モード
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE で使用できる次の 3 とおりの二つのモードがあります :  
  
-   [デザイン モード](#vsconoperationalmodesanchor1)  
  
-   [実行モード](#vsconoperationalmodesanchor2)  
  
-   [中断モード](#vsconoperationalmodesanchor3)  
  
 これらのカスタム \(DE\) モードのデバッグ エンジンの移行が遷移の機能に精通している必要になる実装の決定方法が。  DE は直接これらのモードを実装する場合そうでない場合があります。  これらのモードはde\-DE のユーザー アクションまたはイベントに基づいて切り替えるデバッグのパッケージのモードです。  たとえば実行の中断モードとモードへの遷移は de\-DE から停止のイベントによって処置されます。  別のステップ実行モードまたはモードへの切り替えをステップ実行するなどの操作を実行するユーザーによって処置または実装します。  DE transitions する方法の詳細については[実行の制御](../../extensibility/debugger/control-of-execution.md) を参照してください。  
  
##  <a name="vsconoperationalmodesanchor1"></a> デザイン モード  
 デザイン モードはアプリケーションのデバッグ機能を設定できますがVisual Studio のデバッグ動作しない状態です。  
  
 一部のデバッグ機能だけをデザイン モードで使用されます。  開発者はブレークポイントを設定したりウォッチ式を作成することもあります。  DE はIDE がデザイン モードでの読み込みまたは呼び出されません。  DE との相互作用になったら中断モード中に行われます。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 実行モード  
 実行モードではプログラムが IDE のデバッグ セッションで実行されると発生します。  ブレークポイントにヒットするかまたは例外がスローされるまで終了までアプリケーションの実行。  終了デザイン モードにします transitions へのアプリケーションの実行時。  ブレークポイントにヒットする場合または例外がスローされると中断モードに transitions します。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中断モード  
 中断モード デバッグはプログラムの実行が中断されると発生します。  中断モード時には別の開発者がアプリケーションのスナップショットを提供し開発者がアプリケーションの状態を分析しアプリケーションの動作を変更できるようにします。  開発者はコード編集ポイントし表示するチェックしたりデータを変更するかアプリケーションを再起動するか実行を終了または同じの実行を継続できます。  
  
 中断モードではde\-DE sends 同期停止のイベント送信されます。  またという名前のイベントを停止する同期イベントはデバッグを停止しアプリケーションでコードの実行を停止するとデバッグ セッション マネージャー \(SDM\) および IDE を通知します。  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) と [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) のインターフェイスはイベントを停止する例です。  
  
 停止するイベントが遷移を実行するには \(中断モードまたはモード デバッガーのステップから次のメソッドの 1 回の呼び出しで続行されます :  
  
-   [実行](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [ステップ](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [続行](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> ステップのモード  
 ステップのモードは次のコード行にまたは関数にプログラムステップと発生します。  [ステップ](../../extensibility/debugger/reference/idebugprocess3-step.md) 手順はメソッドを呼び出して実行します。  このメソッドは`DWORD` を必要とする入力パラメーターとして [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) と [STEPKIND](../../extensibility/debugger/reference/stepkind.md) の列挙型を指定します。  
  
 プログラムは次のコード行で関数にステップ インするかカーソルまたは設定のブレークポイントまで実行すると中断モードに戻ります自動的に遷移します。  
  
## 参照  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)