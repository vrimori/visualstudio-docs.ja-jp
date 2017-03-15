---
title: "CA2122: リンク確認要求で間接的にメソッドを公開しないでください | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: リンク確認要求で間接的にメソッドを公開しないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック メンバーまたはプロテクト メンバーは[リンク確認要求](../Topic/Link%20Demands.md)を含み、セキュリティ チェックを実行しないメンバーから呼び出されています。  
  
## 規則の説明  
 リンク確認要求では、直接の呼び出し元のアクセス許可しかチェックされません。  メンバー `X` によって呼び出し元のセキュリティ要求が作成されず、リンク確認要求によって保護されたコードが呼び出される場合、必要なアクセス許可を持たない呼び出し元でも、`X` を使用して保護されたメンバーにアクセスできます。  
  
## 違反の修正方法  
 リンク確認要求で保護されたメンバーに不正にアクセスできないように、セキュリティの[データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)またはリンク確認要求をメンバーに追加します。  
  
## 警告を抑制する状況  
 この規則による警告を安全に抑制するには、破壊的な方法で使用できる操作またはリソースに対するアクセス権を呼び出し元に付与しないようにします。  
  
## 使用例  
 規則に違反するライブラリと、ライブラリの弱点を説明するアプリケーションを次の例に示します。  サンプル ライブラリには、規則に違反する 2 つのメソッドがあります。  `EnvironmentSetting` メソッドは、環境変数へのアクセスを無制限にするリンク確認要求によって保護されています。  `DomainInformation` メソッドは、`EnvironmentSetting` を呼び出す前に、呼び出し元のセキュリティ要求を作成しません。  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## 使用例  
 次のアプリケーションでは、保護されていないライブラリ メンバーを呼び出します。  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **保護されていないメンバーの値: seattle.corp.contoso.com**   
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [リンク確認要求](../Topic/Link%20Demands.md)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)