---
title: Assert クラスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: 14bdea144a28e971d99ea8528b66e0bce1164035
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539398"
---
# <a name="using-the-assert-classes"></a>Assert クラスの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Assert クラスを使用して](https://docs.microsoft.com/visualstudio/test/using-the-assert-classes)します。  
  
UnitTestingFramework 名前空間の Assert クラスは、特定の機能を確認するために使用します。 単体テスト メソッドは開発コード内のメソッドのコードを実行しますが、Assert ステートメントを含める場合にのみコードの動作の正確性を報告します。  
  
## <a name="kinds-of-asserts"></a>Assert の種類  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 名前空間には複数の Assert クラスが用意されています。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 テスト メソッドでは、Assert.AreEqual() などの Assert クラスのメソッドをいくつでも呼び出すことができます。 Assert クラスには、多くの選択可能なメソッドがあり、それらのメソッドの多くには複数のオーバーロードが存在します。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 CollectionAssert クラスを使用して、オブジェクトのコレクションを比較したり、1 つ以上のコレクションの状態を確認したりします。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 StringAssert クラスを使用して、文字列を比較します。 このクラスには、StringAssert.Contains、StringAssert.Matches、StringAssert.StartsWith など、さまざまな便利なメソッドが含まれています。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 AssertFailedException 例外は、テストが失敗するたびにスローされます。 タイムアウトした場合、予期しない例外がスローされた場合、または "失敗しました" の結果を出力する Assert ステートメントを含む場合、テストは失敗します。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 AssertInconclusiveException は、テストで "結果を作成できません" の結果が出力されるたびにスローされます。 通常、まだ編集中のテストに対して、そのテストを実行する準備ができていないことを示すために Assert.Inconclusive ステートメントを追加します。  
  
> [!NOTE]
>  別の方法として、実行の準備が整っていないテストに Ignore 属性でマークを付けることもできます。 しかし、この方法には、まだ実装していないテストの個数に関するレポートを簡単に生成できないという短所があります。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 新しい Assert 例外クラスを記述する場合には、そのクラスに基本クラス UnitTestAssertException を継承させると、例外が発生した場合に、その例外がテストや運用コードからスローされた予期しない例外なのか、アサーションによる失敗なのかを識別しやすくなります。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 テスト メソッドを ExpectedExceptionAttribute 属性で修飾して、開発コード内のメソッドによって例外がスローされることが予期される場合に、例外が実際にそのメソッドでスローされたことを確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [既存コードに対する単体テストの作成と実行](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)



