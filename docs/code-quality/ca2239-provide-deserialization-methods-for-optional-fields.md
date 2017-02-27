---
title: "CA2239: オプションのフィールドに逆シリアル化メソッドを指定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2239: オプションのフィールドに逆シリアル化メソッドを指定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 型に <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> 属性マークされているフィールドがあり、その型に逆シリアル化のイベント ハンドラー メソッドがありません。  
  
## 規則の説明  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 属性はシリアル化に何も影響を及ぼしません。この属性でマークされたフィールドはシリアル化されます。  ただし、逆シリアル化の場合、フィールドは無視され、その型に関連付けられた既定値を保持します。  逆シリアル化プロセス時にフィールドを設定するには、逆シリアル化のイベント ハンドラーを宣言します。  
  
## 違反の修正方法  
 この規則違反を修正するには、型に逆シリアル化のイベント ハンドラー メソッドを追加します。  
  
## 警告を抑制する状況  
 逆シリアル化プロセスでこのフィールドが無視される場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 オプションのフィールドと逆シリアル化のイベント ハンドラー メソッドのある型を、次の例に示します。  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## 関連規則  
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable を正しく実装します](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../Topic/CA2120:%20Secure%20serialization%20constructors.md)