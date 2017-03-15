---
title: "CA1014: アセンブリに CLSCompliantAttribute を設定します | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: アセンブリに CLSCompliantAttribute を設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 アセンブリに、それに適用される <xref:System.CLSCompliantAttribute?displayProperty=fullName> 属性がありません。  
  
## 規則の説明  
 共通言語仕様 \(CLS\) には、名前付けの制約、データ型、および規則が定義されています。アセンブリを複数のプログラミング言語で使用する場合、この仕様に準拠する必要があります。  すべてのアセンブリに <xref:System.CLSCompliantAttribute> を使用して、CLS への準拠を明示することをお勧めします。  この属性が使用されていないアセンブリは、CLS に準拠しません。  
  
 CLS 準拠のアセンブリに、準拠しない型または型のメンバーを含めることもできます。  
  
## 違反の修正方法  
 この規則違反を修正するには、アセンブリにこの属性を追加します。  アセンブリ全体を非準拠とマークするのではなく、準拠していない型または型のメンバーを判断し、その要素にマークします。  可能であれば、準拠していないメンバーを CLS に準拠しているメンバーで置き換え、できるだけ広範囲のユーザーがアセンブリの全機能にアクセスできるようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  アセンブリを仕様準拠にしない場合、この属性を適用し、値を `false` に設定します。  
  
## 使用例  
 CLS 準拠を宣言する <xref:System.CLSCompliantAttribute?displayProperty=fullName> 属性が適用されたアセンブリを次の例に示します。  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## 参照  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)