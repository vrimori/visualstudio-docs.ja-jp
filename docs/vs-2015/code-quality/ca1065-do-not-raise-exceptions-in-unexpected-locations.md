---
title: 'Ca 1065: 予期しない場所での例外を発生させないで |Microsoft Docs'
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
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93be7e14bd095fb7f25c7dcce90eba3d724b05f0
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589214"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: 予期しない場所に例外を発生させません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1065: 予期しない場所で例外を発生させないで](https://docs.microsoft.com/visualstudio/code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations)します。

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 例外をスローしないはずのメソッドが例外をスローします。

## <a name="rule-description"></a>規則の説明
 予期しない例外をスローするメソッドは、次のように分類できます。

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

 次に、これらのメソッドについてを説明します。

### <a name="property-get-methods"></a>プロパティの Get メソッド
 プロパティは、基本的にスマート フィールドです。 そのため、できるだけ多くのフィールドのように動作する必要があります。 フィールドは例外をスローしないとプロパティをもする必要があります。 例外をスローするプロパティがある場合は、メソッドにすることを検討してください。

 プロパティの get メソッドからスローされることができるは、次の例外。

-   <xref:System.InvalidOperationException?displayProperty=fullName> すべての派生物 (を含む<xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> すべての派生

-   <xref:System.ArgumentException?displayProperty=fullName> (インデックスが付けられます) からのみ

-   <xref:System.Collections.Generic.KeyNotFoundException> (インデックスが付けられます) からのみ

### <a name="event-accessor-methods"></a>イベントのアクセサー メソッド
 イベント アクセサーには、単純な操作例外をスローしない必要があります。 イベントは、追加、またはイベント ハンドラーを削除しようとするときに例外をスローしません。

 次の例外は、イベント アクセサーからスローされる使用できます。

-   <xref:System.InvalidOperationException?displayProperty=fullName> すべての派生物 (を含む<xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> すべての派生

-   <xref:System.ArgumentException> 派生

### <a name="equals-methods"></a>Equals メソッド
 次**Equals**メソッドが例外をスローする必要があります。

-   <xref:System.Object.Equals%2A?displayProperty=fullName>

-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

 **Equals**メソッドが返す`true`または`false`例外をスローする代わりにします。 たとえば、Equals には、2 つの一致しない型が渡された場合に返す必要がありますだけ`false`スローする代わりに、<xref:System.ArgumentException>します。

### <a name="gethashcode-methods"></a>GetHashCode メソッド
 次**GetHashCode**メソッドは通常は例外をスローしません。

-   <xref:System.Object.GetHashCode%2A>

-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)

 **GetHashCode**値を常に返す必要があります。 それ以外の場合、ハッシュ テーブル内の項目が失われることができます。

 バージョンの**GetHashCode**スローできる引数を受け取る、<xref:System.ArgumentException>します。 ただし、 **Object.GetHashCode**が例外をスローしない必要があります。

### <a name="tostring-methods"></a>ToString メソッド
 デバッガーを使用して<xref:System.Object.ToString%2A?displayProperty=fullName>オブジェクトに関する情報を文字列の形式で表示できるようにします。 そのため、 **ToString**オブジェクトの状態が変わらないようにして、例外をスローする必要があります。

### <a name="static-constructors"></a>静的コンストラクター
 現在のアプリケーション ドメインで使用できない型を静的コンス トラクターから例外をスローします。 (セキュリティ上の問題) などの非常に良好な理由は、静的コンス トラクターから例外がスローされるが必要です。

### <a name="finalizers"></a>ファイナライザー
 プロセスを廃棄する高速で失敗する、CLR は、ファイナライザーから例外をスローします。 そのため、例外のスローをファイナライザーで常に避けてください。

### <a name="dispose-methods"></a>Dispose メソッド
 A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドが例外をスローする必要があります。 Dispose がクリーンアップのロジックの一部として呼び出される多くの場合、`finally`句。 そのため、例外の内部処理を追加するユーザーを強制的に明示的に Dispose から例外がスローされる、`finally`句。

 **Dispose (false)** これはほぼ常にファイナライザーから呼び出されるために、コード パスは、例外をスローしない必要があります。

### <a name="equality-operators--"></a>等値演算子 (= =、! =)
 Equals メソッドと同様に等値演算子が返す`true`または`false`と例外をスローする必要があります。

### <a name="implicit-cast-operators"></a>暗黙的なキャスト演算子
 ユーザーは、多くの場合、暗黙的なキャスト演算子が呼び出されたことに注意してください、ため、暗黙的なキャスト演算子によってスローされる例外はまったく予測できません。 そのため、例外はスローされません暗黙的なキャスト演算子。

## <a name="how-to-fix-violations"></a>違反の修正方法
 プロパティの get アクセス操作子のいずれかが不要になった例外をスローするか、メソッド、プロパティに変更するロジックを変更します。

 すべての他のメソッドの種類前の表に、変更ロジックが不要になったとして例外をスローする必要がありますようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 スローされた例外ではなく例外宣言、違反が発生した場合、この規則による警告を抑制する安全です。

## <a name="related-rules"></a>関連規則
 [CA2219: exception 句に例外を発生させないでください](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>関連項目
 [デザインの警告](../code-quality/design-warnings.md)



