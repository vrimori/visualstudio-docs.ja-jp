---
title: "CA2112: セキュリティで保護された型はフィールドを公開してはなりません | Microsoft Docs"
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
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112: セキュリティで保護された型はフィールドを公開してはなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型に、パブリック フィールドが含まれ、[リンク確認要求](../Topic/Link%20Demands.md)で保護されています。  
  
## 規則の説明  
 リンク確認要求で保護されている型のインスタンスに対するアクセス権がコードにある場合、その型のフィールドにアクセスするためにリンク確認要求に適合する必要はありません。  
  
## 違反の修正方法  
 この規則違反を修正するには、フィールドをパブリック以外にし、フィールド データを返すパブリックのプロパティまたはメソッドを追加します。  型に対する LinkDemand セキュリティ チェックで、この型のプロパティおよびメソッドへのアクセス権は保護されます。  ただし、コード アクセス セキュリティはフィールドに適用されません。  
  
## 警告を抑制する状況  
 セキュリティ問題と適切なデザインの観点から、パブリック フィールドをパブリック以外に変更して違反を修正してください。  保護する必要のある情報がフィールドに格納されておらず、フィールドのコンテンツに依存しない場合は、この規則による警告を抑制できます。  
  
## 使用例  
 次の例は、保護されていないフィールドを持つライブラリの型 \(`SecuredTypeWithFields`\)、ライブラリの型のインスタンスを作成し、型を作成するアクセス許可のない型のインスタンスを誤って渡す可能性がある型 \(`Distributor`\)、および型を保護するアクセス許可がないのにインスタンスのフィールドを読み取ることができるアプリケーション コードで構成されます。  
  
 この規則に違反するライブラリのコード例を次に示します。  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## 使用例  
 安全な型を保護するリンク確認要求があるため、アプリケーションでインスタンスを作成できません。  次のクラスを使用すると、安全な型のインスタンスをアプリケーションで取得できます。  
  
 [!CODE [FxCop.Security.LDOnFieldsDistributor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor#1)]  
  
## 使用例  
 次のアプリケーションでは、安全な型のメソッドへのアクセス許可がなくてもコードからフィールドにアクセスできる方法を説明しています。  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Creating an instance of SecuredTypeWithFields.**  
**Secured type fields: 22, 33**  
**Changing secured type's field...**  
**Cached Object fields: 99, 33**   
## 関連規則  
 [CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 参照  
 [リンク確認要求](../Topic/Link%20Demands.md)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)