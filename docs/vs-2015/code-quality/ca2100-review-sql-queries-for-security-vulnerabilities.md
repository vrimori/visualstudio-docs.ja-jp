---
title: 'Ca 2100: 確認するセキュリティの脆弱性について、SQL クエリ |Microsoft Docs'
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
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c269fe38a50a6d36003bffd65a7884d48c3473a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589672"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: セキュリティの脆弱性について、SQL クエリを確認してください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2100: セキュリティの脆弱性のレビューの SQL クエリ](https://docs.microsoft.com/visualstudio/code-quality/ca2100-review-sql-queries-for-security-vulnerabilities)します。

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドの設定、<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>プロパティ、メソッドに文字列の引数から構築された文字列を使用しています。

## <a name="rule-description"></a>規則の説明
 この規則では、文字列引数にユーザー入力が含まれていることが想定されています。 ユーザー入力から構築された SQL コマンド文字列には、SQL 注入攻撃に対する脆弱性があります。 SQL インジェクション攻撃では、悪意のあるユーザーは、破損または基になるデータベースへの不正アクセスを確保するために、クエリのデザインを変更する入力を提供します。 標準的な方法は、単一引用符またはアポストロフィ、SQL リテラル文字列の区切り記号; の挿入2 つのダッシュは、SQL コメント; ことを示しますセミコロンでは、新しいコマンドが続くことを示します。 攻撃のリスクを軽減する効果の順序で表示されている場合、ユーザー入力は、次のいずれかを使用して、クエリの一部である必要があります。

-   ストアド プロシージャを使用します。

-   パラメーター化されたコマンド文字列を使用します。

-   コマンド文字列をビルドする前に、型とコンテンツの両方のユーザー入力を検証します。

 次[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]型を実装、<xref:System.Data.IDbCommand.CommandText%2A>プロパティまたは文字列引数を使用して、プロパティを設定するコンス トラクターを提供します。

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> および <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> および <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> および <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   [System.Data.SqlServerCe.SqlCeCommand](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) と [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> および <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

 明示的または暗黙的に型の ToString メソッドを使用する場合に、この規則が違反したことに注意してください。 クエリ文字列を作成します。 次に例を示します。

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 悪意のあるユーザーは、ToString() メソッドをオーバーライドできるため、規則に違反します。

 ルールもが破ら ToString を暗黙的に使用するとします。

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、パラメーター化クエリを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 コマンド テキストでユーザー入力が含まれない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、メソッド、 `UnsafeQuery`、ルールと、メソッドに違反する`SaferQuery`、パラメーター化されたコマンド文字列を使用して、ルールを満たします。

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>関連項目
 [セキュリティの概要](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)



