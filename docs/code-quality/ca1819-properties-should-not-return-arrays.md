---
title: "CA1819: プロパティは、配列を返すことはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1819: プロパティは、配列を返すことはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型のパブリック プロパティまたはプロテクト プロパティで、配列を返しています。  
  
## 規則の説明  
 プロパティが読み取り専用であっても、プロパティで返される配列は書き込みから保護されません。  配列の改ざんを防ぐには、プロパティで配列のコピーを返す必要があります。  一般に、このようなプロパティを呼び出すときのパフォーマンス低下は理解されません。  具体的には、インデックス付きプロパティとして、プロパティを使用する場合があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、プロパティをメソッドにするか、またはコレクションを返すようにプロパティを変更します。  
  
## 警告を抑制する状況  
 属性には、配列を返すプロパティを含めることはできますが、コレクションを返すプロパティを含めることはできません。  [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True) クラスから派生した属性のプロパティに対して発生した警告を抑制できます。  それ以外の場合、この規則による警告は抑制しないでください。  
  
## 違反例  
  
### 説明  
 この規則に違反するプロパティを次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### コメント  
 この規則違反を修正するには、プロパティをメソッドにするか、または配列ではなくコレクションを返すようにプロパティを変更します。  
  
## プロパティをメソッドに変更する例  
  
### 説明  
 プロパティをメソッドに変更することによって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## コレクションを返す例  
  
### 説明  
 以下のコレクションを返すようにプロパティを変更することによって上記の違反を修正するコード例を次に示します。  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### コード  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## ユーザーによるプロパティの修正を許可する  
  
### 説明  
 クラスのコンシューマーがプロパティを修正できるように設定できます。  この規則に違反する読み取り\/書き込みプロパティを次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### コメント  
 <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName> を返すようにプロパティを変更することによって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## 関連規則  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)