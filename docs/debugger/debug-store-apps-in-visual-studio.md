---
title: "Visual Studio での UWP アプリのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3920bfbd5b1ddbddc3166118ead0c7d0fefff8d8
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="debug-uwp-apps-in-visual-studio"></a>Visual Studio での UWP アプリをデバッグします。
Visual Studio デバッガーを使用すると、プログラムの実行を制御し、その状態を確認できます。 UWP アプリの障害の原因を検出し、アプリのしくみを理解するには、デバッガーを使用することができます。 デバッガーで実行を中断すると、実行中のコードが含まれるソース ファイルが Visual Studio に表示され、実行中のステートメントが強調表示されます。 変数の値、実行関数の呼び出し履歴、およびプログラムの状態の他の側面を確認できます。 1 つのステートメントごとにプログラムを実行 (ステップ スルー) し続けると、ステートメントがプログラムの値を変化させるしくみを確認できます。 JavaScript で記述されたアプリでは、ページの DOM を調べて操作できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|[デバッグ セッション (JavaScript) の開始します。](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|「デバッグ セッションを開始する方法」では、JavaScript アプリのデバッグ セッションを構成し開始するための、いくつかのオプションについて説明します。|  
|[デバッグ セッション (JavaScript) での実行制御](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|「デバッガー ナビゲーション」では、簡単なアプリを使って、デバッグの開始と停止、コード内の移動、プログラムの状態を表示する方法を説明します。|  
|[クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)|「HTML および CSS のデバッグ」では、ライブ DOM 検査ツールを使って JavaScript アプリを対話的にデバッグし、HTML と CSS の表示方法や変更方法を示します。|  
|[クイック スタート: JavaScript をデバッグします。](../debugger/quickstart-debug-javascript-using-the-console.md)|コンソールを使用して JavaScript をデバッグする方法を示しますを使って JavaScript アプリを対話的にデバッグ[JavaScript コンソール コマンド](../debugger/javascript-console-commands.md)です。|  
|[(VB、c#、C++ および XAML) は、デバッグ セッションを開始します。](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|「デバッグ セッション (Visual C++、Visual C#、Visual Basic) を開始する方法」では、Visual C++、Visual C#、または Visual Basic で記述されたアプリのデバッグ セッションを構成し開始するための、さまざまなオプションについて説明します。|  
|[(Xaml および C# の場合) は、デバッグ セッションをナビゲートします。](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|「デバッガー ナビゲーション」では、簡単なアプリを使って、デバッグの開始と停止、コード内の移動、プログラムの状態の表示と変更を行う方法を説明します。|  
|[トリガーを中断、再開、およびバック グラウンド イベント UWP アプリの)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|デバッガーは、アプリを中断、再開、および終了する Windows のプロセス継続時間管理 (PLM) イベントを無効にします。 これらのイベントは、デバッガー ツール バーでトリガーさせることができます。<br /><br /> バックグラウンド タスクは、アプリが中断された場合でも重要な操作を実行できるようにします。 デバッガーは、これらのバックグラウンド タスクを開始してデバッグできるようにします。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [(MSDN ライブラリ) 内のデバッガー機能のツアー](http://go.microsoft.com/fwlink/?LinkID=226896)