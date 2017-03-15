---
title: "CA2237: ISerializable 型を SerializableAttribute に設定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237: ISerializable 型を SerializableAttribute に設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 外部から参照できる型で、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> インターフェイスを実装していますが、その型は <xref:System.SerializableAttribute?displayProperty=fullName> 属性でマークされていません。  この規則では、基本型がシリアル化できない派生型は無視されます。  
  
## 規則の説明  
 共通言語ランタイムでシリアル化できると認識されるには、型を <xref:System.SerializableAttribute> 属性でマークする必要があります。<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装して、型でカスタムのシリアル化ルーチンを使用している場合でも、マークする必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、型に <xref:System.SerializableAttribute> 属性を適用します。  
  
## 警告を抑制する状況  
 例外クラスの場合、複数のアプリケーション ドメインで正しく機能するように、シリアル化できる必要があるため、この規則による警告を抑制しないでください。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  この規則に適合するには、<xref:System.SerializableAttribute> 属性行をコメントから外します。  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## 関連規則  
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable を正しく実装します](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../Topic/CA2120:%20Secure%20serialization%20constructors.md)