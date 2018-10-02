---
title: 操作モード |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b23ba695b02a0332ad40a2c51047336903255a13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547073"
---
# <a name="operational-modes"></a>操作モード
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[操作モード](https://docs.microsoft.com/visualstudio/extensibility/debugger/operational-modes)します。  
  
これには、IDE できますが動作する、次のように 3 つのモードがあります。  
  
-   [デザイン モード](#vsconoperationalmodesanchor1)  
  
-   [実行モード](#vsconoperationalmodesanchor2)  
  
-   [中断モード](#vsconoperationalmodesanchor3)  
  
 移行方法を理解する必要がある実装の意思決定は、これらのモードの間で、カスタム デバッグ エンジン (DE) がどのように遷移します。 デは、これらのモードを直接実装しない場合があります。 これらのモードは、デバッグ パッケージ モードを切り替えるユーザーによる操作や、DE からのイベントに基づいてでは実際には。 たとえば、中断モードに実行モードからの移行が、DE から停止イベントによって依存します。 モードまたはモードの手順を実行するか中断からの移行は、ステップ実行などの操作を実行するユーザーに依存します。 DE 遷移の詳細については、次を参照してください。[実行の制御](../../extensibility/debugger/control-of-execution.md)します。  
  
##  <a name="vsconoperationalmodesanchor1"></a> デザイン モード  
 デザイン モードは、その間機能をアプリケーションでのデバッグを設定できますの Visual Studio のデバッグ、nonrunning 状態です。  
  
 のみ、いくつかのデバッグ機能がデザイン モードのときに使用します。 開発者は、ブレークポイントを設定またはウォッチの式を作成できます。 デが読み込まれたまたは、IDE がデザイン モードと呼ばれるしないでください。 のみの実行と中断モード中に行われる、DE との対話します。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 実行モード  
 実行モードでは、プログラムは、IDE でのデバッグ セッションで実行するときに発生します。 アプリケーションは、ブレークポイントがヒットするまで、または例外がスローされるまで、連続コピーの終了まで実行されます。 ときに、アプリケーションは、デザイン モードに DE 遷移、終了時に実行されます。 ブレークポイントにヒットするか、例外がスローされます、DE は、中断モードに移行します。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中断モード  
 中断モードでは、デバッグ、プログラムの実行が中断されたときに発生します。 中断モード、中断時にアプリケーションのスナップショットを開発者に提供され、開発者、アプリケーションの状態を分析し、アプリケーションを実行する方法を変更します。 開発者できます表示しコードを編集、確認またはデータを変更、アプリケーションを再起動、実行を終了または同じポイントから実行を続行します。  
  
 中断モードは、DE、同期の停止イベントを送信するときに入力します。 同期の停止イベント、"stopping"のイベントとも呼ばれます。 セッション デバッグ マネージャー (SDM) に通知し、デバッグ中のアプリケーションにコードの実行が停止している IDE。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)と[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)インターフェイスの停止イベントの例に示します。  
  
 停止イベントがデバッガーを中断モードまたはモードの手順を実行するからに移行するメソッドを次のいずれかを呼び出して継続します。  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> ステップ モード  
 ステップ モードでは、プログラムのコード、またはに、または関数からは、次の行にステップするときに発生します。 メソッドを呼び出してステップが実行された[手順](../../extensibility/debugger/reference/idebugprocess3-step.md)します。 このメソッドが必要な`DWORD`を指定する、 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)と[STEPKIND](../../extensibility/debugger/reference/stepkind.md)入力パラメーターとしての列挙体。  
  
 プログラムが正常にコードの場合、または関数の場合に、次の行にステップまたはブレークポイントの設定には、カーソルが実行されます、DE が自動的に中断モードに移行します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)

