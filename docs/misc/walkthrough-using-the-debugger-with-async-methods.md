---
title: "チュートリアル: 非同期メソッドと共にデバッガーを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "非同期機能, 使用 (デバッガーを)"
  - "await 演算子, 使用 (デバッガーを)"
  - "[ステップ イン] コマンド, await 演算子で"
  - "[ステップ アウト] コマンド, async メソッド内"
  - "[ステップ オーバー] コマンド, await 演算子で"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# チュートリアル: 非同期メソッドと共にデバッガーを使用する
非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。  同期コードを非同期コードにするには、同期メソッドの代わりに非同期メソッドを呼び出して、コードにいくつかのキーワードを追加します。  詳細については、「[Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 Visual Studio デバッガーでは、**\[ステップ イン\]**、**\[ステップ オーバー\]**、**\[ステップ アウト\]** のコマンドを `Async` 機能に使用できます。  ブレークポイントも引き続き使用できます。特に、await 演算子を含むステートメントでの制御フローを表示するためにです。  このチュートリアルでは次のタスクを完了します。実行する順序は任意でかまいません。  
  
-   ブレークポイントを使用して await ステートメントでの制御フローを示す。  
  
-   await 演算子を含むステートメントでの **\[ステップ イン\]** および **\[ステップ オーバー\]** コマンドの動作を理解する。  
  
-   async メソッド内から使用するときの **\[ステップ アウト\]** コマンドを動作を理解する。  
  
## 制御フローを表示するためのブレークポイント  
 メソッドを [Async](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) または [async](/dotnet/csharp/language-reference/keywords/async) \(C\#\) 修飾子でマークした場合は、そのメソッド内で [Await](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) または [await](/dotnet/csharp/language-reference/keywords/await) \(C\#\) 演算子を使用できます。  await 式を作成するには、await 演算子をタスクに関連付けます。  await 式はタスクに対して呼び出され、現在のメソッドはすぐに終了して、別のタスクを返します。  await 演算子に関連付けられているタスクが終了すると、実行は同じメソッド内で再開されます。  詳細については、「[非同期プログラムにおける制御フロー](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
> [!NOTE]
>  async メソッドは、まだ完了していない処理待ちの最初のオブジェクトに達するか、async メソッドの最後に達すると、いずれか先に到した方の呼び出し元に戻ります。  
  
> [!NOTE]
>  これらの例のコンソール アプリケーションでは、<xref:System.Threading.Tasks.Task.Wait%2A> を使用して、アプリケーションが `Main` で終了しないようにしています。  コンソール アプリケーションの外部で <xref:System.Threading.Tasks.Task.Wait%2A> メソッドを使用しないでください。デッドロック状態になる可能性があるためです。  
  
 次の手順では、ブレークポイントを設定して、アプリケーションが await ステートメントに達したときの動作を示します。  `Debug.WriteLine` ステートメントを追加しても制御フローを示すことができます。  
  
1.  コンソール アプリケーションを作成し、そのアプリケーションに次のコードを貼り付けます。  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  「set breakpoint」のコメントで終わる 3 行にデバッグ ブレークポイントを設定します。  
  
3.  F5 キーを押すかメニュー バーで **\[デバッグ\]**、**\[デバッグ開始\]** の順にクリックして、アプリケーションを実行します。  
  
     アプリケーションが `ProcessAsync` メソッドに達すると、await 演算子が含まれる行で中断されます。  
  
4.  F5 キーを再び押します。  
  
     アプリケーションが await 演算子が含まれるステートメントで停止したため、アプリケーションはすぐに async メソッドを終了し、タスクを返します。  したがって、アプリケーションが `ProcessAsync` メソッドを終了し、呼び出し先のメソッド \(`Main`\) 内のブレークポイントで中断されます。  
  
5.  F5 キーを再び押します。  
  
     `DoSomethingAsync` メソッドが完了すると、呼び出し元のメソッド内 await ステートメントの後からコードが再開されます。  したがって、アプリケーションは `ProcessAsync` メソッド内のブレークポイントで中断されます。  
  
     `DoSomethingAsync` が最初に待機状態になったとき、`ProcessAsync` メソッドが終了し、タスクを返しました。  待機状態の `DoSomethingAsync` メソッドが完了すると、await ステートメントの評価により `DoSomethingAsync` の戻り値が生成されました。  `DoSomethingAsync` メソッドは、`Task (Of Integer)` \(Visual Basic\) または `Task<int>` \(C\#\) を返すように定義されているため、その return ステートメントの値は整数です。  詳細については、「[非同期の戻り値の型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
### タスクの取得と待機  
 `ProcessAsync` メソッドでは、`Dim result = Await DoSomethingAsync()` \(Visual Basic\) または `var result = await DoSomethingAsync();` \(C\#\) ステートメントは、次の 2 つのステートメントの省略形です。  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 コードの最初の行は async メソッドを呼び出し、タスクを返します。  そのタスクは次のコード行の await 演算子に関連付けられています。  await ステートメントがメソッド \(`ProcessAsync`\) を終了し、別のタスクを返します。  await 演算子に関連付けられているタスクが完了すると、コードは await メソッドの後のメソッド \(`ProcessAsync`\) から再開されます。  
  
 await ステートメントはすぐに別のタスクを返すとき、そのタスクは await 演算子 \(`ProcessAsync`\) が含まれる async メソッドの戻り引数です。  await よって返されるタスクには、同じメソッド内の await の後ろで発生するコードの実行が含まれます。それが理由で、そのタスクは、await に関連付けられているタスクとは異なります。  
  
## ステップ インとステップ オーバー  
 **\[ステップ イン\]** コマンドはメソッドにステップ インしますが、**\[ステップ オーバー\]** コマンドはメソッド呼び出しを実行してから、呼び出し元のメソッドの次の行で中断します。  詳細については、「[コードをステップ イン、ステップ オーバー、ステップ アウトする](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code)」を参照してください。  
  
 次の手順では、await ステートメントで **\[ステップ イン\]** または **\[ステップ オーバー\]** コマンドを選択したときの動作を示しています。  
  
1.  コンソール アプリケーションのコードを次のコードに置き換えます。  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  F11 キーを押すかメニュー バーで **\[デバッグ\]**、**\[ステップ イン\]** の順にクリックして、await 演算子を含むステートメントでの \[`Step Into`\] コマンドの動作を見てみます。  
  
     アプリケーションが起動され、最初の行で中断されます。その行は Visual Basic では `Sub Main()`、C\# では `Main` メソッドの始め中かっこです。  
  
3.  F11 キーを 3 回以上押します。  
  
     アプリケーションは `ProcessAsync` メソッド内の await ステートメントに達します。  
  
4.  F11 キーを押します。  
  
     アプリケーションは `DoSomethingAsync` メソッドに達して、その最初の行で中断されます。  `await` ステートメントで、アプリケーションがすぐに呼び出し元のメソッド \(`Main`\) に戻っても、この動作は同じです。  
  
5.  アプリケーションが `ProcessAsync` メソッド内の await ステートメントに戻るまで、F11 キーを押し続けます。  
  
6.  F11 キーを押します。  
  
     アプリケーションが await ステートメントの次の行で中断されます。  
  
7.  メニュー バーで **\[デバッグ\]**、**\[デバッグの停止\]** の順にクリックして、アプリケーションの実行を停止します。  
  
     次の手順では、await ステートメントでの **\[ステップ オーバー\]** コマンドの動作示します。  
  
8.  F11 キーを 4 回押すか、メニュー バーで **\[デバッグ\]** をクリックして **\[ステップ イン\]** を 4 回クリックします。  
  
     アプリケーションは `ProcessAsync` メソッド内の await ステートメントに達します。  
  
9. F10 キーを押すか、メニュー バーで **\[デバッグ\]**、**\[ステップ オーバー\]** の順にクリックします。  
  
     実行が await ステートメントの次の行で中断されます。  await ステートメントで、アプリケーションがすぐに呼び出し元のメソッド \(`Main`\) に戻っても、この動作は同じです。  \[`Step Over`\] コマンドは、次に実行される `DoSomethingAsync` メソッドをステップ オーバーします。  
  
10. メニュー バーで **\[デバッグ\]**、**\[デバッグの停止\]** の順にクリックして、アプリケーションの実行を停止します。  
  
     次の手順に示すように、**\[ステップ イン\]** コマンドと **\[ステップ オーバー\]** コマンドの動作は、await 演算子が async メソッドの呼び出しと違う行にあると、若干異なります。  
  
11. `ProcessAsync` メソッドは await ステートメントを次のコードに置き換えます。  元の await ステートメントは次の 2 つのステートメントの省略形です。  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. F11 キーを押すか、メニュー バーで **\[デバッグ\]** をクリックして **\[ステップ イン\]** を複数回クリックすることで、実行を開始し、コードをステップ実行します。  
  
     `DoSomethingAsync` の呼び出しに達すると、**\[ステップ イン\]** コマンドは `DoSomethingAsync` メソッドで中断されますが、**\[ステップ オーバー\]** コマンドは次に実行されるステートメントに進みます。  await ステートメントに達すると、いずれのコマンドも await の次のステートメントで中断されます。  
  
## \[ステップ アウト\]  
 async でないメソッドの場合、**\[ステップ アウト\]** コマンドはメソッド呼び出しに続くコード内の呼び出し元のメソッドで中断されます。  async メソッドの場合、呼び出し元のメソッド内のどこで中断されるかのロジックはより複雑です。そのロジックは、**\[ステップ アウト\]** コマンドを async メソッドの最初の行で実行するかどうかによって異なります。  
  
1.  コンソール アプリケーションのコードを次のコードに置き換えます。  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  `DoSomethingAsync` メソッド内の `Debug.WriteLine("before")` 行にブレークポイントを設定します。  
  
     その目的は、async メソッド内の最初の行でない行からの **\[ステップ アウト\]** コマンドの動作を示すことです。  
  
3.  F5 キーを押すかメニュー バーで **\[デバッグ\]**、**\[デバッグ開始\]** の順にクリックして、アプリケーションを起動します。  
  
     コードは `DoSomethingAsync` メソッド内の `Debug.WriteLine("before")` で中断されます。  
  
4.  Shift \+ F11 キーを押すか、メニュー バーで **\[デバッグ\]**、**\[ステップ アウト\]** の順にクリックします。  
  
     アプリケーションは呼び出し元のメソッド内で、現在のメソッドに関連付けられているタスクの await ステートメントで中断されます。  その結果、アプリケーションは `ProcessAsync` メソッド内の await ステートメントで中断されます。  アプリケーションは、`DoSomethingAsync` メソッドに続く `Dim z = 0` \(Visual Basic\) または `int z = 0;` \(C\#\) では中断されません。  
  
5.  メニュー バーで **\[デバッグ\]**、**\[デバッグの停止\]** の順にクリックして、アプリケーションの実行を停止します。  
  
     次の手順では、async メソッドの最初の行からの **\[ステップ アウト\]** の動作を示します。  
  
6.  既存のブレークポイントを削除し、`DoSomethingAsync` メソッドの最初の行にブレークポイントを追加します。  
  
     C\# では、`DoSomethingAsync` メソッドの始め中かっこにブレークポイントを追加します。  Visual Basic では、`Async Function DoSomethingAsync() As Task(Of Integer)` が含まれる行にブレークポイントを追加します。  
  
7.  F5 キーを押してアプリケーションを実行します。  
  
     コードは `DoSomethingAsync` メソッドの最初の行で中断されます。  
  
8.  メニュー バーで **\[デバッグ\]**、**\[Windows\]**、**\[出力\]** の順にクリックします。  
  
     **\[出力\]** ウィンドウが開きます。  
  
9. Shift \+ F11 キーを押すか、メニュー バーで **\[デバッグ\]**、**\[ステップ アウト\]** の順にクリックします。  
  
     アプリケーションは、async メソッドが最初の await に達するまで実行されて、呼び出し元のステートメントで中断されます。  その結果、アプリケーションは `Dim the Task = DoSomethingAsync()` \(Visual Basic\) または `var theTask = DoSomethingAsync();` \(C\#\) で中断されます。  "変更前" のメッセージは \[出力\] ウィンドウに表示されていますが、"変更後" のメッセージはまだ表示されていません。  
  
10. F5 キーを押して、アプリケーションを続行します。  
  
     アプリケーションは、呼び出し先の async 関数 \(`DoSomethingAsync`\) 内の await ステートメントの次のステートメントから続行されます。  "変更後" のメッセージが \[出力\] ウィンドウに表示されます。  
  
## 参照  
 [デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)