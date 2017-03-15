---
title: "CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照できるインターフェイスが、オーバーロードされたメソッドを宣言しています。  
  
## 規則の説明  
 オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。  後続のオーバーロードは、名前にアンダースコア文字 '\_' およびオーバーロードの宣言の順序に対応する整数が付加され、一意の名前に変更されます。  次にメソッドの例を示します。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 これらのメソッドは、次のように COM クライアントに公開されます。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6 COM クライアントは、名前にアンダースコアを含むインターフェイス メソッドを実装できません。  
  
## 違反の修正方法  
 この規則の違反を修正するには、名前が一意になるようにオーバーロードされたメソッドの名前を変更します。  または、COM からインターフェイスを参照できるようにするために、`internal` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `Friend`\) を変更するか、`false` に設定した <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 属性を適用します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反しているインターフェイスと、規則に適合するインターフェイスを次の例に示します。  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## 関連規則  
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 参照  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)