---
title: 'CA2100: 確認セキュリティの脆弱性について、SQL クエリ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76e1ed96221242676557011b69e0547144d34ffa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: セキュリティの脆弱性について、SQL クエリを確認してください
|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 メソッドの設定、<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>メソッドに文字列引数から組み込まれている文字列を使用してプロパティです。  
  
## <a name="rule-description"></a>規則の説明  
 この規則では、文字列引数にユーザー入力が含まれていることが想定されています。 ユーザー入力から構築された SQL コマンド文字列には、SQL 注入攻撃に対する脆弱性があります。 SQL インジェクション攻撃では、悪意のあるユーザーは、破損または基になるデータベースに不正なアクセスを試行するクエリのデザインを変更する入力を提供します。 標準的な方法は、一重引用符または、SQL のリテラル文字列区切り記号はアポストロフィの挿入2 つのダッシュは、SQL コメント; のことを示しますセミコロンでは、新しいコマンドが続くことを示します。 ユーザー入力は、次のいずれかを使用して、クエリの一部である必要がある場合は、攻撃のリスクを軽減する効果の順序で一覧表示します。  
  
-   ストアド プロシージャを使用します。  
  
-   パラメーター化コマンド文字列を使用します。  
  
-   コマンド文字列をビルドする前に、ユーザー入力の型とコンテンツの両方を検証します。  
  
 次[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型を実装、<xref:System.Data.IDbCommand.CommandText%2A>プロパティまたは文字列引数を使用して、プロパティを設定するコンス トラクターを提供します。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> および <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> および <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> および <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> および <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 このルールが明示的または暗黙的に型の ToString メソッドを使用する場合に違反したことに注意してください。 クエリ文字列を構築するためにします。 次に例を示します。  
  
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
 コマンド テキストにすべてのユーザー入力が含まれていない場合は、この規則による警告を抑制するのには安全です。  
  
## <a name="example"></a>例  
 次の例では、メソッド、 `UnsafeQuery`、ルールと、メソッドに違反する`SaferQuery`、パラメーター化コマンド文字列を使用して、ルールを満たします。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## <a name="see-also"></a>関連項目  
 [セキュリティの概要](/dotnet/framework/data/adonet/security-overview)