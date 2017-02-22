---
title: "CA2147: 透過コードは、セキュリティ アサートを使用してはならない | Microsoft Docs"
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
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2147: 透過コードは、セキュリティ アサートを使用してはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.Security.SecurityTransparentAttribute> とマークされたコードには、アサートに必要なアクセス許可が付与されません。  
  
## 規則の説明  
 この規則では、100% 透過的なアセンブリまたは透過的\/クリティカル混在のアセンブリ内のすべてのメソッドと型を分析し、宣言的または強制的に使用されている <xref:System.Security.CodeAccessPermission.Assert%2A> にフラグを設定します。  
  
 実行時には、透過的なコードから <xref:System.Security.CodeAccessPermission.Assert%2A> を呼び出すと、<xref:System.InvalidOperationException> がスローされます。  この状況は、100% 透過的なアセンブリで発生するだけでなく、透過的\/クリティカル混在のアセンブリでも、メソッドまたは型が透過的と宣言されているにもかかわらず宣言的または強制的な Assert を含んでいる場合に発生することがあります。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 には、*透過性*と呼ばれる機能が導入されました。  メソッド、フィールド、インターフェイス、クラス、および型を個別的に透過的またはクリティカルとすることができます。  
  
 透過的なコードでは、セキュリティ特権を昇格することはできません。  したがって、透過的なコードに付与または要求されるアクセス許可は、自動的にコードを通じて呼び出し元またはホスト アプリケーション ドメインに渡されます。  昇格の例として、Assert、LinkDemand、SuppressUnmanagedCode、`unsafe` コードなどがあります。  
  
## 違反の修正方法  
 この問題を解決するには、Assert を呼び出すコードに対して <xref:System.Security.SecurityCriticalAttribute> を設定するか、Assert を削除します。  
  
## 警告を抑制する状況  
 この規則によるメッセージは抑制しないでください。  
  
## 使用例  
 `SecurityTestClass`  が透過的である場合、`Assert` メソッドが <xref:System.InvalidOperationException> をスローすると、このコードは失敗します。  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## 使用例  
 1 つの方法は、以下の例の SecurityTransparentMethod メソッドのコード レビューを行い、昇格に対して安全であると判断できる場合に、SecurityTransparentMethod メソッドをセキュリティ クリティカルとしてマークすることです。この方法では、メソッドとメソッド内の Assert において発生するすべての呼び出しに対し、詳細で完全なエラーのないセキュリティ監査を実行する必要があります。  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 また、コードから Assert を削除し、後続のファイル I\/O アクセス許可要求が SecurityTransparentMethod を通過して呼び出し元へ到達できるようにする方法もあります。  これにより、セキュリティ チェックが有効になります。  この場合、一般にはセキュリティ監査は必要ありません。アクセス許可要求が呼び出し元またはアプリケーション ドメインに送られるからです。  アクセス許可要求は、セキュリティ ポリシー、ホスト環境、およびコード ソース アクセス許可の付与によって厳密に制御されます。  
  
## 参照  
 [セキュリティの警告](../code-quality/security-warnings.md)