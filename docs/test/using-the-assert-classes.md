---
title: "Assert クラスの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert クラス"
  - "Assert ステートメント"
  - "単体テスト、Assert ステートメント"
  - "単体テスト、Assert クラス"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Assert クラスの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

UnitTestingFramework 名前空間の Assert クラスは、個別の機能を確認するために使用します。  単体テスト メソッドは、開発コード内のメソッドのコードを実行しますが、Assert ステートメントを含むするときにのみコードの実行の正確性報告します。  
  
## Assert の種類  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 名前空間には複数の Assert クラスが用意されています。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 テスト メソッドでは、Assert.AreEqual\(\) などの Assert クラスのメソッドを任意の数だけ呼び出すことができます。  Assert クラスには、多くの選択可能なメソッドがあり、それらのメソッドの多くには複数のオーバーロードが存在します。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 CollectionAssert クラスを使用して、オブジェクトのコレクションを比較したり、1 つ以上のコレクションの状態を確認したりします。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 StringAssert クラスを使用して、文字列を比較します。  このクラスには、StringAssert.Contains、StringAssert.Matches、StringAssert.StartsWith など、さまざまな便利なメソッドが含まれています。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 AssertFailedException 例外は、テストが失敗すると常にスローされます。  タイムアウトした場合、予期しない例外がスローされた場合、または "失敗しました" の結果を出力する Assert ステートメントを含む場合、テストは失敗します。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 AssertInconclusiveException は、テストで "結果を作成できません" の結果が出力されると常にスローされます。  通常 Assert.Inconclusive ステートメントは、まだ編集中のテストに対して、そのテストを実行する準備ができていないことを示すために追加します。  
  
> [!NOTE]
>  他の方法としては、実行の準備が整っていないテストに Ignore 属性を設定して示す方法もあります。  ただし、この方法には、まだ実装していないテストの個数に関するレポートを簡単に作成できないという短所があります。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 新規の Assert 例外クラスを作成する場合には、そのクラスに UnitTestAssertException 基本クラスを継承させると、例外が発生した場合に、その例外がテストや製品コードからスローされた予期しない例外なのか、アサーションによる失敗なのかを識別しやすくなります。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 ExpectedExceptionAttribute 属性をテスト メソッドで使用して、開発コード内のメソッドによって例外がスローされることが予期される場合に、例外が実際にそのメソッドでスローされたかを確認します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/ja-jp/e8370b93-085b-41c9-8dec-655bd886f173)