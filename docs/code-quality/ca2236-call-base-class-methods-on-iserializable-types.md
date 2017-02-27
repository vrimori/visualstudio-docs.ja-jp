---
title: "CA2236: ISerializable 型で基本クラス メソッドを呼び出します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2236: ISerializable 型で基本クラス メソッドを呼び出します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> インターフェイスを実装している型から別の型が派生し、次の条件のいずれかに該当します。  
  
-   型でシリアル化コンストラクター \(つまり、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> を持つコンストラクター\) である <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> パラメーター シグネチャを実装していますが、基本型の同期化コンストラクターを呼び出していません。  
  
-   型で <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> メソッドを実装していますが、基本型の <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドを呼び出していません。  
  
## 規則の説明  
 カスタムのシリアル化プロセスでは、型でフィールドをシリアル化するには <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドを実装し、フィールドを逆シリアル化するにはシリアル化コンストラクターを実装します。  その型が <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する型から派生する場合、基本型の <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドとシリアル化コンストラクターを呼び出して、基本型のフィールドのシリアル化\/逆シリアル化を行う必要があります。  そうしないと、型のシリアル化\/逆シリアル化が正しく行われません。  派生型で新しいフィールドを追加しない場合、型で <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドやシリアル化コンストラクターを実装したり、基本型で対応するメソッドやシリアル化コンストラクターを呼び出す必要はありません。  
  
## 違反の修正方法  
 この規則違反を修正するには、基本型の <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドまたはシリアル化コンストラクターを、対応する派生型のメソッドまたはコンストラクターから呼び出します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例は、基本クラスのシリアル化コンストラクターと <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドを呼び出すことでこの規則に適合する派生型を示します。  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## 関連規則  
 [CA2240: ISerializable を正しく実装します](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../Topic/CA2120:%20Secure%20serialization%20constructors.md)