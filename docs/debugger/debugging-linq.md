---
title: "LINQ のデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ, LINQ"
  - "LINQ, デバッグ"
  - "LINQ, エディット コンティニュ"
  - "LINQ, ステップ実行"
  - "LINQ, 表示 (結果をデバッガーで)"
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LINQ のデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、統合言語クエリ \(LINQ\) コードのデバッグをサポートしていますが、いくつかの制約事項があります。ステップ実行、ブレークポイントの設定、デバッガー ウィンドウでの結果の表示など、ほとんどのデバッグ機能を、LINQ ステートメントと組み合わせて使用することができます。  このトピックでは、LINQ のデバッグに伴う主要な制限事項について説明します。  
  
## このトピックの内容  
 [LINQ の結果の表示](../debugger/debugging-linq.md#BKMK_ViewingLINQResults)  
  
 [ステップ実行と LINQ](../debugger/debugging-linq.md#BKMK_SteppingAndLinq)  
  
 [LINQ でサポートされないエディット コンティニュ](../debugger/debugging-linq.md#BKMK_EditandContinueNotSupportedforLINQ)  
  
##  <a name="BKMK_ViewingLINQResults"></a> LINQ の結果の表示  
 LINQ ステートメントの結果を表示するには、DataTip、\[ウォッチ\] ウィンドウ、および \[クイック ウォッチ\] ダイアログ ボックスを使用します。  ソース ウィンドウを使用すると、ソース ウィンドウ内のクエリ上でポインターを停止し、DataTip を表示することができます。  LINQ 変数をコピーし、\[ウォッチ\] ウィンドウや \[クイック ウォッチ\] ダイアログ ボックスに貼り付けることができます。  
  
 LINQ では、クエリは作成または宣言の時点では評価されず、実行時にのみ評価されます。  したがって、評価の時点までクエリには値がありません。  クエリの作成および評価の詳細については、「[Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)」または「[初めての LINQ クエリの作成](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)」を参照してください。  
  
 クエリの結果を表示するためには、デバッガーがクエリを評価する必要があります。  そのため、LINQ クエリの結果をデバッガーで表示するときには、クエリが評価されることにより、次のような影響が生じます。  
  
-   クエリの評価には時間がかかります。  結果ノードを展開するときにも時間を要します。  クエリによっては、評価の反復によってパフォーマンスが大幅に低下することがあります。  
  
-   クエリの評価は、データの値やプログラムの状態が変化するという副作用をもたらすことがあります。  すべてのクエリに副作用があるわけではありません。  クエリの評価に副作用があるかどうかを確認するためには、クエリを実装するコードの内容を把握する必要があります。  
  
##  <a name="BKMK_SteppingAndLinq"></a> ステップ実行と LINQ  
 LINQ コードをデバッグする場合は、ステップ実行に動作上の違いがいくつかあるため、理解しておく必要があります。  
  
### LINQ to SQL  
 LINQ to SQL クエリでは、述語コードがデバッガーによる処理の対象外となります。  そのため、述語コードにステップ インすることはできません。  式ツリーにコンパイルされるクエリは、デバッガーによる処理の対象とならないコードを生成します。  
  
### Visual Basic でのステップ実行  
 Visual Basic プログラムをステップ実行し、デバッガーがクエリ宣言を検出すると、デバッガーはその宣言にはステップ インせず、宣言全体を 1 つのステートメントとして強調表示します。  この動作が発生するのは、クエリが呼び出されるまで評価されないためです。  詳細については、「[Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)」を参照してください。  
  
 次のようなコードをステップ実行すると、クエリを作成するクエリ宣言が 1 つのステートメントとして強調表示されます。  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 さらにステップ実行すると、`For Each cur In x` が強調表示されます。  次の手順では、デバッガーが関数 `MyFunction` にステップ インします。  `MyFunction` のステップ実行の後、デバッガーは `Console.WriteLine(cur.ToSting())` に戻ります。  どの段階でも、デバッガーはクエリ宣言内の述語コードにはステップ インしません。ただし、述語コードの評価は行います。  
  
### 述語コードを関数に置き換えてステップ実行を可能にする \(Visual Basic\)  
 デバッグのために述語コードをステップ実行する必要がある場合は、述語コードを同じコードが含まれる関数の呼び出しに置き換えることができます。  たとえば、次のようなコードがあるとします。  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 述語コードを次のように `IsEven` という新しい関数に移動できます。  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 修正したクエリは、`items` のパスごとに関数 `IsEven` を呼び出します。  デバッガー ウィンドウで各項目が指定された条件を満たすかどうかを確認し、`IsEven` 内のコードをステップ実行できます。  この例の述語コードはきわめて単純です。  もっと複雑な述語コードをデバッグする場合にも、この方法が十分役に立つことがあります。  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> LINQ でサポートされないエディット コンティニュ  
 エディット コンティニュは、LINQ クエリの変更をサポートしていません。  デバッグ セッション中に LINQ ステートメントを追加、削除、または変更すると、そのような変更がエディット コンティニュでサポートされていないことを示すダイアログ ボックスが表示されます。  このとき、変更を元に戻すか、デバッグ セッションを中止して編集済みのコードで新たなセッションを開始するかを選択できます。  
  
 また、エディット コンティニュでは、LINQ ステートメントで使用されている変数の型や値の変更もサポートされていません。  この場合も、変更を元に戻すか、デバッグ セッションを中止して新たなセッションを開始するかを選択できます。  
  
 C\# では、LINQ クエリを含むメソッドのコードに対してエディット コンティニュを使用することはできません。  
  
 Visual Basic では、LINQ クエリを含むメソッドであっても、LINQ 以外のコードであればエディット コンティニュを使用できます。  LINQ ステートメントの前であれば、LINQ クエリの行番号が変わる場合でも、コードの追加や削除を行うことができます。  LINQ 以外のコードの Visual Basic デバッグは、LINQ が導入される前と同じように動作します。  ただし、デバッグを中止して変更を適用しない限り、LINQ クエリを変更、追加、または削除することはできません。  
  
## 参照  
 [Debugging SQL](http://msdn.microsoft.com/ja-jp/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [副作用と式](../Topic/Side%20Effects%20and%20Expressions.md)   
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)