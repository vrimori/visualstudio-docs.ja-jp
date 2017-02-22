---
title: "CA2132: 既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要 | Microsoft Docs"
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
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132: 既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
> [!NOTE]
>  この警告は、CoreCLR \(Silverlight Web アプリケーションに固有の CLR バージョン\) を実行しているコードにのみ適用されます。  
  
## 原因  
 派生クラスの既定のコンストラクターの透過性属性が、基本クラスの透過性と同程度に重要ではありません。  
  
## 規則の説明  
 <xref:System.Security.SecurityCriticalAttribute> を持つ型やメンバーを Silverlight アプリケーション コードで使用することはできません。  セキュリティが重要な型やメンバーは、.NET Framework for Silverlight クラス ライブラリの信頼されているコードからのみ使用できます。  派生クラスにおけるパブリックな構築または保護された構築の透過性は、基本クラスと同程度以上である必要があるため、アプリケーション内のクラスを、SecurityCritical としてマークされたクラスから派生させることはできません。  
  
 CoreCLR プラットフォーム コードでは、パブリックな、または保護された透過的でない既定のコンストラクターが基本型にある場合、派生型は既定のコンストラクターの継承規則に従う必要があります。  つまり、派生型でも既定のコンストラクターを設定する必要があり、そのコンストラクターは基本型の既定のコンストラクターと同程度以上に重要である必要があります。  
  
## 違反の修正方法  
 この違反を修正するには、型を削除するか、セキュリティ上透過的でない型から派生させないようにします。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しないでください。  アプリケーション コードでこの規則に違反すると、<xref:System.TypeLoadException> が発生し、CoreCLR による型の読み込みが拒否されます。  
  
### コード  
 [!CODE [FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency#1)]  
  
### コメント