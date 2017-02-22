---
title: "CA1053: スタティック ホルダー型にはコンストラクターを含めません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1053: スタティック ホルダー型にはコンストラクターを含めません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型または入れ子になったパブリック型で、静的なメンバーのみが宣言されています。また、パブリックまたはプロテクトの既定のコンストラクターが含まれます。  
  
## 規則の説明  
 静的メンバーの呼び出しに型のインスタンスは必要ないため、コンストラクターは不要です。  また、この型に静的でないメンバーはないため、インスタンスを作成しても型のメンバーにアクセスできません。  
  
## 違反の修正方法  
 この規則違反を修正するには、既定のコンストラクターを削除するか、コンストラクターをプライベートにします。  
  
> [!NOTE]
>  コンパイラによっては、型にコンストラクターが定義されていないと、自動的にパブリックの既定コンストラクターが作成されます。  この場合、違反を防ぐために、プライベートの既定コンストラクターを追加します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  コンストラクターが存在することで、静的な型ではないことがわかります。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  ソース コードには既定のコンストラクターがないことに注意してください。  このコードをアセンブリにコンパイルすると、C\# コンパイラによって既定のコンストラクターが挿入されます。その結果、この規則に違反します。  違反を修正するには、プライベート コンストラクターを宣言します。  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]