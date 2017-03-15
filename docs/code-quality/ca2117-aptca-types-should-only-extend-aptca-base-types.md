---
title: "CA2117: APTCA 型は APTCA 基本型のみを拡張することができます | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117: APTCA 型は APTCA 基本型のみを拡張することができます
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 属性を持つアセンブリのパブリック型またはプロテクト型が、属性のないアセンブリで宣言された型から継承されています。  
  
## 規則の説明  
 厳密な名前を持つアセンブリのパブリック型またはプロテクト型は、既定で、完全信頼の[Inheritance Demands](http://msdn.microsoft.com/ja-jp/28b9adbb-8f08-4f10-b856-dbf59eb932d9)によって暗黙的に保護されます。  <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 属性でマークされた厳密な名前のアセンブリには、この保護がありません。  この属性によって継承確認要求が無効になります。  そのため、公開する型は、完全信頼のない型によって継承できるアセンブリで宣言されます。  
  
 APTCA 属性が完全信頼のアセンブリにあり、アセンブリの型が部分信頼の呼び出し元を許可しない型から継承する場合、セキュリティ上の弱点になります。  `T1` と `T2` という 2 つの型が次の条件に適合する場合、悪意のある呼び出し元は、型 `T1` を使用すると、`T2` を保護する暗黙的な完全信頼の継承確認要求を省略できます。  
  
-   `T1` が、APTCA 属性を持つ完全信頼のアセンブリで宣言されたパブリック型である場合。  
  
-   `T1` がアセンブリ外の型 `T2` から継承する場合。  
  
-   `T2` のアセンブリに APTCA 属性がないため、部分信頼のアセンブリの型から継承できない場合。  
  
 部分信頼の型 `X` は、`T1` から継承できます。この場合、`T2` で宣言された継承メンバーにアクセス権が付与されます。  `T2` には APTCA 属性がないため、直接の派生型 \(`T1`\) は、完全信頼の継承確認要求に適合する必要があります。`T1` には完全信頼があるため、このチェックに適合します。  `X` は、信頼されていないサブクラス化から `T2` を保護する継承確認要求の適合に加わっていないため、セキュリティ上のリスクがあります。  そのため、APTCA 属性を持つ型によって、属性を持たない型を拡張しないでください。  
  
 別の、より一般的なセキュリティ問題を紹介します。プログラマのミスが原因で、派生型 \(`T1`\) によって、完全信頼を必要とする型 \(`T2`\) から保護されたメンバーが公開されることがあります。  この問題が発生すると、信頼関係のない呼び出し元が、完全信頼の型のみが使用できるはずの情報にアクセスできるようになります。  
  
## 違反の修正方法  
 この違反がレポートされた型が APTCA 属性を必要としないアセンブリにある場合、削除します。  
  
 APTCA 属性が必要である場合、型に完全信頼の継承確認要求を追加します。  こうすることで、信頼関係のない型による継承を防ぐことができます。  
  
 この違反でレポートされた基本型のアセンブリに APTCA 属性を追加することで、違反を修正することもできます。  アセンブリ内のすべてのコードとそのアセンブリに依存するすべてのコードについて、必ず、徹底的にセキュリティを再確認してから、この方法を使用してください。  
  
## 警告を抑制する状況  
 この規則による警告を安全に抑制するには、破壊的な方法で使用できる重要な情報、操作、またはリソースに信頼関係のない呼び出し元がアクセスすることを、使用している型で公開された保護されたメンバーによって直接的または間接的に許可しないようにします。  
  
## 使用例  
 次の例では、2 つのアセンブリと 1 つのテスト アプリケーションを使用して、この規則で検出されるセキュリティ上の脆弱性を説明します。  1 つ目のアセンブリ \(上記の説明では `T2`\) に APTCA 属性はなく、部分信頼の型からは継承できません。  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## 使用例  
 2 つ目のアセンブリ \(上記の説明では `T1`\) は完全信頼で、部分信頼の呼び出し元を許可しています。  
  
 [!CODE [FxCop.Security.YesAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit#1)]  
  
## 使用例  
 テストの型 \(上記の説明では `X`\) は、部分信頼のアセンブリに含まれます。  
  
 [!CODE [FxCop.Security.TestAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit#1)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Meet at the shady glen 2\/22\/2003 12:00:00 AM\!**  
**From Test: sunny meadow**  
**Meet at the sunny meadow 2\/22\/2003 12:00:00 AM\!**   
## 関連規則  
 [CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)  
  
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/ja-jp/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [部分信頼コードからのライブラリの使用](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/ja-jp/28b9adbb-8f08-4f10-b856-dbf59eb932d9)