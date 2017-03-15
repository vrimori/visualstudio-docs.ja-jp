---
title: "CA2107: Deny と PermitOnly の用法を再確認します | Microsoft Docs"
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
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: Deny と PermitOnly の用法を再確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドに、PermitOnly または Deny のセキュリティ アクションを指定したセキュリティ チェックが含まれます。  
  
## 規則の説明  
 [Using the PermitOnly Method](http://msdn.microsoft.com/ja-jp/8c7bdb7f-882f-45b7-908c-6cbaa1767649) と <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> のセキュリティ アクションは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のセキュリティについて高度な知識を持っているユーザー以外は使用しないでください。  コードにこのセキュリティ アクションを使用する場合、セキュリティを再確認する必要があります。  
  
 Deny によって、セキュリティ要求に応答して発生するスタック ウォークの既定の動作は変更されます。  これによって、コール スタックの呼び出し元が持つ実際のアクセス許可にかかわらず、拒否するメソッドが存続する間、認めることができないというアクセス許可を指定できるようになります。  スタック ウォークが Deny で保護されたメソッドを検出した場合、および要求されたアクセス許可が拒否されたアクセス許可に含まれる場合、スタック ウォークは失敗します。  PermitOnly でも、スタック ウォークの既定の動作は変更されます。  これで、呼び出し元のアクセス許可にかかわらず、付与することができるアクセス許可のみを指定できるようになります。  スタック ウォークが PermitOnly で保護されたメソッドを検出した場合、および要求されたアクセス許可が PermitOnly で指定されたアクセス許可に含まれていない場合、スタック ウォークは失敗します。  
  
 コードがこれらのアクションに依存している場合、実用性が制限され、動作がわかりづらくなるため、セキュリティ上の脆弱性を慎重に検査する必要があります。  次に例を示します。  
  
-   [リンク確認要求](../Topic/Link%20Demands.md)は、Deny または PermitOnly に影響を受けません。  
  
-   Deny または PermitOnly が、スタック ウォークを実行する要求と同じスタック フレームで発生した場合、セキュリティのアクションによる影響はありません。  
  
-   通常、パスに基づくアクセス許可を構築するときに使用する値を指定するには、複数の方法があります。  あるフォームのパスに対するアクセスを拒否することで、すべてのフォームに対するアクセスが拒否されることはありません。  たとえば、ファイル共有 \\\\Server\\Share がネットワーク ドライブ X: にマップされている場合、その共有上にあるファイルへのアクセスを拒否するには、\\\\Server\\Share\\File、X:\\File など、そのファイルにアクセスするすべてのパスに拒否を設定する必要があります。  
  
-   スタック ウォークが Deny または PermitOnly が検出される前に、<xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> でスタック ウォークを停止できます。  
  
-   Deny による影響がある場合、つまり、呼び出し元が持つアクセス許可が Deny でブロックされる場合、呼び出し元は、Deny を経由せずに、保護されたリソースに直接アクセスできます。  同様に、呼び出し元が拒否されたアクセス許可を持っていない場合、スタック ウォークは Deny がなくても失敗します。  
  
## 違反の修正方法  
 これらのセキュリティ アクションのいずれかを使用すると、違反になります。  違反を修正するには、これらのセキュリティ アクションを使用しないでください。  
  
## 警告を抑制する状況  
 必ずセキュリティの再確認を完了してから、この規則による警告を抑制してください。  
  
## 使用例  
 次の例では、Deny の制限について表しています。  
  
 次のライブラリには、2 つのメソッドを持つクラスが含まれています。これらのメソッドは、保護のセキュリティ要求がある点以外は同じです。  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## 使用例  
 次のアプリケーションは、ライブラリの保護されたメソッドに対して Deny が与える影響の例です。  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Demand: 呼び出し元の Deny は、アサートされたアクセス許可を持つ Demand には影響しません。**  
**LinkDemand: 呼び出し元の Deny は、アサートされたアクセス許可を持つ LinkDemand には影響しません。**  
**LinkDemand: コードを LinkDemand で保護しても、呼び出し元の Deny による影響はありません。**  
**LinkDemand: コードを LinkDemand で保護しても、この Deny による影響はありません。**   
## 参照  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/ja-jp/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/ja-jp/8c7bdb7f-882f-45b7-908c-6cbaa1767649)