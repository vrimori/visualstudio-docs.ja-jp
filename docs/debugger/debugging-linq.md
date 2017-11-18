---
title: "LINQ のデバッグ |Microsoft ドキュメント"
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
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfd356931e33e900d35094c4714d0c3f6fc93abe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-linq"></a>LINQ のデバッグ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、統合言語クエリ (LINQ) コードのデバッグをサポートしていますが、いくつかの制約事項があります。 ステップ実行、ブレークポイントの設定、デバッガー ウィンドウでの結果の表示など、ほとんどのデバッグ機能を、LINQ ステートメントと組み合わせて使用することができます。 このトピックでは、LINQ のデバッグの主要な制限事項について説明します。  
  
##  <a name="BKMK_ViewingLINQResults"></a>LINQ の結果を表示します。  
 LINQ ステートメントの結果を表示するには、DataTip、[ウォッチ] ウィンドウ、および [クイック ウォッチ] ダイアログ ボックスを使用します。 ソース ウィンドウを使用すると、ソース ウィンドウ内のクエリ上でポインターを停止し、DataTip を表示することができます。 LINQ 変数をコピーし、[ウォッチ] ウィンドウや [クイック ウォッチ] ダイアログ ボックスに貼り付けることができます。  
  
 LINQ では、クエリは作成または宣言の時点では評価されず、実行時にのみ評価されます。 したがって、評価の時点までクエリには値がありません。 クエリの作成および評価の詳細については、次を参照してください。 [LINQ クエリ (c#) の概要](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)または[書き込み、最初の LINQ クエリの](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)します。  
  
 クエリの結果を表示するためには、デバッガーがクエリを評価する必要があります。 そのため、LINQ クエリの結果をデバッガーで表示するときには、クエリが評価されることにより、次のような影響が生じます。  
  
-   クエリの評価には時間がかかります。 結果ノードを展開するときにも時間を要します。 クエリによっては、評価の反復によってパフォーマンスが大幅に低下することがあります。  
  
-   クエリの評価は、データの値やプログラムの状態が変化するという副作用をもたらすことがあります。 すべてのクエリに副作用があるわけではありません。 クエリの評価に副作用があるかどうかを確認するためには、クエリを実装するコードの内容を把握する必要があります。  
  
##  <a name="BKMK_SteppingAndLinq"></a>ステップ実行と LINQ  
 LINQ コードをデバッグする場合は、ステップ実行に動作上の違いがいくつかあるため、理解しておく必要があります。  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL クエリでは、述語コードがデバッガーによる処理の対象外となります。 そのため、述語コードにステップ インすることはできません。 式ツリーにコンパイルされるクエリは、デバッガーによる処理の対象とならないコードを生成します。  
  
### <a name="stepping-in-visual-basic"></a>Visual Basic でのステップ実行  
 Visual Basic プログラムをステップ実行し、デバッガーがクエリ宣言を検出すると、デバッガーはその宣言にはステップ インせず、宣言全体を 1 つのステートメントとして強調表示します。 この動作が発生するのは、クエリが呼び出されるまで評価されないためです。 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)です。  
  
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
  
 さらにステップ実行すると、`For Each cur In x` が強調表示されます。 次の手順では、デバッガーが関数 `MyFunction` にステップ インします。 `MyFunction` のステップ実行の後、デバッガーは `Console.WriteLine(cur.ToSting())` に戻ります。 どの段階でも、デバッガーはクエリ宣言内の述語コードにはステップ インしません。ただし、述語コードの評価は行います。  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>述語コードを関数に置き換えてステップ実行を可能にする (Visual Basic)  
 デバッグのために述語コードをステップ実行する必要がある場合は、述語コードを同じコードが含まれる関数の呼び出しに置き換えることができます。 たとえば、次のようなコードがあるとします。  
  
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
  
 修正したクエリは、`IsEven` のパスごとに関数 `items` を呼び出します。 デバッガー ウィンドウで各項目が指定された条件を満たすかどうかを確認し、`IsEven` 内のコードをステップ実行できます。 この例の述語コードはきわめて単純です。 もっと複雑な述語コードをデバッグする場合にも、この方法が十分役に立つことがあります。  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a>エディット コンティニュの LINQ のサポートされていません  
 エディット コンティニュは、LINQ クエリの制限事項と変更をサポートします。 詳細については、「 [EnC サポートされている変更](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>関連項目  
 [SQL のデバッグ](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)    
 [デバッガーでの例外を管理します。](../debugger/managing-exceptions-with-the-debugger.md)   
 [LINQ クエリの概要 (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Visual Basic における LINQ の概要](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)