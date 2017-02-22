---
title: "CA2105: 配列フィールドは読み取り専用にできません | Microsoft Docs"
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
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2105: 配列フィールドは読み取り専用にできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 配列を含むパブリック フィールドまたはプロテクト フィールドが、読み取り専用と宣言されています。  
  
## 規則の説明  
 配列を含むフィールドに `readonly` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `ReadOnly`\) 修飾子を適用すると、そのフィールドで参照先の配列を変更できません。  ただし、読み取り専用フィールドに格納された配列の要素は変更できます。  パブリックにアクセスできる読み取り専用の配列で、その要素に基づいてコードで条件判断または操作を行うと、セキュリティ上の脆弱性が生じます。  
  
 パブリック フィールドが存在すること自体も、デザイン規則「[CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)」に違反しています。  
  
## 違反の修正方法  
 この規則で特定されるセキュリティ上の脆弱性を修正するには、パブリックにアクセスできる読み取り専用の配列の要素に依存しないようにします。  次の手順のいずれかを実行することを強くお勧めします。  
  
-   変更できない、厳密に型指定されたコレクションで、配列を置換します。  詳細については、「<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>」を参照してください。  
  
-   プライベート配列のクローンを返すメソッドで、パブリック フィールドを置換します。  コードはクローンに依存しないため、要素が変更されても危険はありません。  
  
 2 つ目の方法を選択した場合、フィールドをプロパティで置換しないでください。配列を返すプロパティの場合、パフォーマンスに悪影響を及ぼすことがあります。  詳細については、「[CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)」を参照してください。  
  
## 警告を抑制する状況  
 この規則からは、できるだけ警告を除外しないでください。  読み取り専用フィールドの内容が重要ではない場合はほとんどありません。  読み取り専用フィールドの内容が重要ではない場合、メッセージを除外するのではなく、`readonly` 修飾子を削除します。  
  
## 使用例  
 この規則に違反した場合の危険性について、例を説明します。  最初の部分には、`MyClassWithReadOnlyArrayField` という型のサンプル ライブラリが表示されます。安全ではない 2 つのフィールド \(`grades` と `privateGrades`\) が含まれています。  `grades` フィールドはパブリックであるため、どのような呼び出し元に対しても脆弱性があります。  `privateGrades` フィールドはプライベートですが、`GetPrivateGrades` メソッドで呼び出し元に返されるため、脆弱性があります。  `securePrivateGrades` フィールドは、`GetSecurePrivateGrades` メソッドを使用すると安全な方法で公開されます。  適切なデザイン方法に従って、プライベートと宣言します。  2 つ目の部分には、`grades` メンバーと `privateGrades` メンバーに格納されている値を変更するコードが表示されます。  
  
 サンプルのクラス ライブラリを次に示します。  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## 使用例  
 次のコードでは、サンプルのクラス ライブラリを使用して、読み取り専用の配列が持つセキュリティ問題を表しています。  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 このサンプルによる出力は次のとおりです。  
  
  **変更前: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90**  
**変更後: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90**   
## 参照  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>