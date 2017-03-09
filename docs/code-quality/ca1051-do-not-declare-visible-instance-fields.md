---
title: "CA1051: 参照できるインスタンス フィールドを宣言しないでください | Microsoft Docs"
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
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: 参照できるインスタンス フィールドを宣言しないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照できる型に、外部から参照できるインスタンス フィールドがあります。  
  
## 規則の説明  
 フィールドの主な用途は、実装の詳細にする必要があります。  フィールドは `private` または `internal` にし、プロパティによって公開するようにします。  プロパティのアクセス方法はフィールドの場合と同様に簡単です。また、プロパティのアクセサーでは、互換性に影響を与えずに型の機能が拡張されるため、コードで変更できます。  プライベート フィールドまたは内部フィールドの値を返すだけのプロパティは、フィールドにアクセスする場合と同様に、簡単に実行できます。外部から参照できるフィールドを使用することで、プロパティの場合よりもパフォーマンスが向上することはほとんどありません。  
  
 外部から参照できるフィールドとは、`public`、`protected`、および `protected internal` \(Visual Basic では `Public`、`Protected`、および `Protected Friend`\) のアクセシビリティ レベルが指定されたフィールドです。  
  
## 違反の修正方法  
 この規則違反を修正するには、フィールドを `private` または `internal` にするか、外部から参照できるプロパティを使用して公開します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  外部から参照できるフィールドの利点のすべては、プロパティでも実現できます。  さらに、パブリック フィールドは[リンク確認要求](../Topic/Link%20Demands.md)で保護されません。  「[CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)」を参照してください。  
  
## 使用例  
 この規則に違反する型 \(`BadPublicInstanceFields`\) を次の例に示します。  `GoodPublicInstanceFields` は、修正後のコードを示します。  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## 関連規則  
 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## 参照  
 [リンク確認要求](../Topic/Link%20Demands.md)