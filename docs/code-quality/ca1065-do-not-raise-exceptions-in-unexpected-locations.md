---
title: "Ca 1065: 予期しない場所に例外を発生させません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3511778536bb9664726fc9a61b4773c209a0fd46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: 予期しない場所に例外を発生させません
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 例外をスローしないはずのメソッドが例外をスローします。  
  
## <a name="rule-description"></a>規則の説明  
 予期しない例外をスローするメソッドに次のように分類できます。  
  
-   プロパティの Get メソッド  
  
-   イベントのアクセサー メソッド  
  
-   Equals メソッド  
  
-   GetHashCode メソッド  
  
-   ToString メソッド  
  
-   静的コンストラクター  
  
-   ファイナライザー  
  
-   Dispose メソッド  
  
-   等値演算子  
  
-   暗黙的なキャスト演算子  
  
 次のセクションでは、これらのメソッドの型について説明します。  
  
### <a name="property-get-methods"></a>プロパティの Get メソッド  
 プロパティは、基本的にはスマート フィールドです。 そのため、できるだけ多くのフィールドのように動作する必要があります。 フィールドは、例外をスローしないでし、もプロパティ必要があります。 例外をスローするプロパティがある場合は、メソッドにすることを検討します。  
  
 プロパティの get メソッドからスローされることができるは、次の例外。  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>すべての派生 (含む<xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>すべての派生  
  
-   <xref:System.ArgumentException?displayProperty=fullName>(インデックス付きの get) からのみ  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>(インデックス付きの get) からのみ  
  
### <a name="event-accessor-methods"></a>イベントのアクセサー メソッド  
 イベント アクセサーは、例外をスローしない単純な操作をする必要があります。 イベントを追加またはイベント ハンドラーを削除しようとすると例外をスローする必要があります。  
  
 イベント アクセサーからスローされることができるは、次の例外。  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>すべての派生 (含む<xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>すべての派生  
  
-   <xref:System.ArgumentException>派生  
  
### <a name="equals-methods"></a>Equals メソッド  
 次**Equals**メソッドが例外をスローする必要があります。  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Equals**メソッドが返す`true`または`false`例外をスローする代わりにします。 たとえば、Equals には、次の 2 つの一致しない型が渡された場合に返す必要がありますだけ`false`スローする代わりに、<xref:System.ArgumentException>です。  
  
### <a name="gethashcode-methods"></a>GetHashCode メソッド  
 次**GetHashCode**メソッドは通常例外をスローしません。  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode**は常に値を返します。 それ以外の場合、ハッシュ テーブル内の項目が失われることができます。  
  
 バージョンの**GetHashCode**引数を生成する可能性を受け取る、<xref:System.ArgumentException>です。 ただし、 **Object.GetHashCode**が例外をスローしない必要があります。  
  
### <a name="tostring-methods"></a>ToString メソッド  
 デバッガーを使用して<xref:System.Object.ToString%2A?displayProperty=fullName>文字列の形式でのオブジェクトに関する情報を表示できるようにします。 したがって、 **ToString**オブジェクトの状態が変わらないようにして、例外をスローする必要があります。  
  
### <a name="static-constructors"></a>静的コンストラクター  
 現在のアプリケーション ドメインで使用できない型を静的コンス トラクターから例外をスローします。 (セキュリティ上の問題) などの明確な理由は、静的コンス トラクターから例外をスローしないが必要です。  
  
### <a name="finalizers"></a>ファイナライザー  
 ファイナライザーから例外をスローして、プロセスをダウン廃棄する CLR が高速、エラーが発生します。 そのため、ファイナライザーで例外のスロー常に避けてください。  
  
### <a name="dispose-methods"></a>Dispose メソッド  
 A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドが例外をスローする必要があります。 Dispose がクリーンアップのロジックの一部として呼び出される多くの場合、`finally`句。 そのため、例外の内部処理を追加するユーザー強制的に明示的に破棄から例外をスロー、`finally`句。  
  
 **Dispose (false)**ファイナライザーから呼び出されるほとんどの場合このため、コード パスは例外をスローしない必要があります。  
  
### <a name="equality-operators--"></a>等値演算子 (= =、! =)  
 Equals メソッドのように等値演算子返す必要がありますか`true`または`false`し、例外をスローする必要があります。  
  
### <a name="implicit-cast-operators"></a>暗黙的なキャスト演算子  
 ユーザーは、多くの場合、暗黙的なキャスト演算子が呼び出されたことに注意してくださいはであるため、暗黙的なキャスト演算子によってスローされる例外はまったく予測不可能です。 そのため、例外がスローされますなしの暗黙的なキャスト演算子から。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 プロパティ get アクセス操作子のいずれかされが不要になった例外をスローまたはメソッドに、プロパティを変更するロジックを変更します。  
  
 すべての他のメソッドの型の前の表が不要になったとして例外をスローする必要がありますようにロジックを変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 スローされた例外ではなく例外宣言によって、違反が発生した場合は、この規則による警告を抑制するのには安全です。  
  
## <a name="related-rules"></a>関連規則  
 [CA2219: exception 句に例外を発生させないでください](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## <a name="see-also"></a>関連項目  
 [デザインの警告](../code-quality/design-warnings.md)