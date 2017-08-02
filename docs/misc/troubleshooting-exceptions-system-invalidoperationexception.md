---
title: "例外のトラブルシューティング : System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException クラス"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.InvalidOperationException
<xref:System.InvalidOperationException?displayProperty=fullName> は、オブジェクトのメソッドが呼び出されたときに、そのオブジェクトの状態が、メソッドの呼び出しをサポートできない場合にスローされます。 この例外は、メソッドがメインまたは UI 以外のスレッドから UI を操作しようとしたときにもスローされます。  
  
> [!IMPORTANT]
>  <xref:System.InvalidOperationException> はさまざまな状況でスローされるので、例外処理アシスタントに表示される <xref:System.Exception.Message%2A> を読んで、その内容を理解することが重要です。  
  
##  <a name="BKMK_In_this_article"></a> この記事の内容  
 [UI 以外のスレッドで実行されているメソッドによって UI が更新される](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [foreach (Visual Basic では For Each) ブロック内のステートメントによって、反復処理中のコレクションが変更される](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [null の Nullable &lt;T&gt; が T にキャストされる](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [System.Linq.Enumerable メソッドが空のコレクションに対して呼び出される](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [関連記事](#BKMK_Related_articles)  
  
 この記事のコード例では、アプリにおいて、<xref:System.InvalidOperationException> 例外が発生する可能性があるいくつかの一般的な状況を示します。問題への対処方法は、その状況によって異なります。アプリの機能にとって致命的な例外がある場合は、[try … catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \(Visual Basic では [Try ..Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)\) コンストラクトを使用してその例外をキャプチャし、アプリの状態を消去した後、アプリを終了することをお勧めします。ただし、その他の <xref:System.InvalidOperationException> は、予想して回避できます。変更後のメソッドの例で、これらの手法をいくつか紹介します。  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> UI 以外のスレッドで実行されているメソッドによって UI が更新される  
 [UI 以外のスレッドからの UI の更新を原因とする InvalidOperationException の発生](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [UI 以外のスレッドにおける InvalidOperationExceptions の回避](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 Windows フォームや Windows Presentation Foundation \(WPF\) など、ほとんどの .NET GUI \(グラフィカル ユーザー インターフェイス\) アプリ フレームワークでは、UI を管理するスレッド \(**メイン**または **UI** スレッド\) からのみ、GUI オブジェクトにアクセスできます。 UI 以外のスレッドから UI 要素にアクセスしようとすると、<xref:System.InvalidOperationException> がスローされます。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> UI 以外のスレッドからの UI の更新を原因とする InvalidOperationException の発生  
  
> [!NOTE]
>  次の例では、[Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md) を使用して UI 以外のスレッドを作成します。 ただし、これらの例はすべて .NET の[Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md)に関連しています。  
  
 これらの例では、`ThreadsExampleBtn_Click` イベント ハンドラーが `DoSomeWork` メソッドを 2 回呼び出します。 メソッドの 1 回目の呼び出し \(`DoSomeWork(20);`\) は同期的に実行され、成功します。 ただし、2 回目の呼び出し \(`Task.Run( () => { DoSomeWork(1000);});`\) はアプリの[スレッド プール](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx)内のスレッドで実行されます。 この呼び出しは UI 以外のスレッドから UI を更新しようとするので、ステートメントは <xref:System.InvalidOperationException> をスローします。  
  
 **WPF およびストア アプリ**  
  
> [!NOTE]
>  ストア Phone アプリでは、より詳細な <xref:System.Exception> ではなく、<xref:System.InvalidOperationException> がスローされます。  
  
 **例外メッセージ:**  
  
|||  
|-|-|  
|WPF アプリ|追加情報: このオブジェクトは別のスレッドに所有されているため、呼び出しスレッドはこのオブジェクトにアクセスできません。|  
|ストア アプリ|追加情報: アプリケーションは、別のスレッドにマーシャリングされたインターフェイスを呼び出しました。 \(HRESULT からの例外: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Windows フォーム アプリ**  
  
 **例外メッセージ:**  
  
-   追加情報: 有効ではないスレッド間の操作: コントロールが作成されたスレッド以外のスレッドからコントロール 'TextBox1' がアクセスされました。  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [UI 以外のスレッドで実行されているメソッドによって UI が更新される](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> UI 以外のスレッドにおける InvalidOperationExceptions の回避  
 Windows UI フレームワークでは、UI 要素のメンバーへの呼び出しが UI スレッドで実行されているかどうかを確認するメソッドと、UI スレッドでの呼び出しをスケジュールするその他のメソッドを含む、*ディスパッチャー* パターンが実装されます。  
  
 **WPF アプリ**  
  
 WPF アプリでは、いずれかの <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> メソッドを使用して、UI スレッドでデリゲートを実行します。 必要に応じて、<xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> メソッドを使用して、メソッドが UI 以外のスレッドで実行されているかどうかを確認します。  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Windows フォーム アプリ**  
  
 Windows フォーム アプリでは、<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> メソッドを使用して、UI スレッドを更新するデリゲートを実行します。 必要に応じて、<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> プロパティを使用して、メソッドが UI 以外のスレッドで実行されているかどうかを確認します。  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **ストア アプリ**  
  
 ストア アプリでは、<xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> メソッドを使用して、UI スレッドを更新するデリゲートを実行します。 必要に応じて、<xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> プロパティを使用して、メソッドが UI 以外のスレッドで実行されているかどうかを確認します。  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [UI 以外のスレッドで実行されているメソッドによって UI が更新される](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> foreach \(Visual Basic では For Each\) ブロック内のステートメントによって、反復処理中のコレクションが変更される  
 [foreach での InvalidOperationException の発生](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [ループ内での InvalidOperationExceptions の回避](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ステートメント \(Visual Basic では [For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)\) は、<xref:System.Collections.IEnumerable?displayProperty=fullName> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> インターフェイスが実装された配列またはコレクション内の各要素に対して、埋め込みステートメントのグループを繰り返し実行します。`foreach` ステートメントを使用すると、コレクションの反復処理による要素の読み取りと変更を行うことができますが、コレクションに対する項目の追加または削除を行うことはできません。 foreach ステートメント内でソース コレクションに対して項目を追加または削除した場合、<xref:System.InvalidOperationException> がスローされます。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> foreach での InvalidOperationException の発生  
 この例では、<xref:System.InvalidOperationException> ステートメントが foreach ブロック内でリストを変更しようとしたときに、`numList.Add(5);` がスローされます。  
  
 **例外メッセージ:**  
  
-   追加情報: コレクションは変更されています。列挙操作は実行されない場合があります。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [foreach (Visual Basic では For Each) ブロック内のステートメントによって、反復処理中のコレクションが変更される](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> ループ内での InvalidOperationExceptions の回避  
  
> [!IMPORTANT]
>  コレクションの反復処理中に、要素をリストに対して追加または削除した場合、予測しにくい想定外の悪影響が発生する可能性があります。 可能な限り、この操作を反復処理以外の部分に移動してください。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 コレクションの反復処理中に、リストに対して要素を追加または削除する必要がある場合は、[for](/dotnet/csharp/language-reference/keywords/for) \(Visual Basic では [For](/dotnet/visual-basic/language-reference/statements/for-next-statement)\) ループを使用します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [foreach (Visual Basic では For Each) ブロック内のステートメントによって、反復処理中のコレクションが変更される](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> null の Nullable \<T\> が T にキャストされる  
 [無効なキャストを原因とする InvalidOperationException の発生](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [無効なキャストを原因とする InvalidOperationException の回避](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 <xref:System.Nullable%601> \(Visual Basic では `null`\) の `Nothing` 構造体を、その基になる型にキャストした場合、<xref:System.InvalidOperationException> 例外がスローされます。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> 無効なキャストを原因とする InvalidOperationException の発生  
 このメソッドでは、Select メソッドが dbQueryResults の null 要素を int にキャストしたときに、<xref:System.InvalidOperationException> がスローされます。  
  
 **例外メッセージ:**  
  
-   追加情報: Null 許容のオブジェクトには値を指定しなければなりません。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [null の Nullable &lt;T&gt; が T にキャストされる](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> 無効なキャストを原因とする InvalidOperationException の回避  
 <xref:System.InvalidOperationException> を回避する方法は、次のとおりです。  
  
-   <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> プロパティを使用して、null 以外の要素のみを選択します。  
  
-   オーバーロードされたいずれかの <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> メソッドを使用して、null の項目の既定値を指定します。  
  
 **Nullable\<T\>.HasValue の例**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Nullable\<T\>.GetValueOrDefault の例**  
  
 この例では、<xref:System.Nullable%601.GetValueOrDefault%28%600%29> を使用して、`dbQueryResults` から返されることが予期される値以外の既定値を指定します。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [null の Nullable &lt;T&gt; が T にキャストされる](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> System.Linq.Enumerable メソッドが空のコレクションに対して呼び出される  
 <xref:System.Linq.Enumerable> メソッド <xref:System.Linq.Enumerable.Aggregate%2A>、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Last%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.First%2A>、<xref:System.Linq.Enumerable.Single%2A>、および <xref:System.Linq.Enumerable.SingleOrDefault%2A> は、シーケンスに対して操作を実行し、1 つの結果を返します。  
  
 これらのメソッドの一部のオーバーロードは、シーケンスが空の場合、<xref:System.InvalidOperationException> 例外をスローします \(その他のオーバーロードは `null` \(Visual Basic では `Nothing`\) を返します\)。<xref:System.Linq.Enumerable.SingleOrDefault%2A> も、シーケンスに複数の要素が含まれている場合、<xref:System.InvalidOperationException> をスローします。  
  
> [!TIP]
>  このセクションで説明する <xref:System.Linq.Enumerable> メソッドのほとんどは、オーバーロードされています。 使用するオーバーロードは、その動作を理解したうえで選択してください。  
  
 **例外メッセージ:**  
  
 [Aggregate、Average、Last、Max、および Min メソッド](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [First および FirstOrDefault メソッド](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Single および SingleOrDefault メソッド](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Aggregate、Average、Last、Max、および Min メソッド  
  
-   追加情報: シーケンスに要素が含まれていません  
  
 **Average での InvalidOperationException の発生**  
  
 この例では、次のメソッドが <xref:System.InvalidOperationException> メソッドを呼び出すときに、<xref:System.Linq.Enumerable.Average%2A> がスローされます。これは、Linq 式が 4 を超える要素を含まないシーケンスを返すからです。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 空のシーケンスを確認せずに、これらのメソッドのいずれかを使用した場合、シーケンスが空ではないこと、および空のシーケンスの発生を予期していないことを暗黙的に仮定することになります。 シーケンスが空ではないと仮定した場合、例外をキャッチまたはスローすることは適切です。  
  
 **空のシーケンスを原因とする InvalidOperationException の回避**  
  
 いずれかの <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> メソッドを使用して、シーケンスが空であるかどうかを確認します。  
  
> [!TIP]
>  <xref:System.Linq.Enumerable.Any%2A> を使用すると、シーケンスに平均して多くの要素が含まれている可能性がある場合や、シーケンスを生成する操作の負荷が高い場合、確認のパフォーマンスが向上することがあります。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [System.Linq.Enumerable メソッドが空のコレクションに対して呼び出される](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> First および FirstOrDefault メソッド  
 <xref:System.Linq.Enumerable.First%2A> はシーケンス内の最初の項目を返し、シーケンスが空の場合は <xref:System.InvalidOperationException> をスローします。<xref:System.Linq.Enumerable.FirstOrDefault%2A> の代わりに <xref:System.Linq.Enumerable.First%2A> メソッドを呼び出して、例外をスローする代わりに、指定した値または既定値を返すことができます。  
  
> [!NOTE]
>  .NET Framework では、型に既定値の概念があります。 たとえば、参照型の既定値は null で、整数型の既定値は 0 です。 「[既定値の一覧表](/dotnet/csharp/language-reference/keywords/default-values-table)」を参照してください。  
  
 **First での InvalidOperationException の発生**  
  
 <xref:System.Linq.Enumerable.First%2A> は、指定した条件を満たすシーケンス内の最初の要素を返す最適化メソッドです。 条件を満たす要素が見つからない場合、このメソッドは <xref:System.InvalidOperationException> 例外をスローします。  
  
 この例では、`First` に 4 よりも大きい要素が含まれていないので、`dbQueryResults` メソッドは例外をスローします。  
  
 **例外メッセージ:**  
  
-   追加情報: シーケンスに、一致する要素は含まれていません  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **FirstOrDefault を原因とする例外の回避**  
  
 <xref:System.Linq.Enumerable.FirstOrDefault%2A> の代わりに、いずれかの <xref:System.Linq.Enumerable.First%2A> メソッドを使用して、`firstNum` シーケンスに少なくとも 1 つの要素が含まれているかどうかを確認できます。 クエリの条件を満たす要素が見つからない場合は、指定した値または既定値が返されます。 該当する要素が見つかったかどうかは、戻り値で確認できます。  
  
> [!NOTE]
>  型の既定値がシーケンス内の有効な要素である場合、<xref:System.Linq.Enumerable.FirstOrDefault%2A> を使用するときの実装は、より複雑になる可能性があります。  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [System.Linq.Enumerable メソッドが空のコレクションに対して呼び出される](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Single および SingleOrDefault メソッド  
 <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> メソッドは、シーケンスの唯一の要素、または指定されたテストの条件を満たす、シーケンスの 1 つの要素を返します。  
  
 シーケンス内に要素がない場合、または複数の要素がある場合、このメソッドは <xref:System.InvalidOperationException> 例外をスローします。  
  
 <xref:System.Linq.Enumerable.SingleOrDefault%2A> を使用すると、シーケンスに要素が含まれていない場合に、例外をスローする代わりに、指定した値または既定値を返すことができます。 ただし、<xref:System.Linq.Enumerable.SingleOrDefault%2A> を使用しても、選択述語と一致する複数の要素がシーケンスに含まれている場合は、<xref:System.InvalidOperationException> がスローされます。  
  
> [!NOTE]
>  .NET Framework では、型に既定値の概念があります。 たとえば、参照型の既定値は null で、整数型の既定値は 0 です。 「[既定値の一覧表](/dotnet/csharp/language-reference/keywords/default-values-table)」を参照してください。  
  
 **Single での InvalidOperationExceptions の発生**  
  
 この例では、`singleObject` に 4 より大きい要素が含まれていないので、<xref:System.InvalidOperationException> は `dbQueryResults` をスローします。  
  
 **例外メッセージ:**  
  
-   追加情報: シーケンスに、一致する要素は含まれていません  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Single または SingleOrDefault での InvalidOperationExceptions の発生**  
  
 この例では、`singleObject` に 2 より大きい複数の要素が含まれているので、<xref:System.InvalidOperationException> は `dbQueryResults` をスローします。  
  
 **例外メッセージ:**  
  
-   追加情報: シーケンスに複数の一致する要素が含まれています  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Single での InvalidOperationExceptions の回避**  
  
 <xref:System.Linq.Enumerable.Single%2A> と <xref:System.Linq.Enumerable.SingleOrDefault%2A> をドキュメントとして使用して、開発者の意図を伝えることもできます。<xref:System.Linq.Enumerable.Single%2A> からは、条件から返される結果が 1 つだけであることを予期していることがよくわかります。<xref:System.Linq.Enumerable.SingleOrDefault%2A> からは、予期している結果の数が 1 または 0 であり、それを超える数ではないことがわかります。 これらの条件が無効である場合は、<xref:System.InvalidOperationException> をスローおよびキャッチすることが適切です。 ただし、無効な条件がある程度の頻度で発生することが予想される場合は、<xref:System.Linq.Enumerable> や <xref:System.Linq.Enumerable.First%2A> などの他の <xref:System.Linq.Enumerable.Where%2A> メソッドを使用して結果を生成することを検討してください。  
  
 開発中は、いずれかの <xref:System.Diagnostics.Debug.Assert%2A> メソッドを使用して、予期している内容を確認できます。 この例では、強調表示されたコードによってデバッガーが中断され、開発時のアサート ダイアログ ボックスが表示されます。 このアサートはリリース コードでは削除され、結果が無効である場合は <xref:System.Linq.Enumerable.Single%2A> が例外をスローします。  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> を使用し、その `count` パラメーターを 2 に設定すると、返されるシーケンスの要素が最大 2 つに制限されます。 このシーケンスには、確認する必要があるすべての状況 \(要素が 0 個、1 個、および複数の場合\) が含まれているので、シーケンスに多くの要素が含まれている可能性がある場合や、シーケンスを生成する操作の負荷が高い場合は、確認のパフォーマンスが向上することがあります。  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 リリース コードで例外を回避し、さらに無効な状態も処理する必要がある場合は、上記の手法を変更できます。 この例のメソッドは、switch ステートメント内の `moreThan2` によって返された要素の数に応じて、異なる処理を実行します。  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [System.Linq.Enumerable メソッドが空のコレクションに対して呼び出される](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> 関連記事  
 [例外のデザイン ガイドライン \(.NET Framework デザイン ガイドライン\)](http://msdn.microsoft.com/library/ms229014)  
  
 [例外の処理とスロー \(.NET Framework アプリケーションの基本\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [方法: 初回例外通知を受信する \(.NET Framework 開発ガイド\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [方法: PLINQ クエリで例外を処理する \(.NET Framework 開発ガイド\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [マネージ スレッドにおける例外 \(.NET Framework 開発ガイド\)](http://msdn.microsoft.com/library/ms228965)  
  
 [例外と例外処理 \(C\# プログラミング ガイド\)](http://msdn.microsoft.com/library/ms173160)  
  
 [例外処理ステートメント \(C\# リファレンス\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally ステートメント \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [例外処理 \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [C\+\+\/CLI の例外](http://msdn.microsoft.com/library/Hh875008)  
  
 [例外処理 \(タスク並列ライブラリ\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [例外処理 \(デバッグ\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [チュートリアル: 同時実行例外の処理 \(Visual Studio におけるデータのアクセス\)](http://msdn.microsoft.com/library/ms171936)  
  
 [方法: データバインド \(Windows フォーム\) により発生するエラーと例外を処理する](http://msdn.microsoft.com/library/k26k86tb)  
  
 [ネットワーク アプリにおける例外の処理 \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![ページのトップへ](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [この記事の内容](#BKMK_In_this_article)