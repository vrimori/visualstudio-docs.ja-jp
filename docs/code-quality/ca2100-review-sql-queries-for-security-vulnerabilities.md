---
title: "CA2100: セキュリティの脆弱性について、SQL クエリを確認してください | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: セキュリティの脆弱性について、SQL クエリを確認してください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドに渡された文字列引数から構築された文字列を使用して <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> プロパティが設定されています。  
  
## 規則の説明  
 この規則では、文字列引数にユーザー入力が含まれていることが想定されています。  ユーザー入力から構築された SQL コマンド文字列には、SQL 注入攻撃に対する脆弱性があります。  SQL 注入攻撃では、基となるデータベースに被害を与える、または不正にアクセスすることを目的に、悪意のあるユーザーがクエリのデザインを変更する入力を行います。  一般的な攻撃方法には、SQL のリテラル文字列区切り文字である単一引用符またはアポストロフィ、SQL コメントを表す 2 つのダッシュ、さらに新しいコマンドが後に続くことを示すセミコロンを挿入する方法などがあります。  ユーザー入力をクエリに含める必要がある場合は、攻撃のリスクを少なくするために、次のいずれかの方法を使用してください。これは有効性のある順に並んでいます。  
  
-   ストアド プロシージャを使用する。  
  
-   パラメーター付きコマンド文字列を使用する。  
  
-   コマンド文字列を構築する前に、ユーザー入力の型と内容を検証する。  
  
 次に示す [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の型は、<xref:System.Data.IDbCommand.CommandText%2A> プロパティを実装するか、文字列引数を使用してプロパティを設定するコンストラクターを提供します。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> および <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> および <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> および <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) と [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> および <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 クエリ文字列を作成するために型の ToString メソッドを明示的または暗黙的に使用すると、この規則に対する違反となることに注意してください。  例を次に示します。  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 悪意のあるユーザーが ToString\(\) メソッドをオーバーライドできるため、この規則に対する違反となります。  
  
 また、ToString が次のように暗黙的に使用されたときにも、この規則に対する違反となります。  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## 違反の修正方法  
 この規則違反を修正するには、パラメーター付きクエリを使用します。  
  
## 警告を抑制する状況  
 コマンド テキストにユーザー入力が含まれない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反しているメソッド `UnsafeQuery` と、パラメーター付きコマンド文字列を使用したことで規則に適合しているメソッド `SaferQuery` を次の例に示します。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## 参照  
 [セキュリティの概要 ](../Topic/Security%20Overview2.md)