---
title: "CA1019: 属性引数にアクセサーを定義します | Microsoft Docs"
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
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019: 属性引数にアクセサーを定義します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 属性のコンストラクターで、対応するプロパティのない引数が定義されています。  
  
## 規則の説明  
 属性では、対象に適用するときに必ず指定する必須の引数を定義できます。  この引数は、コンストラクターに位置指定パラメーターで属性を指定できるようになるため、位置指定引数とも呼ばれます。  必須のすべての引数について、対応する読み取り専用のプロパティも属性で規定する必要があります。これは、引数値を実行時に取得できるようにするためです。  この規則では、各コンストラクターのパラメーターについて、対応するプロパティが定義されているかどうかを確認します。  
  
 また、属性ではオプションの引数も定義できます。これは名前付き引数とも呼ばれます。  この引数は、名前でコンストラクターに属性を指定するときに使用されます。また、対応する読み取り\/書き込みプロパティが必要です。  
  
 必須の引数でもオプションの引数でも、対応するプロパティとコンストラクターのパラメーターは、同じ名前を使用する必要があります。ただし、大文字と小文字の表記方法は異なります。  プロパティでは Pascal 形式、パラメーターでは Camel 形式の表記方法が使用されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、コンストラクターのパラメーターに読み取り専用プロパティがなければ追加します。  
  
## 警告を抑制する状況  
 必須の引数値を取得できるようにしない場合、この規則からの警告を抑制します。  
  
## カスタム属性の例  
  
### 説明  
 必須の \(位置\) パラメーターが定義された 2 つの属性を次の例に示します。  属性の 1 つ目の実装は、誤って定義されています。  2 つ目の実装は正しく定義されています。  
  
### コード  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## 位置指定引数と名前付き引数  
  
### 説明  
 位置指定引数と名前付き引数は、必須または省略可能な属性の引数をライブラリのコンシューマーに示します。  
  
 次の例は、位置指定引数と名前付き引数の両方を持つ属性の実装を示しています。  
  
### コード  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### コメント  
 次の例は、カスタム属性を 2 つのプロパティに適用する方法を示しています。  
  
### コード  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## 関連規則  
 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 参照  
 [属性](../Topic/Attributes1.md)