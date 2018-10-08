---
title: 'Ca 2000: スコープが失われる前にオブジェクトを破棄 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 878c016f718693210a196d687ebe520b20cf277a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549070"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: スコープが失われる前にオブジェクトを破棄します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|カテゴリ|Microsoft.Reliability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 <xref:System.IDisposable> 型のローカル オブジェクトは作成されますが、そのオブジェクトに対するすべての参照がスコープ外になる前に、オブジェクトが破棄されていません。  
  
## <a name="rule-description"></a>規則の説明  
 破棄できるオブジェクトに対するすべての参照がスコープ外になる前に、オブジェクトが明示的に破棄されない場合、ガベージ コレクターでオブジェクトのファイナライザーが実行されるときに破棄されますが、タイミングは一定ではありません。 例外的なイベントが発生するとオブジェクトのファイナライザーを実行できないため、オブジェクトは明示的に破棄する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、オブジェクトに対するすべての参照がスコープ外になる前に、そのオブジェクトで <xref:System.IDisposable.Dispose%2A> を呼び出します。  
  
 `using` ステートメント (`Using` の場合は [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) を使用して、`IDisposable` を実装するオブジェクトをラップすることができます。 このステートメントによってラップされたオブジェクトは、`using` ブロックの終わりで自動的に破棄されます。  
  
 using ステートメントでは十分に IDisposable オブジェクトを保護できない次のような場合があります。この場合、CA2000 が発生する可能性があります。  
  
-   破棄可能オブジェクトを返すには、このオブジェクトは using ブロック外の try/finally ブロックで構築される必要があります。  
  
-   破棄可能オブジェクトのメンバーは、using ステートメントのコンストラクターでは初期化できません。  
  
-   1 つの例外ハンドラーによってのみ保護された入れ子のコンストラクター。 たとえば、オブジェクトに適用された  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     この場合、StreamReader オブジェクトの構築が失敗すると FileStream オブジェクトが閉じられなくなることがあるので、CA2000 が発生します。  
  
-   動的オブジェクトは、シャドウ オブジェクトを使用して IDisposable オブジェクトの Dispose パターンを実装する必要があります。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 `Dispose` を呼び出すオブジェクトに対して <xref:System.IO.Stream.Close%2A> などのメソッドを呼び出した場合、または警告を発生させたメソッドがオブジェクトをラップする IDisposable オブジェクトを返す場合を除き、この規則による警告を抑制しないでください。  
  
## <a name="related-rules"></a>関連規則  
 [CA2213: 破棄可能なフィールドは破棄されなければなりません](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: オブジェクトを複数回破棄しません](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>例  
 破棄可能なオブジェクトを返すメソッドを実装している場合は、catch ブロックのない try/finally ブロックを使用して、そのオブジェクトが確実に破棄されるようにします。 try/finally ブロックを使用することによって、障害点での例外の発生が可能になり、そのオブジェクトが確実に破棄されます。  
  
 OpenPort1 メソッドでは、ISerializable オブジェクトの SerialPort を開くための呼び出し、または SomeMethod の呼び出しが失敗する可能性があります。 この実装では CA2000 警告は発生しません。  
  
 OpenPort2 メソッドでは、次の 2 つの SerialPort オブジェクトが宣言され、null に設定されます。  
  
-   `tempPort`。メソッド操作が成功しているかどうかをテストするのに使用されます。  
  
-   `port`。メソッドの戻り値に使用されます。  
  
 `tempPort` は、`try` ブロックで構築され、開かれます。その他必要な作業も同じ `try` ブロック内で実行されます。 `try` ブロックの最後に、開かれたポートが `port` オブジェクトに割り当てられ、このオブジェクトが返されます。`tempPort` オブジェクトは `null` に設定されます。  
  
 `finally` ブロックは `tempPort` 値をチェックします。 null でない場合、メソッド内の操作は失敗しています。`tempPort` は閉じられ、すべてのリソースが解放されます。 返されるオブジェクトには、メソッド操作が成功した場合、開かれた SerialPort オブジェクトが含まれます。メソッドの操作が失敗した場合は null になります。  
  
 [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>例  
 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] コンパイラは既定ですべての算術演算子のオーバーフローをチェックします。 そのため、いずれかの Visual Basic 算術演算子で <xref:System.OverflowException> がスローされる可能性があります。 これにより、CA2000 のような予期しない規則違反が発生する場合があります。 たとえば、次の CreateReader1 関数では、Visual Basic コンパイラが加算に対するオーバーフロー チェックを実行し、それが例外をスローすると StreamReader が破棄されなくなるので、CA2000 違反が発生します。  
  
 これを修正するには、プロジェクトで Visual Basic コンパイラによるオーバーフロー チェックの実施を無効にするか、または次の CreateReader2 関数のようにコードを変更します。  
  
 オーバーフロー チェックの実施を無効にするには、ソリューション エクスプ ローラーでプロジェクト名を右クリックし をクリックし、**プロパティ**します。 をクリックして**コンパイル**、 をクリックして**詳細コンパイル オプション**、し確認**整数オーバーフローのチェックを解除**します。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IDisposable>   
 [Dispose パターン](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)