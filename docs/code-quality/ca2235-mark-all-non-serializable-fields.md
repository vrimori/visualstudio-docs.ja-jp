---
title: "CA2235: すべてのシリアル化不可能なフィールドを設定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2235: すべてのシリアル化不可能なフィールドを設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。  
  
## 規則の説明  
 シリアル化できる型とは、<xref:System.SerializableAttribute?displayProperty=fullName> 属性でマークされている型です。  型をシリアル化するとき、型にシリアル化できない型のインスタンス フィールドが含まれると、<xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 例外がスローされます。  
  
## 違反の修正方法  
 この規則違反を修正するには、シリアル化できないフィールドに <xref:System.NonSerializedAttribute?displayProperty=fullName> 属性を適用します。  
  
## 警告を抑制する状況  
 フィールドのインスタンスをシリアル化および逆シリアル化できるように <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 型を宣言する場合にのみ、この規則による警告を抑制します。  
  
## 使用例  
 この規則に違反している型と、規則に適合する型を次の例に示します。  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## 関連規則  
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable を正しく実装します](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../Topic/CA2120:%20Secure%20serialization%20constructors.md)