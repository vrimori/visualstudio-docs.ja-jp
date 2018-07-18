---
title: 操作モード |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ae5a36f9f0547635872f5c8ebe30f2f3c53d5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105568"
---
# <a name="operational-modes"></a>操作モード
これには、IDE が動作する、次のように 3 つのモードがあります。  
  
-   [デザイン モード](#vsconoperationalmodesanchor1)  
  
-   [実行モード](#vsconoperationalmodesanchor2)  
  
-   [中断モード](#vsconoperationalmodesanchor3)  
  
 必要とすると、遷移のメカニズムに理解して実装意思決定には、カスタム デバッグ エンジン (DE) がこれらのモードの間で移行する方法です。 デは、これらのモードを直接実装することができません。 これらのモードは本当にデバッグ パッケージのモードを切り替えるユーザー操作またはデからのイベントに基づきます。 たとえば、実行モードから中断モードに移行が、DE から停止イベントに依存します。 中断するか、またはを実行するモード ステップ モードからの移行は、ステップまたは Execute などの操作を実行するユーザーに依存します。 DE 遷移の詳細については、次を参照してください。[実行の制御](../../extensibility/debugger/control-of-execution.md)です。  
  
##  <a name="vsconoperationalmodesanchor1"></a> デザイン モード  
 デザイン モードは、この期間の機能をアプリケーションのデバッグを設定できます Visual Studio のデバッグ、nonrunning 状態です。  
  
 のみ、いくつかのデバッグ機能はデザイン モード中に使用されます。 ブレークポイントを設定またはウォッチ式を作成する開発者もかまいません。 デが読み込まれたまたはと呼ばれ、IDE がデザイン モードでしないでください。 デとの対話は、のみの実行と中断モード中に行われます。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 実行モード  
 実行モードは、プログラムは、IDE でのデバッグ セッションで実行するときに発生します。 アプリケーションは、ブレークポイントがヒットするまで、または例外がスローされるまで、連続コピーの終了まで実行されます。 ときに、アプリケーションは、デザイン モードに DE 遷移の終了に実行されます。 ブレークポイントにヒットまたは例外がスローされます、デは中断モードに移行します。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中断モード  
 中断モードでは、デバッグ、プログラムの実行が中断されている場合に発生します。 中断モード、中断時に、アプリケーションのスナップショットを開発者に提供でき、開発者は、アプリケーションの状態を分析し、アプリケーションを実行する方法を変更できます。 開発者は、表示しコードを編集を確認またはデータを変更する、アプリケーションを再起動、実行を終了しますしたり同じポイントから実行を継続できます。  
  
 中断モードは、DE が同期の停止イベントを送信するときに入力されます。 同期の停止イベント、停止イベントとも呼ばれますが、セッション デバッグ マネージャー (SDM) を通知し、デバッグ中のアプリケーションはコードの実行を停止した IDE です。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)と[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)インターフェイスは、停止イベントの例を示します。  
  
 停止イベントがデバッガー ステップ モードまたは実行を中断モードからに移行するメソッドを次のいずれかへの呼び出しによって継続します。  
  
-   [実行します。](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> ステップ モード  
 ステップ モードは、プログラムは、コードのかに、または関数から次の行にステップする場合に発生します。 ステップが、メソッドを呼び出すことによって実行された[ステップ](../../extensibility/debugger/reference/idebugprocess3-step.md)です。 このメソッドが必要な`DWORD`s を指定する、 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)と[STEPKIND](../../extensibility/debugger/reference/stepkind.md)入力パラメーターとしての列挙体です。  
  
 プログラムが正常にコードまたは関数の場合には、次の行にステップか、カーソルにまたは一連のブレークポイントまで実行、中断モードに戻る、DE が自動的に移行します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)